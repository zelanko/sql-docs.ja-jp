---
title: PredictAdjustedProbability (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9fd11ec1fcdf9a3c6ce5dc6476e877d808710b54
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989641"
---
# <a name="predictadjustedprobability-dmx"></a>PredictAdjustedProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された状態の調整済みの確率を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictAdjustedProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列です。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>コメント  
 予測された状態が省略されている場合、省略した状態バケットを除いて、最も予測可能性が高い状態が使用されます。 省略した状態バケットを含めるには設定、\<予測状態 > に**INCLUDE_** します。  
  
 省略した状態の調整済みの確率を返すには、設定、\<予測状態 > を NULL にします。  
  
 **PredictAdjustedProbability**関数は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]拡張機能を[!INCLUDE[msCoName](../includes/msconame-md.md)]OLE DB for Data Mining 仕様です。  
  
## <a name="examples"></a>使用例  
 次の例は、自然予測結合を使用して、個人が TM Decision Tree マイニング モデルに基づいた自転車購入者である可能性を判断します。また、予測の調整済みの確率も判断します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictAdjustedProbability([Bike Buyer]) AS [Adjusted Probability]  
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
  
  
