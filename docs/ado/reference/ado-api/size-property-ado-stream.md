---
title: "Size プロパティ (ADO ストリーム) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _Stream::Size
helpviewer_keywords: Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0a58ee1c4e425af65518a1be5d8629acc849c67
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
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
