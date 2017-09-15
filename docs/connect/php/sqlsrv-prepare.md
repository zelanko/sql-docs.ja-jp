---
title: "sqlsrv_prepare |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_prepare
apitype: NA
helpviewer_keywords:
- executing queries
- API Reference, sqlsrv_prepare
- sqlsrv_prepare
ms.assetid: 8c74c697-3296-4f5d-8fb9-e361f53f19a6
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cd60e909ae6369376447e5ec40d3af98459ae6d7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvprepare"></a>sqlsrv_prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

指定した接続に関連付けられているステートメントのリソースを作成します。 この関数は、複数のクエリを実行するのに便利です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_prepare( resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: 作成したステートメントに関連付けられた接続リソースです。  
  
*$tsql*: 作成したステートメントに対応する TRANSACT-SQL 式です。  
  
*$params* [省略可能]:**配列**パラメーター化されたクエリ パラメーターに対応する値。 配列の各要素には、次のいずれかを指定できます。  
  
-   リテラル値。  
  
-   PHP 変数への参照。  
  
-   次の構造を持つ **配列** 。  
  
    ```  
    array(&$value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    > [!NOTE]  
    > クエリ パラメーターとして渡された変数は、値ではなく参照によって渡される必要があります。 たとえば、 `&$myVariable` の代わりに、 `$myVariable`を渡します。 by-value パラメーターを使用してクエリを実行すると、PHP の警告が生成されます。  
  
    次の表では、これらの配列の要素を説明します。  
  
    |要素|説明|  
    |-----------|---------------|  
    |*&$value*|リテラル値または PHP の変数への参照。|  
    |*$direction*[省略可能]|次のいずれかの**sqlsrv_param _\* **パラメーターの方向を示すために使用される定数: **SQLSRV_PARAM_IN**、 **SQLSRV_PARAM_OUT**、 **SQLSRV_PARAM_INOUT**です。 既定値は**SQLSRV_PARAM_IN**です。<br /><br />PHP 定数の詳細については、次を参照してください。[定数 & #40 です。Microsoft Drivers for PHP for SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[省略可能]|A **sqlsrv_phptype _\* **戻り値の PHP データ型を指定する定数。|  
    |*$sqlType*[省略可能]|A **sqlsrv_sqltype _\* **入力値の SQL Server データ型を指定する定数。|  
  
*$options* [省略可能]: クエリのプロパティを設定する連想配列。 次の表に、サポートされているキーと対応する値を示します。  
  
|[キー]|サポートされている値|説明|  
|-------|--------------------|---------------|  
|QueryTimeout|正の整数値です。|クエリのタイムアウト (秒単位) を設定します。 既定で、ドライバーは、結果を無制限に待機します。|  
|SendStreamParamsAtExec|**true** または **false**<br /><br />既定値は **true**です。|すべてのストリームの実行時データを送信するドライバーを構成 (**true**)、またはストリーム データをチャンク単位で送信する (**false**)。 既定では、この値は **true**に設定されています。 詳細については、「 [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)」を参照してください。|  
|スクロール可能|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|これらの値の詳細については、「 [カーソルの種類を指定し、行を選択する](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)」を参照してください。|  
  
## <a name="return-value"></a>戻り値  
ステートメント リソースです。 ステートメント リソースを作成できない場合、 **false** が返されます。  
  
## <a name="remarks"></a>解説  
パラメーターとして変数を使用するステートメントを準備するときに、変数がステートメントにバインドされます。 つまり、変数の値を更新すると、次回ステートメントを実行する際に、更新されたパラメーター値を使用して実行されます。  
  
組み合わせ**sqlsrv_prepare**と**sqlsrv_execute**離職ステートメントの準備とステートメントの実行で 2 つに関数呼び出しとパラメーター化クエリを実行するために使用できます。 この関数は、実行ごとに異なるパラメーター値を使用してステートメントを複数回実行する場合に適しています。  
  
大量の情報の書き込みと読み取りを行う別の手法については、「 [Batches of SQL Statements (SQL ステートメントのバッチ)](http://go.microsoft.com/fwlink/?LinkId=104225) 」と「 [BULK INSERT](http://go.microsoft.com/fwlink/?LinkId=104226)」を参照してください。  
  
詳細については、「 [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)」を参照してください。  
  
## <a name="example"></a>例  
次の例では、ステートメントを準備して実行します。 ステートメントを実行すると (を参照してください[sqlsrv_execute](../../connect/php/sqlsrv-execute.md))、フィールドを更新、 *Sales.SalesOrderDetail* AdventureWorks データベースのテーブルです。 この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
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
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ?   
         WHERE SalesOrderDetailID = ?";  
  
/* Assign parameter values. */  
$param1 = 5;  
$param2 = 10;  
$params = array( &$param1, &$param2);  
  
/* Prepare the statement. */  
if( $stmt = sqlsrv_prepare( $conn, $tsql, $params))  
{  
      echo "Statement prepared.\n";  
}   
else  
{  
      echo "Statement could not be prepared.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement. */  
if( sqlsrv_execute( $stmt))  
{  
      echo "Statement executed.\n";  
}  
else  
{  
      echo "Statement could not be executed.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>例  
次の例では、ステートメントを準備し、異なるパラメーター値で再実行する方法を示します。 この例では、AdventureWorks データベースの *Sales.SalesOrderDetail* テーブルの *OrderQty* 列を更新します。 更新されたら、更新プログラムが成功したことを確認するため、データベースが照会されます。 この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
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
  
/* Define the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail  
         SET OrderQty = ?  
         WHERE SalesOrderDetailID = ?";  
  
/* Initialize parameters and prepare the statement. Variables $qty  
and $id are bound to the statement, $stmt1. */  
$qty = 0; $id = 0;  
$stmt1 = sqlsrv_prepare( $conn, $tsql, array( &$qty, &$id));  
if( $stmt1 )  
{  
     echo "Statement 1 prepared.\n";  
}   
else   
{  
     echo "Error in statement preparation.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the SalesOrderDetailID and OrderQty information. This array  
maps the order ID to order quantity in key=>value pairs. */  
$orders = array( 1=>10, 2=>20, 3=>30);  
  
/* Execute the statement for each order. */  
foreach( $orders as $id => $qty)  
{  
     // Because $id and $qty are bound to $stmt1, their updated  
     // values are used with each execution of the statement.   
     if( sqlsrv_execute( $stmt1) === false )  
     {  
          echo "Error in statement execution.\n";  
          die( print_r( sqlsrv_errors(), true));  
     }  
}  
echo "Orders updated.\n";  
  
/* Free $stmt1 resources.  This allows $id and $qty to be bound to a different statement.*/  
sqlsrv_free_stmt( $stmt1);  
  
/* Now verify that the results were successfully written by selecting   
the newly inserted rows. */  
$tsql = "SELECT OrderQty   
         FROM Sales.SalesOrderDetail   
         WHERE SalesOrderDetailID = ?";  
  
/* Prepare the statement. Variable $id is bound to $stmt2. */  
$stmt2 = sqlsrv_prepare( $conn, $tsql, array( &$id));  
if( $stmt2 )  
{  
     echo "Statement 2 prepared.\n";  
}   
else   
{  
     echo "Error in statement preparation.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement for each order. */  
foreach( array_keys($orders) as $id)  
{  
     /* Because $id is bound to $stmt2, its updated value   
        is used with each execution of the statement. */  
     if( sqlsrv_execute( $stmt2))  
     {  
          sqlsrv_fetch( $stmt2);  
          $quantity = sqlsrv_get_field( $stmt2, 0);  
          echo "Order $id is for $quantity units.\n";  
     }  
     else  
     {  
          echo "Error in statement execution.\n";  
          die( print_r( sqlsrv_errors(), true));  
     }  
}  
  
/* Free $stmt2 and connection resources. */  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[方法: パラメーター化クエリを実行する](../../connect/php/how-to-perform-parameterized-queries.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
[方法: ストリームとしてデータを送信する](../../connect/php/how-to-send-data-as-a-stream.md)  
[方向パラメーターを使用する](../../connect/php/using-directional-parameters.md)  
[データの取得](../../connect/php/retrieving-data.md)  
[データの更新 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
  

