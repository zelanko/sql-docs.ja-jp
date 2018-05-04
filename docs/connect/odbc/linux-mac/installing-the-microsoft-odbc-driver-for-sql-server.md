---
title: Linux および macOS 上の SQL Server 用 Microsoft ODBC Driver をインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48397442b628be54f0d25d545dacc6c494a00d75
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="installing-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Linux および macOS に Microsoft ODBC Driver for SQL Server をインストールする
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

この記事をインストールする方法を説明します、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux と macOS、SQL Server の省略可能なコマンド ライン ツールに (`bcp`と`sqlcmd`) および unixODBC 開発ヘッダー。

## <a name="microsoft-odbc-driver-17-for-sql-server"></a>SQL Server 用 Microsoft ODBC Driver 17 

> [!IMPORTANT]
> V17 をインストールした場合`msodbcsql`について簡単に使用可能なパッケージを削除するかインストールする前に、`msodbcsql17`パッケージです。 これにより、競合が回避されます。 `msodbcsql17`でパッケージをインストールする、 `msodbcsql` v13 パッケージです。

### <a name="debian-8-and-9"></a>Debian 8 と 9
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Debian 8
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Debian 9
curl https://packages.microsoft.com/config/debian/9/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6-and-7"></a>Red Hat Enterprise Server 6、7
```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#RedHat Enterprise Server 6
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo

#RedHat Enterprise Server 7
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo

exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11sp4-and-12"></a>SUSE Linux Enterprise Server 11SP4、12

```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#SUSE Linux Enterprise Server 11 SP4
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo

#SUSE Linux Enterprise Server 12
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo

exit
sudo ACCEPT_EULA=Y zypper install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1404-1604-and-1710"></a>Ubuntu 14.04、16.04 と 17.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Ubuntu 14.04
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 16.04
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 17.10
curl https://packages.microsoft.com/config/ubuntu/17.10/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="os-x-1011-el-capitan-macos-1012-sierra-and-macos-1013-high-sierra"></a>OS X 10.11 (許可されて)、macOS 10.12 (Sierra) や macOS 10.13 (高 Sierra)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox msodbcsql17 mssql-tools
```

## <a name="microsoft-odbc-driver-131-for-sql-server"></a>Microsoft ODBC Driver 13.1 for SQL Server 

### <a name="debian-8"></a>Debian 8
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11"></a>SUSE Linux Enterprise Server 11

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1610"></a>Ubuntu 16.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="os-x-1011-el-capitan-and-macos-1012-sierra"></a>OS X 10.11 (許可されて) や macOS 10.12 (Sierra)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="microsoft-odbc-driver-13-for-sql-server"></a>Microsoft ODBC Driver 13 for SQL Server

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su 
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo 
zypper update 
sudo ACCEPT_EULA=Y zypper install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
zypper install unixODBC-utf16-devel
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="offline-installation"></a>オフライン インストール
優先または必要とする場合、[!INCLUDE[msCoName](../../../includes/msconame_md.md)]パッケージの依存関係を手動で解決する必要があるインターネットに接続せずにコンピューターにインストールされる ODBC Driver 13、します。 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 が次の直接の依存関係。
- Ubuntu: libc6 (> = 2.21)、ため libstdc++ + + 6 (> = 4.9)、libkrb5 3、libcurl3、openssl、debconf (> = 0.5)、unixodbc (> 2.3.1-1 を =)
- Red Hat は: ```glibc, e2fsprogs, krb5-libs, openssl, unixODBC```
- SuSE: ```glibc, libuuid1, krb5, openssl, unixODBC```

これらの各パッケージが、独自の依存関係があり、システムに存在していない可能性があります。 この問題に一般的なソリューションは、配布のパッケージ マネージャーのドキュメントを参照してください: [Red Hat](https://wiki.centos.org/HowTos/CreateLocalRepos)、 [Ubuntu](http://unix.stackexchange.com/questions/87130/how-to-quickly-create-a-local-apt-repository-for-random-packages-using-a-debian)、および[SUSE](https://en.opensuse.org/Portal:Zypper)

終了したすべての依存パッケージを手動でダウンロード、インストール コンピューター上に一緒に配置し、各パッケージを手動でインストールに共通ではまた、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 パッケージです。

#### <a name="redhat-linux-enterprise-server-7"></a>Red Hat Linux Enterprise Server 7
  - 最新版をダウンロード`msodbcsql``.rpm`ここから。 http://packages.microsoft.com/rhel/7/prod/
  - 依存関係と、ドライバーをインストールします。
  
```
yum install glibc e2fsprogs krb5-libs openssl unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

