---
title: "Ubuntu の SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、Ubuntu に SQL Server 2017 をインストールし、sqlcmd によりデータベースを作成してクエリを実行する方法を示します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Active
ms.openlocfilehash: e0dc1d24963e1e00018d5b5ac1418d68a4a22577
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="install-sql-server-and-create-a-database-on-ubuntu"></a>Ubuntu に SQL Server をインストールし、データベースを作成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このクイック スタート チュートリアルでは、初めに Ubuntu 16.04 に SQL Server 2017 をインストールします。 その後 **sqlcmd** で接続して最初のデータベースを作成し、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 興味のある場合、[無人](sql-server-linux-setup.md#unattended)または[オフライン](sql-server-linux-setup.md#offline)インストール手順を参照してください[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)です。

## <a name="prerequisites"></a>前提条件

Ubuntu 16.04 コンピューターに **少なくとも 2 GB** メモリを搭載する必要があります。

Ubuntu を自分のコンピューターにインストールするには [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) に移動してください。 Azure の Ubuntu 仮想マシンを作成することもできます。 [Azure CLI を使用して Linux Vm を作成および管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm) を参照してください。

> [!NOTE]
> 現時点で、 Windows 10 の [Windows Subsystem for Linux](https://msdn.microsoft.com/commandline/wsl/about) は、インストール対象としてサポートされていません。

その他のシステム要件については、次を参照してください。 [Linux の SQL Server のシステム要件](sql-server-linux-setup.md#system)

## <a id="install"></a>SQL Server をインストールします。

Ubuntu で SQL Server を構成するには、ターミナルで次のコマンドを実行し、**mssql-server** パッケージをインストールします。

> [!IMPORTANT]
> 既に SQL Server 2017 の CTP または RC リリースをインストールしている場合は、古いリポジトリを削除してからその GA リポジトリの一つを登録する必要があります。 詳細については、 [リポジトリをプレビュー リポジトリからGA リポジトリに変更する](sql-server-linux-change-repo.md) を参照してください。

1. パブリック リポジトリ GPG キーをインポートします。

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > これは、累積的な更新プログラム (CU) リポジトリです。 リポジトリ オプションとそれらの相違点についての詳細は、次を参照してください。 [Linux に SQL Server 用のリポジトリを構成する](sql-server-linux-change-repo.md)です。

1. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. パッケージのインストールが完了したら、**mssql-conf setup** の実行後に、SA パスワードの設定とエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > このチュートリアルで SQL Server 2017 を試す場合、次のエディションはライセンスフリーです: Evaluation、Developer、および Express

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、10 進数の数字や英数字以外の記号を含む)。

1. 構成が完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

1. リモートで接続する場合はファイアウォールで SQL Server の TCP ポート (既定は 1433) を開く必要もあります。

この時点で、Ubuntu コンピューター上で SQL Server を実行し、使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順では、次の SQL Server コマンド ライン ツールをインストールします。[sqlcmd](../tools/sqlcmd-utility.md) と[bcp](../tools/bcp-utility.md)

1. パブリック リポジトリ GPG キーをインポートします。

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
   ```

1. ソース リストを更新し、unixODBC Developer パッケージでインストール コマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-tools unixodbc-dev
   ```

1. 利便性のため、`/opt/mssql-tools/bin/` を、**PATH** 環境変数に追加します。 これにより、完全なパスを指定せずに、ツールを実行することができます。 次のコマンドを実行し、**PATH** をログイン セッションと対話型/非ログイン セッションの両方に変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd** はクエリを実行し、管理と開発タスクを実行する SQL Server に接続するためのツールの 1 つです。 その他のツールは次のとおりです。
>
> * [SQL Server Operations Studio (プレビュー)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。
> * [mssql-cli (プレビュー)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
