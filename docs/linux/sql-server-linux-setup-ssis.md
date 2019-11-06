---
title: SQL Server Integration Services on Linux をインストールする
description: この記事では、SQL Server Integration Services (SSIS) on Linux をインストール方法について説明します。
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 68f3497e9f3f47d7e43c2bda0083bc25632d8221
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032443"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>SQL Server Integration Services (SSIS) on Linux をインストールする

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事の手順に従って、SQL Server Integration Services (`mssql-server-is`) on Linux をインストールします。 今回の Linux 用の Integration Services のリリースでサポートされる機能の詳細については、[リリース ノート](sql-server-linux-release-notes.md)を参照してください。

お使いのプラットフォームに SQL Server Integration Servers をインストールする

- [Ubuntu 16.04](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Ubuntu に SSIS をインストールする
`mssql-server-is` パッケージを Ubuntu にインストールするには、次の手順を実行します。

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. 次のコマンドを実行して SQL Server Integration Services をインストールします。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Integration Services をインストールした後、`ssis-conf` を実行します。 詳細については、「[ssis-conf を使用して SSIS on Linux を構成する](sql-server-linux-configure-ssis.md)」を参照してください。

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. 構成が完了したら、パスを設定します。

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>SSIS を更新する
既に `mssql-server-is` がインストールされている場合は、次のコマンドを使用して最新バージョンに更新できます。

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>SSIS を削除する
`mssql-server-is` を削除するには、次のコマンドを実行できます。
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> RHEL に SSIS をインストールする
`mssql-server-is` パッケージを RHEL にインストールするには、次の手順を実行します。

1. Microsoft SQL Server Red Hat リポジトリ構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. 次のコマンドを実行して SQL Server Integration Services をインストールします。

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. インストール後、`ssis-conf` を実行します。 詳細については、「[ssis-conf を使用して SSIS on Linux を構成する](sql-server-linux-configure-ssis.md)」を参照してください。

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. 構成が完了したら、パスを設定します。

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>SSIS を更新する
既に `mssql-server-is` がインストールされている場合は、次のコマンドを使用して最新バージョンに更新できます。

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>SSIS を削除する
`mssql-server-is` を削除するには、次のコマンドを実行できます。
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>自動実行インストール
`ssis-conf setup` を実行するときに自動実行インストールを実行するには、次の操作を行います。
1.  `-n` (プロンプトなし) オプションを指定します。
2.  環境変数を設定することで、必要な値を指定します。

次の例では、次の処理が実行されます。
-   SSIS をインストールします。
-   `SSIS_PID` 環境変数の値を指定することで、Developer エディションを指定します。
-   `ACCEPT_EULA` 環境変数の値を指定することで、ライセンス条項に同意します。
-   `-n`(プロンプトなし) オプションを指定することで、自動実行インストールを実行します。

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>自動実行インストール用の環境変数

| 環境変数 | [説明] |
|---|---|
| **ACCEPT_EULA** | 任意の値 (例: `Y`) に設定すると、SQL Server 使用許諾契約書に同意します。|
| **SSIS_PID** | SQL Server のエディションまたはプロダクト キーを設定します。 可能な値を次に示します。<br/>Evaluation<br/>Developer<br/>Express <br/>Web <br/>Standard<br/>Enterprise <br/>プロダクト キー<br/><br/>プロダクト キーを指定する場合は、プロダクト キーの書式を `#####-#####-#####-#####-#####` にする必要があります。ここで、`#` は文字または数字です。  |
| | |

## <a name="next-steps"></a>次の手順

Linux 上で SSIS パッケージを実行するには、「[SSIS を使用して SQL Server on Linux 用のデータの抽出、変換、および読み込みを行う](sql-server-linux-migrate-ssis.md)」を参照してください。

Linux 上で SSIS 設定を追加で構成するには、「[ssis-conf を使用して SQL Server Integration Services on Linux を構成する](sql-server-linux-configure-ssis.md)」を参照してください。

## <a name="related-content-about-ssis-on-linux"></a>SSIS on Linux の関連コンテンツ
-   [SSIS を使用して Linux 上でデータの抽出、変換、読み込みを行う](sql-server-linux-migrate-ssis.md)
-   [ssis-conf を使用して SQL Server Integration Services on Linux を構成する](sql-server-linux-configure-ssis.md)
-   [SSIS on Linux の制限事項と既知の問題](sql-server-linux-ssis-known-issues.md)
-   [cron を使用して Linux 上で SQL Server Integration Services パッケージの実行スケジュールを設定する](sql-server-linux-schedule-ssis-packages.md)
