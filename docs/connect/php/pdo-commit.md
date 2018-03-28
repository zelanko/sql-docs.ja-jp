---
title: Pdo::commit |Microsoft ドキュメント
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
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f734c30d7b4577229f9e69e05291ab8305b19407
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="pdocommit"></a>PDO::commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) を呼び出した後に発行されたデータベースにコマンドを送信し、接続を自動コミット モードに戻します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDO::commit();  
```  
  
## <a name="return-value"></a>戻り値  
メソッドの呼び出しに成功した場合は true、それ以外の場合は false。  
  
## <a name="remarks"></a>解説  
PDO::commit は PDO::ATTR_AUTOCOMMIT の値によって影響を受けず、PDO::ATTR_AUTOCOMMIT の値に影響を与えません。  
  
PDO::commit の使用例については、「 [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) 」を参照してください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
