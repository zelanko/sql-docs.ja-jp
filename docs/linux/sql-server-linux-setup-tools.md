---
title: Linux 上の SQL Server コマンド ライン ツールのインストール |Microsoft Docs
description: この記事では、Linux に SQL Server ツールをインストールする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.openlocfilehash: 4dc9dd24bc3bdfa918ffdc7d02688303d8dcde5e
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393756"
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Sqlcmd および bcp、SQL Server コマンド ライン ツールを Linux にインストールします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次の手順では、コマンド ライン ツール、Microsoft ODBC ドライバー、およびその依存関係をインストールします。 **Mssql ツール**パッケージが含まれています。

- **sqlcmd**: コマンド ライン クエリ ユーティリティ。
- **bcp**: 一括インポート/エクスポート ユーティリティ。

お使いのプラットフォーム ツールをインストールします。

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

この記事では、コマンド ライン ツールをインストールする方法について説明します。 使用する方法の例を探しているかどうかは**sqlcmd**または**bcp**を参照してください、[リンク](#next-steps)このトピックの最後にします。

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>RHEL 7 にツールをインストールします。

次の手順を使用してインストールする、 **mssql ツール**Red Hat Enterprise linux。 

1. スーパー ユーザー モードに入ります。

   ```bash
   sudo su
   ```

1. Microsoft の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. スーパー ユーザーのモードを終了します。

   ```bash
   exit
   ```

1. インストールされている **mssql ツール** の以前のバージョンがあれば、古い unixODBC パッケージを削除します。

   ```bash
   sudo yum remove mssql-tools unixODBC-utf16-devel
   ```

1. 次のコマンドを実行して **mssql-tools** を unixODBC 開発者パッケージとともにインストールします。

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > 最新バージョンに更新する**mssql ツール**次のコマンドを実行します。
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **省略可能な**: 追加`/opt/mssql-tools/bin/`を**パス**bash シェル内の環境変数。

   させる**sqlcmd と bcp**ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bash_profile**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   させる**sqlcmd と bcp**対話型/非ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bashrc**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Ubuntu 16.04 にツールをインストールします。

次の手順を使用してインストールする、 **mssql ツール**ubuntu の場合。 

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Ubuntu の Microsoft リポジトリを登録します。

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. ソースの一覧を更新して、unixODBC 開発者のパッケージをインストール コマンドを実行します。

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > 最新バージョンに更新する**mssql ツール**次のコマンドを実行します。
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **省略可能な**: 追加`/opt/mssql-tools/bin/`を**パス**bash シェル内の環境変数。

   させる**sqlcmd と bcp**ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bash_profile**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   させる**sqlcmd と bcp**対話型/非ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bashrc**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>SLES 12 でツールをインストールします。

次の手順を使用してインストールする、 **mssql ツール**SUSE Linux Enterprise server。 

1. Zypper を Microsoft SQL Server リポジトリを追加します。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. インストール**mssql ツール**unixODBC 開発者パッケージにします。

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > 最新バージョンに更新する**mssql ツール**次のコマンドを実行します。
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **省略可能な**: 追加`/opt/mssql-tools/bin/`を**パス**bash シェル内の環境変数。

   させる**sqlcmd と bcp**ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bash_profile**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   させる**sqlcmd と bcp**対話型/非ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bashrc**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> MacOS でのツールをインストールします。

プレビュー **sqlcmd**と**bcp** macOS で公開されています。 詳細については、次を参照してください。、[アナウンス](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/)します。

*インストール[Homebrew](https://brew.sh)まだ持っていない場合。*

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Mac El Capitan と Sierra のツールをインストールするには、次のコマンドを使用します。

```
# brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox mssql-tools
#for silent install: 
#ACCEPT_EULA=y brew install --no-sandbox mssql-tools
```

## <a id="docker"></a> Docker

SQL Server 2017 CTP 2.0 以降、SQL Server コマンド ライン ツールは、Docker イメージに含まれます。 対話型コマンド プロンプトで、イメージをアタッチする場合は、ローカルのツールを実行できます。

## <a name="offline-installation"></a>オフライン インストール

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

次の表では、最新のツール パッケージの場所を示します。

| ツール パッケージ | バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM ツール パッケージ | 14.0.5.0-1 | [mssql ツール RPM パッケージ](https://packages.microsoft.com/rhel/7.3/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| SLES RPM ツール パッケージ | 14.0.5.0-1 | [mssql ツール RPM パッケージ](https://packages.microsoft.com/sles/12/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian ツール パッケージ | 14.0.5.0-1 | [mssql ツール Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |
| Ubuntu 16.10 Debian ツール パッケージ | 14.0.5.0-1 | [mssql ツール Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |

これらのパッケージが依存**移動**を最初にインストールする必要があります。 **移動**パッケージもいずれかに依存している**unixODBC devel** (RPM) または**unixodbc dev** (Debian)。 場所、**移動**パッケージが次の表に一覧表示します。

| パッケージの移動 | バージョン | ダウンロード |
|-----|-----|-----|
| 移動の Red Hat の RPM パッケージ | 13.1.6.0-1 | [msodbcsql RPM package](https://packages.microsoft.com/rhel/7.3/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| 移動の SLES RPM パッケージ | 13.1.6.0-1 | [msodbcsql RPM package](https://packages.microsoft.com/sles/12/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian msodbcsql package | 13.1.6.0-1 | [Debian パッケージの移動](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |
| Ubuntu 16.10 Debian msodbcsql package | 13.1.6.0-1 | [Debian パッケージの移動](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |

これらのパッケージを手動でインストールするには、次の手順を使用します。

1. **Linux コンピューターにダウンロードしたパッケージを移動**します。 Linux コンピューターに、パッケージを移動する方法の 1 つは、パッケージをダウンロードする別のコンピューターを使用した場合、 **scp**コマンド。

1. **インストール、およびパッケージ**: インストール、 **mssql ツール**と**msodbc**パッケージ。 すべての依存関係エラーが発生した場合は、次の手順まで無視します。

    | プラットフォーム | パッケージのインストール コマンド |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo yum localinstall mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | SLES | `sudo zypper install msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo zypper install mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_13.1.6.0-1_amd64.deb`<br/>`sudo dpkg -i mssql-tools_14.0.5.0-1_amd64.deb` |

1. **解決するには依存関係がない**: 依存関係をこの時点で不足している必要があります。 それ以外の場合は、この手順をスキップすることができます。 場合によってでは、手動で検索して、これらの依存関係をインストールする必要があります。

    RPM パッケージでは、次のコマンドで必要な依存関係を確認できます。

    ```bash
    rpm -qpR msodbcsql-13.1.6.0-1.x86_64.rpm
    rpm -qpR mssql-tools-14.0.5.0-1.x86_64.rpm
    ```

    Debian パッケージは、それらの依存関係を含む承認済みのリポジトリにアクセスする場合、最も簡単なソリューションを使用する、 **apt-get と**コマンド。

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > このコマンドは、SQL Server パッケージのインストールを完了します。

    これが機能しない、Debian パッケージの場合は、次のコマンドで必要な依存関係を確認できます。

    ```bash
    dpkg -I msodbcsql_13.1.6.0-1_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_14.0.5.0-1_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>次のステップ

使用する方法の例については**sqlcmd**を SQL Server に接続し、データベースの作成には、次のクイック スタートのいずれかを表示します。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)

使用する方法の例については**bcp**データを一括インポートおよびエクスポートを参照してください。 [Linux 上の SQL Server にデータの一括コピー](sql-server-linux-migrate-bcp.md)します。
