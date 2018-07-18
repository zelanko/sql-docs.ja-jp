---
title: '方法: 組み込みの utf-8 サポートを使用した utf-8 データの送受信 |Microsoft ドキュメント'
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
- retrieving data, UTF-8 encoded data
- converting data types
- updating data
ms.assetid: 366c57cf-352f-4202-8074-6ddce44880d1
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01baad352386b88b54412b4390df7cce40df6996
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307761"
---
# <a name="how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support"></a>方法: 組み込みの UTF-8 サポートを使用した UTF-8 データの送信と取得
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO_SQLSRV ドライバーを使用している場合、PDO::SQLSRV_ATTR_ENCODING 属性を使用してエンコードを指定できます。 詳細については、「 [定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)」を参照してください。  
  
このトピックの残りの部分では、SQLSRV ドライバーを使用したエンコード方法について説明します。  
  
UTF-8 でエンコードされたデータを送信または取得するには:  
  
1.  取得元または送信先の列の型が **nchar** または **nvarchar**であることを確認します。  
  
2.  パラメーター配列で PHP の型として `SQLSRV_PHPTYPE_STRING('UTF-8')` を指定します。 または、接続オプションとして `"CharacterSet" => "UTF-8"` を指定します。  
  
    接続オプションの一部として文字セットを指定すると、ドライバーは、その他の接続オプション文字列で同じ文字セットを使用すると見なします。 サーバー名およびクエリ文字列も同じ文字セットを使用すると見なします。  
  
Utf-8 または SQLSRV_ENC_CHAR を渡すことができます**CharacterSet**SQLSRV_ENC_BINARY を渡すことはできませんが、します。 既定のエンコーディングは SQLSRV_ENC_CHAR です。  
  
## <a name="example"></a>例  
次の例では、接続の作成時に、UTF-8 文字セットを指定して、UTF-8 でエンコードされたデータを送信および取得する方法を示します。 この例では、Production.ProductReview テーブルの指定したレビュー ID の Comments 列を更新します。 この例では、新規に更新したデータも取得し、それを表示します。 なお、Comments 列は、型の**nvarchar(3850) です。** なお、データがサーバーに送信される前に、PHP を使用してエンコーディング utf-8 に変換されます**utf8_encode**関数。 これはデモンストレーションのみを目的としています。 実際のアプリケーション シナリオでは、utf-8 でエンコードされたデータで開始します。  
  
例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]と[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 ブラウザーからこの例を実行すると、すべての出力はブラウザーに書き込まれます。  
  
```  
<?php  
  
// Connect to the local server using Windows Authentication and  
// specify the AdventureWorks database as the database in use.   
//   
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "CharacterSet" => "UTF-8");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Set up the Transact-SQL query.  
//   
$tsql1 = "UPDATE Production.ProductReview  
          SET Comments = ?  
          WHERE ProductReviewID = ?";  
  
// Set the parameter values and put them in an array. Note that  
// $comments is converted to UTF-8 encoding with the PHP function  
// utf8_encode to simulate an application that uses UTF-8 encoded data.   
//   
$reviewID = 3;  
$comments = utf8_encode("testing 1, 2, 3, 4.  Testing.");  
$params1 = array(  
                  array( $comments, null ),  
                  array( $reviewID, null )  
                );  
  
// Execute the query.  
//   
$stmt1 = sqlsrv_query($conn, $tsql1, $params1);  
  
if ( $stmt1 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
else {  
   echo "The update was successfully executed.<br>";  
}  
  
// Retrieve the newly updated data.  
//   
$tsql2 = "SELECT Comments   
          FROM Production.ProductReview   
          WHERE ProductReviewID = ?";  
  
// Set up the parameter array.  
//   
$params2 = array($reviewID);  
  
// Execute the query.  
//   
$stmt2 = sqlsrv_query($conn, $tsql2, $params2);  
if ( $stmt2 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data.   
//   
if ( sqlsrv_fetch($stmt2) ) {  
   echo "Comments: ";  
   $data = sqlsrv_get_field( $stmt2, 0 );  
   echo $data."<br>";  
}  
else {  
   echo "Error in fetching data.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Free statement and connection resources.  
//   
sqlsrv_free_stmt( $stmt1 );  
sqlsrv_free_stmt( $stmt2 );  
sqlsrv_close( $conn);  
?>  
```  
  
Unicode データを格納する方法については、次を参照してください。 [Unicode データを扱う](https://msdn.microsoft.com/library/ms175180.aspx)です。  
  
## <a name="example"></a>例  
次の例は最初のサンプルと似ていますが、このサンプルでは接続で UTF-8 文字セットを指定する代わりに、列に UTF-8 文字セットを指定する方法を示します。  
  
```  
<?php  
  
// Connect to the local server using Windows Authentication and  
// specify the AdventureWorks database as the database in use.   
//   
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Set up the Transact-SQL query.  
//   
$tsql1 = "UPDATE Production.ProductReview  
          SET Comments = ?  
          WHERE ProductReviewID = ?";  
  
// Set the parameter values and put them in an array. Note that  
// $comments is converted to UTF-8 encoding with the PHP function  
// utf8_encode to simulate an application that uses UTF-8 encoded data.   
//   
$reviewID = 3;  
$comments = utf8_encode("testing");  
$params1 = array(  
                  array($comments,  
                        SQLSRV_PARAM_IN,  
                        SQLSRV_PHPTYPE_STRING('UTF-8')  
                  ),  
                  array($reviewID)  
                );  
  
// Execute the query.  
//   
$stmt1 = sqlsrv_query($conn, $tsql1, $params1);  
  
if ( $stmt1 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
else {  
   echo "The update was successfully executed.<br>";  
}  
  
// Retrieve the newly updated data.  
//   
$tsql2 = "SELECT Comments   
          FROM Production.ProductReview   
          WHERE ProductReviewID = ?";  
  
// Set up the parameter array.  
//   
$params2 = array($reviewID);  
  
// Execute the query.  
//   
$stmt2 = sqlsrv_query($conn, $tsql2, $params2);  
if ( $stmt2 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data.   
//   
if ( sqlsrv_fetch($stmt2) ) {  
   echo "Comments: ";  
   $data = sqlsrv_get_field($stmt2,   
                            0,   
                            SQLSRV_PHPTYPE_STRING('UTF-8')  
                           );  
   echo $data."<br>";  
}  
else {  
   echo "Error in fetching data.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Free statement and connection resources.  
//   
sqlsrv_free_stmt( $stmt1 );  
sqlsrv_free_stmt( $stmt2 );  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[データの取得](../../connect/php/retrieving-data.md)

[Windows 以外の ASCII データの使用](../../connect/php/how-to-send-and-retrieve-ascii-data-in-linux-mac.md)

[データの更新 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[サンプル アプリケーション &#40;SQLSRV ドライバー&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  
