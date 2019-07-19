---
title: Linux で ssis conf と SSIS を構成します。
description: この記事では、ssis conf ユーティリティを使用した Linux 上の SQL Server Integration Services (SSIS) を構成する方法について説明します。
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 51dc2ba27e346dea75f1bd347491d4932695fd43
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077532"
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Ssis conf で Linux 上の SQL Server Integration Services を構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

実行する、 `ssis-conf` Red Hat Enterprise Linux と Ubuntu 用 SQL Server Integration Services (SSIS) をインストールするときに、構成スクリプト。 SSIS をインストールする方法の詳細については、次を参照してください。[インストール SQL Server Integration Services (SSIS) on Linux](sql-server-linux-setup-ssis.md)します。

使用することも、`ssis-conf`ユーティリティは、次のプロパティを構成します。

| コマンド | 説明 |
|-------------|---------------------------------------------------------------------|
| set-edition | SQL Server のエディションを設定します。                                       |
| 製品利用統計情報   | 有効にするか、SQL Server Integration Services の製品利用統計情報サービスを無効にします。 |
| セットアップ       | Microsoft SQL Server Integration Services の初期化し、セットアップ      |
|||

## <a name="run-ssis-conf"></a>Ssis conf を実行します。

例を実行するこの記事では、`ssis-conf`の完全なパスを指定することによって:`/opt/ssis/bin/ssis-conf`します。 実行する前に、その場所に移動すると`ssis-conf`、ユーティリティを実行するには、現在のディレクトリのコンテキストで:`./ssis-conf`します。

ルート権限では、この記事で説明されているコマンドを実行してください。 たとえば、実行`sudo /opt/ssis/bin/ssis-conf setup`なく`/opt/ssis/bin/ssis-conf setup`します。

を使用する言語のプロンプトでこれらのコマンドを実行するには、ロケールを指定できます。 たとえば、中国語では、画面の指示を受信するに次のコマンドを実行します。`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`します。

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>セット edition を使用して、SQL Server Integration Services のエディションを設定するには

SSIS のエディションは、SQL Server のエディションに揃えられます。

次のコマンドを入力します:`$ sudo /opt/ssis/bin/ssis-conf set-edition`します。

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

1 から 7 に値を入力すると、システムは、無料または有料エディションを構成します。 8 を入力すると、ユーティリティでは、購入したプロダクト キーを入力するように求められます。

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>製品利用統計情報を使用して、お客様のフィードバックを構成するには

`telemetry`コマンドは、SSIS が Microsoft にフィードバックを送信するかどうかを判断します。

無料エディション (つまり、Express、Developer、および Evaluation エディション) では、テレメトリ サービスは常に有効にします。 無償のエディションがある場合は使用できません、`telemetry`テレメトリを無効にするコマンド。

次のコマンドを入力します:`$ sudo /opt/ssis/bin/ssis-conf telemetry`します。

有料エディションで、コマンドを入力した後と、次の次のプロンプトが送信されます。

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

選択した場合**はい**、製品利用統計情報サービスが有効になり、実行が開始されます。 サービスは、各起動後に自動的に開始します。 選択した場合**いいえ**、製品利用統計情報サービスが停止し、無効になっています。

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>セットアップを使用して初期化し、Microsoft SQL Server Integration Services のセットアップ

使用して、 `setup` SSIS をインストールするたびにコマンドします。

次のコマンドを入力します:`sudo /opt/ssis/bin/ssis-conf setup`します。

ユーティリティでは、承認、または、次の項目の値を指定するように求められます。
-   製品のライセンス
-   使用許諾契約書
-   製品利用統計情報サービス
-   Integration Services で使用される言語

実行する、`setup`言語でのプロンプトでコマンドを必要に応じて、ロケールを指定することができます。 たとえば、中国語では、画面の指示を受信するに次のコマンドを実行します。`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`します。

## <a name="ssisconf-format"></a>ssis.conf 形式

次`/var/opt/ssis/ssis.conf`ファイルは、各設定の例を示します。

For SQL Server を内の値を変更することでシステム設定を変更することができます、`mssql.conf`ファイル。 SSIS でのする*できません*内の値を変更することでシステム設定を変更、`ssis.conf`ファイル。 `ssis.conf`ファイルは、セットアップの結果のみを示しています。 SSIS の設定を変更する場合は、削除、`ssis.conf`実行ファイルを開き、`setup`コマンドを再実行します。

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

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS に関する関連コンテンツ
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [制限事項と Linux での SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
-   [スケジュールの SQL Server Integration Services パッケージ cron を使用した Linux 上の実行](sql-server-linux-schedule-ssis-packages.md)
