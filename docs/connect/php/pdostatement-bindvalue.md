---
title: PDOStatement::bindValue |Microsoft ドキュメント
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
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 293437aabacd65e16bc7312c080ac54fa4d70999
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34563850"
---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQL ステートメントで名前付きまたは疑問符プレースホルダーに値をバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::bindValue($parameter, $value[, $data_type]);  
```  
  
#### <a name="parameters"></a>パラメーター  
$*パラメーター*: (混合) パラメーター識別子。 ステートメントを使用して、名前付きプレース ホルダー、パラメーター名を使用して (: 名前)。 疑問符構文を使用して、準備されたステートメントのパラメーターの 1 から始まるインデックスを勧めします。
  
$*値*: パラメーターにバインドする (複合) 値です。  
  
$*data_type*: pdo::param _ * 定数によって表される省略可能な (整数) データ型。 既定は PDO::PARAM_STR です。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>コメント  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例は、$contact の値をバインドした後に、値を変更してもクエリで渡される値が変更されないことを示しています。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```

> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。 当てはまります bigint 型の列値の範囲は次の場合は特に、[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)です。

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
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
