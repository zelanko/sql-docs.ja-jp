---
title: "sqlsrv_connect |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
caps.latest.revision: "67"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f87b73eee57279a1f3b8bd39abb8f8986076b653
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlsrvconnect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

接続リソースを作成し、接続を開きます。 既定では、Windows 認証を使用して接続は試行されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>パラメーター  
*$serverName*: 接続が確立されるサーバー名を指定する文字列です。 この文字列の一部には、インスタンス名 (たとえば、"myserver \instancename") またはポート番号 (たとえば、"myServer, 1521") を含めることができます。 このパラメーターに使用できるオプションの詳細については、「 [SQL Native Client での接続文字列キーワードの使用](http://go.microsoft.com/fwlink/?LinkId=105504)」の「ODBC ドライバー接続文字列キーワード」の Server キーワードの説明を参照してください。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 3.0 以降では、 `"(localdb)\instancename"`で LocalDB インスタンスを指定することもできます。 詳細については、「 [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)」を参照してください。  
  
また、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 3.0 以降では、AlwaysOn 可用性グループへの接続に仮想ネットワーク名を指定することもできます。 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] の [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]によるサポートの詳細については、「 [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)」(高可用性、障害復旧の PHP Driver for SQL Server のサポート) を参照してください。  
  
*$connectionInfo* [省略可能]: 連想**配列**接続属性を格納している (たとえば、**配列**("Database"= >"AdventureWorks"))。 配列でサポートしているキーの一覧については、「 [Connection Options](../../connect/php/connection-options.md) 」を参照してください。  
  
## <a name="return-value"></a>戻り値  
PHP 接続リソースです。 接続を正常に作成して開くことができない場合、 **false** が返されます。  
  
## <a name="remarks"></a>解説  
*UID* キーおよび *PWD* キーの値がオプションの *$connectionInfo* パラメーターで指定されていない場合、Windows 認証を使用して接続は試行されます。 サーバーに接続する方法の詳細については、「 [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) 」および「 [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md)」を参照してください。  
  
## <a name="example"></a>例  
次の例では、Windows 認証を使用して接続を作成して開きます。 この例では、SQL Server および [AdventureWorks](http://www.codeplex.com/SqlServerSamples) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[Connecting to the Server](../../connect/php/connecting-to-the-server.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
