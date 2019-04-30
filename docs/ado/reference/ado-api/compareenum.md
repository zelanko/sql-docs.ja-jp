---
title: CompareEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareEnum
helpviewer_keywords:
- CompareEnum enumeration [ADO]
ms.assetid: bc8f710d-0621-4673-8d8e-0361e44abed0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1f28a5dfc7e8abb15d1adf2f457ab49b4fbdd9c
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63459875"
---
# <a name="compareenum"></a>CompareEnum
ブックマークによって表される 2 つのレコードの相対位置を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adCompareEqual**|1|ブックマークが等しいことを示します。|  
|**adCompareGreaterThan**|2|2 つ目の後に最初のブックマークがあることを示します。|  
|**adCompareLessThan**|0|2 つ目の最初のブックマークがあることを示します。|  
|**adCompareNotComparable**|4|ブックマークを比較できないことを示します。|  
|**adCompareNotEqual**|3|ブックマークが異なっており、順位がないことを示します。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Compare.EQUAL|  
|AdoEnums.Compare.GREATERTHAN|  
|AdoEnums.Compare.LESSTHAN|  
|AdoEnums.Compare.NOTCOMPARABLE|  
|AdoEnums.Compare.NOTEQUAL|  
  
## <a name="applies-to"></a>適用対象  
 [CompareBookmarks メソッド (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)  
  
## <a name="see-also"></a>参照  
 [CompareBookmarks メソッド (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)
