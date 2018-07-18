---
title: Size プロパティ (ADO ストリーム) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6d39bb563acfde83a08f08c00fee66cc9b81967
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281887"
---
# <a name="size-property-ado-stream"></a>Size プロパティ (ADO Stream)
バイト数でストリームのサイズを示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**長い**ストリームのサイズをバイト数で指定する値。 既定値は、ストリームのサイズが不明の場合に、ストリーム、または-1 のサイズです。  
  
## <a name="remarks"></a>コメント  
 **サイズ**開くでのみ使用できます[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
> [!NOTE]
>  任意のビット数を格納できる、**ストリーム**オブジェクト、システム リソースによってのみ制限されます。 場合、**ストリーム**で表現できる以上のビット数を含む、**長い**値、**サイズ**は切り捨てられ、そのため正確に表さない、の長さ**ストリーム**です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Size プロパティ (ADO Parameter)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
