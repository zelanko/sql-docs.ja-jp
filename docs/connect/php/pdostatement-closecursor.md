---
title: "Pdostatement::closecursor 呼び出します |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cf4a899dc14eea3bdf1cb2bf5f2be3ccf26eca89
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

カーソルを閉じて、もう一度実行するステートメントを有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>戻り値  
成功した場合は true、それ以外の場合は false です。  
  
## <a name="remarks"></a>解説  
MultipleActiveResultSets 接続オプションが false に設定されている場合に、closeCursor は有効になります。  MultipleActiveResultSets 接続オプションの詳細については、次を参照してください。[する方法: 無効にする複数のアクティブな結果セット (MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)です。  
  
closeCursor を呼び出す代わりに、ステートメント ハンドルを null に設定するだけでも同じことができます。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
