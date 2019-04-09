---
title: Linux 上の使用量と SQL Server 用の診断データ コレクションの構成 |Microsoft Docs
description: SQL Server の顧客の使用状況データと診断データが収集および Linux 上の設定方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: c94023e89dbdfb784f2b1bc8db8c9842c4455fb1
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59243606"
---
# <a name="configure-usage-and-diagnostic-data-collection-for-sql-server-on-linux"></a>Linux 上の使用量と SQL Server 用の診断データ コレクションを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Microsoft SQL Server は既定で、お客様のアプリケーションの使用状態に関する情報を収集します。 具体的には、SQL Server はインストール エクスペリエンス、利用状況、およびパフォーマンスに関する情報を収集します。 この情報は、Microsoft が製品の向上を図り、お客様のニーズをさらに満たすのに役立ちます。 たとえば Microsoft では、お客様が受け取るエラー コードの種類に関する情報を収集して、関連するバグの修正、SQL Server の使用方法に関するドキュメントの改善、より良いサービスのために製品に機能を追加すべきかどうかの判断を行います。

このドキュメントではどのような種類の情報を収集および送信を収集する Linux 上の Microsoft SQL Server を構成する方法についての詳細情報を Microsoft にします。 SQL Server 2017 には、ユーザーから収集することはできませんし、どのような情報を説明するプライバシーに関する声明が含まれています。 詳細については、次を参照してください。、[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=868444)します。

具体的には、Microsoft はこのメカニズムでは次の種類の情報は送信しません。

- ユーザー テーブル内からのすべての値
- すべてのログオン資格情報またはその他の認証情報
- 個人を特定できる情報 (PII)

SQL Server 2017 は、インストール エクスペリエンスに関する情報をセットアップ時点から常に収集および送信して、お客様側で発生しているインストールの問題をすばやく発見し修正できるようにします。 SQL Server 2017 にを介して Microsoft に (サーバーのインスタンスごと) に関する情報を送信しないように構成できます**mssql conf**します。 mssql conf は、Red Hat Enterprise Linux、SUSE Linux Enterprise Server、および Ubuntu 用 SQL Server 2017 をインストールする構成スクリプトです。

> [!NOTE]
> Microsoft への情報送信を無効にできるのは、有料版の SQL Server のみです。

## <a name="disable-usage-and-diagnostic-data-collection"></a>使用状況と診断データの収集を無効にします。

このオプションを使用して、SQL Server が送信する場合使用状況と診断データの収集を Microsoft にかどうかを変更できます。 既定では、この値を設定を true にします。 値を変更するには、次のコマンドを実行します。

> [!IMPORTANT]
> いないオフにできます使用状況と診断データの収集を無料の SQL Server、Express、および Developer エディション。

### <a name="on-red-hat-suse-and-ubuntu"></a>Red Hat、SUSE、Ubuntu 上

1. Mssql conf スクリプトをルートとして実行、**設定**コマンドを**telemetry.customerfeedback**します。 指定することで、次の例が使用状況と診断データの収集をオフに**false**します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Docker で
使用状況と docker での診断データの収集を無効にするには Docker が必要[のデータを保存](sql-server-linux-configure-docker.md)します。 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. 追加、 `mssql.conf` 、行を含むファイル`[telemetry]`と`customerfeedback = false`ホスト ディレクトリ。
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. コンテナー イメージを実行します。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. 追加、 `mssql.conf` 、行を含むファイル`[telemetry]`と`customerfeedback = false`ホスト ディレクトリ。

   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. コンテナー イメージを実行します。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

::: moniker-end

## <a name="local-audit-for-sql-server-on-linux-usage-and-diagnostic-data-collection"></a>SQL Server on Linux の使用状況と診断データ コレクションの local Audit

Microsoft SQL Server 2017 を収集し、コンピューターやデバイス (以下「標準的なコンピューター情報」) に関する情報を Microsoft に送信するインターネット対応機能にはが含まれています。 SQL Server の使用状況と診断データ収集の Local Audit コンポーネントは、Microsoft に送信されるデータ (ログ) を表す、指定されたフォルダーに、サービスによって収集されたデータを記述できます。 Local Audit の目的は、Microsoft がこの機能で収集するすべてのデータをユーザーがコンプライアンス、法規制、またはプライバシーの検証目的で確認できるようにすることです。

Linux 上の SQL server では Local Audit は SQL Server データベース エンジンのインスタンス レベルで構成できます。 他の SQL Server コンポーネントおよび SQL Server ツールの使用状況と診断データ コレクションの Local Audit 機能はありません。

### <a name="enable-local-audit"></a>Local Audit を有効にします。

このオプション Local Audit を有効にし、ローカルの監査ログが作成されるディレクトリを設定することができます。

1. 新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例では、作成、新しい**tmp/監査**ディレクトリ。

   ```bash
   sudo mkdir /tmp/audit
   ```

2. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

3. Mssql conf スクリプトをルートとして実行、**設定**コマンドを**telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

4. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Docker で
Docker で Local Audit を有効にするには Docker が必要[のデータを保存](sql-server-linux-configure-docker.md)します。 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. 新しいローカルの監査ログのターゲット ディレクトリは、コンテナーになります。 コンピューターにホスト ディレクトリに新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例では、作成、新しい **/監査**ディレクトリ。

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. 追加、 `mssql.conf` 、行を含むファイル`[telemetry]`と`userrequestedlocalauditdirectory = <host directory>/audit`ホスト ディレクトリ。
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. コンテナー イメージを実行します。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. 新しいローカルの監査ログのターゲット ディレクトリは、コンテナーになります。 コンピューターにホスト ディレクトリに新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例では、作成、新しい **/監査**ディレクトリ。

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. 追加、 `mssql.conf` 、行を含むファイル`[telemetry]`と`userrequestedlocalauditdirectory = <host directory>/audit`ホスト ディレクトリ。
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. コンテナー イメージを実行します。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

::: moniker-end

## <a name="next-steps"></a>次のステップ

Linux 上の SQL Server に関する詳細については、次を参照してください。、 [Linux に SQL Server の概要](sql-server-linux-overview.md)します。
