---
title: Linux および macOS Microsoft Drivers for PHP for SQL Server のインストール チュートリアル |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: c1115eaf304fa360cf446b67fe98157d324c2347
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux および macOS Microsoft Drivers for PHP for SQL Server のインストールのチュートリアル
次の手順では、クリーンな環境を想定しており、PHP 7.x、Microsoft ODBC driver、Apache、および Microsoft Drivers for PHP および用のインストール Ubuntu と 16.04 17.10、RedHat 7 上の SQL Server、Debian 8 と 9、Suse 12 と macOS X 10.11 10.12 する方法を示します。 これらの手順では、PECL を使用してドライバーをインストールするよう指示がからビルド済みのバイナリをダウンロードすることも、 [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github ページのプロジェクトおよび」の手順に従ってそれらをインストール[SQL server 用 Microsoft Drivers for PHP 読み込む](../../connect/php/loading-the-php-sql-driver.md)します。 拡張機能の読み込みと理由おに追加していない拡張機能 php.ini の詳細についてを参照してください[ドライバーを読み込む](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup)します。

これらの命令インストール PHP 7.2 - 既定では、PHP 7.0 をインストールするには、各セクションまたは 7.1 の先頭にある注意事項を参照してください。

## <a name="contents-of-this-page"></a>このページの内容:

- [Ubuntu 16.04 および 17.10 にドライバーをインストールします。](#installing-the-drivers-on-ubuntu-1604-and-1710)
- [Red Hat 7 に、ドライバーをインストールします。](#installing-the-drivers-on-red-hat-7)
- [Debian 8. と 9. でドライバーをインストールします。](#installing-the-drivers-on-debian-8-and-9)
- [Suse 12 に、ドライバーをインストールします。](#installing-the-drivers-on-suse-12)
- [許可されておよび Sierra macos ドライバーをインストールします。](#installing-the-drivers-on-macos-el-capitan-and-sierra)

## <a name="installing-the-drivers-on-ubuntu-1604-and-1710"></a>Ubuntu 16.04 および 17.10 にドライバーをインストールします。

> [!NOTE]
> PHP 7.0 または 7.1 をインストールするには、7.0、または次のコマンドで 7.1 で 7.2 を置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.2 php7.2-dev php7.2-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
Ubuntu 用の指示に従って、ODBC ドライバーをインストール、 [Linux や macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)です。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 [、インストールをテスト](#testing-your-installation)、このドキュメントの最後。

## <a name="installing-the-drivers-on-red-hat-7"></a>Red Hat 7 に、ドライバーをインストールします。

> [!NOTE]
> PHP 7.0 または 7.1 をインストールするには、remi php70 または次のコマンドでそれぞれの remi php71 で remi php72 を置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum-config-manager --enable remi-php72
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
次の手順の Red Hat 7 の ODBC ドライバーをインストール、 [Linux や macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)です。

PHP 7.2 と PECL と PHP のドライバーをコンパイルするには、既定値よりも新しい GCC が必要です。
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
PECL で発生する問題は、GCC をアップグレードした場合でも、ドライバーの最新バージョンの正しいインストールにすることができなくなります。 インストールするには、パッケージをダウンロードし、手動でコンパイルします。
```
pecl download sqlsrv
tar xvzf sqlsrv-5.2.0.tgz
cd sqlsrv-5.2.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
またはからビルド済みのバイナリをダウンロードすることができます、 [Github プロジェクト ページ](https://github.com/Microsoft/msphpsql/releases)、Remi リポジトリからインストールします。
```
sudo yum install php-sqlsrv php-pdo_sqlsrv
```
### <a name="step-4-install-apache"></a>手順 4. Apache をインストールします。
```
sudo yum install httpd
```
SELinux は既定ではインストールし、Enforcing モードで実行します。 Apache SELinux を通じてデータベースに接続を許可するのには、次のコマンドを実行します。
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo apachectl restart
```
インストールをテストするには、次を参照してください。 [、インストールをテスト](#testing-your-installation)、このドキュメントの最後。

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Debian 8. と 9. でドライバーをインストールします。

> [!NOTE]
> PHP 7.0 または 7.1 をインストールするには、7.0 または 7.1 で次のコマンドで 7.2 を置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.2 php7.2-dev php7.2-xml
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
次の手順の Debian の ODBC ドライバーをインストール、 [Linux や macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)です。 

また、ブラウザーで正しく表示する PHP の出力を取得する適切なロケールを生成する必要があります。 たとえば、en_US utf-8 ロケールの場合は、次のコマンドを実行します。
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
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 [、インストールをテスト](#testing-your-installation)、このドキュメントの最後。

## <a name="installing-the-drivers-on-suse-12"></a>Suse 12 に、ドライバーをインストールします。

> [!NOTE]
> PHP 7.0 をインストールするには、skip 次のコマンドは、suse 12 の既定の PHP は 7.0 のリポジトリを追加します。
> PHP 7.1 をインストールするには、次の URL を下のリポジトリの URL に置き換えます。 `http://download.opensuse.org/repositories/devel:/languages:/php:/php71/SLE_12/devel:languages:php:php71.repo`

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
zypper -n ar -f http://download.opensuse.org/repositories/devel:languages:php/SLE_12/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
次の手順の Suse 12 の ODBC ドライバーをインストール、 [Linux や macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)です。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo systemctl restart apache2
```
インストールをテストするには、次を参照してください。 [、インストールをテスト](#testing-your-installation)、このドキュメントの最後。

## <a name="installing-the-drivers-on-macos-el-capitan-and-sierra"></a>許可されておよび Sierra macos ドライバーをインストールします。

既にがあるありませんが場合、は、次のように brew をインストールします。
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> PHP 7.0 または 7.1 をインストールするには、置換php@7.2でphp@7.0またはphp@7.1次のコマンドでそれぞれします。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。

```
brew tap
brew tap homebrew/core
brew install php@7.2
```
PHP が実行--パスにする必要があります今すぐ`php -v`を正しいバージョンの PHP が実行されていることを確認します。 PHP がパス上にあるか、次を実行して、正しいバージョンではありません: 場合
```
brew link --force --overwrite php@7.2
```

### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
次の手順の macOS の ODBC ドライバーをインストール、 [Linux や macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)です。 

さらに、GNU 作成ツールをインストールする必要があります。
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
brew install apache2
```
Apache Apache インストール用の構成ファイルを検索するには、次のように実行します。 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
パスを置き換えると`httpd.conf`次のコマンドで。
```
echo "LoadModule php7_module /usr/local/opt/php@7.2/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo apachectl restart
```
インストールをテストするには、次を参照してください。 [、インストールをテスト](#testing-your-installation)、このドキュメントの最後。

## <a name="testing-your-installation"></a>インストールのテスト

このサンプル スクリプトをテストするには、システムのドキュメントのルートで testsql.php という名前のファイルを作成します。 これは`/var/www/html/`Ubuntu、Debian、および Redhat、 `/srv/www/htdocs` SUSE、上または`/usr/local/var/www`macos です。 サーバー、データベース、ユーザー名、および必要に応じてパスワードを交換して、次のスクリプトをコピーします。
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "Database" => "yourDatabase",
    "Uid" => "yourUsername",
    "PWD" => "yourPassword"
);

//Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if( $conn === false ) {
    die( FormatErrors( sqlsrv_errors()));
}

//Select Query
$tsql= "SELECT @@Version as SQL_VERSION";

//Executes the query
$getResults= sqlsrv_query($conn, $tsql);

//Error handling
if ($getResults == FALSE)
    die(FormatErrors(sqlsrv_errors()));
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($getResults, SQLSRV_FETCH_ASSOC)) {
    echo ($row['SQL_VERSION']);
    echo ("<br/>");
}

sqlsrv_free_stmt($getResults);

function FormatErrors( $errors )
{
    /* Display errors. */
    echo "Error information: <br/>";
    foreach ( $errors as $error )
    {
        echo "SQLSTATE: ".$error['SQLSTATE']."<br/>";
        echo "Code: ".$error['code']."<br/>";
        echo "Message: ".$error['message']."<br/>";
    }
}
?>
```
ブラウザーのポイントhttp://localhost/testsql.php(http://localhost:8080/testsql.php macos)。 SQL Server と Azure SQL データベースに接続できるようになりましたに。

## <a name="see-also"></a>参照  
[入門 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Microsoft Drivers for PHP SQL Server を読み込む](../../connect/php/loading-the-php-sql-driver.md)

[システム要件の Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
