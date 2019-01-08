---
title: Red Hat Enterprise Linux 上の SQL Server の概要します。
titleSuffix: SQL Server
description: このクイック スタートでは、Red Hat Enterprise Linux に SQL Server 2017 または SQL Server 2019 インストール作成し、sqlcmd でデータベースをクエリする方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.custom: sql-linux, seodec18
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 794d241773addc5584869eaa2e05cfa316908ce1
ms.sourcegitcommit: de8ef246a74c935c5098713f14e9dd06c4733713
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160480"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>クイック スタート:SQL Server をインストールし、Red Hat でデータベースを作成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

このクイック スタートでインストールする SQL Server 2017 または SQL Server 2019 の Red Hat Enterprise Linux (RHEL) 7.3 以降。 接続して**sqlcmd**最初のデータベースを作成し、クエリを実行します。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

このクイック スタートで SQL Server 2019 プレビューにで Red Hat Enterprise Linux (RHEL) 7.3 以降をインストールします。 接続して**sqlcmd**最初のデータベースを作成し、クエリを実行します。

::: moniker-end

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 [無人](sql-server-linux-setup.md#unattended) または [オフライン](sql-server-linux-setup.md#offline) インストール手順に興味のある場合、[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md) を参照してください。

## <a name="prerequisites"></a>前提条件

RHEL 7.3 または 7.4 マシンで **少なくとも 2 GB** のメモリが必要です。

自分のコンピューターで Red Hat Enterprise Linux をインストールするには[ https://access.redhat.com/products/red-hat-enterprise-linux/evaluation](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation)します。 Azure で RHEL 仮想マシンを作成することもできます。 参照してください[の作成と Azure CLI を使用した Linux Vm の管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)、および使用`--image RHEL`への呼び出しで`az vm create`します。

CTP または SQL Server 2017 の RC リリースをインストールした場合は、次の手順に従う前に、古いリポジトリを削除する必要があります。 詳細については、次を参照してください。 [Linux の構成リポジトリの SQL Server 2017 と 2019](sql-server-linux-change-repo.md)します。

その他のシステム要件については、[Linux 上の SQL Server のシステム要件](sql-server-linux-setup.md#system) を参照してください。

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>SQL Server をインストールします。

RHEL で SQL Server を構成するためには、ターミナルで次のコマンドを実行して **mssql サーバー** パッケージをインストールします。

1. Microsoft SQL Server 2017 の Red Hat のリポジトリの構成ファイルをダウンロードするには。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > SQL Server 2019 を試す場合は、代わりに登録する必要あります、**プレビュー (2019)** リポジトリ。 次のコマンドを使用して、SQL Server 2019 のインストール用。
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   > ```

2. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo yum install -y mssql-server
   ```

3. パッケージのインストールが完了したら、**mssql-conf setup** の実行後に、SA パスワードの設定とエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > 次の SQL Server 2017 エディションのライセンスは自由に。Evaluation、Developer、および高速です。

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、10 進数の数字や英数字以外の記号を含む)。

4. 構成を完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

5. リモート接続を許可するには、RHEL 上のファイアウォールで SQL Server のポートを開きます。 SQL Server の既定ポートは、TCP 1433 です。 ファイアウォールとして **FirewallD** を使用している場合、次のコマンドを使用することができます。

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

この時点で、SQL Server はRHEL コンピューター上で実行されており、使用する準備ができました!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>SQL Server をインストールします。

RHEL で SQL Server を構成するためには、ターミナルで次のコマンドを実行して **mssql サーバー** パッケージをインストールします。

1. Microsoft SQL Server 2019 プレビュー Red Hat リポジトリ構成ファイルをダウンロードするには。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   ```

2. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo yum install -y mssql-server
   ```

3. パッケージのインストールが完了したら、**mssql-conf setup** の実行後に、SA パスワードの設定とエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、10 進数の数字や英数字以外の記号を含む)。

4. 構成を完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```

5. リモート接続を許可するには、RHEL 上のファイアウォールで SQL Server のポートを開きます。 SQL Server の既定ポートは、TCP 1433 です。 ファイアウォールとして **FirewallD** を使用している場合、次のコマンドを使用することができます。

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

この時点では、SQL Server 2019 プレビューでは、RHEL コンピューターで実行しているしを使用する準備ができました!

::: moniker-end

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順で、SQL Server コマンド ライン ツール: [sqlcmd](../tools/sqlcmd-utility.md) と [bcp](../tools/bcp-utility.md) をインストールします。

1. Microsoft の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. インストールされている **mssql ツール** の以前のバージョンがあれば、古い unixODBC パッケージを削除します。

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. 次のコマンドを実行して **mssql-tools** を unixODBC 開発者パッケージとともにインストールします。

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. 利便性のために、`/opt/mssql-tools/bin/` を **PATH** 環境変数に追加します。 これにより、完全なパスを指定せずに、ツールを実行することができます。 次のコマンドを実行し、**PATH** をログイン セッションと対話型/非ログイン セッションの両方に変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
