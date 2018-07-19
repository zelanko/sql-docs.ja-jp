---
title: IsDescendant (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c33a607587ee19de0f47942cd2c1e5b350229a88
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061040"
---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  現在のノードが、指定したノードからの降順であるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>戻り値の型  
 Boolean 型。  
  
## <a name="remarks"></a>コメント  
 **IsDescendant**でのみ使用が[SELECT FROM&#60;モデル&#62;します。コンテンツ&#40;DMX&#41; ](../dmx/select-from-model-content-dmx.md)と[SELECT FROM&#60;モデル&#62;します。DIMENSION_CONTENT &#40;DMX&#41; ](../dmx/select-from-model-dimension-content-dmx.md)クエリ。  
  
## <a name="examples"></a>使用例  
 次の例は、IsDescendant 関数に指定されたノードの子孫であるケースをすべて返します。  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
