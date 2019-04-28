---
title: PredictProbability (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f2a01e2cfd460d503e4326c44eaf356b8a5ecb4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659165"
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
  
## <a name="remarks"></a>コメント  
 予測された状態が省略されている場合、省略した状態バケットを除いて、確率が最も高い状態が使用されます。 省略した状態バケットを含めるには設定、\<予測状態 > に**INCLUDE_** します。 省略した状態の確率を返すには、設定、\<予測状態 > を NULL にします。  
  
> [!NOTE]  
>  一部のマイニング モデルでは、確率値を指定しないと、そのため、この関数を使用することはできません。 さらに、任意の特定のターゲット値の確率値は別に計算したり、クエリを実行するモデルの種類に応じて解釈が異なる場合があります。 特定のモデルの種類に関する確率を計算する方法の詳細については、個々 のアルゴリズムのトピックを参照してください。[マイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)します。  
  
## <a name="examples"></a>使用例  
 次の例では、自然予測結合を使用して、個人が TM Decision Tree マイニング モデルに基づいた自転車購入者である可能性がかどうかを決定しも、予測の確率を決定します。 この例では、それぞれの値に対して 1 つ、2 つの PredictProbability 関数があります。 この引数を省略する場合が最も高い値の確率を返します。  
  
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
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
