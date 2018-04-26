---
title: Linux での SQL Server カスタマー フィードバック |Microsoft ドキュメント
description: SQL Server カスタマー フィードバックの収集方法と Linux のように構成する方法について説明します。
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 0cc16f093a04876a07cbc4566138861f268453ba
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="customer-feedback-for-sql-server-on-linux"></a>Linux での SQL Server カスタマー フィードバック

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Microsoft SQL Server は既定で、お客様のアプリケーションの使用状態に関する情報を収集します。 具体的には、SQL Server はインストール エクスペリエンス、利用状況、およびパフォーマンスに関する情報を収集します。 この情報は、Microsoft が製品の向上を図り、お客様のニーズをさらに満たすのに役立ちます。 たとえば Microsoft では、お客様が受け取るエラー コードの種類に関する情報を収集して、関連するバグの修正、SQL Server の使用方法に関するドキュメントの改善、より良いサービスのために製品に機能を追加すべきかどうかの判断を行います。

このドキュメントではどのような種類の情報が収集および送信を収集する Linux の Microsoft SQL Server を構成する方法に関する詳細情報がマイクロソフトにします。 SQL Server 2017 には、お行い、ユーザーから収集することはありませんは、どのような情報を説明するプライバシーに関する声明が含まれています。 プライバシーに関する声明をお読みください。

具体的には、Microsoft はこのメカニズムでは次の種類の情報は送信しません。

- ユーザー テーブル内からのすべての値
- すべてのログオン資格情報またはその他の認証情報
- 個人を特定できる情報 (PII)

SQL Server 2017 は、インストール エクスペリエンスに関する情報をセットアップ時点から常に収集および送信して、お客様側で発生しているインストールの問題をすばやく発見し修正できるようにします。 SQL Server 2017 されません (サーバー インスタンスごと) に関する情報を Microsoft に送信を構成できます**mssql conf**です。 mssql conf は、Red Hat Enterprise Linux、SUSE Linux Enterprise Server、および Ubuntu Server 2017 年 SQL と共にインストールされる構成スクリプトを示します。

> [!NOTE]
> Microsoft への情報送信を無効にできるのは、有料版の SQL Server のみです。

## <a name="disable-customer-feedback"></a>お客様のフィードバックを無効にします。

このオプションを使用して、か、SQL Server が Microsoft にフィードバックを送信する場合に変更できます。 既定では、この設定は true に設定します。 値を変更するには、次のコマンドを実行します。

### <a name="on-red-hat-suse-and-ubuntu"></a>Red Hat、SUSE、Ubuntu で

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**telemetry.customerfeedback**です。 指定して、次の例がお客様のフィードバックをオフに**false**です。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Docker で
Docker でお客様のフィードバックを無効にする必要があります Docker [、データを永続化](sql-server-linux-configure-docker.md)です。 

1. 追加、`mssql.conf`の行を含むファイル`[telemetry]`と`customerfeedback = false`ホスト ディレクトリ。
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```
2. コンテナー イメージを実行します。
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```
   
## <a name="local-audit-for-sql-server-on-linux-usage-feedback-collection"></a>ローカルの監査 for SQL Server on Linux の使用状況のフィードバックの収集

Microsoft SQL Server 2017 には収集し、コンピューターやデバイス (以下「標準的なコンピューター情報」) に関する情報をマイクロソフトに送信するインターネット対応機能にはが含まれています。 SQL Server の使用状況に関するフィードバックのコレクションのローカルの監査コンポーネントは、Microsoft に送信されるデータ (ログ) を表す、指定したフォルダに、サービスによって収集されたデータを記述できます。 Local Audit の目的は、Microsoft がこの機能で収集するすべてのデータをユーザーがコンプライアンス、法規制、またはプライバシーの検証目的で確認できるようにすることです。

Linux 上の SQL server ではローカルの監査は SQL Server データベース エンジンのインスタンス レベルで構成できます。 他の SQL Server コンポーネントおよび SQL Server ツールには、使用状況のフィードバックの収集のローカルの監査機能はありません。

### <a name="enable-local-audit"></a>ローカルの監査を有効にします。

このオプションは、ローカルの監査を有効にし、ローカルの監査ログが作成される場所にディレクトリを設定することができます。

1. 新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/監査**ディレクトリ。

   ```bash
   sudo mkdir /tmp/audit
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Docker で
Docker でローカルの監査を有効にする必要があります Docker [、データを永続化](sql-server-linux-configure-docker.md)です。 

1. 新しいローカルの監査ログのターゲット ディレクトリをコンテナーになります。 コンピューターにホスト ディレクトリ内には、新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例は、新しい作成**監査/** ディレクトリ。

   ```bash
   sudo mkdir <host directory>/audit
   ```

   
1. 追加、`mssql.conf`の行を含むファイル`[telemetry]`と`userrequestedlocalauditdirectory = <host directory>/audit`ホスト ディレクトリ。
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```
2. コンテナー イメージを実行します。
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
   ```
   
## <a name="next-steps"></a>次の手順

Linux 上の SQL Server に関する詳細については、次を参照してください。、 [Linux に SQL Server の概要](sql-server-linux-overview.md)です。
