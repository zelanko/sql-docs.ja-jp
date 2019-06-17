---
title: Pdostatement::errorcode |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6a5d32c29368dc141a12ae6eb300137b91935fb3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780472"
---
# <a name="pdostatementerrorcode"></a>PDOStatement::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

データベース ステートメント オブジェクトの最新の操作の SQLSTATE を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
string PDOStatement::errorCode();  
```  
  
## <a name="return-value"></a>戻り値  
5 文字の SQLSTATE を文字列として返すか、ステートメント ハンドルに操作がない場合は、NULL が返されます。  
  
## <a name="remarks"></a>Remarks  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
次の例では、エラーが発生している SQL クエリを示します。  さらに、エラー コードを示します。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print $stmt->errorCode();  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
