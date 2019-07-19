---
title: PredictHistogram (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 61a90dc7fa034fc8983246aa4eb7119832a2d47d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008010"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された列の予測のためのヒストグラムを表すテーブルを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列参照またはクラスター列参照。 除くすべての種類のアルゴリズムで使用できる、[!INCLUDE[msCoName](../includes/msconame-md.md)]アソシエーション アルゴリズムです。  
  
## <a name="return-type"></a>戻り値の型  
 テーブルです。  
  
## <a name="remarks"></a>コメント  
 ヒストグラムには、統計の列が生成されます。 返されたヒストグラムの列構造で使用される列参照の種類によって異なります、 **PredictHistogram**関数。  
  
## <a name="scalar-columns"></a>スカラー列  
 \<スカラー列参照 >、ヒストグラムを**PredictHistogram**関数の戻り値は、次の列で構成されます。  
  
-   予測される値。  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] データ マイニング アルゴリズムをサポートしていない **$ProbabilityVariance**します。 この列は、0 を常に含まれています。[!INCLUDE[msCoName](../includes/msconame-md.md)]アルゴリズム。  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] データ マイニング アルゴリズムをサポートしていない **$ProbabilityStdev**します。 この列は、0 を常に含まれています。[!INCLUDE[msCoName](../includes/msconame-md.md)]アルゴリズム。  
  
-   **$AdjustedProbability**  
  
     **$AdjustedProbability**列は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]拡張機能を[!INCLUDE[msCoName](../includes/msconame-md.md)]OLE DB for Data Mining 仕様です。  
  
## <a name="cluster-columns"></a>クラスター列  
 ヒストグラムを**PredictHistogram**関数を返します、\<クラスター列参照 >、次の列で構成されています。  
  
-   **$Cluster** (クラスター名を表します)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>使用例  
 次の例では、単一クエリで、Bike Buyer 列の予測された状態を返します。 クエリを使用して取得される調整済みの確率に基づいて、Bike Buyer 属性の上位 2 つの最も可能性の高い状態も返されます、 **PredictHistogram**関数。  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>関連項目  
 [クラスター &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
