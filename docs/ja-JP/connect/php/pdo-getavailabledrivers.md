---
title: PDO::getAvailableDrivers |Microsoft ドキュメント
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
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ccc7d27f4e96c2e0694b40edd3b0d9644831f6c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PHP のインストールで PDO ドライバーの配列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>戻り値  
PDO ドライバーの一覧が格納された配列。  
  
## <a name="remarks"></a>解説  
PDO ドライバーの名前は、PDO インスタンスを作成するときに PDO::__construct で使用されます。  
  
PHP ドライバーで実行する場合、PDO::getAvailableDrivers は必要ありません。 このメソッドの詳細については、PHP ドキュメントを参照してください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
