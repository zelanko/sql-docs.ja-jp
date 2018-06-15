---
title: sqlsrv_fetch |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_fetch
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch
- API Reference, sqlsrv_fetch
- retrieving data, as a single field
ms.assetid: a5a640a1-6e7d-452e-8b66-850a4dc2ce89
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf3aeff30e84deed5f66eb65d778aa4c154eef98
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309031"
---
# <a name="sqlsrvfetch"></a>sqlsrv_fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

結果セットの次の行を読み取り可能にします。 使用して[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)行のフィールドを読み取れません。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_fetch( resource $stmt[, row[, ]offset])  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 実行されたステートメントに対応するステートメント リソースです。  
  
> [!NOTE]  
> 結果を取得するには、ステートメントを実行する必要があります。 ステートメントを実行する方法の詳細については、「 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 」と「 [sqlsrv_execute](../../connect/php/sqlsrv-execute.md)」を参照してください。  
  
*行*[省略可能]: スクロール可能なカーソルを使用して結果セットにアクセスする行を指定する、次の値のいずれか。  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
これらの値の詳細については、「 [カーソルの種類を指定し、行を選択する](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)」を参照してください。  
  
*オフセット*[省略可能]: SQLSRV_SCROLL_ABSOLUTE と SQLSRV_SCROLL_RELATIVE と共に取得する行を指定するために使用します。 結果セットの最初のレコードは 0 です。  
  
## <a name="return-value"></a>戻り値  
結果セットの次の行が正常に取得された場合は、 **true** が返されます。 結果セットに他に結果がない場合は、 **null** が返されます。 エラーが発生した場合は、 **false** が返されます。  
  
## <a name="example"></a>例  
次の例では、 **sqlsrv_fetch** を使用して、製品レビューとレビュー担当者の名前を含むデータの行を取得します。 結果セットからデータを取得する[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)を使用します。 例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of SQL Server type nvarchar. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false)  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream ))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[データの取得](../../connect/php/retrieving-data.md)  

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
