---
title: sqlsrv_num_fields |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/23/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- sqlsrv_num_fields
apitype: NA
helpviewer_keywords:
- sqlsrv_num_fields
- API Reference, sqlsrv_num_fields
ms.assetid: 03ca1860-01ed-408c-862a-57a7355de4bf
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80028fcf1b4a1c3d947bef49c2a4edc617f9d2d1
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="sqlsrvnumfields"></a>sqlsrv_num_fields
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

アクティブな結果セット内のフィールド数を取得します。 この関数は前に、または実行後、準備したステートメントで呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_num_fields( resource $stmt)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 対象の結果セットがアクティブなステートメント。  
  
## <a name="return-value"></a>戻り値  
アクティブな結果セットのフィールド数を表す整数値。 エラーが発生すると、ブール値 **false** が返されます。  
  
## <a name="example"></a>例  
次の例の先頭の 3 行のすべてのフィールドを取得するクエリの実行、 *HumanResources.Department* AdventureWorks データベースのテーブルです。 **Sqlsrv_num_fields**関数は、結果セット内のフィールドの数を決定します。 この結果を利用して、返される各行のフィールドを反復処理してデータを表示します。  
  
例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
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
  
/* Define and execute the query. */  
$tsql = "SELECT TOP (3) * FROM HumanResources.Department";  
$stmt = sqlsrv_query($conn, $tsql);  
if( $stmt === false)  
{  
     echo "Error in executing query.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve the number of fields. */  
$numFields = sqlsrv_num_fields( $stmt );  
  
/* Iterate through each row of the result set. */  
while( sqlsrv_fetch( $stmt ))  
{  
     /* Iterate through the fields of each row. */  
     for($i = 0; $i < $numFields; $i++)  
     {  
          echo sqlsrv_get_field($stmt, $i,   
                   SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR))." ";  
     }  
     echo "\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt );  
sqlsrv_close( $conn );  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
