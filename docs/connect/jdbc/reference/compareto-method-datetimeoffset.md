---
title: compareTo (DateTimeOffset) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04f19f08deda9cd42affa0a5ced28255c1bb521b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742930"
---
# <a name="compareto-method-datetimeoffset"></a>compareTo (DateTimeOffset) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この比較**DateTimeOffset**を別のオブジェクト**DateTimeOffset** GMT 時刻に基づいてオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>パラメーター  
 現在のインスタンスと比較する [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) 値です。  
  
## <a name="return-value"></a>戻り値  
 次の表で、このメソッドの戻り値について説明します。  
  
|戻り値|[説明]|  
|------------------|-----------------|  
|0|両方**DateTimeOffset**オブジェクトの同じ時点を表しています。|  
|負の数|これは、 **DateTimeOffset**オブジェクトは、前にある時間の時点を表します*他*します。|  
|正の数|これは、 **DateTimeOffset**オブジェクトは、後にある時間の時点を表します*他*します。|  
  
## <a name="remarks"></a>Remarks  
 2 つの **DateTimeOffset** オブジェクトが GMT で同じ時間を表している場合は、オフセットに基づいたオブジェクトの追加の順序はありません。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
