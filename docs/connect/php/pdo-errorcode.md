---
title: PDO::errorCode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 143a7bef0a0be2d125068a7f003b0b941ff39617
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode はデータベース ハンドルの最新の操作の SQLSTATE を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>戻り値  
PDO::errorCode は、5 文字の SQLSTATE を文字列として返すか、データベース ハンドルに操作がない場合、NULL を返されます。  
  
## <a name="remarks"></a>解説  
PDO_SQLSRV ドライバーの pdo::errorcode は、一部の操作に関する警告を返します。 たとえば、正常に接続する、pdo::errorcode「01000」を示す SQL_SUCCESS_WITH_INFO を返します。  
  
PDO::errorCode は、データベース接続で直接実行された操作のエラー コードのみを返します。 Pdo::prepare で PDOStatement インスタンスを作成するか、または pdo::query し、エラーは、ステートメント オブジェクトで、pdo::errorcode はそのエラーを取得できません。 特定のステートメント オブジェクトで実行された操作のエラー コードを返すには、PDOStatement::errorCode を呼び出す必要があります。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例では、列の名前のスペルが正しい (`Cityx`の代わりに`City`)、結果、エラーが報告されます。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
