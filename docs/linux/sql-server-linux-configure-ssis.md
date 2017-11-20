---
title: "Ssis conf と Linux の SSIS を構成する |Microsoft ドキュメント"
description: "この記事では、ssis conf ユーティリティを使用して Linux 上の SQL Server Integration Services (SSIS) を構成する方法について説明します。"
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 2e738f1d8088a974e698a0787370f34216c254a4
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Ssis conf で Linux 上の SQL Server Integration Services を構成します。

実行する、 `ssis-conf` Red Hat Enterprise Linux および Ubuntu 用 SQL Server Integration Services (SSIS) をインストールすると、構成スクリプト。 このユーティリティを使用するには、次のプロパティを構成します。

| Command | Description |
|-------------|---------------------------------------------------------------------|
| セット エディション | SQL Server のエディションを設定します。                                       |
| 製品利用統計情報   | 有効にするにまたは SQL Server Integration Services 製品利用統計情報サービスを無効にします。 |
| セットアップ       | Microsoft SQL Server Integration Services の初期化し、セットアップ      |
|||

## <a name="run-ssis-conf"></a>Ssis conf を実行します。

例を実行するこの記事では、`ssis-conf`完全なパスを指定することによって:`/opt/ssis/bin/ssis-conf`です。 実行する前に、その場所に移動すると`ssis-conf`、ユーティリティを実行するには、現在のディレクトリのコンテキストで:`./ssis-conf`です。

ルートの権限を持つこの記事で説明されているコマンドを実行することを確認します。 たとえば、実行`sudo /opt/ssis/bin/ssis-conf setup`および not`/opt/ssis/bin/ssis-conf setup`です。

を使用する言語のプロンプトをこれらのコマンドを実行するには、ロケールを指定します。 たとえば、中国語でメッセージを受信する、次のコマンドを実行します。`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`です。

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>セット エディションを使用して、SQL Server Integration Services のエディションを設定するには

SSIS のエディションは、SQL Server のエディションに揃えられます。

次のコマンドを入力してください:`$ sudo /opt/ssis/bin/ssis-conf set-edition`です。

コマンドを入力すると、次のプロンプトをお送りします。

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409.

Use of PAID editions of this software requires separate licensing through a Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate number of licenses in place to install and run this software.

Enter your edition (1-8):
```

1 ~ 7 に値を入力する場合、システムは、無料または有料のエディションを構成します。 8 を入力する場合、ユーティリティでは、購入したプロダクト キーを入力するように求められます。

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>製品利用統計情報を使用して、お客様のフィードバックを構成するには

`telemetry`コマンドでは、SSIS は、フィードバックを Microsoft に送信するかどうかを判断します。

無償のエディション (つまり、Express、Developer、および Evaluation edition)、製品利用統計情報サービスは常に有効にします。 無償のエディションがある場合は使用できません、`telemetry`テレメトリを無効にするコマンド。

次のコマンドを入力してください:`$ sudo /opt/ssis/bin/ssis-conf telemetry`です。

支払いのエディションで、コマンドを入力した後と、次の次のプロンプトが表示されます。

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

選択した場合**はい**、製品利用統計情報サービスを有効にして実行を開始します。 サービスは、各起動後に自動的に開始します。 選択した場合**いいえ**、製品利用統計情報サービスが停止し、無効になっています。

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>セットアップを使用して初期化し、Microsoft SQL Server Integration Services セットアップ

使用して、 `setup` SSIS をインストールするたびにコマンドします。

次のコマンドを入力してください:`sudo /opt/ssis/bin/ssis-conf setup`です。

ユーティリティでは、確認したり、次の項目の値を指定するように求められます。
-   製品のライセンス
-   使用許諾契約書
-   製品利用統計情報サービス
-   Integration Services で使用される言語

実行する、`setup`コマンドを使用して、言語のプロンプトを必要に応じて、ロケールを指定することができます。 たとえば、中国語でメッセージを受信する、次のコマンドを実行します。`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`です。

## <a name="ssisconf-format"></a>ssis.conf 形式

次`/var/opt/ssis/ssis.conf`ファイルは、各設定の例を示します。

For SQL Server 内の値を変更することによってシステムの設定を変更することができます、`mssql.conf`ファイル。 For SSIS、する*できません*内の値を変更することによってシステムの設定を変更、`ssis.conf`ファイル。 `ssis.conf`ファイルは、セットアップの結果のみを示しています。 SSIS の設定を変更する場合は、削除、`ssis.conf`ファイル実行して、`setup`もう一度コマンドします。

サンプルを次に示します`ssis.conf`ファイル。 各フィールドは、1 つのセットアップ手順の結果に対応します。

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```

