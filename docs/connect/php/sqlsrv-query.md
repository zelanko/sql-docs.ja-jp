---
title: "sqlsrv_query |Microsoft ドキュメント"
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
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1dbc5c20a1d9fb1210bb7729f36299ea4392ebc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

ステートメントを準備して実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_query( resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: 準備済みステートメントに関連付けられた接続リソースです。  
  
*$tsql*: 準備済みステートメントに対応する TRANSACT-SQL 式です。  
  
*$params* [省略可能]:**配列**パラメーター化されたクエリ パラメーターに対応する値。 配列の各要素には、次のいずれかを指定できます。  
  
-   リテラル値。  
  
-   PHP 変数。  
  
-   次の構造を持つ **配列** 。  
  
    ```  
    array($value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    次の表で配列の各要素を説明します。  
  
    |要素|説明|  
    |-----------|---------------|  
    |*$value*|リテラル値、PHP 変数、または PHP by-reference 変数。|  
    |*$direction*[省略可能]|次のいずれかの**sqlsrv_param _\* **パラメーターの方向を示すために使用される定数: **SQLSRV_PARAM_IN**、 **SQLSRV_PARAM_OUT**、 **SQLSRV_PARAM_INOUT**です。 既定値は**SQLSRV_PARAM_IN**です。<br /><br />PHP 定数の詳細については、次を参照してください。[定数 & #40 です。Microsoft Drivers for PHP for SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[省略可能]|A **sqlsrv_phptype _\* **戻り値の PHP データ型を指定する定数。<br /><br />PHP 定数の詳細については、次を参照してください。[定数 & #40 です。Microsoft Drivers for PHP for SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[省略可能]|A **sqlsrv_sqltype _\* **入力値の SQL Server データ型を指定する定数。<br /><br />PHP 定数の詳細については、次を参照してください。[定数 & #40 です。Microsoft Drivers for PHP for SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* [省略可能]: クエリのプロパティを設定する連想配列。 サポートされるキーは次のとおりです。  
  
|[キー]|サポートされる値|説明|  
|-------|--------------------|---------------|  
|QueryTimeout|正の整数値です。|クエリのタイムアウト (秒単位) を設定します。 既定で、ドライバーは、結果を無制限に待機します。|  
|SendStreamParamsAtExec|**true** または **false**<br /><br />既定値は **true**です。|すべてのストリームの実行時データを送信するドライバーを構成 (**true**)、またはストリーム データをチャンク単位で送信する (**false**)。 既定では、この値は **true**に設定されています。 詳細については、「 [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)」を参照してください。|  
|スクロール可能|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|これらの値の詳細については、「 [カーソルの種類を指定し、行を選択する](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)」を参照してください。|  
  
## <a name="return-value"></a>戻り値  
ステートメント リソースです。 場合は、ステートメントを作成または実行すると、 **false**が返されます。  
  
## <a name="remarks"></a>解説  
**Sqlsrv_query**関数が 1 回限りのクエリに最適し、特殊な状況を除き、クエリを実行する既定の選択肢をする必要があります。 この関数は、最小限のコードでクエリを実行するための簡素化されたメソッドを提供します。 **Sqlsrv_query**関数はステートメントの準備とステートメントの実行の両方を行うし、パラメーター化クエリを実行するために使用できます。  
  
詳細については、「 [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)」を参照してください。  
  
## <a name="example"></a>例  
次の例では、AdventureWorks データベースの *Sales.SalesOrderDetail* テーブルに 1 つの行を挿入します。 この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
> [!NOTE]  
> 次の例では、INSERT ステートメントを使用しての使用例を示すを**sqlsrv_query**任意の Transact SQL ステートメントに 1 回限りのステートメントの実行の概念が適用されます。  
  
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
  
/* Set up the parameterized query. */  
$tsql = "INSERT INTO Sales.SalesOrderDetail   
        (SalesOrderID,   
         OrderQty,   
         ProductID,   
         SpecialOfferID,   
         UnitPrice,   
         UnitPriceDiscount)  
        VALUES   
        (?, ?, ?, ?, ?, ?)";  
  
/* Set parameter values. */  
$params = array(75123, 5, 741, 1, 818.70, 0.00);  
  
/* Prepare and execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Row successfully inserted.\n";  
}  
else  
{  
     echo "Row insertion failed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>例  
次の例では、AdventureWorks データベースの *Sales.SalesOrderDetail* テーブルのフィールドを更新します。 この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Assign literal parameter values. */  
$params = array( 5, 10);  
  
/* Execute the query. */  
if( sqlsrv_query( $conn, $tsql, $params))  
{  
      echo "Statement executed.\n";  
}   
else  
{  
      echo "Error in statement execution.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[方法: パラメーター化クエリを実行する](../../connect/php/how-to-perform-parameterized-queries.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
[方法: ストリームとしてデータを送信する](../../connect/php/how-to-send-data-as-a-stream.md)  
[方向パラメーターを使用する](../../connect/php/using-directional-parameters.md)  
  

