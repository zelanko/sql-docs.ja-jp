---
title: "Ubuntu で SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタートでは、Ubuntu で SQL Server 2017 をインストールし、作成し、sqlcmd によるデータベースのクエリを実行する方法を示します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Active
ms.openlocfilehash: 17d6ebb3df10a5bc8b5801c11cc8ac12cde372a2
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="install-sql-server-and-create-a-database-on-ubuntu"></a>SQL Server をインストールし、Ubuntu でデータベースを作成

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタートでは、Ubuntu 16.04 に初めて SQL Server 2017 をインストールするだけです。 接続し、 **sqlcmd**を最初にデータベースを作成し、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 興味のある場合、[無人](sql-server-linux-setup.md#unattended)または[オフライン](sql-server-linux-setup.md#offline)インストール手順を参照してください[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)です。

## <a name="prerequisites"></a>Prerequisites

Ubuntu 16.04 コンピューターにする必要があります**に少なくとも 2 GB**メモリです。

Ubuntu を自分のコンピューターにインストールするに移動[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)です。 Azure の Ubuntu 仮想マシンを作成することもできます。 参照してください[を作成および管理の Azure CLI を使用して Linux Vm](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)です。

> [!NOTE]
> この時点で、 [for Linux の Windows サブシステム](https://msdn.microsoft.com/commandline/wsl/about)Windows 10 は、インストール対象としてサポートされていません。

その他のシステム要件については、次を参照してください。 [Linux に SQL Server のシステム要件](sql-server-linux-setup.md#system)です。

## <a id="install"></a>SQL Server をインストールします。

Ubuntu で SQL Server を構成するをインストールするターミナルで次のコマンドを実行、 **mssql サーバー**パッケージです。

> [!IMPORTANT]
> 既に CTP または SQL Server 2017 年 1 の RC リリースをインストールされている場合は、GA リポジトリを登録する前に、古いリポジトリを削除する必要があります。 詳細については、次を参照してください。[プレビュー リポジトリからリポジトリを GA リポジトリに変更](sql-server-linux-change-repo.md)です。

1. パブリック リポジトリ鍵キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > これは、累積的な更新プログラム (CU) リポジトリです。 詳細については、リポジトリ オプションとそれらの相違点については、次を参照してください。[ソース リポジトリを変更](sql-server-linux-setup.md#repositories)です。

1. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. パッケージのインストールが完了すると、実行後に**mssql conf セットアップ**SA パスワードを設定しのエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > このチュートリアルでは SQL Server 2017 を行う場合、次のエディションのライセンスは自由に: Evaluation、Developer、および高速です。

   > [!NOTE]
   > (最小長さが 8 文字で、大文字と小文字のアルファベット、基本 10 桁の数字や英数字以外の記号) は、SA アカウントの強力なパスワードを指定することを確認してください。

1. 構成を完了すると、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

1. リモートで接続する場合はを開くには、ファイアウォールで SQL Server の TCP ポート (既定は 1433) する必要もあります。

この時点では、SQL Server では、Ubuntu コンピューター上で実行しを使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順は、SQL Server コマンド ライン ツールをインストール: [sqlcmd](../tools/sqlcmd-utility.md)と[bcp](../tools/bcp-utility.md)です。

1. パブリック リポジトリ鍵キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
   ```

1. ソース リストを更新し、unixODBC 開発者のパッケージでインストール コマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-tools unixodbc-dev
   ```

1. 便宜上、次のように追加します。`/opt/mssql-tools/bin/`を、**パス**環境変数。 これにより、完全なパスを指定せず、ツールを実行することができます。 変更するのには、次のコマンドを実行、**パス**ログイン セッションと対話型/以外のログイン セッションの両方の。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd**クエリの実行し、管理と開発タスクを実行する SQL Server に接続するためのツールの 1 つだけです。 その他のツールは次のとおりです。
>
> * [SQL Server 操作 Studio (プレビュー)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。
> * [mssql cli (プレビュー)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
