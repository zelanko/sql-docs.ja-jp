---
title: システム要件の Microsoft Drivers for PHP for SQL Server |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/23/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8b98b10ee285c8e6be4e34214689eeaa7d7049f
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309801"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>システム要件の Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このドキュメントには、SQL Server または Azure SQL データベースを使用して、データにアクセスするシステムにインストールする必要があります、コンポーネント、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。

3.1 および SQL Server 用 Microsoft PHP ドライバーの以降のバージョンは公式にサポートされています。 サポート ライフ サイクルと以前のバージョンの PHP ドライバーを含む要件の詳細については、次を参照してください。、[サポート マトリックス](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md)です。

## <a name="php"></a>PHP (PHP)

ダウンロードして、最新の安定した PHP バイナリをインストールする方法については、次を参照してください。 [PHP web サイト](http://php.net)です。  Microsoft Drivers for PHP for SQL Server には、次のバージョンの PHP が必要です。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;PHP バージョン|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|7.2|Windows 上の 7.2.1+<br/>他のプラットフォームで 7.2.0+ | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |5.6.4+  |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |5.4.32  |5.4.32  |

-   ドライバー ファイルのバージョンは、PHP 拡張機能ディレクトリにあります。 参照してください[ドライバーのバージョンが](#driver-versions)については、さまざまなドライバー ファイル。  ドライバーをダウンロードするを参照してください。 [for PHP for SQL Server、Microsoft ドライバーをダウンロード](download-drivers-php-sql-server.md)です。 PHP のドライバーを構成する方法の詳細については、次を参照してください。[用 Microsoft Drivers for PHP for SQL Server 読み込む](../../connect/php/loading-the-php-sql-driver.md)します。

-   Web サーバーが必要です。 Web サーバーは、PHP を実行するように構成する必要があります。 IIS で PHP アプリケーションをホストする方法については、次を参照してください。、 [PHP の web サイトのチュートリアル](http://php.net/manual/fa/install.windows.iis.php)です。  

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] IIS 10 を使用すると FastCGI でテストされています。  

    > [!NOTE]  
    > Microsoft は、IIS のサポートのみを提供しています。  

## <a name="odbc-driver"></a>ODBC ドライバー

Microsoft ODBC Driver for SQL Server の正しいバージョンが PHP が実行されているコンピューターに必要です。 次のリンクからダウンロードします。
- [SQL Server 用 Microsoft ODBC Driver 17](https://www.microsoft.com/en-us/download/details.aspx?id=56567)
- [Microsoft ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=53339)
- [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)
- [Microsoft ODBC Driver 11 for SQL Server](http://www.microsoft.com/download/details.aspx?id=36434)

64 ビット オペレーティング システムを使用している場合、ODBC 64 ビットのインストーラーには、32 ビットおよび 64 ビットの両方の ODBC ドライバーがインストールされます。 32 ビット オペレーティング システムを使用する場合は、ODBC x86 を使用してインストーラーです。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;ODBC ドライバーのバージョン|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|ODBC ドライバー 17  |Y| | | | |
|ODBC Driver 13.1|Y|Y|Y| | |
|ODBC Driver 13  | | |Y| | |
|ODBC Driver 11  |Y|Y|Y|Y|Y|

SQLSRV ドライバーを使用している場合[sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md)のバージョンに関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が Microsoft ODBC Driver for SQL Server を使用している、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。 PDO_SQLSRV ドライバーを使用している場合を使用できます[:getattribute](../../connect/php/pdo-getattribute.md)バージョンを検出します。  

## <a name="sql-server"></a>SQL Server

Azure SQL データベースはサポートされています。 詳細については、次を参照してください。 [Microsoft Azure SQL Database に接続する](../../connect/php/connecting-to-microsoft-azure-sql-database.md)です。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;SQL Server のバージョン|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Azure SQL のマネージ インスタンス<br/> (拡張プライベート プレビューで)|Y|Y| | | |
|Azure SQL データ ウェアハウス|Y|Y| | | |
|SQL Server 2017   |Y|Y| | | |
|SQL Server 2016   |Y|Y|Y| | |
|SQL Server 2014   |Y|Y|Y|Y|Y|
|SQL Server 2012   |Y|Y|Y|Y|Y|
|SQL Server 2008 R2|Y|Y|Y|Y|Y|
|SQL Server 2008:   | | |Y|Y|Y|

## <a name="operating-systems"></a>オペレーティング システム
サポートされるオペレーティング システム、ドライバーのバージョンは次のとおりです。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;オペレーティング システム|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Windows Server 2016                      |Y|Y| | | |
|Windows Server 2012 R2                   |Y|Y|Y|Y|Y|
|Windows Server 2012                      |Y|Y|Y|Y|Y|
|Windows Server 2008 R2 SP1               | | |Y|Y|Y|
|Windows Server 2008 SP2                  | | |Y|Y|Y|
|Windows 10                               |Y|Y|Y| | |
|Windows 8.1                              |Y|Y|Y|Y|Y|
|Windows 8                                | |Y|Y|Y|Y|
|Windows 7 SP1                            | | |Y|Y|Y|
|Windows Vista SP2                        | | |Y|Y|Y|
|Ubuntu 17.10 (64 ビット)                    |Y| | | | |
|Ubuntu 16.04 (64 ビット)                    |Y|Y|Y| | |
|Ubuntu 15.10 (64 ビット)                    | |Y| | | |
|Ubuntu 15.04 (64 ビット)                    | | |Y| | |
|Debian 9 (64 ビット)                        |Y| | | | |
|Debian 8 (64 ビット)                        |Y|Y| | | |
|Red Hat Enterprise Linux 7 (64 ビット)      |Y|Y|Y| | |
|Suse Enterprise Linux (64 ビット) の 12        |Y| | | | |
|macOS Sierra (64 ビット)                    |Y|Y| | | |
|macOS 許可されて (64 ビット)                |Y|Y| | | |

## <a name="driver-versions"></a>ドライバー バージョン  
このセクションの各バージョンに含まれているドライバー ファイルを一覧表示、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。 各インストール パッケージには、スレッドとスレッド以外のバリアントに SQLSRV および PDO_SQLSRV のドライバー ファイルが含まれています。 Windows では、ことも 32 ビットおよび 64 ビットのバリエーションで使用できます。 インストール指示に従って、PHP ランタイムで使用するため、ドライバーを構成するに[用 Microsoft Drivers for PHP for SQL Server 読み込む](../../connect/php/loading-the-php-sql-driver.md)します。

Linux および macOS のサポートされているバージョンは、適切なドライバーをインストールできる次の PHP の PECL パッケージ システムを使用して、[インストール手順については Linux および macOS](../../connect/php/installation-tutorial-linux-mac.md)です。 該当するプラットフォームからのビルド済みのバイナリをダウンロードする代わりに、 [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github プロジェクト ページ - 次の表は構築済みのバイナリのパッケージ内のファイルを一覧表示します。

**Microsoft Drivers 5.2 for PHP for SQL Server:**  

Windows では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|32 ビット php_sqlsrv_7_nts.dll <br />32 ビット php_pdo_sqlsrv_7_nts.dll |7.0|いいえ |32 ビット php7.dll|
|32 ビット php_sqlsrv_7_ts.dll  <br />32 ビット php_pdo_sqlsrv_7_ts.dll  |7.0|はい|32 ビット php7ts.dll|
|64 ビット php_sqlsrv_7_nts.dll <br />64 ビット php_pdo_sqlsrv_7_nts.dll |7.0|いいえ |64 ビット php7.dll|  
|64 ビット php_sqlsrv_7_ts.dll  <br />64 ビット php_pdo_sqlsrv_7_ts.dll  |7.0|はい|64 ビット php7ts.dll|
|32 ビット php_sqlsrv_71_nts.dll<br />32 ビット php_pdo_sqlsrv_71_nts.dll|7.1|いいえ |32 ビット php7.dll|  
|32 ビット php_sqlsrv_71_ts.dll <br />32 ビット php_pdo_sqlsrv_71_ts.dll |7.1|はい|32 ビット php7ts.dll|  
|64 ビット php_sqlsrv_71_nts.dll<br />64 ビット php_pdo_sqlsrv_71_nts.dll|7.1|いいえ |64 ビット php7.dll|  
|64 ビット php_sqlsrv_71_ts.dll <br />64 ビット php_pdo_sqlsrv_71_ts.dll |7.1|はい|64 ビット php7ts.dll|   
|32 ビット php_sqlsrv_72_nts.dll<br />32 ビット php_pdo_sqlsrv_72_nts.dll|7.2|いいえ |32 ビット php7.dll|  
|32 ビット php_sqlsrv_72_ts.dll <br />32 ビット php_pdo_sqlsrv_72_ts.dll |7.2|はい|32 ビット php7ts.dll|  
|64 ビット php_sqlsrv_72_nts.dll<br />64 ビット php_pdo_sqlsrv_72_nts.dll|7.2|いいえ |64 ビット php7.dll|  
|64 ビット php_sqlsrv_72_ts.dll <br />64 ビット php_pdo_sqlsrv_72_ts.dll |7.2|はい|64 ビット php7ts.dll|  

Linux では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|いいえ |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|はい|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|いいえ |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|はい|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|いいえ |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|はい|

**Microsoft Drivers 4.3 for PHP for SQL Server:**  

Windows では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|32 ビット php_sqlsrv_7_nts.dll <br />32 ビット php_pdo_sqlsrv_7_nts.dll |7.0|いいえ |32 ビット php7.dll|
|32 ビット php_sqlsrv_7_ts.dll  <br />32 ビット php_pdo_sqlsrv_7_ts.dll  |7.0|はい|32 ビット php7ts.dll|
|64 ビット php_sqlsrv_7_nts.dll <br />64 ビット php_pdo_sqlsrv_7_nts.dll |7.0|いいえ |64 ビット php7.dll|  
|64 ビット php_sqlsrv_7_ts.dll  <br />64 ビット php_pdo_sqlsrv_7_ts.dll  |7.0|はい|64 ビット php7ts.dll|
|32 ビット php_sqlsrv_71_nts.dll<br />32 ビット php_pdo_sqlsrv_71_nts.dll|7.1|いいえ |32 ビット php7.dll|  
|32 ビット php_sqlsrv_71_ts.dll <br />32 ビット php_pdo_sqlsrv_71_ts.dll |7.1|はい|32 ビット php7ts.dll|  
|64 ビット php_sqlsrv_71_nts.dll<br />64 ビット php_pdo_sqlsrv_71_nts.dll|7.1|いいえ |64 ビット php7.dll|  
|64 ビット php_sqlsrv_71_ts.dll <br />64 ビット php_pdo_sqlsrv_71_ts.dll |7.1|はい|64 ビット php7ts.dll|   

Linux では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|いいえ |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|はい|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|いいえ |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|はい|  

**PHP for SQL Server 用 Microsoft ドライバー 4.0:**  

Windows では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|いいえ|32 ビット php7.dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|はい|32 ビット php7ts.dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|いいえ|64 ビット php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|はい|64 ビット php7ts.dll|   

Linux では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|いいえ |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|はい|

**Microsoft Drivers 3.2 for PHP for SQL Server:**  

Windows では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|いいえ|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|はい|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|いいえ|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|はい|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|いいえ|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|はい|php5ts.dll|  

**Microsoft Drivers 3.1 for PHP for SQL Server:**  

Windows では、次のバージョンのドライバーのとおりです。

|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|いいえ|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|はい|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|いいえ|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|はい|php5ts.dll|  

## <a name="see-also"></a>参照  
[入門 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
