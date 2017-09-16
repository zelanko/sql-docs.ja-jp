---
title: "PHP Linux、Mac ドライバー インストール チュートリアル |Microsoft ドキュメント"
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
author: ulvii
ms.author: v-ulibra
manager: Hadis Fard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6ca464b620a092a910d341c90b0fec364dadd89b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="php-linux-and-mac-drivers-installation-tutorial"></a>PHP の Linux および Mac のドライバーのインストールのチュートリアル
以下の手順は、クリーンな環境を想定し、PHP 7.x、Microsoft ODBC ドライバー、Apache、および Microsoft PHP をインストールする方法を示して Ubuntu 15.10、16.04、RedHat 7、Debian 8、および Mac OS X 上のドライバーです。
## <a name="installing-the-drivers-on-ubuntu-1510-for-php-70"></a>PHP 7.0 Ubuntu 15.10 でドライバーのインストール
Ubuntu 15.10 の使用可能な PHP 7.1 パッケージはありません。
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
sh -c 'echo "deb http://packages.dotdeb.org jessie all \ndeb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list'
apt-get update
apt-get install php7.0 php7.0-fpm php-pear php7.0-dev mcrypt php7.0-mcrypt php-mbstring php7.0-xml
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql mssql-tools
sudo apt-get install unixodbc-dev
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pear config-set php_ini `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"` system
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.0 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.0
echo "extension=sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="installing-the-drivers-on-ubuntu-1604-for-php-70"></a>PHP 7.0 Ubuntu 16.04 でドライバーのインストール
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。 
```
sudo su
apt-get update
apt-get -y install php7.0 mcrypt php7.0-mcrypt php-mbstring php-pear php7.0-dev php7.0-xml 
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql mssql-tools 
sudo apt-get install unixodbc-dev
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pear config-set php_ini `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"` system
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.0 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.0
echo "extension=sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="installing-the-drivers-on-ubuntu-1604-for-php-71"></a>PHP 7.1 Ubuntu 16.04 でドライバーのインストール
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。 
```
sudo su
add-apt-repository ppa:ondrej/php
apt-get update
apt-get -y install php7.1 mcrypt php7.1-mcrypt php-mbstring php-pear php7.1-dev php7.1-xml
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql mssql-tools 
sudo apt-get install unixodbc-dev
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pear config-set php_ini `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"` system
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.1 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.1
echo "extension=sqlsrv.so" >> /etc/php/7.1/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.1/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="installing-the-drivers-on-red-hat-7-for-php-70-and-71"></a>Red Hat 7 で PHP 7.0、7.1、ドライバーのインストール
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。 
PHP 7.1 をインストールするには、次のコマンドでの remi php71 を remi php70 に置き換えます。 
```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum-config-manager --enable remi-php70 
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC-utf16-devel
sudo ACCEPT_EULA=Y yum install msodbcsql mssql-tools 
sudo yum install unixODBC-devel
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
yum install httpd
echo "extension=sqlsrv.so" > /etc/php.d/sqlsrv.ini
echo "extension=pdo_sqlsrv.so" > /etc/php.d/pdo_sqlsrv.ini
```
SELinux は既定ではインストールし、Enforcing モードで実行します。 Apache SELinux を通じてデータベースに接続を許可するのには、次のコマンドを実行します。
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo apachectl restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="installing-the-drivers-on-debian-8-for-php-70"></a>PHP 7.0 Debian 8 でのドライバーのインストール
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。 
```
sudo su
apt-get install curl apt-transport-https
curl https://www.dotdeb.org/dotdeb.gpg | apt-key add -
echo "deb http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list
echo "deb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list
apt-get update
apt-get install –y php7.0 php-pear php7.0-dev php7.0-xml
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
apt-get install -y locales
echo "en_US.UTF-8 UTF-8" > /etc/locale.gen 
locale-gen
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
sudo apt-get install unixodbc-dev
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pear config-set php_ini `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"` system
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.0 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.0
echo "extension=sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="installing-the-drivers-on-debian-8-for-php-71"></a>PHP 7.1 Debian 8 でのドライバーのインストール
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。 
```
sudo su
apt-get install curl apt-transport-https 
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install –y php7.1 php-pear php7.1-dev php7.1-xml
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
apt-get install -y locales
echo "en_US.UTF-8 UTF-8" > /etc/locale.gen 
locale-gen
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
sudo apt-get install unixodbc-dev
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pear config-set php_ini `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"` system
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
sudo su
apt-get install libapache2-mod-php7.1 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.1
echo "extension=sqlsrv.so" >> /etc/php/7.1/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.1/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="installing-the-drivers-on-macos-el-capitan-and-sierra"></a>許可されて MacOS および Sierra にドライバーをインストールします。
### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。 
PHP 7.1 をインストールするには、次のコマンドで php71 を php70 を置き換えます。
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap 
brew tap homebrew/dupes
brew tap homebrew/versions
brew tap homebrew/homebrew-php
brew install php70 --with-pear --with-httpd24 --with-cgi
echo 'export PATH="/usr/local/sbin:$PATH"' >> ~/.bash_profile
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
```
### <a name="step-2-install-prerequisites"></a>手順 2. インストールの前提条件
```
brew tap microsoft/msodbcsql https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql
brew install mssql-tools
brew install autoconf
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>手順 4. Apache をインストールし、ドライバーの読み込みの構成
```
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/apache2/2.4/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo apachectl restart
```
インストールをテストするには、次を参照してください。 **、インストールをテスト**、このドキュメントの最後。
 
## <a name="testing-your-installation"></a>インストールのテスト
このサンプル スクリプトをテストするには、testsql.php/var www/html/で (/usr/ローカル/var/www/htdocs macos) という名前のファイルを作成し、サーバー、データベース、ユーザー名、および必要に応じてパスワードを交換して、次のスクリプトをコピーします。 
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
Http://localhost/testsql.php (macos http://localhost:8080/testsql.php) をお使いのブラウザーをポイントします。 SQL Server と Azure SQL データベースに接続できるようになりましたに。


