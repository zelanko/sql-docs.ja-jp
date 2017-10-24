---
title: "EOS プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c29c72e9cd88ff5672b90aeab5da97c7742f5b30
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="eos-property"></a>EOS プロパティ
現在の位置がの末尾にあるかどうかを示す、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)です。  
  
## <a name="return-values"></a>戻り値  
 返します、**ブール**を現在の位置がストリームの末尾にするかどうかを示す値。 **EOS**返します**True**以上のバイトがストリームである場合を返します**False**現在の位置より多くの容量がある場合。  
  
 ストリームの位置の末尾を設定するには、使用、 [SetEOS](../../../ado/reference/ado-api/seteos-method.md)メソッドです。 現在の位置を確認するには[位置](../../../ado/reference/ado-api/position-property-ado.md)プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [EOS と LineSeparator プロパティ SkipLine メソッドの例 (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

