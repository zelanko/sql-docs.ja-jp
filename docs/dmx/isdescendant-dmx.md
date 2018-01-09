---
title: "IsDescendant (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: IsDescendant
dev_langs: DMX
helpviewer_keywords: IsDescendant function
ms.assetid: d9fe7446-edb5-487b-8ea6-c9efaccf6d90
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 179a9f3f04db55cffb74f6417c3339ceeb20aa11
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
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
  
## <a name="remarks"></a>解説  
 **IsDescendant**だけで使われる[SELECT FROM &#60; モデル &#62;。コンテンツ &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)と[SELECT FROM &#60; モデル &#62;。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)クエリ。  
  
## <a name="examples"></a>使用例  
 次の例は、IsDescendant 関数に指定されたノードの子孫であるケースをすべて返します。  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
