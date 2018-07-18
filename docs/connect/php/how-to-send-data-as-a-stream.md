---
title: '方法: データをストリームとして送信 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data
- streaming data
ms.assetid: ab6b95d6-b6e6-4bd7-a18c-50f2918f7532
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5305fb34790313d5b9c246d701b0974096ce6e6
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307691"
---
# <a name="how-to-send-data-as-a-stream"></a>方法: ストリームとしてデータを送信する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、ラージ オブジェクトをサーバーに送信するために PHP ストリームを利用します。 このトピックの例では、ストリームとしてデータを送信する方法を示します。 最初の例では、SQLSRV ドライバーを使用して、クエリの実行時にすべてのストリーム データを送信する既定の動作を示します。 2 番目の例は、サーバーに一度にストリーム データの最大 8 キロバイト (8 kB) を送信するのに方法を示すの SQLSRV ドライバーを使用します。  
  
3 番目の例では、PDO_SQLSRV ドライバーを使用して、サーバーにストリーム データを送信する方法を示します。  
  
## <a name="example-sending-stream-data-at-execution"></a>例: 実行時にストリーム データを送信します。
次の例では、AdventureWorks データベースの *Production.ProductReview* テーブルに行を挿入します。 顧客のコメント (*$comments*)、PHP でストリームとして開かれた[fopen](http://php.net/manual/en/function.fopen.php)関数し、クエリの実行時にサーバーにストリームされます。  
  
例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 すべての出力がコンソールに書き込まれます。  
  
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
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$comments = fopen( "data://text/plain,[ Insert lengthy comment here.]",  
                  "r");  
$params = array($productID, $name, $date, $email, $rating, $comments);  
  
/* Execute the query. All stream data is sent upon execution.*/  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
else  
{  
     echo "The query was successfully executed.";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example-sending-stream-data-using-sqlsrvsendstreamdata"></a>例: sqlsrv_send_stream_data のストリームを使用してデータを送信します。
次の例は前の例と同じですが、実行時にすべてのストリーム データを送信するの既定の動作がになっています。 この例では、 [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md) を使用して、ストリーム データをサーバーに送信します。 呼び出しごとに最大 8 キロバイト (8 kB) のデータが送信される**sqlsrv_send_stream_data**です。 スクリプトでは、 **sqlsrv_send_stream_data** によって行われた呼び出しの数をカウントし、カウントをコンソールに表示します。  
  
例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 すべての出力がコンソールに書き込まれます。  
  
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
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$comments = fopen( "data://text/plain,[ Insert lengthy comment here.]",  
                  "r");  
$params = array($productID, $name, $date, $email, $rating, $comments);  
  
/* Turn off the default behavior of sending all stream data at  
execution. */  
$options = array("SendStreamParamsAtExec" => 0);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params, $options);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Send up to 8K of parameter data to the server with each call to  
sqlsrv_send_stream_data. Count the calls. */  
$i = 1;  
while( sqlsrv_send_stream_data( $stmt))   
{  
     echo "$i call(s) made.\n";  
     $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
このトピックの例では文字データをサーバーに送信し、任意の形式のデータをストリームとして送信できます。 たとえば、このトピックで紹介されている手法を使用し、ストリームとしてバイナリ形式で画像を送信することもできます。  
  
## <a name="example-sending-an-image-as-a-stream"></a>例: ストリームとして画像を送信します。 
  
```  
<?php  
   $server = "(local)";   
   $database = "Test";  
   $conn = new PDO( "sqlsrv:server=$server;Database = $database", "", "");  
  
   $binary_source = fopen( "data://text/plain,", "r");  
  
   $stmt = $conn->prepare("insert into binaries (imagedata) values (?)");  
   $stmt->bindParam(1, $binary_source, PDO::PARAM_LOB);   
  
   $conn->beginTransaction();  
   $stmt->execute();  
   $conn->commit();  
?>  
```  
  
## <a name="see-also"></a>参照  
[データの更新 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[SQLSRV ドライバーを使用してデータをストリームとして取得する](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
