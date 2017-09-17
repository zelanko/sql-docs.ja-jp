---
title: ":Errorinfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3e570149983e08d69d32da146871ad4ae0c4f52
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementerrorinfo"></a>PDOStatement::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

ステートメント ハンドルの最新の操作に関する拡張エラー情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array PDOStatement::errorInfo();  
```  
  
## <a name="return-value"></a>戻り値  
ステートメント ハンドルに対する最新の操作に関するエラー情報の配列。 配列は、次のフィールドで構成されます。  
  
-   SQLSTATE エラー コード  
  
-   ドライバー固有のエラー コード  
  
-   ドライバー固有のエラー メッセージ  
  
エラーがない場合、または SQLSTATE が設定されていない場合、ドライバー固有のフィールドは NULL になります。  
  
## <a name="remarks"></a>解説  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例では、SQL ステートメントにエラーがあるので、そのエラーがレポートされます。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print_r ($stmt->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