#### <a name="ubuntu-1604"></a>Ubuntu 16.04
- 最新版をダウンロード`msodbcsql``.deb`ここから。 http://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/ 
- 依存関係と、ドライバーをインストールします。 

```
sudo apt-get install libc6 libstdc++6 libkrb5-3 libcurl3 openssl debconf unixodbc unixodbc-dev #install dependencies
sudo dpkg -i msodbcsql_13.1.X.X-X_amd64.deb #install the Driver
```

#### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12
- 最新版をダウンロード`msodbcsql``.rpm`ここから。 http://packages.microsoft.com/sles/12/prod/
- 依存関係と、ドライバーをインストールします。

```
zypper install glibc, libuuid1, krb5, openssl, unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

パッケージのインストールが完了したら、できることを確認する、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 ldd を実行し、不足しているライブラリの出力を調べることですべての依存関係を見つけることができます。
```
ldd /opt/microsoft/msodbcsql/lib64/libmsodbcsql-*
```
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-linux"></a>Microsoft ODBC Driver 11 for SQL Server on Linux

ドライバーを使用することができます、前に、unixODBC ドライバー マネージャーをインストールします。 詳細については、次を参照してください。 [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)です。

**インストール手順**  

> [!IMPORTANT]  
> これらの手順を参照してください`msodbcsql-11.0.2270.0.tar.gz`、Red Hat Linux 用のインストール ファイルがあります。 SUSE Linux のプレビューをインストールする場合、ファイル名は`msodbcsql-11.0.2260.0.tar.gz`します。  
  
ドライバーをインストールするには:

1.  ルートのアクセス許可があることを確認します。  

2.  ダウンロードがファイルを配置する場所のディレクトリに移動`msodbcsql-11.0.2270.0.tar.gz`です。 使用している Linux のバージョンに対応する \*.tar.gz ファイルがあることを確認します。 ファイルを抽出は、次のコマンドを実行する`tar xvzf msodbcsql-11.0.2270.0.tar.gz`です。  
  
3.  変更、`msodbcsql-11.0.2270.0`ディレクトリがという名前のファイルを表示する必要がありますと**内に install.sh**です。  
  
4.  使用可能なインストール オプションの一覧を表示するには、コマンド **./install.sh**を実行します。  
  
5.  **odbcinst.ini**のバックアップを作成します。 ドライバーのインストールで、 **odbcinst.ini**を更新します。 odbcinst.ini には、unixODBC ドライバー マネージャーで登録されたドライバーの一覧が含まれます。 コンピューターの odbcinst.ini の場所を検出するには、次のコマンドを実行します。```odbc_config --odbcinstini```です。  
  
6.  ドライバーをインストールする前に、次のコマンドを実行します。`./install.sh verify`です。 出力`./install.sh verify`on Linux の ODBC ドライバーをサポートするために必要なソフトウェアがコンピューターにあるかどうかに報告します。  
  
7.  Linux の ODBC ドライバーをインストールする準備ができたら、コマンドを実行します。`./install.sh install`です。 インストール コマンドを指定する必要がある場合 (`bin-dir`または`lib-dir`)、後にコマンドを指定して、**インストール**オプション。  
  
8.  使用許諾契約を確認し、 **YES** と入力してインストールを続行します。  
  
インストールによって、ドライバー`/opt/microsoft/msodbcsql/11.0.2270.0`です。 ドライバーとそのサポート ファイルである必要があります`/opt/microsoft/msodbcsql/11.0.2270.0`です。  
  
Microsoft ODBC driver on Linux が正常に登録されていることを確認するには、次のコマンドを実行します。```odbcinst -q -d -n "ODBC Driver 11 for SQL Server"```です。  
  
「[Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux (Linux の ODBC ドライバーに既存の MSDN C++ ODBC サンプルを使用する)](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) 」には、Linux の ODBC ドライバーを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] に接続するコード サンプルが紹介されています。  
  
**アンインストール**  
  
Linux で ODBC driver 11 をアンインストールするには、次のコマンドを実行します。  
  
1.  `rm -f /usr/bin/sqlcmd`
  
2.  `rm -f /usr/bin/bcp`  
  
3.  `rm -rf /opt/microsoft/msodbcsql`  
  
4.  `odbcinst -u -d -n "ODBC Driver 11 for SQL Server"`
  
## <a name="troubleshooting-connection-problems"></a>接続の問題のトラブルシューティング  
接続できない場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]次の情報を使用して、問題を特定する ODBC ドライバーを使用します。  
  
最も一般的な接続の問題は、2 つの UnixODBC ドライバー マネージャーがインストールされている場合です。 /usr で libodbc\*.so\*を検索します。 複数バージョンのファイルがある場合、複数のドライバー マネージャーがインストールされている可能性があります。 また、アプリケーションに不適切なバージョンが使用される可能性があります。
  
編集することによって、接続ログを有効にする、`/etc/odbcinst.ini`をこれらの項目には、次のセクションを含めるファイル。

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
別の接続エラーが発生し、ログ ファイルが見つからない場合、コンピューターに 2 つのドライバー マネージャーが存在する可能性があります。 それ以外の場合、ログの出力は次のようになります。  
  
```  
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 13 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
ASCII 文字エンコーディングがない場合、utf-8 などです。 
  
