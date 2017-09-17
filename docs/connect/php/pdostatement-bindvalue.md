---
title: "PDOStatement::bindValue |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c006ba33bad8d0afb010b0f0bbe316d7a5e3e28f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQL ステートメントで名前付きまたは疑問符プレースホルダーに値をバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::bindValue( $parameter, $value [,$data_type] );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*パラメーター*: (混合) パラメーター識別子。 名前付きプレースホルダーを使用するステートメントの場合、パラメーター名 (:name)。 疑問符構文を使用する準備されたステートメントの場合、これはパラメーターの 1 から始まるインデックスになります。  
  
$*値*: パラメーターにバインドする (複合) 値です。  
  
$*data_type*: pdo::param _ * 定数によって表される省略可能な (整数) データ型。 既定は PDO::PARAM_STR です。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>解説  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例は、$contact の値をバインドした後に、値を変更してもクエリで渡される値が変更されないことを示しています。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

