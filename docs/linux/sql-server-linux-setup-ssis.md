---
title: Linux 上の SQL Server Integration Services のインストール |Microsoft Docs
description: この記事では、Linux に SQL Server Integration Services (SSIS) をインストールする方法について説明します。
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: c9d18e948a415a1d549c21a7c78e0117c6ab819c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602500"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Linux 上の SQL Server Integration Services (SSIS) のインストールします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Integration Services をインストールするには、この記事の手順に従います (`mssql-server-is`) Linux 上。 Linux Integration Services のこのリリースでサポートされる機能については、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)します。

お使いのプラットフォームには、SQL Server の統合サーバーをインストールします。

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Ubuntu での SSIS をインストールします。
インストールする、 `mssql-server-is` Ubuntu 上でパッケージ化、これらの手順に従います。

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Microsoft SQL Server の Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. SQL Server Integration Services をインストールするには、次のコマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Integration Services をインストールすると、実行`ssis-conf`します。 詳細については、次を参照してください。 [ssis conf を使った Linux 上の SSIS の構成](sql-server-linux-configure-ssis.md)します。

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. 構成が完了すると、パスを設定します。

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>SSIS を更新します。
既にある場合`mssql-server-is`インストールされている場合、次のように、次のコマンドで最新バージョンに更新できます。

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>SSIS を削除します。
削除する`mssql-server-is`、次のコマンドを実行することができます。
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> RHEL での SSIS をインストールします。
インストールする、 `mssql-server-is` RHEL でパッケージ化、これらの手順に従います。

1. Microsoft SQL Server の Red Hat のリポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. SQL Server Integration Services をインストールするには、次のコマンドを実行します。

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. インストール後に、実行`ssis-conf`します。 詳細については、次を参照してください。 [ssis conf を使った Linux 上の SSIS の構成](sql-server-linux-configure-ssis.md)します。

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. 構成を完了すると、パスを設定します。

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>SSIS を更新します。
既にある場合`mssql-server-is`インストールされている場合、次のように、次のコマンドで最新バージョンに更新できます。

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>SSIS を削除します。
削除する`mssql-server-is`、次のコマンドを実行することができます。
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>無人インストール
実行すると、無人インストールを実行する`ssis-conf setup`、次の操作を行います。
1.  指定、 `-n` (プロンプトなし) オプション。
2.  環境変数を設定して、必要な値を提供します。

次の例は、次の操作を行います。
-   SSIS をインストールします。
-   値を提供することで、Developer edition を指定します、`SSIS_PID`環境変数。
-   値を提供することで、使用許諾契約書を受け入れる、`ACCEPT_EULA`環境変数。
-   指定することによって、無人インストールを実行、 `-n` (プロンプトなし) オプション。

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>無人インストール用の環境変数

| 環境変数 | 説明 |
|---|---|
| **ACCEPT_EULA** | 任意の値に設定すると、SQL Server の使用許諾契約に受け取ります (たとえば、 `Y`)。|
| **SSIS_PID** | SQL Server のエディションまたはプロダクト キーを設定します。 使用可能な値を次に示します。<br/>Evaluation<br/>Developer<br/>Express <br/>Web <br/>Standard<br/>Enterprise <br/>プロダクト キー<br/><br/>プロダクト キーが形式である必要があります、プロダクト キーを指定する場合`#####-#####-#####-#####-#####`ここで、`#`が文字または数字。  |
| | |

## <a name="next-steps"></a>次の手順

Linux 上の SSIS パッケージを実行するを参照してください。[抽出、変換、および SSIS を使用した Linux 上の SQL Server のデータの読み込み](sql-server-linux-migrate-ssis.md)します。

Linux で SSIS の追加の設定を構成するのを参照してください。 [ssis conf Linux で SQL Server Integration Services を構成する](sql-server-linux-configure-ssis.md)します。

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS に関する関連コンテンツ
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)
-   [Ssis conf で Linux 上の SQL Server Integration Services を構成します。](sql-server-linux-configure-ssis.md)
-   [制限事項と Linux での SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
-   [スケジュールの SQL Server Integration Services パッケージ cron を使用した Linux 上の実行](sql-server-linux-schedule-ssis-packages.md)
