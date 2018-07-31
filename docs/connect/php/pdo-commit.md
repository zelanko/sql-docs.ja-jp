---
title: Pdo::commit |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b60b75aea820f1f9ef41c099aa8d9b2bb98b875
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979684"
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
  
## <a name="remarks"></a>Remarks  
PDO::commit は PDO::ATTR_AUTOCOMMIT の値によって影響を受けず、PDO::ATTR_AUTOCOMMIT の値に影響を与えません。  
  
PDO::commit の使用例については、「 [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) 」を参照してください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
