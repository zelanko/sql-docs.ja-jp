---
title: Linux と macOS の Microsoft Drivers for PHP for SQL Server のインストールのチュートリアル |Microsoft Docs
ms.date: 07/20/2018
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: 5b22d2c74ad356a9466c8441f979414857865386
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174899"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux と macOS の Microsoft Drivers for PHP for SQL Server のインストールのチュートリアル
次の手順がクリーンな環境を想定し、for PHP for SQL Server を Ubuntu 16.04、17.10 と 18.04、red Hat 7、Debian 8、9、Suse 12、および macOS 10.11 PHP 7.x、Microsoft ODBC driver、Apache、および Microsoft ドライバーをインストールする方法を示します、10.12 と 10.13 します。 これらの手順では、PECL を使用してドライバーをインストールするよう指示がからビルド済みのバイナリをダウンロードすることも、 [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github プロジェクト ページおよび」の手順に従ってそれらをインストール[For PHP for SQL Server、Microsoft ドライバーを読み込み](../../connect/php/loading-the-php-sql-driver.md)します。 拡張機能の読み込み、なぜ私たちを追加しない拡張機能を php.ini の詳細については、上のセクションを参照してください。[ドライバーを読み込む](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup)します。

これらの手順インストール PHP 7.2 - 既定では、PHP 7.0 をインストールするには、各セクションまたは 7.1 の先頭にある注記を参照してください。

## <a name="contents-of-this-page"></a>このページの内容:

- [Ubuntu 16.04、17.10、および 18.04 でドライバーをインストールします。](#installing-the-drivers-on-ubuntu-1604-1710-and-1804)
- [Red Hat 7 でドライバーをインストールします。](#installing-the-drivers-on-red-hat-7)
- [Debian 8 と 9 にドライバーをインストールします。](#installing-the-drivers-on-debian-8-and-9)
- [Suse 12 でドライバーをインストールします。](#installing-the-drivers-on-suse-12)
- [MacOS El Capitan、Sierra、High Sierra でドライバーをインストールします。](#installing-the-drivers-on-macos-el-capitan-sierra-and-high-sierra)

## <a name="installing-the-drivers-on-ubuntu-1604-1710-and-1804"></a>Ubuntu 16.04、17.10 と 18.04 でドライバーをインストールします。

> [!NOTE]
> PHP 7.0 または 7.1 をインストールするには、7.0、7.1 で、次のコマンドに 7.2 を置き換えます。
> Ubuntu 18.04、PHP 7.0 や 7.1 が必要な場合を除き、ondrej リポジトリを追加する手順は必要ありません。 ただし、Ubuntu 18.04 での PHP 7.0 や 7.1 のインストールが機能しない ondrej リポジトリからパッケージが付属して Ubuntu 18.04 インストール ベースで競合する可能性がある依存関係とします。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.2 php7.2-dev php7.2-xml -y --allow-unauthenticated
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
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>手順 5. Apache を再起動し、サンプル スクリプトをテストします。
```
sudo service apache2 restart
```
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="installing-the-drivers-on-red-hat-7"></a>Red Hat 7 でドライバーをインストールします。

> [!NOTE]
> PHP 7.0 または 7.1 をインストールするには、remi php70 または remi-php71 それぞれに、次のコマンドで remi php72 を置き換えます。

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
### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順で Red Hat 7 用 ODBC ドライバーをインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

PECL PHP 7.2 での PHP ドライバーをコンパイルするには、既定値よりも最近 GCC が必要です。
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
tar xvzf sqlsrv-5.3.0.tgz
cd sqlsrv-5.3.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
またはからビルド済みのバイナリをダウンロードすることができます、 [Github プロジェクト ページ](https://github.com/Microsoft/msphpsql/releases)、または Remi リポジトリからインストールします。
```
sudo yum install php-sqlsrv php-pdo_sqlsrv
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
> PHP 7.0 または 7.1 をインストールするには、7.0 または 7.1 で、次のコマンドで 7.2 を置き換えます。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.2 php7.2-dev php7.2-xml
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
インストールをテストするには、次を参照してください。[インストールのテスト](#testing-your-installation)このドキュメントの最後にします。

## <a name="installing-the-drivers-on-suse-12"></a>Suse 12 でドライバーをインストールします。

> [!NOTE]
> PHP 7.0 をインストールするには、skip 次のコマンドは、suse 12 で既定の PHP は 7.0 - リポジトリを追加します。
> PHP 7.1 をインストールするには、下のリポジトリの URL に次の URL を置き換えます。 `http://download.opensuse.org/repositories/devel:/languages:/php:/php71/SLE_12/devel:languages:php:php71.repo`

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。
```
sudo su
zypper -n ar -f http://download.opensuse.org/repositories/devel:languages:php/SLE_12/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel
```
### <a name="step-2-install-prerequisites"></a>手順 2. 必須コンポーネントのインストール
次の手順で、Suse 12 の ODBC ドライバーをインストール、 [Linux と macOS のインストール ページ](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>手順 3. Microsoft SQL Server 用 PHP ドライバーをインストールします。
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

## <a name="installing-the-drivers-on-macos-el-capitan-sierra-and-high-sierra"></a>MacOS El Capitan、Sierra、High Sierra でドライバーをインストールします。

既にがあるありませんが場合、は、次のように brew をインストールします。
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> PHP 7.0 や 7.1 をインストールするには、置き換えるphp@7.2でphp@7.0またはphp@7.1それぞれに、次のコマンド。

### <a name="step-1-install-php"></a>手順 1. PHP をインストールします。

```
brew tap
brew tap homebrew/core
brew install php@7.2
```
PHP が実行 - パスになります`php -v`を正しいバージョンの PHP が実行されていることを確認します。 PHP は、パスにない、または適切なバージョンではありませんは、次を実行します。
```
brew link --force --overwrite php@7.2
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
ブラウザーをポイントしますhttp://localhost/testsql.php(http://localhost:8080/testsql.php macos)。 SQL Server または Azure SQL database に接続できるようになりましたにします。

## <a name="see-also"></a>参照  
[概要 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Microsoft SQL Server 用 Drivers for PHP を読み込む](../../connect/php/loading-the-php-sql-driver.md)

[Microsoft SQL Server 用 Drivers for PHP のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)
