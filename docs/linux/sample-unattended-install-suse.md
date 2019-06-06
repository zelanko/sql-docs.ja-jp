---
title: SUSE Linux Enterprise Server 上の SQL Server の無人インストール
titleSuffix: SQL Server
description: SQL Server のスクリプト サンプル - SUSE Linux Enterprise server の無人インストール
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 6216d7b1a241229fabf9ce9d9d2ed3a63658b2a5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713569"
---
# <a name="sample-unattended-sql-server-installation-script-for-suse-linux-enterprise-server"></a>サンプル:SUSE Linux Enterprise Server の無人インストール用の SQL Server のインストール スクリプト

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このサンプルの Bash スクリプトは、対話型の入力なしの SUSE Linux Enterprise Server (SLES) v12 sp2、SQL Server 2017 をインストールします。 データベース エンジン、SQL Server エージェント、SQL Server コマンド ライン ツールのインストールの例を紹介し、インストール後の手順を実行します。 必要に応じて、フルテキスト検索をインストールし、管理ユーザーを作成できます。

> [!TIP]
> SQL Server をインストールする最も簡単な方法に従うには、無人インストール スクリプトを必要がない場合、 [SLES のクイック スタート](quickstart-install-connect-suse.md)します。 その他のセットアップの情報については、 [Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md) を参照してください。

## <a name="prerequisites"></a>前提条件

