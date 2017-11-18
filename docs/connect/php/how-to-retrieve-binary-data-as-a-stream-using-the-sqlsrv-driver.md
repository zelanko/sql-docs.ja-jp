---
title: "方法: SQLSRV ドライバーを使用してストリームとしてバイナリ データの取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
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
- retrieving data, as a binary stream
- streaming data
ms.assetid: cd8d6382-abe6-48ee-9d10-4e6c52c0cb9a
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9cfd6c030465016673acc6c81706e88979078629
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver"></a>方法: SQLSRV ドライバーを使用してバイナリ データをストリームとして取得する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

ストリームがあるだけの SQLSRV ドライバーで使用できるようにデータを取得する、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、し、PDO_SQLSRV ドライバーでは使用できません。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、サーバーから大量のバイナリ データを取得するために PHP ストリームを利用します。 このトピックでは、バイナリ データをストリームとして取得する方法を説明します。  
  
ストリームを使用して画像などのバイナリ データを取得すると、オブジェクト全体をスクリプト メモリに読み込むのではなく、データのチャンクが取得されるので、大量のスクリプト メモリを使用しなくて済みます。  
  
## <a name="example"></a>例  
次の例では、AdventureWorks データベースの *Production.ProductPhoto* テーブルからバイナリ データ (この場合は画像) を取得します。 画像はストリームとして取得されて、ブラウザーに表示されます。  
  
ストリームとしての画像データの取得は、戻り値の型をバイナリ ストリームとして指定した [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) および [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) を使用して行われます。 戻り値の型が定数を使用して、指定された**SQLSRV_PHPTYPE_STREAM**です。 について**sqlsrv**定数を参照してください[定数 & #40 です。Microsoft Drivers for PHP for SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 ブラウザーからこの例を実行すると、すべての出力はブラウザーに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT LargePhoto   
         FROM Production.ProductPhoto   
         WHERE ProductPhotoID = ?";  
  
/* Set the parameter values and put them in an array. */  
$productPhotoID = 70;  
$params = array( $productPhotoID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data.  
The return data is retrieved as a binary stream. */  
if ( sqlsrv_fetch( $stmt ) )  
{  
   $image = sqlsrv_get_field( $stmt, 0,   
                      SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_BINARY));  
   header("Content-Type: image/jpg");  
   fpassthru($image);  
}  
else  
{  
     echo "Error in retrieving data.</br>";  
     die(print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
この例の戻り値の型の指定では、バイナリ ストリームとして PHP の戻り値の型を指定する方法が示されています。 技術的には、これは必須でない例では、ため、 *LargePhoto*フィールド varbinary (max) 型の SQL Server があり、既定でバイナリ ストリームとして返されるためです。 既定の PHP データ型の詳細については、「 [Default PHP Data Types](../../connect/php/default-php-data-types.md)」を参照してください。 PHP の戻り値の型の指定方法の詳細については、「 [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[データの取得](../../connect/php/retrieving-data.md)  
[SQLSRV ドライバーを使用してデータをストリームとして取得する](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  

