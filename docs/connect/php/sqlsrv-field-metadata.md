---
title: sqlsrv_field_metadata |Microsoft ドキュメント
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
apiname:
- sqlsrv_field_metadata
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_field_metadata
- sqlsrv_field_metadata
ms.assetid: c02f6942-0484-4567-a78e-fe8aa2053536
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e7f7d66bb363ec42b6dc0ad5e0d9cd019ffe78f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvfieldmetadata"></a>sqlsrv_field_metadata
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

準備されたステートメントのフィールドのメタデータを取得します。 ステートメントの準備については、「 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 」または「 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)」を参照してください。 なお**sqlsrv_field_metadata**前または実行後、準備されたステートメントで呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_field_metadata( resource $stmt)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: フィールドのメタデータを要求するステートメント リソース。  
  
## <a name="return-value"></a>戻り値  
配列の **array** 、または **false**。 array は、結果セット内のフィールドごとに 1 つの配列で構成されます。 各サブ配列には、次の表で示すようなキーがあります。 フィールド メタデータの取得中にエラーが発生した場合は、 **false** が返されます。  
  
|Key|Description|  
|-------|---------------|  
|名前|フィールドが対応する列の名前。|  
|型|SQL 型に対応する数値。|  
|サイズ|文字型 (char(n)、varchar(n)、nchar(n)、nvarchar(n)、XML) のフィールドの文字数。 バイナリ型 (binary(n)、varbinary(n)、UDT) のフィールドのバイト数。 他の SQL Server データ型の場合は**NULL** 。|  
|有効桁数|可変精度の型 (real、numeric、decimal、datetime2、datetimeoffset、time) の有効桁数。 他の SQL Server データ型の場合は**NULL** 。|  
|Scale|可変スケールの型 (numeric、decimal、datetime2、datetimeoffset、time) のスケール。 他の SQL Server データ型の場合は**NULL** 。|  
|[可]|列が null 値を許容するかどうかを示す列挙値 (**SQLSRV_NULLABLE_YES**)、列値が許容されません (**SQLSRV_NULLABLE_NO**)、列が null 許容の場合は、不明または (**SQLSRV_NULLABLE_UNKNOWN**)。|  
  
次の表では、各サブ配列のキーについての詳細を示します (これらの型の詳細については、SQL Server のマニュアルを参照してください)。  
  
|SQL Server 2008 のデータ型|型|最小/最大有効桁数|最小/最大スケール|サイズ|  
|-----------------------------|--------|----------------------|------------------|--------|  
|bigint|SQL_BIGINT (-5)|||8|  
|binary|SQL_BINARY (-2)|||0 < *n* < 8000 <sup>1</sup>|  
|bit|SQL_BIT (-7)||||  
|char|SQL_CHAR (1)|||0 < *n* < 8000 <sup>1</sup>|  
|date|SQL_TYPE_DATE (91)|10/10|0/0||  
|datetime|SQL_TYPE_TIMESTAMP (93)|23/23|3/3||  
|datetime2|SQL_TYPE_TIMESTAMP (93)|19/27|0/7||  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET (-155)|26/34|0/7||  
|decimal|SQL_DECIMAL (3)|1/38|0/有効桁数の値||  
|float|SQL_FLOAT (6)|4/8|||  
|image|SQL_LONGVARBINARY (-4)|||2 GB|  
|int|SQL_INTEGER (4)||||  
|money|SQL_DECIMAL (3)|19/19|4/4||  
|NCHAR|SQL_WCHAR (-8)|||0 < *n* < 4000 <sup>1</sup>|  
|ntext|SQL_WLONGVARCHAR (-10)|||1 GB|  
|numeric|SQL_NUMERIC (2)|1/38|0/有効桁数の値||  
|nvarchar|SQL_WVARCHAR (-9)|||0 < *n* < 4000 <sup>1</sup>|  
|real|SQL_REAL (7)|4/4|||  
|smalldatetime|SQL_TYPE_TIMESTAMP (93)|16/16|0/0||  
|smallint|SQL_SMALLINT (5)|||2 バイト|  
|Smallmoney|SQL_DECIMAL (3)|10/10|4/4||  
|text|SQL_LONGVARCHAR (-1)|||2 GB|  
|time|SQL_SS_TIME2 (-154)|8/16|0/7||  
|timestamp|SQL_BINARY (-2)|||8 バイト|  
|tinyint|SQL_TINYINT (-6)|||1 バイト|  
|udt|SQL_SS_UDT (-151)|||変数 (variable)|  
|uniqueidentifier|SQL_GUID (-11)|||16|  
|varbinary|SQL_VARBINARY (-3)|||0 < *n* < 8000 <sup>1</sup>|  
|varchar|SQL_VARCHAR (12)|||0 < *n* < 8000 <sup>1</sup>|  
|xml|SQL_SS_XML (-152)|||0|  
  
(1) 0 は最大サイズが許容されることを示します。  
  
Nullable キーは yes または no です。  
  
## <a name="example"></a>例  
次の例では、ステートメント リソースを作成した後、フィールド メタデータを取得して表示します。 例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
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
  
/* Prepare the statement. */  
$tsql = "SELECT ReviewerName, Comments FROM Production.ProductReview";  
$stmt = sqlsrv_prepare( $conn, $tsql);  
  
/* Get and display field metadata. */  
foreach( sqlsrv_field_metadata( $stmt) as $fieldMetadata)  
{  
      foreach( $fieldMetadata as $name => $value)  
      {  
           echo "$name: $value\n";  
      }  
      echo "\n";  
}  
  
/* Note: sqlsrv_field_metadata can be called on any statement  
resource, pre- or post-execution. */  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  

[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
