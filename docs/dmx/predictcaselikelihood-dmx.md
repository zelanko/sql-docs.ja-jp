---
title: PredictCaseLikelihood (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e061269ebf864a93d6dde50455627cf8e2ea780
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659215"
---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  この関数は、既存のモデル内に入力したケースが収まる確率値を返します。 クラスター モデルでのみ使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictCaseLikelihood([NORMALIZED|NONNORMALIZED])  
```  
  
## <a name="arguments"></a>引数  
 NORMALIZED  
 戻り値は、モデル内のケースの確率をモデルのないケースの確率で除算した結果を格納します。  
  
 正規化  
 戻り値は、ケースの未加工の確率、つまりケース属性の確率の積を格納します。  
  
## <a name="applies-to"></a>適用対象  
 使用して作成されたモデルの[!INCLUDE[msCoName](../includes/msconame-md.md)]クラスタ リングと[!INCLUDE[msCoName](../includes/msconame-md.md)]シーケンス クラスター アルゴリズムです。  
  
## <a name="return-type"></a>戻り値の型  
 0 ~ 1 の間、浮動小数点数を倍精度。 値が 1 に近い場合にこのモデルで発生する可能性が高くを示します。 値が 0 に近いほど、このモデルでケースが発生する確率が低くなります。  
  
## <a name="remarks"></a>コメント  
 既定の結果、 **PredictCaseLikelihood**関数を正規化します。 通常、正規化された値は、ケース内の属性の数が増え、任意の 2 つのケースの未加工の確率の差が小さくなるほど、有用性が増します。  
  
 次の式は、指定した x および y は、正規化された値の計算に使用されます。  
  
-   x = クラスタリング モデルに基づいたケースの確率値  
  
-   y = トレーニング ケースの数に基づいたケースの対数尤度として計算周辺確率値の大文字と小文字  
  
-   Z = Exp( log(x) - Log(Y))  
  
 正規化された = (z/(1 + z))  
  
## <a name="examples"></a>使用例  
 次の例は、指定したケースがクラスター モデルに基づく内で発生する可能性を返します、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW データベース。  
  
```  
SELECT  
  PredictCaseLikelihood() AS Default_Likelihood,  
  PredictCaseLikelihood(NORMALIZED) AS Normalized_Likelihood,  
  PredictCaseLikelihood(NONNORMALIZED) AS Raw_Likelihood,  
FROM  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 期待される結果:  
  
|Default_Likelihood|Normalized_Likelihood|Raw_Likelihood|  
|-------------------------|----------------------------|---------------------|  
|6.30672792729321E-08|6.30672792729321E-08|9.5824454056846E-48|  
  
 これらの結果の違いは、正規化の影響を示します。 生の値**CaseLikelihood**提案のケースの確率は約 20%; ただし、結果を正規化すると明らかになります、ケースの発生確率が非常に低いことです。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
