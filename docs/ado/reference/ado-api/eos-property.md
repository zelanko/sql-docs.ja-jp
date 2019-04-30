---
title: EOS プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47b3e48e612e0ee5595ada33127f016ee6b986f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180993"
---
# <a name="eos-property"></a>EOS プロパティ
現在の位置がの末尾にあるかどうかを示す、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)します。  
  
## <a name="return-values"></a>戻り値  
 返します、**ブール**現在の位置がストリームの末尾かどうかを示す値です。 **EOS**返します**True**以上のバイトがストリームである場合を返します**False**現在の位置より多くの容量がある場合。  
  
 ストリームの位置の末尾を設定するには、使用、 [SetEOS](../../../ado/reference/ado-api/seteos-method.md)メソッド。 現在の位置を調べるには、[位置](../../../ado/reference/ado-api/position-property-ado.md)プロパティ。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [EOS および LineSeparator プロパティの SkipLine メソッドの例 (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
