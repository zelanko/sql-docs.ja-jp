---
title: IsDescendant (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2ef32a9e133c199aae0779c819736d77e0d15c45
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670062"
---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  現在のノードが、指定されたノードから下降しているかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>戻り値の型  
 ブール型です。  
  
## <a name="remarks"></a>Remarks  
 **Isdescendant**は、 [SELECT FROM &#60;model&#62; でのみ使用されます。コンテンツ &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md) 、 [&#60;モデル&#62; から選択します。DMX&#41;クエリを &#40;DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)します。  
  
## <a name="examples"></a>例  
 次の例は、IsDescendant 関数に指定されたノードの子孫であるケースをすべて返します。  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)  
  
  
