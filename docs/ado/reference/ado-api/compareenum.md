---
title: "CompareEnum |Microsoft ドキュメント"
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
- CompareEnum
helpviewer_keywords:
- CompareEnum enumeration [ADO]
ms.assetid: bc8f710d-0621-4673-8d8e-0361e44abed0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 01574487f221503f93e8ff58ba59c8afebe1bf9e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="compareenum"></a>CompareEnum
ブックマークによって表される 2 つのレコードの相対位置を指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adCompareEqual**|1|ブックマークが等しいことを示します。|  
|**adCompareGreaterThan**|2|最初のブックマークが、2 つ目の後にあることを示します。|  
|**adCompareLessThan**|0|2 つ目の最初のブックマークであることを示します。|  
|**adCompareNotComparable**|4|ブックマークを比較できないことを示します。|  
|**adCompareNotEqual**|3|ブックマークが異なっており、順位がないことを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
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
