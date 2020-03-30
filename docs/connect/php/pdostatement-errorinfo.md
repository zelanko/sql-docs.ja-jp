---
title: PDOStatement::errorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15686a93c5e23a476968332479897d2fb5b90220
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993070"
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

[PDO](https://php.net/manual/book.pdo.php)  
  
