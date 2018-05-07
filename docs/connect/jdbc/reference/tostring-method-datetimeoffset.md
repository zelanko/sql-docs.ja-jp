---
title: toString メソッド (DateTimeOffset) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c9290b3a86d97efb3dd507819d4e858f3bf1ba7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tostring-method-datetimeoffset"></a>toString (DateTimeOffset) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  文字列表現を返します、 **DateTimeOffset**オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>戻り値  
 文字列表現、 **DateTimeOffset**オブジェクト。  
  
## <a name="remarks"></a>解説  
 文字列形式には*YYYY*-*MM*-*DD * * hh*:*mm*:*の*[.*fffffff*] [+ |-]*hh*:*mm*です。  
  
 返される文字列の小数部では、宣言されている有効桁数になるまでゼロが埋め込まれます。 たとえば、 **datetimeoffset(6)** 値は"2010-03-10 12:34:56.78 -08:00"として DateTimeOffset.toString でフォーマットされているが"2010-03-10 12:34:56.780000 -08:00"です。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
