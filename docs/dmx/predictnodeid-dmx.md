---
title: PredictNodeId (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5202662b1bd41671905379272b2a52ba87510ecc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037360"
---
# <a name="predictnodeid-dmx"></a>PredictNodeId (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ケースが分類されるノードの Node_ID を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictNodeId(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列です。  
  
## <a name="return-type"></a>戻り値の型  
 \<スカラー式 >  
  
## <a name="examples"></a>使用例  
 次の例は、指定された個人が自転車を購入するかどうかを返します。また、含まれている可能性が最も高いノードの nodeID も返します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictNodeId([Bike Buyer])  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 さらに、次のステートメントを使用して、何がノード内に含まれているかを判断します。  
  
```  
SELECT   
  NODE_CAPTION   
FROM   
  [TM Decision Tree].CONTENT  
WHERE NODE_UNIQUE_NAME= '00000000100'   
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
