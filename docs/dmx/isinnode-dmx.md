---
title: IsInNode (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsInNode
dev_langs:
- DMX
helpviewer_keywords:
- IsInNode function
ms.assetid: 47b2114f-9ad6-45cc-9498-193ad6fa5288
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5db634f9fdffc8792ab72523f59f886ddb37b442
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="isinnode-dmx"></a>IsInNode (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたノードが現在のケースを含んでいるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsInNode(<NodeID>)  
```  
  
## <a name="return-type"></a>戻り値の型  
 Boolean 型。  
  
## <a name="remarks"></a>解説  
 **IsInNode**だけで使われる[SELECT FROM&#60;モデル&#62;です。ケース&#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md)と[SELECT FROM&#60;モデル&#62;です。SAMPLE_CASES &#40;DMX&#41; ](../dmx/select-from-model-sample-cases-dmx.md)クエリ。  
  
## <a name="examples"></a>使用例  
 次の例は、IsInNode 関数に指定されたノードと関連付けられているモデルの作成に使用された、すべてのケースを返します。  
  
```  
Select * from [TM Decision Tree].Cases  
WHERE IsInNode('0')  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