- Linux 上の SQL Server を実行するには少なくとも 2 GB のメモリ必要があります。
- ファイル システムは **XFS** または **EXT4** でなければいけません。 **BTRFS** といったその他のファイル システムはサポートされていません。
- その他のシステム要件については、[Linux 上の SQL Server のシステム要件](sql-server-linux-setup.md#system) を参照してください。

> [!IMPORTANT]
> SQL Server 2017 では、libsss_nss_idmap0 で、既定の SLES リポジトリによって提供されていない必要があります。 SLES v12 SP2 SDK からインストールすることができます。

## <a name="sample-script"></a>サンプル スクリプト

```bash
#!/bin/bash -e

# Use the following variables to control your install:

# Password for the SA user (required)
MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'

# Product ID of the version of SQL server you're installing
# Must be evaluation, developer, express, web, standard, enterprise, or your 25 digit product key
# Defaults to developer
MSSQL_PID='evaluation'

# Install SQL Server Agent (recommended)
SQL_INSTALL_AGENT='y'

# Install SQL Server Full Text Search (optional)
# SQL_INSTALL_FULLTEXT='y'

# Create an additional user with sysadmin privileges (optional)
# SQL_INSTALL_USER='<Username>'
# SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'

if [ -z $MSSQL_SA_PASSWORD ]
then
  echo Environment variable MSSQL_SA_PASSWORD must be set for unattended install
  exit 1
fi

echo Adding Microsoft repositories...
sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
sudo zypper --gpg-auto-import-keys refresh

#Add the SLES v12 SP2 SDK to obtain libsss_nss_idmap0
sudo SUSEConnect -p sle-sdk/12.2/x86_64

echo Installing SQL Server...
sudo zypper install -y mssql-server

echo Running mssql-conf setup...
sudo MSSQL_SA_PASSWORD=$MSSQL_SA_PASSWORD \
     MSSQL_PID=$MSSQL_PID \
     /opt/mssql/bin/mssql-conf -n setup accept-eula

echo Installing mssql-tools and unixODBC developer...
sudo ACCEPT_EULA=Y zypper install -y mssql-tools unixODBC-devel

# Add SQL Server tools to the path by default:
echo Adding SQL Server tools to your path...
echo PATH="$PATH:/opt/mssql-tools/bin" >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc

# Optional SQL Server Agent installation:
if [ ! -z $SQL_INSTALL_AGENT ]
then
  echo Installing SQL Server Agent...
  sudo zypper install -y mssql-server-agent
fi

# Optional SQL Server Full Text Search installation:
if [ ! -z $SQL_INSTALL_FULLTEXT ]
then
    echo Installing SQL Server Full-Text Search...
    sudo zypper install -y mssql-server-fts
fi

# Configure firewall to allow TCP port 1433:
echo Configuring SuSEfirewall2 to allow traffic on port 1433...
sudo SuSEfirewall2 open INT TCP 1433
sudo SuSEfirewall2 stop
sudo SuSEfirewall2 start

# Example of setting post-installation configuration options
# Set trace flags 1204 and 1222 for deadlock tracing:
# echo Setting trace flags...
# sudo /opt/mssql/bin/mssql-conf traceflag 1204 1222 on

# Restart SQL Server after making configuration changes:
echo Restarting SQL Server...
sudo systemctl restart mssql-server

# Connect to server and get the version:
counter=1
errstatus=1
while [ $counter -le 5 ] && [ $errstatus = 1 ]
do
  echo Waiting for SQL Server to start...
  sleep 5s
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "SELECT @@VERSION" 2>/dev/null
  errstatus=$?
  ((counter++))
done

# Display error if connection failed:
if [ $errstatus = 1 ]
then
  echo Cannot connect to SQL Server, installation aborted
  exit $errstatus
fi

# Optional new user creation:
if [ ! -z $SQL_INSTALL_USER ] && [ ! -z $SQL_INSTALL_USER_PASSWORD ]
then
  echo Creating user $SQL_INSTALL_USER
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "CREATE LOGIN [$SQL_INSTALL_USER] WITH PASSWORD=N'$SQL_INSTALL_USER_PASSWORD', DEFAULT_DATABASE=[master], CHECK_EXPIRATION=ON, CHECK_POLICY=ON; ALTER SERVER ROLE [sysadmin] ADD MEMBER [$SQL_INSTALL_USER]"
fi

echo Done!
```

### <a name="running-the-script"></a>スクリプトを実行します。

スクリプトを実行するには

1. サンプルをお気に入りのテキストエディターに貼り付け、`install_sql.sh` といった覚えやすい名前で保存します。

1. `MSSQL_SA_PASSWORD`、`MSSQL_PID`、および変更したいその他の変数をカスタマイズします。

1. スクリプトを実行可能としてマークします

   ```bash
   chmod +x install_sql.sh
   ```

1. スクリプトを実行します

   ```bash
   ./install_sql.sh
   ```

### <a name="understanding-the-script"></a>スクリプトをについてください。
Bash スクリプトでは、まず変数を設定します。 これらの変数は、このサンプルのようにスクリプト変数として指定することもできますし、環境変数として指定することもできます。 変数 `MSSQL_SA_PASSWORD` は SQL Server インストールでは **必須** です。その他は、スクリプト用に作成されたカスタム変数です。 サンプル スクリプトは、次の手順を実行します。

1. Microsoft GPG の公開鍵をインポートします。

1. SQL Server およびコマンド ライン ツール用の Microsoft リポジトリを登録します。

1. ローカル リポジトリを更新します。

1. SQL Server をインストールする

1. ```MSSQL_SA_PASSWORD``` で SQL Server を構成し、使用許諾契約書に自動的に同意します。

1. SQL Server コマンド ライン ツールの使用許諾契約書に自動的に同意し、インストールを行い、unixodbc-devel パッケージをインストールします。

1. SQL Server コマンド ライン ツールを使いやすくするために、パスに追加します。

1. スクリプト変数 ```SQL_INSTALL_AGENT``` が設定されている場合もしくはデフォルトで、SQL Server エージェントをインストールします。

1. 変数 ```SQL_INSTALL_FULLTEXT``` が設定されている場合、SQL Server フルテキスト検索をインストールすることもできます。

1. 別のシステムから SQL Server に接続するために必要な tcp ポート 1433 のブロックをファイアウォール上で解除します。

1. 必要に応じてデッドロックのトレースのトレース フラグを設定します。 (行のコメントを解除する必要があります)

1. これで SQL Server がインストールされました。利用できるようにするために、プロセスを再起動します。

1. すべてのエラー メッセージを非表示にし、 SQL Server が正しくインストールされていることを確認します。

1. ```SQL_INSTALL_USER``` と ```SQL_INSTALL_USER_PASSWORD``` がどちらも設定されている場合、新しいサーバー管理者のユーザーを作成します。

## <a name="next-steps"></a>次のステップ

複数回の無人インストールを簡略化し、適切な環境変数を設定するスタンドアロン Bash スクリプトを作成します。 サンプル スクリプトが使用している変数はいずれも削除することができ、独自の Bash スクリプトに配置することができます。

```bash
#!/bin/bash
export MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'
export MSSQL_PID='evaluation'
export SQL_INSTALL_AGENT='y'
export SQL_INSTALL_USER='<Username>'
export SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'
export SQL_INSTALL_AGENT='y'
```

その後、次のようにBash スクリプトを実行します。
```bash
. ./my_script_name.sh
```

Linux 上の SQL Server に関する詳細については、次を参照してください。 [SQL Server on Linux の概要](sql-server-linux-overview.md)します。
