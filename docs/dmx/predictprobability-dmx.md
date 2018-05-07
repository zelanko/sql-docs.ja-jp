---
title: PredictProbability (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PredictProbability
dev_langs:
- DMX
helpviewer_keywords:
- PredictProbability function
ms.assetid: 7bb7e74f-e33b-4f7b-ade8-be21ace0dbd0
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 067a0159698357a42ff49780d4ae61cd3c64ecd8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="predictprobability-dmx"></a>PredictProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された状態の確率を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列です。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>解説  
 予測された状態が省略されている場合、省略した状態バケットを除いて、確率が最も高い状態が使用されます。 省略した状態バケットを含めるには、設定、\<予測状態 > に**INCLUDE_** です。 省略した状態の確率を返すには、設定、\<予測状態 > を NULL にします。  
  
> [!NOTE]  
>  一部のマイニング モデルでは、確率値が提供されていないため、この関数を使用できません。 また、特定の対象の値に関する確率値の計算方法は異なります。つまり、クエリの対象となるモデルに応じてこの確率値の解釈は異なる場合があります。 特定のモデルの種類の確率の計算方法の詳細については、個々 のアルゴリズムのトピックを参照してください。[マイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)です。  
  
## <a name="examples"></a>使用例  
 次の例は、自然予測結合を使用して、個人が TM Decision Tree マイニング モデルに基づいた自転車購入者である可能性を判断します。また、予測の確率も判断します。 この例では 2 つの PredictProbability 関数が示されています。使用可能な各値に対して 1 つの PredictProbability 関数が使用されています。 この引数を省略すると、関数は、最も可能性の高い値の確率を返します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 例の結果を次に示します。  
  
|Bike Buyer|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
