---
title: "SUSE Linux Enterprise Server 上の SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、SUSE Linux Enterprise Server を SQL Server 2017 をインストールし、作成し、sqlcmd によるデータベースのクエリを実行する方法を示します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.translationtype: MT
ms.sourcegitcommit: 6d18cbe5b20882581afa731ce5d207cbbc69be6c
ms.openlocfilehash: a15f88d8bc7d7684e8e8d0014bb24a082c5b0be2
ms.contentlocale: ja-jp
ms.lasthandoff: 10/21/2017

---
# <a name="install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>SQL Server をインストールし、SUSE Linux Enterprise Server にデータベースを作成

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタート チュートリアルでは、SUSE Linux Enterprise Server (SLES) v12 SP2 に初めて SQL Server 2017 をインストールするだけです。 接続し、 **sqlcmd**を最初にデータベースを作成し、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 興味のある場合、[無人](sql-server-linux-setup.md#unattended)または[オフライン](sql-server-linux-setup.md#offline)インストール手順を参照してください[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)です。

## <a name="prerequisites"></a>前提条件

SLES v12 SP2 コンピューターでする必要があります**3.25 GB 以上**メモリです。 ファイル システムである必要があります**XFS**または**EXT4**です。 その他のファイル システム**BTRFS**、サポートされていません。

自分のコンピューター上の SUSE Linux Enterprise Server をインストールするに移動[https://www.suse.com/products/server](https://www.suse.com/products/server)です。 Azure で SLES 仮想マシンを作成することもできます。 参照してください[作成と Azure CLI を使用して Linux Vm の管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)、および使用`--image SLES`への呼び出しで`az vm create`です。

> [!NOTE]
> この時点で、 [for Linux の Windows サブシステム](https://msdn.microsoft.com/commandline/wsl/about)Windows 10 は、インストール対象としてサポートされていません。

その他のシステム要件については、次を参照してください。 [Linux に SQL Server のシステム要件](sql-server-linux-setup.md#system)です。

## <a id="install"></a>SQL Server をインストールします。

SLES で SQL Server を構成するには、インストールするターミナル次のコマンドを実行、 **mssql サーバー**パッケージ。

> [!IMPORTANT]
> 既に CTP または SQL Server 2017 年 1 の RC リリースをインストールされている場合は、GA リポジトリを登録する前に、古いリポジトリを削除する必要があります。 詳細については、次を参照してください。[プレビュー リポジトリからリポジトリを GA リポジトリに変更](sql-server-linux-change-repo.md)です。

1. Microsoft SQL Server SLES リポジトリの構成ファイルをダウンロードするには。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   sudo zypper --gpg-auto-import-keys refresh
   ```

   > [!NOTE]
   > これは、累積的な更新プログラム (CU) リポジトリです。 詳細については、リポジトリ オプションとそれらの相違点については、次を参照してください。[ソース リポジトリを変更](sql-server-linux-setup.md#repositories)です。

1. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo zypper install -y mssql-server
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

1. リモートで接続する場合はを開くには、ファイアウォールで SQL Server の TCP ポート (既定は 1433) する必要もあります。 SuSE ファイアウォールを使用している場合は、編集する必要があります。、 **/etc/sysconfig/SuSEfirewall2**構成ファイル。 変更、 **FW_SERVICES_EXT_TCP**エントリを SQL Server のポート番号が含まれます。

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

この時点では、SQL Server では、SLES コンピューター上で実行しを使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順は、SQL Server コマンド ライン ツールをインストール: [sqlcmd](../tools/sqlcmd-utility.md)と[bcp](../tools/bcp-utility.md)です。

1. Zypper に Microsoft SQL Server リポジトリを追加します。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. インストール**mssql ツール**unixODBC 開発者パッケージにします。

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. 便宜上、次のように追加します。`/opt/mssql-tools/bin/`を、**パス**環境変数。 これにより、完全なパスを指定せず、ツールを実行することができます。 変更するのには、次のコマンドを実行、**パス**ログイン セッションと対話型/以外のログイン セッションの両方の。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd**クエリの実行し、管理と開発タスクを実行する SQL Server に接続するためのツールの 1 つだけです。 その他のツールが含まれます[SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)と[Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]

