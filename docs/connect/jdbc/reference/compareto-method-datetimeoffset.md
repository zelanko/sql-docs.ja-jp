---
title: compareTo メソッド (DateTimeOffset) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e2953d21306cf69582e2744c4fb96e13e0098d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="compareto-method-datetimeoffset"></a>compareTo (DateTimeOffset) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これと比較**DateTimeOffset**を別のオブジェクト**DateTimeOffset**オブジェクトが GMT の時間に基づいています。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>パラメーター  
 A [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)を現在のインスタンスを比較する値。  
  
## <a name="return-value"></a>戻り値  
 次の表で、このメソッドの戻り値について説明します。  
  
|戻り値|Description|  
|------------------|-----------------|  
|0|両方**DateTimeOffset**オブジェクトでは、時間の同じ時点を表しています。|  
|負の数|これは、 **DateTimeOffset**オブジェクトは、前にある時間の時点を表します*他*です。|  
|正の数値|これは、 **DateTimeOffset**オブジェクトは、後にある時間の時点を表します*他*です。|  
  
## <a name="remarks"></a>解説  
 2 つ**DateTimeOffset**オブジェクト、同時に GMT のオフセットに基づいて、オブジェクトの追加順序がありません。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
