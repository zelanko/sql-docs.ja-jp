---
title: Pdostatement::execute |Microsoft ドキュメント
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
ms.assetid: c2e80566-fa41-4918-8521-cf2e05374cbd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dabdabb4b3a4d20884004909dfaab0272f2e9c43
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34563870"
---
# <a name="pdostatementexecute"></a>PDOStatement::execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

ステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::execute ([ $input ] );  
```  
  
#### <a name="parameters"></a>パラメーター  
*$input*: (省略可能) パラメーター マーカーの値を含む連想配列。  
  
## <a name="return-value"></a>戻り値  
成功した場合は true、それ以外の場合は false。  
  
## <a name="remarks"></a>コメント  
PDOStatement::execute で実行するステートメントは、最初に [PDO::prepare](../../connect/php/pdo-prepare.md)で準備する必要があります。 ステートメントの直接実行または準備された実行を指定する方法については、「 [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md) 」(PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行) を参照してください。  
  
入力パラメーター配列のすべての値は、PDO::PARAM_STR 値として扱われます。  
  
準備されたステートメントにパラメーター マーカーが含まれる場合は、PDOStatement::bindParam を呼び出して PHP 変数をパラメーター マーカーにバインドするか、入力専用パラメーター値の配列を渡す必要があります。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query );  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
  
echo "\n";  
$param = "Owner";  
$query = "select * from Person.ContactType where name = ?";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
?>  
```  
  
> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。 当てはまります bigint 型の列値の範囲は次の場合は特に、[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)です。

## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
