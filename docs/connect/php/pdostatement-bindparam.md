---
title: Pdostatement::bindparam |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 476030f5a5f08b2226036b5214ebc973a8a04b3a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34563940"
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQL ステートメントで名前付きまたは疑問符プレースホルダーにパラメーターをバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>パラメーター  
$*パラメーター*: (混合) パラメーター識別子。 ステートメントを使用して、名前付きプレース ホルダー、パラメーター名を使用して (: 名前)。 疑問符構文を使用して、準備されたステートメントのパラメーターの 1 から始まるインデックスを勧めします。  
  
&$*変数*: (混合の) SQL ステートメントのパラメーターにバインドする PHP 変数の名前。  
  
$*data_type*: 省略可能な (整数) pdo::param _ * 定数。 既定値は、pdo::param_str です。  
  
$*長さ*: データ型の省略可能な (整数) 長さ。 $ で PDO::param_int またはを使用する場合は、既定のサイズを示すように pdo::sqlsrv_param_out_default_size を指定する*data_type*です。  
  
$*指定する*: (混合の) ドライバー固有の省略可能なオプションです。 たとえば、PDO::SQLSRV_ENCODING_UTF8 と指定すると、UTF-8 でエンコードされた文字列として列を変数にバインドできます。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>コメント  
型 varbinary、binary、または varbinary (max) のサーバー列に null データをバインドするときは、バイナリ エンコード (pdo::sqlsrv_encoding_binary) を使用して $a を指定する必要があります*を指定する*です。 エンコード定数の詳細については、次を参照してください。[定数](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)です。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  

## <a name="example"></a>例  
このコード例は、$contact をパラメーターにバインドした後に値を変更すると、クエリで渡される値が変更されることを示しています。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>例  
このコード サンプルは、出力パラメーターにアクセスする方法を示しています。  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> 場合は、値がの範囲外に至る可能性があります、bigint 型出力パラメーターをバインドするときに、[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)、:param_int ように pdo::sqlsrv_param_out_default_size にされる可能性があります「範囲外の値」例外が発生します。 したがって、既定の pdo::param_str を代わりに使用され、21 は、最大で、結果の文字列のサイズを指定します。 これは、bigint 値の負の符号を含め、桁の最大数です。 

## <a name="example"></a>例  
このコード サンプルは、入力/出力パラメーターを使用する方法を示しています。  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。 当てはまります bigint 型の列値の範囲は次の場合は特に、[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)です。

## <a name="example"></a>例  
このコード サンプルでは、入力パラメーターとして 10 進値をバインドする方法を示します。  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
