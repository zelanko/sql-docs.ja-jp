---
title: "Linux 上の SQL Server コマンド ライン ツールのインストール |Microsoft ドキュメント"
description: "この記事では、Linux に SQL Server ツールをインストールする方法について説明します。"
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
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.workload: Active
ms.openlocfilehash: 92b04366f3dbcba517c5c82b0e7d65e862890cc3
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Sqlcmd および bcp、SQL Server コマンド ライン ツールを Linux にインストールします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次の手順では、コマンド ライン ツール、Microsoft ODBC ドライバー、およびその依存関係をインストールします。 **Mssql ツール**パッケージが含まれています。

- **sqlcmd**: コマンド ライン クエリ ユーティリティです。
- **bcp**: 一括インポートとエクスポート ユーティリティです。

お使いのプラットフォーム用のツールをインストールします。

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

この記事では、コマンド ライン ツールをインストールする方法について説明します。 使用する方法の例を探しているかどうかは**sqlcmd**または**bcp**を参照してください、[リンク](#next-steps)このトピックの最後。

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>RHEL 7 にツールをインストールします。

インストールする次の手順を使用して、 **mssql ツール**Red Hat Enterprise Linux にします。 

1. スーパー ユーザーのモードを入力します。

   ```bash
   sudo su
   ```

1. Microsoft Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. スーパー ユーザーのモードを終了します。

   ```bash
   exit
   ```

1. 以前のバージョンがあれば**mssql ツール**インストールされている、古い unixODBC パッケージを削除します。

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. インストールする次のコマンド実行**mssql ツール**unixODBC 開発者パッケージにします。

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > 最新バージョンに更新する**mssql ツール**次のコマンドを実行します。
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **省略可能な**: 追加`/opt/mssql-tools/bin/`を**パス**bash シェルの環境変数。

   させる**sqlcmd と bcp**ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bash_profile**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   させる**sqlcmd と bcp**対話型/以外のログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bashrc**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Ubuntu 16.04 にツールをインストールします。

インストールする次の手順を使用して、 **mssql ツール**Ubuntu でします。 

1. パブリック リポジトリ鍵キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Microsoft Ubuntu リポジトリを登録します。

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. ソース リストを更新し、unixODBC 開発者のパッケージでインストール コマンドを実行します。

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

1. **省略可能な**: 追加`/opt/mssql-tools/bin/`を**パス**bash シェルの環境変数。

   させる**sqlcmd と bcp**ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bash_profile**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   させる**sqlcmd と bcp**対話型/以外のログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bashrc**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>SLES 12 にツールをインストールします。

インストールする次の手順を使用して、 **mssql ツール**SUSE Linux Enterprise Server にします。 

1. Zypper に Microsoft SQL Server リポジトリを追加します。

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

1. **省略可能な**: 追加`/opt/mssql-tools/bin/`を**パス**bash シェルの環境変数。

   させる**sqlcmd と bcp**ログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bash_profile**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   させる**sqlcmd と bcp**対話型/以外のログイン セッションでは、bash シェルからアクセス可能な変更、**パス**で、 **~/.bashrc**次のコマンドでファイル。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> MacOS にツールをインストールします。

プレビュー **sqlcmd**と**bcp** macOS 上で利用できます。 詳細については、次を参照してください。、[アナウンス](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/)です。

*インストール[Homebrew](https://brew.sh)既にお持ちでない場合。*

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

許可されて Mac および Sierra ツールをインストールするには、次のコマンドを使用します。

```
# brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox mssql-tools
#for silent install: 
#ACCEPT_EULA=y brew install --no-sandbox mssql-tools
```

## <a id="docker"></a> Docker

SQL Server 2017 CTP 2.0 以降では、SQL Server コマンド ライン ツールは、Docker イメージに含まれます。 対話型のコマンド プロンプトで、イメージをアタッチする場合は、ツールをローカルで実行することができます。

## <a name="offline-installation"></a>オフライン インストール

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

次の表は、最新ツール パッケージの場所を示します。

| ツール パッケージ | バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM ツール パッケージ | 14.0.5.0-1 | [mssql-tools RPM package](https://packages.microsoft.com/rhel/7.3/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| SLES RPM ツール パッケージ | 14.0.5.0-1 | [mssql-tools RPM package](https://packages.microsoft.com/sles/12/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian ツール パッケージ | 14.0.5.0-1 | [mssql-tools Debian package](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |
| Ubuntu 16.10 Debian ツール パッケージ | 14.0.5.0-1 | [mssql-tools Debian package](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |

これらのパッケージに依存**移動**を最初にインストールする必要があります。 **移動**パッケージもいずれかに依存している**unixODBC devel** (RPM) または**unixodbc デベロッパー** (Debian)。 場所、**移動**パッケージは、次の表に一覧表示されます。

| msodbcsql package | バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM 移動パッケージ | 13.1.6.0-1 | [msodbcsql RPM package](https://packages.microsoft.com/rhel/7.3/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| SLES RPM 移動パッケージ | 13.1.6.0-1 | [msodbcsql RPM package](https://packages.microsoft.com/sles/12/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian msodbcsql package | 13.1.6.0-1 | [Debian パッケージの移動](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |
| Ubuntu 16.10 Debian msodbcsql package | 13.1.6.0-1 | [Debian パッケージの移動](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |

これらのパッケージを手動でインストールするには、次の手順に従います。

1. **Linux コンピューターにダウンロードしたパッケージを移動**です。 パッケージのダウンロードに、別のコンピューターを使用した場合、Linux コンピューターに、パッケージを移動する方法の 1 つはでは、 **scp**コマンド。

1. **インストール、およびパッケージ**: インストール、 **mssql ツール**と**msodbc**パッケージです。 依存関係エラーが発生した場合は、次の手順まで無視します。

    | プラットフォーム | パッケージのインストール コマンド |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo yum localinstall mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | SLES | `sudo zypper install msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo zypper install mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_13.1.6.0-1_amd64.deb`<br/>`sudo dpkg -i mssql-tools_14.0.5.0-1_amd64.deb` |

1. **見つからない依存関係を解決するには**: 見つからない依存関係をこの時点でする必要があります。 それ以外の場合は、この手順をスキップすることができます。 場合によっては、手動で検索して、これらの依存関係をインストールする必要があります。

    RPM パッケージの次のコマンドで必要な依存関係を調査できます。

    ```bash
    rpm -qpR msodbcsql-13.1.6.0-1.x86_64.rpm
    rpm -qpR mssql-tools-14.0.5.0-1.x86_64.rpm
    ```

    Debian パッケージは、それらの依存関係を含む承認済みのリポジトリにアクセスする場合、最も簡単なソリューションを使用する、 **apt get**コマンド。

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > このコマンドは、同様に SQL Server パッケージのインストールを完了します。

    これが機能しない、Debian パッケージの場合は、次のコマンドで必要な依存関係を検査することができます。

    ```bash
    dpkg -I msodbcsql_13.1.6.0-1_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_14.0.5.0-1_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>次の手順

使用する方法の例については**sqlcmd**を SQL Server に接続し、データベースを作成には、次のクイック スタートのいずれかを表示します。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)

使用する方法の例については**bcp**データを一括インポートおよびエクスポートを参照してください。 [Linux に SQL Server にデータの一括コピー](sql-server-linux-migrate-bcp.md)です。
