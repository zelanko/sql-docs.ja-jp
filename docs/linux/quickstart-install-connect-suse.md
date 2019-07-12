---
title: SUSE Linux Enterprise Server 上の SQL Server の概要します。
titleSuffix: SQL Server
description: このクイック スタートでは、SUSE Linux Enterprise Server 上の SQL Server 2017 または SQL Server 2019 のインストールしし、作成し、sqlcmd を使用したデータベースの照会する方法を示します。
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: 19f74067db365fd9bdc867b97cef6ee5aa5162d8
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833254"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>クイック スタート: SQL Server をインストールし、SUSE Linux Enterprise Server にデータベースを作成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

このクイック スタートで SUSE Linux Enterprise Server (SLES) v12 sp2、SQL Server 2017 または SQL Server 2019 preview をインストールします。 接続して**sqlcmd**最初のデータベースを作成し、クエリを実行します。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

このクイック スタートでは、SUSE Linux Enterprise Server (SLES) v12 SP2 の SQL Server 2019 preview をインストールします。 接続して**sqlcmd**最初のデータベースを作成し、クエリを実行します。

::: moniker-end

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 [無人](sql-server-linux-setup.md#unattended) または [オフライン](sql-server-linux-setup.md#offline) インストール手順に興味のある場合、[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md) を参照してください。

## <a name="prerequisites"></a>前提条件

SLES v12 SP2 コンピューターでする必要があります**に少なくとも 2 GB**メモリ。 ファイル システムは **XFS** または **EXT4** でなければいけません。 **BTRFS** といったその他のファイル システムはサポートされていません。

を、自分のマシンを SUSE Linux Enterprise Server をインストールするには[ https://www.suse.com/products/server](https://www.suse.com/products/server)します。 Azure SLES 仮想マシンを作成することもできます。 参照してください[の作成と Azure CLI を使用した Linux Vm の管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)、および使用`--image SLES`への呼び出しで`az vm create`します。

CTP または SQL Server 2017 の RC リリースをインストールした場合は、次の手順に従う前に、古いリポジトリを削除する必要があります。 詳細については、次を参照してください。 [Linux の構成リポジトリの SQL Server 2017 と 2019](sql-server-linux-change-repo.md)します。

> [!NOTE]
> 現時点で、 Windows 10 の [Windows Subsystem for Linux](https://msdn.microsoft.com/commandline/wsl/about) は、インストール対象としてサポートされていません。

その他のシステム要件については、次を参照してください。 [Linux の SQL Server のシステム要件](sql-server-linux-setup.md#system)

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>SQL Server をインストールします。

Sles SQL Server を構成するには、インストールするターミナルで次のコマンドを実行、 **mssql server**パッケージ。

1. Microsoft SQL Server 2017 SLES リポジトリの構成ファイルをダウンロードするには。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!TIP]
   > SQL Server 2019 を試す場合は、代わりに登録する必要あります、**プレビュー (2019)** リポジトリ。 次のコマンドを使用して、SQL Server 2019 のインストール用。
   >
   > ```bash
   > sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   > ```

2. リポジトリを更新します。

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo zypper install -y mssql-server
   ```

4. パッケージのインストールが完了したら、**mssql-conf setup** の実行後に、SA パスワードの設定とエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > 次の SQL Server 2017 エディションのライセンスは自由に。Evaluation、Developer、および高速です。

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、10 進数の数字や英数字以外の記号を含む)。

5. 構成が完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

6. リモートで接続する場合はファイアウォールで SQL Server の TCP ポート (既定は 1433) を開く必要もあります。 編集する必要があります、SuSE ファイアウォールを使用している場合、 **/etc/sysconfig/SuSEfirewall2**構成ファイル。 変更、 **FW_SERVICES_EXT_TCP**エントリを SQL Server のポート番号が含まれます。

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

この時点では、SQL Server は SLES コンピューター上で実行しを使用する準備ができました!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>SQL Server をインストールします。

Sles SQL Server を構成するには、インストールするターミナルで次のコマンドを実行、 **mssql server**パッケージ。

1. Microsoft SQL Server 2019 プレビュー SLES リポジトリ構成ファイルをダウンロードするには。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   ```

2. リポジトリを更新します。

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo zypper install -y mssql-server
   ```

4. パッケージのインストールが完了したら、**mssql-conf setup** の実行後に、SA パスワードの設定とエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、10 進数の数字や英数字以外の記号を含む)。

5. 構成が完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

6. リモートで接続する場合はファイアウォールで SQL Server の TCP ポート (既定は 1433) を開く必要もあります。 編集する必要があります、SuSE ファイアウォールを使用している場合、 **/etc/sysconfig/SuSEfirewall2**構成ファイル。 変更、 **FW_SERVICES_EXT_TCP**エントリを SQL Server のポート番号が含まれます。

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

この時点では、SQL Server 2019 プレビューは SLES コンピューター上で実行しを使用する準備ができました!

::: moniker-end


## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順で、SQL Server コマンド ライン ツール: [sqlcmd](../tools/sqlcmd-utility.md) と [bcp](../tools/bcp-utility.md) をインストールします。

1. Zypper を Microsoft SQL Server リポジトリを追加します。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. インストール**mssql ツール**unixODBC 開発者パッケージにします。

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. 利便性のために、`/opt/mssql-tools/bin/` を **PATH** 環境変数に追加します。 これにより、完全なパスを指定せずに、ツールを実行することができます。 次のコマンドを実行し、**PATH** をログイン セッションと対話型/非ログイン セッションの両方に変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
