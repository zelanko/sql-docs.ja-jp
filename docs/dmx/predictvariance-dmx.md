---
title: PredictVariance (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6217df2efb63b691ad565ea4d6466cdbd5831830
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970680"
---
# <a name="predictvariance-dmx"></a>PredictVariance (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  指定された列の分散を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictVariance(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列。  
  
## <a name="return-type"></a>戻り値の型  
 によって指定された型のスカラー値 *\<scalar column reference>* 。  
  
## <a name="remarks"></a>注釈  
 列参照が不連続の場合、 **Predictvariance**は0を返します。これは、不連続値から分散を計算できないためです。  
  
## <a name="examples"></a>例  
 次の例では、自然予測結合を使用して、個人が TM デシジョンツリーマイニングモデルに基づいた自転車購入者である可能性があるかどうかを判断し、さらに予測の分散を決定します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictVariance([Bike Buyer]) AS [Variance]  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)  
  
  
