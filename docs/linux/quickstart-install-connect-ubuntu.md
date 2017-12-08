---
title: "Ubuntu の SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、Ubuntu に SQL Server 2017 をインストールし、sqlcmd によりデータベースを作成するクエリを実行する方法を示します。"
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
ms.openlocfilehash: d708c0711c1b1fd4ccf79d9c4bfbd382c8d97486
ms.sourcegitcommit: 085dd05d56afecbb454206ed8402cfbaa597cfbe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="install-sql-server-and-create-a-database-on-ubuntu"></a>Ubuntu に SQL Server をインストールし、データベースを作成

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタート チュートリアルでは、初めに Ubuntu 16.04 にSQL Server 2017 をインストールし、**sqlcmd** で接続し、最初のデータベースを作成する、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザーの入力と、インターネット接続が必要です。 [無人](sql-server-linux-setup.md#unattended)または[オフライン](sql-server-linux-setup.md#offline)インストールに興味がある場合、次の手順を参照してください。[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)

## <a name="prerequisites"></a>前提条件

Ubuntu 16.04 コンピューターに**少なくとも 2 GB**メモリを搭載する必要があります。

Ubuntu を自分のコンピューターにインストールするには [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) に移動してください。 Azure の Ubuntu 仮想マシンを作成することもできます。 [Azure CLI を使用して Linux Vm を作成および管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)を参照してください。

> [!NOTE]
> 現時点で、 Windows 10 の[Windows Subsystem for Linux ](https://msdn.microsoft.com/commandline/wsl/about)は、インストール対象としてサポートされていません。

その他のシステム要件については、次を参照してください。 [Linux の SQL Server のシステム要件](sql-server-linux-setup.md#system)

## <a id="install"></a>SQL Server をインストールします。

SQL Server を構成する Ubuntu のターミナルで次のコマンドを実行し、 **mssql-server** パッケージをインストールします。

> [!IMPORTANT]
> 既に CTP または SQL Server 2017 年 1 の RC リリースをインストールしている場合は、GA リポジトリを登録する前に、古いリポジトリを削除する必要があります。 詳細については、次を参照してください。[プレビュー リポジトリからリポジトリを GA リポジトリに変更](sql-server-linux-change-repo.md)

1. パブリック リポジトリ GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > これは、累積的な更新プログラム (CU) リポジトリです。 リポジトリ オプションとそれらの相違点についての詳細は、次を参照してください。[ソース リポジトリを変更](sql-server-linux-setup.md#repositories)

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
   > このチュートリアルでは SQL Server 2017 の、次のライセンスフリーのエディションを選択します Evaluation、Developer、および Express

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、基本 10 桁の数字や英数字以外の記号) 

1. 構成が完了し、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

1. リモートで接続する場合はファイアウォールで SQL Server の TCP ポート (既定は 1433) を開く必要もあります。

この時点で、Ubuntu コンピューター上で SQL Server を実行し、使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順では、SQL Server コマンド ライン ツールをインストールします。[sqlcmd](../tools/sqlcmd-utility.md)と[bcp](../tools/bcp-utility.md)

1. パブリック リポジトリ GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
   ```

1. ソース リストを更新し、unixODBC Developer パッケージをインストールするコマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-tools unixodbc-dev
   ```

1. 利便性のため、`/opt/mssql-tools/bin/`を、**PATH** 環境変数に追加します。 これにより、完全なパスを指定せずに、ツールを実行することができます。 次のコマンドを実行し、**PATH** をログイン セッションと対話型/非ログイン セッションの両方に変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd** はクエリを実行し、管理と開発タスクを実行する SQL Server に接続するためのツールの 1 つです。 その他のツールには [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)と[Visual Studio Code](sql-server-linux-develop-use-vscode.md) が含まれます。

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
