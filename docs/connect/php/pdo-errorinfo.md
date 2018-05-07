---
title: Pdo::errorinfo |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9d5481d5-13bc-4388-b3aa-78676c0fc709
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba820eb4c534fb94302c2aa041e573c591376eda
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pdoerrorinfo"></a>PDO::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

データベース ハンドルの最新の操作のエラーの詳細情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array PDO::errorInfo();  
```  
  
## <a name="return-value"></a>戻り値  
データベース ハンドルの最新の操作に関するエラー情報の配列。 配列は、次のフィールドで構成されます。  
  
-   SQLSTATE エラー コード。  
  
-   ドライバー固有のエラー コード。  
  
-   ドライバー固有のエラー メッセージ。  
  
エラーがない場合、または SQLSTATE が設定されていない場合は、ドライバー固有のフィールドは NULL にします。  
  
## <a name="remarks"></a>解説  
PDO::errorInfo は、データベースで直接実行された操作のエラー情報だけを取得します。 PDO::prepare または PDO::query を使用して PDOStatement インスタンスを作成する場合は、PDOStatement::errorInfo を使用します。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例では、列の名前のスペルが正しい (`Cityx`の代わりに`City`)、結果、エラーが報告されます。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
echo "\n";  
print_r ($conn->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
