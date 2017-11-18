---
title: "PHP SQL Driver のシステム要件 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba7e8cde4b8d3b77effca06b00303984223551f5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="system-requirements-for-the-php-sql-driver"></a>PHP SQL Driver のシステム要件
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQL Server または Azure SQL データベースを使用して、データにアクセスする、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、次のコンポーネントがコンピューターにインストールする必要があります。  
  
-   PHP が必要です。 ダウンロードして、最新の安定したバイナリをインストールする方法については、次を参照してください。 [http://php.net](http://go.microsoft.com/fwlink/?LinkId=101876)です。  Microsoft Drivers for PHP for SQL Server では、次のバージョンが必要です。
  
|Microsoft SQL Server 用 Drivers for PHP バージョン|サポートされる PHP バージョン|  
|----------------------------------------------------|--------------------------|  
|4.3|PHP 7.0 および PHP 7.1| 
|4.0|PHP 7.0|  
|3.2|PHP 5.6.4+ または<br /><br />PHP 5.5.16+ または<br /><br />PHP 5.4.32|  
|3.1|PHP 5.5.16+ または<br /><br />PHP 5.4.32|  
|3.0|PHP 5.4.32 または<br /><br />PHP 5.3.0|  
|2.0|PHP 5.3.0 または<br /><br />PHP 5.2.4 または<br /><br />PHP 5.2.13|  
  
-   ドライバー ファイルのバージョンは、PHP 拡張機能ディレクトリにあります。 さまざまなドライバー ファイルの詳細については、このトピックの後半に登場する「ドライバー バージョン」を参照してください。 PHP ランタイムのドライバーを構成する方法については、「 [PHP SQL ドライバーの読み込み](../../connect/php/loading-the-php-sql-driver.md)  」を参照してください。 ドライバーをダウンロードする方法については、「 [Microsoft SQL Server 用 Drivers for PHP](http://www.microsoft.com/download/details.aspx?id=20098)」を参照してください。  
  
-   Web サーバーが必要です。 Web サーバーは、PHP を実行するように構成する必要があります。 インターネット インフォメーション サービス (IIS) 6.0 で PHP アプリケーションをホストする方法については、次を参照してください。 [IIS 6.0 で PHP アプリケーションをホストするのを使用する FastCGI](http://go.microsoft.com/fwlink/?LinkId=117131)です。 IIS 7.0 で PHP アプリケーションをホストする方法については、「 [Using FastCGI to Host PHP Applications on IIS 7.0 (IIS 7.0 でPHP アプリケーションをホストするための FastCGI の使用)](http://go.microsoft.com/fwlink/?LinkId=117132)」を参照してください。  
  
    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は IIS 6 と IIS 7 と FastCGI でテストされています。  
  
    > [!NOTE]  
    > Microsoft は、IIS のサポートのみを提供しています。  
  
-   Microsoft ODBC Driver for SQL Server または SQL Server Native Client の正しいバージョンが PHP が実行されているコンピューターに必要です。  64 ビット オペレーティング システムを使用している場合、ODBC 64 ビットのインストーラーには、32 ビットおよび 64 ビットの両方の ODBC ドライバーがインストールされます。 32 ビット オペレーティング システムを使用する場合は、ODBC x86 を使用してインストーラーです。

|Microsoft SQL Server 用 Drivers for PHP バージョン|Microsoft ODBC Driver for SQL Server または SQL Server Native Client のバージョン|  
|----------------------------------------------------|--------------------------|
|4.3|SQL Server または Microsoft ODBC Driver 13.1 for SQL Server 用 Microsoft ODBC Driver 11。 Microsoft ODBC Driver をダウンロードするを参照してください、 [Microsoft ODBC Driver 11 for SQL Server のページ](http://www.microsoft.com/download/details.aspx?id=36434)または[Microsoft ODBC Driver 13.1 for SQL Server のページ。](https://www.microsoft.com/en-us/download/details.aspx?id=53339)|    
|4.0|SQL Server または Microsoft ODBC Driver 13 for SQL Server 用 Microsoft ODBC Driver 11。 Microsoft ODBC Driver をダウンロードするを参照してください、 [Microsoft ODBC Driver 11 for SQL Server のページ](http://www.microsoft.com/download/details.aspx?id=36434)または[Microsoft ODBC Driver 13 for SQL Server のページ。](https://www.microsoft.com/download/details.aspx?id=50420)|  
|3.2 または <br><br> 3.1|Microsoft ODBC Driver 11 for SQL Server にします。 Microsoft ODBC Driver をダウンロードするを参照してください、 [Microsoft ODBC Driver 11 for SQL Server のページ。](http://www.microsoft.com/download/details.aspx?id=36434)|   
|3.0|Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client。 Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] ネイティブ クライアントは [SQL Server 2012 機能パック ページ](http://go.microsoft.com/fwlink/?LinkID=236805)| 
|2.0|Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro_md.md)] Native Client:<br /><br />[X86 パッケージのダウンロード](http://go.microsoft.com/fwlink/?LinkID=188400&clcid=0x409)32 ビット オペレーティング システム <br /><br />[X64 パッケージのダウンロード](http://go.microsoft.com/fwlink/?LinkID=188401&clcid=0x409)64 ビット オペレーティング システム|  

  
SQLSRV ドライバーを使用している場合[sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md)のバージョンに関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Native Client または Microsoft ODBC Driver for SQL Server で使用されている、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。 PDO_SQLSRV ドライバーを使用している場合を使用できます[:getattribute](../../connect/php/pdo-getattribute.md)バージョンを検出します。  



## <a name="database-versions"></a>データベースのバージョン
-   Azure SQL データベースはサポートされています。 詳細については、次を参照してください。 [Microsoft Azure SQL Database に接続する](../../connect/php/connecting-to-microsoft-azure-sql-database.md)です。 

- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]バージョン 4.3 サポートの SQL Server 2008 R2 以降
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]SQL Server 2008 以降のバージョン 4.0 のサポート
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]3.1 のバージョンの SQL Server 2008 以降のサポート
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]SQL Server 2005 以降のバージョン 2.0 および 3.0 サポート


## <a name="driver-versions"></a>ドライバー バージョン  
このセクションの各バージョンに含まれているドライバーの一覧、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。  
  
インストール指示に従って、PHP ランタイムで使用するため、ドライバーを構成するに[PHP SQL ドライバーの読み込み](../../connect/php/loading-the-php-sql-driver.md)です。  
  
**Microsoft Drivers 4.3 for PHP for SQL Server:**  

Windows では、4.3 次のバージョンのドライバーがインストールされます。
  
|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|いいえ|32 ビット php7.dll| 
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|はい|32 ビット php7ts.dll| 
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|いいえ|64 ビット php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|はい|64 ビット php7ts.dll| 
|php_sqlsrv_71_nts_x86.dll<br /><br />php_pdo_sqlsrv_71_nts_x86.dll|7.1|いいえ|32 ビット php7.dll|  
|php_sqlsrv_71_ts_x86.dll<br /><br />php_pdo_sqlsrv_71_ts_x86.dll|7.1|はい|32 ビット php7ts.dll|  
|php_sqlsrv_71_nts_x64.dll<br /><br />php_pdo_sqlsrv_71_nts_x64.dll|7.1|いいえ|64 ビット php7.dll|  
|php_sqlsrv_71_ts_x64.dll<br /><br />php_pdo_sqlsrv_71_ts_x64.dll|7.1|はい|64 ビット php7ts.dll|   
  
**PHP for SQL Server 用 Microsoft ドライバー 4.0:**  

Windows では、4.0 以下のバージョンのドライバーがインストールされます。
  
|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|いいえ|32 ビット php7.dll|  
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|はい|32 ビット php7ts.dll|  
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|いいえ|64 ビット php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|はい|64 ビット php7ts.dll|   
  
Linux のサポートされているバージョンは、PHP の PECL パッケージ システムを使用して sqlsrv や pdo_sqlsrv の適切なバージョンをインストールすることができます。 
  
**Microsoft SQL Server 用 Drivers 3.2 for PHP では、次のバージョンのドライバーがインストールされます。**  
  
|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|いいえ|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|はい|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|いいえ|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|はい|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br /><br />php_pdo_sqlsrv_56_nts.dll|5.6|いいえ|php5.dll|  
|php_sqlsrv_56_ts.dll<br /><br />php_pdo_sqlsrv_56_ts.dll|5.6|はい|php5ts.dll|  
  
**Microsoft SQL Server 用 Drivers 3.1 for PHP では、次のバージョンのドライバーがインストールされます。**  
  
|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|いいえ|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|はい|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|いいえ|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|はい|php5ts.dll|  
  
**Microsoft SQL Server 用 Drivers 3.0 for PHP では、次のバージョンのドライバーがインストールされます。**  
  
|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts.dll<br /><br />php_pdo_sqlsrv_53_nts.dll|5.3|いいえ|php5.dll|  
|php_sqlsrv_53_ts.dll<br /><br />php_pdo_sqlsrv_53_ts.dll|5.3|はい|php5ts.dll|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|いいえ|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|はい|php5ts.dll|  
  
**Microsoft SQL Server 用 Drivers 2.0 for PHP では、次のバージョンのドライバーがインストールされます。**  
  
|ドライバー ファイル|PHP バージョン|スレッド セーフですか。|PHP .dll で使用|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts_vc6.dll<br /><br />php_pdo_sqlsrv_53_nts_vc6.dll|5.3|いいえ|php5.dll|  
|php_sqlsrv_53_nts_vc9.dll<br /><br />php_pdo_sqlsrv_53_nts_vc9.dll|5.3|いいえ|php5.dll|  
|php_sqlsrv_53_ts_vc6.dll<br /><br />php_pdo_sqlsrv_53_ts_vc6.dll|5.3|はい|php5ts.dll|  
|php_sqlsrv_53_ts_vc9.dll<br /><br />php_pdo_sqlsrv_53_ts_vc9.dll|5.3|はい|php5ts.dll|  
|php_sqlsrv_52_nts_vc6.dll<br /><br />php_pdo_sqlsrv_52_nts_vc6.dll|5.2|いいえ|php5.dll|  
|php_sqlsrv_52_ts_vc6.dll<br /><br />php_pdo_sqlsrv_52_ts_vc6.dll|5.2|はい|php5ts.dll|  
  
ドライバー ファイルの名前に「vc9」が含まれる場合、Visual C++ 9.0 でコンパイルされた PHP バーションと共に使用する必要があります。  
## <a name="operating-systems"></a>オペレーティング システム 
サポートされるオペレーティング システム、ドライバーのバージョンは次のとおりです。

-   4.3:
    -   Windows Server 2012  
    -   Windows Server 2012 R2
    -   Windows Server 2016 
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10
    -   Ubuntu 15.10 (64 ビット)
    -   Ubuntu 16.04 (64 ビット)
    -   Debian 8 (64 ビット)
    -   Red Hat Enterprise Linux 7 (64 ビット)
    -   Mac OS Sierra (64 ビット)
    -   Mac OS 許可されて (64 ビット)
    
-   4.0:  
    -   Windows Server 2008 SP2
    -   Windows Server 2008 R2 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows Vista SP2  
    -   Windows 7 SP1  
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10 
    -   Ubuntu 15.04 (64 ビット)
    -   Ubuntu 16.04 (64 ビット)
    -   Red Hat Enterprise Linux 7 (64 ビット)

 
-   3.2 および 3.1:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows 8  
    -   Windows 8.1  
  
  
-   3.0:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  


-   2.0:
    -   [!INCLUDE[winxpsvr](../../includes/winxpsvr_md.md)] Service Pack 1  
    -   Windows XP Service Pack 3  
    -   Windows Vista Service Pack 1 以降  
    -   Windows Server 2008  
    -   Windows Server 2008 R2  
    -   Windows 7  
  
## <a name="see-also"></a>参照  
[作業の開始](../../connect/php/getting-started-with-the-php-sql-driver.md)
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
  

