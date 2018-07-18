---
title: PredictSupport (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57b340d4f79ec093f6322687ceca0186931a9dcf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037340"
---
# <a name="predictsupport-dmx"></a>PredictSupport (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された状態に対するサポート値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列です。  
  
## <a name="return-type"></a>戻り値の型  
 指定された型のスカラー値 *\<* スカラー列参照*>* します。  
  
## <a name="remarks"></a>コメント  
 予測された状態が省略されている場合、省略した状態バケットを除いて、最も予測可能性が高い状態が使用されます。 省略した状態バケットを含めるには設定、\<予測状態 > に**INCLUDE_** します。  
  
 省略した状態のサポートを返すには、設定、\<予測状態 > を NULL にします。  
  
> [!NOTE]  
>  サポートされている値の計算方法は異なります。つまり、クエリの対象となるモデルに応じてこの値の解釈は異なる場合があります。 任意の特定のモデル型のサポートを計算する方法の詳細については、各アルゴリズムの種類を参照してください。[マイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)します。  
  
## <a name="examples"></a>使用例  
 次の例は、単一クエリを使用して、個人が自転車購入者となるかどうかを予測します。また、TM Decision Tree マイニング モデルに基づいて、予測に対するサポートも判断します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
