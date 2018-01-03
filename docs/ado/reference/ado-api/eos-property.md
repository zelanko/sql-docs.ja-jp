---
title: "EOS プロパティ |Microsoft ドキュメント"
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
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords: EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf26c00ecf445c9354d20fa5878942b56f2d2d19
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="eos-property"></a>EOS プロパティ
現在の位置がの末尾にあるかどうかを示す、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)です。  
  
## <a name="return-values"></a>戻り値  
 返します、**ブール**を現在の位置がストリームの末尾にするかどうかを示す値。 **EOS**返します**True**以上のバイトがストリームである場合を返します**False**現在の位置より多くの容量がある場合。  
  
 ストリームの位置の末尾を設定するには、使用、 [SetEOS](../../../ado/reference/ado-api/seteos-method.md)メソッドです。 現在の位置を確認するには[位置](../../../ado/reference/ado-api/position-property-ado.md)プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [EOS と LineSeparator プロパティ SkipLine メソッドの例 (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
