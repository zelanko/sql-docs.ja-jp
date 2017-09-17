---
title: "Pdostatement::bindparam |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 02d31959423de5c0df4dc06e9caa16ea983ef000
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQL ステートメントで名前付きまたは疑問符プレースホルダーにパラメーターをバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::bindParam( $parameter, &$variable [,$data_type[, $length[, $driver_options]]] );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*パラメーター*: (混合) パラメーター識別子。 名前付きプレースホルダーを使用するステートメントの場合、パラメーター名 (:name)。 疑問符構文を使用する準備されたステートメントの場合、これはパラメーターの 1 から始まるインデックスになります。  
  
&$*変数*: (混合の) SQL ステートメントのパラメーターにバインドする PHP 変数の名前。  
  
$*data_type*: 省略可能な (整数) pdo::param _ * 定数。 既定値は、pdo::param_str です。  
  
$*長さ*: データ型の省略可能な (整数) 長さ。 $ で PDO::param_int またはを使用する場合は、既定のサイズを示すように pdo::sqlsrv_param_out_default_size を指定する*data_type*です。  
  
$*指定する*: (混合の) ドライバー固有の省略可能なオプションです。 たとえば、PDO::SQLSRV_ENCODING_UTF8 と指定すると、UTF-8 でエンコードされた文字列として列を変数にバインドできます。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>解説  
型 varbinary、binary、または varbinary (max) のサーバー列に null データをバインドするときは、バイナリ エンコード (pdo::sqlsrv_encoding_binary) を使用して $a を指定する必要があります*を指定する*です。 エンコード定数の詳細については、「 [定数](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md) 」を参照してください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
このコード例は、$contact をパラメーターにバインドした後に値を変更すると、クエリで渡される値が変更されることを示しています。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
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
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(* ) from Sys.tables");  
$stmt->bindParam( 1, $input1, PDO::PARAM_STR, 10 );  
$stmt->execute();  
echo $input1;  
?>  
```  
  
## <a name="example"></a>例  
このコード サンプルは、入力/出力パラメーターを使用する方法を示しています。  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

