---
title: Ubuntu:Linux 上に SQL Server をインストールする
description: このクイックスタートでは、Ubuntu に SQL Server 2017 または SQL Server 2019 をインストールしてから、sqlcmd を使用してデータベースを作成してクエリを実行する方法を示します。
author: VanMSFT
ms.author: vanto
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.custom: seo-lt-2019
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 69f1ac170d70c10d9a7061b3fc18f6c8a62db704
ms.sourcegitcommit: efb2bb07700f645b3fbfcb400a0666de01388305
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79319852"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>クイック スタート:Ubuntu に SQL Server をインストールし、データベースを作成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]


<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

このクイックスタートでは、Ubuntu 16.04 に SQL Server 2017 をインストールします。 次に、**sqlcmd** と接続して最初のデータベースを作成し、クエリを実行します。

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

このクイックスタートでは、Ubuntu 18.04 に SQL Server 2019 をインストールします。 次に、**sqlcmd** と接続して最初のデータベースを作成し、クエリを実行します。

::: moniker-end

> [!TIP]
> このチュートリアルには、ユーザー入力とインターネット接続が必要です。 無人またはオフラインのインストール手順について関心をお持ちの場合は、[SQL Server on Linux のインストール ガイダンス](sql-server-linux-setup.md)に関する記事を参照してください。

## <a name="prerequisites"></a>前提条件

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Ubuntu 16.04 マシンには**少なくとも 2 GB** のメモリが必要です。

ご自分のマシンに Ubuntu 16.04 をインストールするには、<http://releases.ubuntu.com/xenial/> にアクセスします。 Azure で Ubuntu 仮想マシンを作成することもできます。 「[Azure CLI を使用した Linux VM の作成と管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)」を参照してください。

> [!NOTE]
> 現時点では、Windows 10 用の [Windows Subsystem for Linux](https://msdn.microsoft.com/commandline/wsl/about) はインストール先としてサポートされていません。

他のシステム要件については、[SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)に関する記事を参照してください。

> [!NOTE]
> Ubuntu 18.04 はまだ正式にサポートされていませんが、[修正](https://blogs.msdn.microsoft.com/sql_server_team/installing-sql-server-2017-for-linux-on-ubuntu-18-04-lts/)を加えることで SQL Server を実行できます。

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Ubuntu 18.04 マシンには**少なくとも 2 GB** のメモリが必要です。

ご自分のマシンに Ubuntu 18.04 をインストールするには、<http://releases.ubuntu.com/bionic/> にアクセスします。 Azure で Ubuntu 仮想マシンを作成することもできます。 「[Azure CLI を使用した Linux VM の作成と管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)」を参照してください。

> [!NOTE]
> 現時点では、Windows 10 用の [Windows Subsystem for Linux](https://msdn.microsoft.com/commandline/wsl/about) はインストール先としてサポートされていません。

他のシステム要件については、[SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)に関する記事を参照してください。

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a name="install-sql-server"></a><a id="install"></a>SQL Server をインストールする

Ubuntu 上で SQL Server を構成するには、ターミナルで次のコマンドを実行して **mssql-server** パッケージをインストールします。

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!TIP]
   > SQL Server 2019 をインストールする場合は、代わりに SQL Server 2019 リポジトリを登録する必要があります。 SQL Server 2019 のインストールには、次のコマンドを使用します。
   >
   > ```bash
   > sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
   > ```

3. 次のコマンドを実行して SQL Server をインストールします。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. パッケージのインストールが完了したら、**mssql-conf setup** を実行し、プロンプトに従って SA パスワードを設定し、エディションを選択します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > 次の SQL Server 2017 エディションは無料でライセンスが付与されます。Evaluation、Developer、Express。

   > [!NOTE]
   > SA アカウントには必ず強力なパスワードを指定してください (大文字と小文字、10 進数の数字、英数字以外の記号を含む、最小 8 文字の長さ)。

5. 構成が完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. リモート接続を計画している場合は、必要に応じてファイアウォールで SQL Server の TCP ポート (既定値は 1433) も開きます。

この時点で、SQL Server は Ubuntu マシン上で動作しており、使用する準備ができています。

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="install-sql-server"></a><a id="install"></a>SQL Server をインストールする

Ubuntu 上で SQL Server を構成するには、ターミナルで次のコマンドを実行して **mssql-server** パッケージをインストールします。

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. SQL Server 2019 用の Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/mssql-server-2019.list)"
   ```

3. 次のコマンドを実行して SQL Server をインストールします。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. パッケージのインストールが完了したら、**mssql-conf setup** を実行し、プロンプトに従って SA パスワードを設定し、エディションを選択します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > SA アカウントには必ず強力なパスワードを指定してください (大文字と小文字、10 進数の数字、英数字以外の記号を含む、最小 8 文字の長さ)。

5. 構成が完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. リモート接続を計画している場合は、必要に応じてファイアウォールで SQL Server の TCP ポート (既定値は 1433) も開きます。

この時点で、SQL Server 2019 は Ubuntu マシン上で動作しており、使用する準備ができています。

::: moniker-end

## <a name="install-the-sql-server-command-line-tools"></a><a id="tools"></a>SQL Server コマンドライン ツールをインストールする

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

データベースを作成するには、SQL Server 上で Transact-SQL ステートメントを実行できるツールと接続する必要があります。 次の手順で SQL Server コマンドライン ツールの [sqlcmd](../tools/sqlcmd-utility.md) と [bcp](../tools/bcp-utility.md) をインストールします。

次の手順を使用して、Ubuntu に **mssql-tools** をインストールします。 

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft Ubuntu リポジトリを登録します。

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. ソース一覧を更新し、unixODBC 開発者パッケージを使用してインストール コマンドを実行します。

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > 最新バージョンの **mssql-tools** に更新するには、次のコマンドを実行します。
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **省略可能**:bash シェルで **PATH** 環境変数に `/opt/mssql-tools/bin/` を追加します。

   ログイン セッション用に bash シェルから **sqlcmd/bcp** にアクセスできるようにするには、次のコマンドで **~/.bash_profile** ファイルの **PATH** を変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   対話型/非ログイン セッション用に bash シェルから **sqlcmd/bcp** にアクセスできるようにするには、次のコマンドで **~/.bashrc** ファイルの **PATH** を変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

データベースを作成するには、SQL Server 上で Transact-SQL ステートメントを実行できるツールと接続する必要があります。 次の手順で SQL Server コマンドライン ツールの [sqlcmd](../tools/sqlcmd-utility.md) と [bcp](../tools/bcp-utility.md) をインストールします。

次の手順を使用して、Ubuntu に **mssql-tools** をインストールします。 

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft Ubuntu リポジトリを登録します。

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. ソース一覧を更新し、unixODBC 開発者パッケージを使用してインストール コマンドを実行します。

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > 最新バージョンの **mssql-tools** に更新するには、次のコマンドを実行します。
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **省略可能**:bash シェルで **PATH** 環境変数に `/opt/mssql-tools/bin/` を追加します。

   ログイン セッション用に bash シェルから **sqlcmd/bcp** にアクセスできるようにするには、次のコマンドで **~/.bash_profile** ファイルの **PATH** を変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   対話型/非ログイン セッション用に bash シェルから **sqlcmd/bcp** にアクセスできるようにするには、次のコマンドで **~/.bashrc** ファイルの **PATH** を変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

::: moniker-end

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
