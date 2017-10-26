---
title: "Pdostatement::getcolumnmeta |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 98925f324725be6c061c0baed6a3df320d1b39e2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

列のメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: (整数) を取得するメタデータを持つ列の 0 から始まる番号。  
  
## <a name="return-value"></a>戻り値  
列のメタデータを格納している連想配列 (キーと値)。 配列内のフィールドの詳細については「解説」セクションを参照してください。  
  
## <a name="remarks"></a>解説  
次の表では、getColumnMeta によって返される配列内のフィールドについて説明します。  
  
|NAME|VALUES|  
|--------|----------|  
|native_type|列の PHP 型を指定します。 常に文字列です。|  
|driver:decl_type|データベースで列の値を表すために使用される SQL 型を指定します。 結果セット内の列が関数の結果である場合、この値は PDOStatement::getColumnMeta では返されません。|  
|flags|この列に設定されているフラグを指定します。 常に 0 です。|  
|NAME|データベースでの列の名前を指定します。|  
|テーブル|データベースで列を含むテーブルの名前を指定します。 常に空白です。|  
|len|列の長さを指定します。|  
|有効桁数 (precision)|この列の数値の有効桁数を指定します。|  
|pdo_type|PDO::PARAM_* 定数によって表される、この列の型を指定します。 常に PDO::PARAM_STR (2) です。|  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

