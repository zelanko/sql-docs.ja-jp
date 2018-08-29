---
title: カーソルの種類 (SQLSRV ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: deffdb98790baa64eaa1983fee6839a65289d0d4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37990164"
---
# <a name="cursor-types-sqlsrv-driver"></a>カーソルの種類 (SQLSRV ドライバー)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQLSRV ドライバーでは、カーソルの種類に基づき、任意の順番で行にアクセスできる結果セットを作成できます。  このトピックではクライアント側 (バッファー) とサーバー側 (バッファーなし) について説明しますカーソル。  
  
## <a name="cursor-types"></a>カーソルの種類  
結果セットを作成すると[sqlsrv_query](../../connect/php/sqlsrv-query.md)または[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)カーソルの種類を指定することができます。 既定では、順方向専用カーソルが使用になり、結果セットの末尾に到達するまで、結果セットの最初の行から一度に 1 つの行を移動することができます。  
  
任意の順序で、結果セットの任意の行にアクセスすることができます、スクロール可能なカーソルを含む結果セットを作成することができます。 次の表は、sqlsrv_query または sqlsrv_prepare において **Scrollable** オプションに渡すことができる値を示しています。
  
|オプション|[説明]|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|結果セットの末尾に到達するまで、結果セットの最初の行から一度に 1 つの行を移動できます。<br /><br />これは、既定のカーソルの種類です。<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)このカーソルの種類で作成した結果セットのエラーが返されます。<br /><br />**フォワード**SQLSRV_CURSOR_FORWARD の省略形式です。|  
|SQLSRV_CURSOR_STATIC|により、任意の順序で行にアクセスするが、データベースの変更は反映されません。<br /><br />**静的**SQLSRV_CURSOR_STATIC の省略形式です。|  
|SQLSRV_CURSOR_DYNAMIC|により、任意の順序で行にアクセスして、データベースの変更が反映されます。<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)このカーソルの種類で作成した結果セットのエラーが返されます。<br /><br />**動的**SQLSRV_CURSOR_DYNAMIC の省略形式です。|  
|SQLSRV_CURSOR_KEYSET|により、任意の順序で行にアクセスします。 ただし、行がテーブルから削除される場合 (削除された行は、値なしで返されます)、キーセット カーソルは行の数を更新しません。<br /><br />**キーセット**SQLSRV_CURSOR_KEYSET の省略形式です。|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|により、任意の順序で行にアクセスします。 クライアント側カーソル クエリを作成します。<br /><br />**バッファー** SQLSRV_CURSOR_CLIENT_BUFFERED の省略形式です。|  
  
クエリが複数の結果セットを生成する場合、 **Scrollable**オプションは、すべての結果セットに適用されます。  
  
## <a name="selecting-rows-in-a-result-set"></a>結果セット内の行を選択します。  
使用することができます、結果セットを作成したら、 [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)、 [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)、または[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)行を指定します。  
  
次の表で指定できる値、*行*パラメーター。  
  
|パラメーター|[説明]|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|次の行を指定します。 これは、指定しない場合の既定値は、*行*スクロール可能な結果セットのパラメーター。|  
|SQLSRV_SCROLL_PRIOR|現在の行の前に、の行を指定します。|  
|SQLSRV_SCROLL_FIRST|結果セットの最初の行を指定します。|  
|SQLSRV_SCROLL_LAST|結果セット内の最後の行を指定します。|  
|SQLSRV_SCROLL_ABSOLUTE|指定された行を指定します、*オフセット*パラメーター。|  
|SQLSRV_SCROLL_RELATIVE|指定された行を指定します、*オフセット*現在の行からのパラメーター。|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>サーバー側のカーソルと SQLSRV ドライバー  
次の例では、さまざまなカーソルの効果を示します。 例の 33 の行を別のカーソルを指定する 3 つのクエリ ステートメントの最初の数値が表示されます。  2 つのクエリ ステートメントがコメントされています。 プログラムを実行するたびにでは、異なるカーソルの種類を使用して、47 行目のデータベース更新の影響を参照してください。  
  
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
クライアント側のカーソルは、のバージョン 3.0 で追加された機能、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]メモリ セット全体の結果をキャッシュすることができます。 行の数は、クライアント側カーソルを使用する場合、クエリの実行後に使用できます。  
  
クライアント側のカーソルは、小規模から中規模の結果セットに対して使用する必要があります。 大きな結果セットのサーバー側カーソルを使用します。  
  
クエリは、バッファーが結果セット全体を保持するために十分な大きさでない場合は false を返します。 PHP メモリの上限に達するまでバッファー サイズを増やすことができます。  
  
SQLSRV ドライバーを使用して、ClientBufferMaxKBSize の設定を使用して結果セットを保持するバッファーのサイズを構成することができます[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)します。 [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) ClientBufferMaxKBSize の値を返します。 Sqlsrv で php.ini ファイルの最大バッファー サイズを設定することもできます。ClientBufferMaxKBSize (sqlsrv など。ClientBufferMaxKBSize = 1024)。  
  
次の例を示しています。  
  
-   行の数では、クライアント側のカーソルで使用可能な常にします。  
  
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
  
次の例を使用して、クライアント側カーソル[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)します。  
  
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
  
