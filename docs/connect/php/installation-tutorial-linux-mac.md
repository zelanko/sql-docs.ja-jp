---
title: Linux と macOS の Microsoft Drivers for PHP for SQL Server のインストールのチュートリアル |Microsoft Docs
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: a31b17b8fbe2130b84b27be08d1a6218d697f9f2
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744632"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux と macOS の Microsoft Drivers for PHP for SQL Server のインストールのチュートリアル
次の手順は、クリーンな環境を想定し、PHP 7.x、Microsoft ODBC driver、Apache、および Microsoft Drivers for PHP for ubuntu 16.04、18.04、および 18.10、red Hat 7、Debian 8、9、SQL Server をインストールする方法について説明 Suse 12、15、および macOS 10.12、10.13、および 10.14 します。 これらの手順では、PECL を使用してドライバーをインストールするよう指示がからビルド済みのバイナリをダウンロードすることも、 [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github プロジェクト ページおよび」の手順に従ってそれらをインストール[For PHP for SQL Server、Microsoft ドライバーを読み込み](../../connect/php/loading-the-php-sql-driver.md)します。 拡張機能の読み込み、なぜ私たちを追加しない拡張機能を php.ini の詳細については、上のセクションを参照してください。[ドライバーを読み込む](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup)します。

これらの手順では、既定では PHP 7.3 をインストールします。 For SQL Server--PHP ドライバーのサポートされていない Linux ディストリビューションの既定を PHP 7.0 以前がサポートされているいくつかメモは、PHP 7.1 または 7.2 の代わりにインストールするには、各セクションの先頭にある注記を参照してください。

## <a name="contents-of-this-page"></a>このページの内容:

- [Ubuntu 16.04、18.04、および 18.10 でドライバーをインストールします。](#installing-the-drivers-on-ubuntu-1604-1804-and-1810)
- [Red Hat 7 でドライバーをインストールします。](#installing-the-drivers-on-red-hat-7)
- [Debian 8 と 9 にドライバーをインストールします。](#installing-the-drivers-on-debian-8-and-9)
- [Suse 12、15 のドライバーをインストールします。](#installing-the-drivers-on-suse-12-and-15)
- [MacOS Sierra、High Sierra、および Mojave でドライバーをインストールします。](#installing-the-drivers-on-macos-sierra-high-sierra-and-mojave)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1810"></a>Ubuntu 16.04、18.04、および 18.10 でドライバーをインストールします。

> [!NOTE]
> PHP 7.1、7.2 をインストールするには、7.1、7.2 次のコマンドと 7.3 を置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.3 php7.3-dev php7.3-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順で Ubuntu の ODBC ドライバーをインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールして、ドライバーの読み込みを構成します。
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="installing-the-drivers-on-red-hat-7"></a>Red Hat 7 でドライバーをインストールします。

> [!NOTE]
> PHP 7.1、7.2 をインストールするには、remi php71 または remi-php72 それぞれに、次のコマンドで remi php73 を置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php73
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順で Red Hat 7 用 ODBC ドライバーをインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

PHP 7.2 と 7.3 PECL の PHP ドライバーをコンパイルするには、既定値よりも最近 GCC が必要です。
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
PECL で発生する問題は、GCC をアップグレードした場合でも、ドライバーの最新バージョンの正しいインストールをできない可能性があります。 インストール、パッケージをダウンロードおよびコンパイルを手動で (pdo_sqlsrv の同様の手順)。
```
pecl download sqlsrv
tar xvzf sqlsrv-5.6.0.tgz
cd sqlsrv-5.6.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
またはからビルド済みのバイナリをダウンロードすることができます、 [Github プロジェクト ページ](https://github.com/Microsoft/msphpsql/releases)、または Remi リポジトリからインストールします。
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>手順 4. Apache をインストールします。
```
sudo yum install httpd
```
SELinux は既定でインストールし、Enforcing モードで実行します。 SELinux をデータベースに接続する Apache を許可するのには、次のコマンドを実行します。
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo apachectl restart
```
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Debian 8 と 9 にドライバーをインストールします。

> [!NOTE]
> PHP 7.1、7.2 をインストールするには、7.1、7.2 と 7.3 では、次のコマンドを置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.3 php7.3-dev php7.3-xml
```
### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順で Debian 用 ODBC ドライバーをインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。 

また、ブラウザーで正しく表示する PHP の出力を取得する適切なロケールを生成する必要があります。 たとえば、en_US utf-8 ロケールの場合に、次のコマンドを実行します。
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールして、ドライバーの読み込みを構成します。
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Suse 12、15 のドライバーをインストールします。

> [!NOTE]
> 次の手順で置換<SuseVersion>Suse でのバージョンの場合、Suse Enterprise Linux 15 を使用していることが SLE_15 または SLE_15_SP1 と同様に他のバージョン。 Suse Linux でのすべてのバージョンを参照してください、PHP のすべてのバージョンが利用`http://download.opensuse.org/repositories/devel:/languages:/php`Suse のどのバージョンがある使用可能な PHP の既定のバージョンを確認するまたは`http://download.opensuse.org/repositories/devel:/languages:/php:/`を確認するその他のバージョンの PHP は Suse のどのバージョンを使用できます。

> [!NOTE]
> Suse 12 の PHP 7.3 のパッケージが利用できません。 PHP 7.1 をインストールするには、次の URL での下のリポジトリの URL を置き換えます:`https://download.opensuse.org/repositories/devel:/languages:/php:/php71/<SuseVersion>/devel:languages:php:php71.repo`します。
> PHP 7.2 をインストールするには、次の URL での下のリポジトリの URL を置き換えます:`https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`します。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順で Suse 用 ODBC ドライバーをインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
> [!NOTE]
> というエラー メッセージが表示された場合`Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`、/usr/bin/pecl で pecl のスクリプトを編集および削除、`-n`最後の行に切り替えます。 このスイッチは、PHP が呼び出されると、OpenSSL 拡張機能を読み込みを禁止する ini ファイルの読み込みから PECL をできないようにします。

```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールして、ドライバーの読み込みを構成します。
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo systemctl restart apache2
```
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="installing-the-drivers-on-macos-sierra-high-sierra-and-mojave"></a>MacOS Sierra、High Sierra、および Mojave でドライバーをインストールします。

既にがあるありませんが場合、は、次のように brew をインストールします。
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> PHP 7.1、7.2 をインストールするには、置き換えるphp@7.3でphp@7.1またはphp@7.2それぞれに、次のコマンド。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。

```
brew tap
brew tap homebrew/core
brew install php@7.3
```
PHP が実行 - パスになります`php -v`を正しいバージョンの PHP が実行されていることを確認します。 PHP は、パスにない、または適切なバージョンではありませんは、次を実行します。
```
brew link --force --overwrite php@7.3
```

### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順での macOS の ODBC ドライバーのインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。 

さらに、GNU 作成ツールをインストールする必要があります。
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールして、ドライバーの読み込みを構成します。
```
brew install apache2
```
Apache、Apache インストールの構成ファイルを検索するには、次のように実行します。 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
パスを置き換えると`httpd.conf`次のコマンド。
```
echo "LoadModule php7_module /usr/local/opt/php@7.2/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo apachectl restart
```
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="testing-your-installation"></a>インストールのテスト

このサンプル スクリプトをテストするには、システムのドキュメントのルートで testsql.php をという名前のファイルを作成します。 これは`/var/www/html/`では、Ubuntu、Debian、および red Hat、 `/srv/www/htdocs` 、SUSE にまたは`/usr/local/var/www`macOS でします。 サーバー、データベース、ユーザー名、および適切なパスワードに置き換えて、次のスクリプトをコピーします。
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "database" => "yourDatabase",
    "uid" => "yourUsername",
    "pwd" => "yourPassword"
);

// Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if ($conn === false) {
    die(formatErrors(sqlsrv_errors()));
}

// Select Query
$tsql = "SELECT @@Version AS SQL_VERSION";

// Executes the query
$stmt = sqlsrv_query($conn, $tsql);

// Error handling
if ($stmt === false) {
    die(formatErrors(sqlsrv_errors()));
}
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
    echo $row['SQL_VERSION'] . PHP_EOL;
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

function formatErrors($errors)
{
    // Display errors
    echo "Error information: <br/>";
    foreach ($errors as $error) {
        echo "SQLSTATE: ". $error['SQLSTATE'] . "<br/>";
        echo "Code: ". $error['code'] . "<br/>";
        echo "Message: ". $error['message'] . "<br/>";
    }
}
?>
```
ブラウザーをポイントします https://localhost/testsql.php(https://localhost:8080/testsql.php macos)。 SQL Server または Azure SQL database に接続できるようになりましたにします。

## <a name="see-also"></a>参照  
[概要 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Microsoft SQL Server 用 Drivers for PHP を読み込む](../../connect/php/loading-the-php-sql-driver.md)

[Microsoft SQL Server 用 Drivers for PHP のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)
