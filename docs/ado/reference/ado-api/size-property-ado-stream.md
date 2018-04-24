---
title: Size プロパティ (ADO ストリーム) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
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
ms.workload: Inactive
ms.openlocfilehash: 5b1ecbc53ec085ec67b827338dbf7899245278e9
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="size-property-ado-stream"></a>Size プロパティ (ADO Stream)
バイト数でストリームのサイズを示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**長い**ストリームのサイズをバイト数で指定する値。 既定値は、ストリームのサイズが不明の場合に、ストリーム、または-1 のサイズです。  
  
## <a name="remarks"></a>解説  
 **サイズ**開くでのみ使用できます[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
> [!NOTE]
>  任意のビット数を格納できる、**ストリーム**オブジェクト、システム リソースによってのみ制限されます。 場合、**ストリーム**で表現できる以上のビット数を含む、**長い**値、**サイズ**は切り捨てられ、そのため正確に表さない、の長さ**ストリーム**です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Size プロパティ (ADO Parameter)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
