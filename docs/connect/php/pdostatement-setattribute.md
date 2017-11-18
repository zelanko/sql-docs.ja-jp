---
title: "Pdostatement::setattribute |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 31e760b44469df1e1f3a0d1c285b731d87155bcf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済み PDO 属性またはカスタム ドライバー属性のいずれかの属性値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*属性*::attr _ * または pdo::sqlsrv_attr _ のいずれかの整数\*定数。 使用可能な属性の一覧については、「解説」セクションを参照してください。  
  
$*値*: 指定された $ 用に設定する (複合) 値*属性*です。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>解説  
次の表に、使用可能な属性の一覧を示します。  
  
|attribute|値|Description|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|PHP メモリの制限に 1。|クライアント側カーソルの結果セットを保持するバッファーのサイズを設定します。<br /><br />既定では 10,240 KB (10 MB) です。<br /><br />クライアント側のカーソルの詳細については、次を参照してください。[カーソルの種類 & #40 です。PDO_SQLSRV ドライバー &#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|Integer<br /><br />PDO::SQLSRV_ENCODING_UTF8 (既定)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|ドライバーがサーバーとの通信に使用する文字セット エンコーディングを設定します。|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true または false|数値の SQL 型 (ビット、integer、smallint、tinyint、float または real) と列からの数値のフェッチを処理します。<br /><br />接続オプション フラグ ATTR_STRINGIFY_FETCHES が on の場合は、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がある場合でも文字列は、戻り値です。<br /><br />バインド列で返される PDO 型 PDO_PARAM_INT がある場合は、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がオフの場合でも、int は整数型の列からの戻り値です。|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Integer|クエリのタイムアウト (秒単位) を設定します。<br /><br />既定で、ドライバーは、結果を無制限に待機します。 負の数値は許可できません。<br /><br />0 は、タイムアウトがないことを示します。|  
  
## <a name="example"></a>例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

