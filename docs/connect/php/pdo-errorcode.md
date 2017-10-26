---
title: "Pdo::errorcode |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a0104db7e46a377fa78b7f323de6ad237431a032
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
PDO_SQLSRV ドライバーの PDO::errorCode は、一部の操作の完了時に警告を返します。 たとえば、接続に成功すると、PDO::errorCode は "01000" を返します。これは SQL_SUCCESS_WITH_INFO を示します。  
  
PDO::errorCode は、データベース接続で直接実行された操作のエラー コードのみを返します。 PDO::prepare または PDO::query で PDOStatement インスタンスを作成し、ステートメント オブジェクトでエラーを生成すると、PDO::errorCode はそのエラーを取得しません。 特定のステートメント オブジェクトで実行された操作のエラー コードを返すには、PDOStatement::errorCode を呼び出す必要があります。  
  
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
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

