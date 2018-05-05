---
title: カーソルの種類 (SQLSRV ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecd36e81f537ba6033e2c9ba6f5586723670a100
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cursor-types-sqlsrv-driver"></a>カーソルの種類 (SQLSRV ドライバー)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQLSRV ドライバーでは、カーソルの種類に応じて、任意の順序でアクセスできる行を含む結果セットを作成できます。  このトピックは、クライアント側 (バッファー) とサーバー側 (バッファーなし) について説明カーソル。  
  
## <a name="cursor-types"></a>カーソルの種類  
含む結果セットを作成するとき[sqlsrv_query](../../connect/php/sqlsrv-query.md)または[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)カーソルの種類を指定することができます。 既定では、順方向専用カーソルが使用される、結果セットの末尾に到達するまで、結果セットの最初の行から一度に 1 つの行を移動することができます。  
  
任意の順序で、結果セット内の任意の行にアクセスすることができます、スクロール可能なカーソルを含む結果セットを作成することができます。 次の表に、値を渡すことができる、 **Scrollable** sqlsrv_query または sqlsrv_prepare オプション。  
  
|オプション|Description|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|結果セットの末尾に到達するまで、結果セットの最初の行から一度に 1 つの行を移動することができます。<br /><br />これは、既定のカーソルの種類です。<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)このカーソルの種類で作成した結果セットのエラーが返されます。<br /><br />**フォワード**SQLSRV_CURSOR_FORWARD の省略形は、します。|  
|SQLSRV_CURSOR_STATIC|により、任意の順序で行にアクセスするが、データベース内の変更は反映されません。<br /><br />**静的**SQLSRV_CURSOR_STATIC の省略形は、します。|  
|SQLSRV_CURSOR_DYNAMIC|により、任意の順序で行にアクセスして、データベース内の変更が反映されます。<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)このカーソルの種類で作成した結果セットのエラーが返されます。<br /><br />**動的**SQLSRV_CURSOR_DYNAMIC の省略形は、します。|  
|SQLSRV_CURSOR_KEYSET|により、任意の順序で行にアクセスします。 ただし、行が、(削除された行が返されるテーブルの値がない) から削除された場合、キーセット カーソルは行の数を更新できません。<br /><br />**キーセット**SQLSRV_CURSOR_KEYSET の省略形は、します。|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|により、任意の順序で行にアクセスします。 クライアント側カーソル クエリを作成します。<br /><br />**バッファー内の**SQLSRV_CURSOR_CLIENT_BUFFERED の省略形は、します。|  
  
クエリが複数の結果セットを生成する場合、 **Scrollable**オプションは、すべての結果セットに適用されます。  
  
## <a name="selecting-rows-in-a-result-set"></a>結果セットに行を選択します。  
結果セットを作成した後に行うこともできます[sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)、 [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)、または[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)行を指定します。  
  
次の表で指定できる値、*行*パラメーター。  
  
|パラメーター|Description|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|次の行を指定します。 これは、既定値を指定しない場合、*行*スクロール可能な結果セットのパラメーターです。|  
|SQLSRV_SCROLL_PRIOR|現在の行の前に、の行を指定します。|  
|SQLSRV_SCROLL_FIRST|結果セットの最初の行を指定します。|  
|SQLSRV_SCROLL_LAST|結果セットの最後の行を指定します。|  
|SQLSRV_SCROLL_ABSOLUTE|指定された行を指定します、*オフセット*パラメーター。|  
|SQLSRV_SCROLL_RELATIVE|指定された行を指定します、*オフセット*現在の行からのパラメーターです。|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>サーバー側のカーソルと SQLSRV ドライバー  
次の例では、さまざまなカーソルの効果を示します。 例では、行 33 には、異なるカーソルを指定する 3 つのクエリ ステートメントの最初の参照してください。  2 つのクエリ ステートメントをコメントします。 プログラムを実行するたびにでは、別のカーソルの種類を使用して、行 47 のデータベースの更新の効果を参照してください。  
  
```  
<?php  
$server = "server_name";  
$conn = sqlsrv_connect( $server, array( 'Database' => 'test' ));  
if ( $conn === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "DROP TABLE dbo.ScrollTest" );  
if ( $stmt !== false ) {   
   sqlsrv_free_stmt( $stmt );   
}  
  
$stmt = sqlsrv_query( $conn, "CREATE TABLE ScrollTest (id int, value char(10))" );  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 1, "Row 1" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 2, "Row 2" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 3, "Row 3" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'keyset' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'dynamic' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'static' ));  
  
$rows = sqlsrv_has_rows( $stmt );  
if ( $rows != true ) {  
   die( "Should have rows" );  
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
$stmt2 = sqlsrv_query( $conn, "delete from ScrollTest where id = 3" );  
// or  
// $stmt2 = sqlsrv_query( $conn, "UPDATE ScrollTest SET id = 4 WHERE id = 3" );  
if ( $stmt2 !== false ) {   
   sqlsrv_free_stmt( $stmt2 );   
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
sqlsrv_free_stmt( $stmt );  
sqlsrv_close( $conn );  
?>  
```  
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>クライアント側のカーソルと SQLSRV ドライバー  
クライアント側のカーソルは、version 3.0 で追加された機能、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]結果セット全体をメモリにキャッシュすることができます。 行の数は、クライアント側カーソルを使用するときに、クエリが実行された後に使用できます。  
  
クライアント側のカーソルは、小規模から中規模の結果セットに使用する必要があります。 大きな結果セットをサーバー側カーソルを使用します。  
  
クエリは、バッファーが結果セット全体を保持するのに十分でない場合は false を返します。 PHP メモリの上限に達するまでバッファー サイズを増やすことができます。  
  
SQLSRV ドライバーを使用して、ClientBufferMaxKBSize 設定を使用して結果セットを保持するバッファーのサイズを構成することができます[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)です。 [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) ClientBufferMaxKBSize の値を返します。 Sqlsrv で php.ini ファイルで、バッファーの最大サイズを設定することもできます。ClientBufferMaxKBSize (たとえば、sqlsrv です。ClientBufferMaxKBSize = 1024)。  
  
次の例を示しています。  
  
-   行の数は、クライアント側のカーソルで使用可能では常にします。  
  
-   クライアント側のカーソルとバッチのステートメントを使用します。  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Department";  
  
// Execute the query with client-side cursor.  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// row count is always available with a client-side cursor  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count = $row_count\n";  
  
// Move to a specific row in the result set.  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_LAST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
?>  
```  
  
次の例を使用して、クライアント側カーソル[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)です。  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Employee";  
$stmt = sqlsrv_prepare( $conn, $tsql, array(), array("Scrollable"=>SQLSRV_CURSOR_CLIENT_BUFFERED));  
  
if (! $stmt ) {  
   echo "Statement could not be prepared.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_execute( $stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
if ($row_count)  
   echo "\nRow count = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
if ($row ) {  
   $EmployeeID = sqlsrv_get_field( $stmt, 0);  
   echo "Employee ID = $EmployeeID \n";  
}  
?>  
```  
  
## <a name="see-also"></a>参照  
[カーソルの種類を指定し、行を選択する](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  