```  
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
複数のドライバー マネージャーがインストールされていると、アプリケーションが 1 つ、または、ドライバー マネージャーが正しく構築されなかった間違ったを使用して 1 つです。  
  
接続エラーの解決の詳細については、以下を参照してください。  
  
-   [SQL の接続問題のトラブルシューティングの手順](http://blogs.msdn.com/b/sql_protocols/archive/2008/04/30/steps-to-troubleshoot-connectivity-issues.aspx)  
  
-   [SQL Server 2005 Connectivity Issue Troubleshoot - Part I (SQL Server 2005 の接続に関する問題のトラブルシューティング - パート 1)](http://blogs.msdn.com/b/sql_protocols/archive/2005/10/22/sql-server-2005-connectivity-issue-troubleshoot-part-i.aspx)  
  
-   [Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer (接続リング バッファーを使用している SQL Server 2008 の接続のトラブルシューティング)](http://blogs.msdn.com/b/sql_protocols/archive/2008/05/20/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer.aspx)  
  
-   [SQL Server Authentication Troubleshooter (SQL Server 認証のトラブルシューティング)](http://blogs.msdn.com/b/sqlsecurity/archive/2010/03/29/sql-server-authentication-troubleshooter.aspx)  
  
-   [エラーの詳細 (http://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=11001)](http://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=001)  
  
    URL (11001) に指定するエラー番号は、表示されたエラーに合わせて変更する必要があります。  
  
## <a name="driver-files"></a>ドライバー ファイル
ODBC Driver on Linux and MacOS は、次のコンポーネントで構成されます。

### <a name="linux"></a>Linux

|コンポーネント|Description|  
|---------------|-----------------|  
|libmsodbcsql 17 です。X.so.X.X または libmsodbcsql 13。X.so.X.X|共有オブジェクト (`so`) のすべてのドライバーの機能を含むダイナミック ライブラリ ファイル。 このファイルがインストールされている`/opt/microsoft/msodbcsql17/lib64/`ドライバー 17 し`/opt/microsoft/msodbcsql/lib64/`Driver 13。|  
|`msodbcsqlr17.rll`または`msodbcsqlr13.rll`|ドライバー ライブラリに付随するリソース ファイル。 このファイルはのインストールします。 `[driver .so directory]../share/resources/en_US/`| 
|msodbcsql.h|すべてのドライバーを使用するために必要な新しい定義を含むヘッダー ファイル。<br /><br /> **注:**  msodbcsql.h と odbcss.h を同じプログラムで参照することはできません。<br /><br /> msodbcsql.h にインストールされている`/opt/microsoft/msodbcsql17/include/`ドライバー 17 し`/opt/microsoft/msodbcsql/include/`Driver 13。 |
|LICENSE.txt|使用許諾契約書の用語を含むテキスト ファイル。 このファイルが配置されます`/usr/share/doc/msodbcsql17/`ドライバー 17 し`/usr/share/doc/msodbcsql/`Driver 13。|
|RELEASE_NOTES|リリース ノートを含むテキスト ファイル。 このファイルが配置されます`/usr/share/doc/msodbcsql17/`ドライバー 17 し`/usr/share/doc/msodbcsql/`Driver 13。|


### <a name="macos"></a>MacOS

|コンポーネント|Description|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib or libmsodbcsql.13.dylib|ダイナミック ライブラリ (`dylib`) のすべてのドライバーの機能を含むファイルです。 このファイルがインストールされている`/usr/local/lib/`です。|  
|`msodbcsqlr17.rll`または`msodbcsqlr13.rll`|ドライバー ライブラリに付随するリソース ファイル。 このファイルがインストールされている`[driver .dylib directory]../share/msodbcsql17/resources/en_US/`ドライバー 17 し`[driver .dylib directory]../share/msodbcsql/resources/en_US/`Driver 13。 | 
|msodbcsql.h|すべてのドライバーを使用するために必要な新しい定義を含むヘッダー ファイル。<br /><br /> **注:**  msodbcsql.h と odbcss.h を同じプログラムで参照することはできません。<br /><br /> msodbcsql.h にインストールされている`/usr/local/include/msodbcsql17/`ドライバー 17 し`/usr/local/include/msodbcsql/`Driver 13。 |
|LICENSE.txt|使用許諾契約書の用語を含むテキスト ファイル。 このファイルが配置されます`/usr/local/share/doc/msodbcsql17/`ドライバー 17 し`/usr/local/share/doc/msodbcsql/`Driver 13。 |
|RELEASE_NOTES|リリース ノートを含むテキスト ファイル。 このファイルが配置されます`/usr/local/share/doc/msodbcsql17/`ドライバー 17 し`/usr/local/share/doc/msodbcsql/`Driver 13。 |

## <a name="resource-file-loading"></a>リソース ファイルの読み込み

ドライバーは、機能するために、リソース ファイルを読み込む必要があります。 このファイルが呼び出され`msodbcsqlr17.rll`または`msodbcsqlr13.rll`ドライバーのバージョンによって異なります。 場所、`.rll`ドライバー自体の場所に対する相対ファイル パスです (`so`または`dylib`) 上の表で説明したとおり、します。 ドライバーは、読み込みにも試みますバージョン 17.1 の時点で、`.rll`既定値からディレクトリの相対パスから読み込む場合は失敗します。 リソース ファイルの既定のパスは次のとおりです。

Linux: `/opt/microsoft/msodbcsql17/share/resources/en_US/`

MacOS: `/usr/local/share/msodbcsql17/resources/en_US/`


  
## <a name="see-also"></a>参照

[ドライバー マネージャーのインストール](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)

[システム要件](../../../connect/odbc/linux-mac/system-requirements.md)
