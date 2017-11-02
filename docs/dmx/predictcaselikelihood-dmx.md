---
title: "PredictCaseLikelihood (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PredictCaseLikelihood
dev_langs:
- DMX
helpviewer_keywords:
- PredictCaseLikelihood function
ms.assetid: b00180e5-b2eb-49e2-891d-e39fb378f50a
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99a6d2927d0164f4c23dbb2c34d1d9ab6bab511f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  この関数は、入力ケースが既存のモデル内に収まる確率を返します。 クラスター モデルでのみ使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictCaseLikelihood([NORMALIZED|NONNORMALIZED])  
```  
  
## <a name="arguments"></a>引数  
 NORMALIZED  
 戻り値は、モデル内のケースの確率をモデルのないケースの確率で除算した結果を格納します。  
  
 NONNORMALIZED  
 戻り値は、ケースの未加工の確率、つまりケース属性の確率の積を格納します。  
  
## <a name="applies-to"></a>適用対象  
 使用して作成されたモデルの[!INCLUDE[msCoName](../includes/msconame-md.md)]クラスタ リングと[!INCLUDE[msCoName](../includes/msconame-md.md)]シーケンス クラスター アルゴリズムです。  
  
## <a name="return-type"></a>戻り値の型  
 0 ～ 1 の範囲の倍精度浮動小数点値です。 値が 1 に近いほど、このモデルでケースが発生する確率が高くなります。 値が 0 に近いほど、このモデルでケースが発生する確率が低くなります。  
  
## <a name="remarks"></a>解説  
 既定では、結果、 **PredictCaseLikelihood**関数は正規化されます。 通常、正規化された値は、ケース内の属性の数が増え、任意の 2 つのケースの未加工の確率の差が小さくなるほど、有用性が増します。  
  
 x と y を指定した、次の式を使用して、正規化された値を計算します。  
  
-   x = クラスタリング モデルに基づいたケースの確率値  
  
-   y = トレーニング ケースの数に基づいたケースの対数尤度として計算された、周辺確率の値  
  
-   Z = Exp( log(x) – Log(Y))  
  
 正規化された = (z/(1 + z))  
  
## <a name="examples"></a>使用例  
 次の例は、指定したケースに基づいて、クラスタ リング モデル内で発生する可能性を返して、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW データベース。  
  
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
  
 これらの結果の違いは、正規化の影響を示します。 生の値**CaseLikelihood**提案をケースの確率約 20% です。 ただし、結果を正規化するときに明らかになり、ケースの発生確率が非常に低いことです。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

