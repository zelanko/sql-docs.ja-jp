---
title: Pdo::begintransaction |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f4c785d876629c3a2f95f70f15de6145f50e1af
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

自動コミット モードをオフにしてトランザクションを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>戻り値  
メソッドの呼び出しに成功した場合は true、それ以外の場合は false。  
  
## <a name="remarks"></a>解説  
Pdo::begintransaction で開始されたトランザクションが終了[pdo::commit](../../connect/php/pdo-commit.md)または[pdo::rollback](../../connect/php/pdo-rollback.md)と呼びます。  
  
PDO::beginTransaction は PDO::ATTR_AUTOCOMMIT の値によって影響を受けず、PDO::ATTR_AUTOCOMMIT の値に影響を与えません。  
  
前の PDO::beginTransaction が PDO::rollback または PDO::commit で終了する前に PDO::beginTransaction を呼び出すことはできません。  
  
接続は、このメソッドが失敗した場合に、自動コミット モードを返します。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
次の例では、「Test」という名前のデータベースと「Table1」という名前のテーブルを使用します。 トランザクションを開始し、コマンドを発行して 2 つの行を追加し、1 つの行を削除します。 コマンドはデーダースに送信され、トランザクションは `PDO::commit`で明示的に終了します。  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
