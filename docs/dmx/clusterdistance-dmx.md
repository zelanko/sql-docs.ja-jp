---
title: ClusterDistance (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1884bf191d842ba136165cf28aa14c23dd82b2e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071073"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  **ClusterDistance**関数では、入力したケースの距離を返します、指定されたクラスターでは、クラスターが指定されていない場合、最も可能性の高いクラスターから入力したケースの距離。  
  
## <a name="syntax"></a>構文  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>適用対象  
 この関数は、基本となるデータ マイニング モデルがクラスターをサポートする場合にのみ使用できます。 クラスタ リング モデルの種類を問わず、関数を使用できます (EM、K-means など)、結果はアルゴリズムによって異なりますが。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>コメント  
 **ClusterDistance**関数が、入力したケースとその入力したケースの確率の高いクラスターとの間の距離を返します。  
  
 K-means クラスタ リングが発生した場合に 1 つのみのクラスター メンバーシップの重みが 1.0 では、どのケースが属することができますので、クラスターの距離は常に 0 です。 ただし、K-Means では、各クラスターに重心があると想定されています。 クエリを実行するか、マイニング モデル内容を入れ子になった NODE_DISTRIBUTION テーブルを参照して、重心の値を取得できます。 詳細については、「 [クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)」を参照してください。  
  
 既定の EM クラスタ リング手法の場合、クラスター内のすべてのポイントと見なされます同程度です。そのため、設計ではありません、クラスターの重心です。 値**ClusterDistance**特定のケースと特定のクラスター間*N*は次のように計算されます。  
  
 ClusterDistance(N) =1-(membershipWeight(N))  
  
 または:  
  
 ClusterDistance(N) = 1 ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>関連する予測関数  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] クラスタ リング モデルを照会するためには、次の追加機能を提供します。  
  
-   使用して、[クラスター &#40;DMX&#41; ](../dmx/cluster-dmx.md)関数可能性が最も高いクラスターを返します。  
  
-   使用して、 [ClusterProbability &#40;DMX&#41; ](../dmx/clusterprobability-dmx.md)ケースが特定のクラスターに所属する確率を取得します。 この値は、クラスターの距離の逆関数として機能します。  
  
-   使用して、 [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md)関数をそれぞれのモデルのクラスターで、入力ケース既存の確率値のヒストグラムを返します。  
  
-   使用して、 [PredictCaseLikelihood &#40;DMX&#41; ](../dmx/predictcaselikelihood-dmx.md)関数を入力したケース可能性を示す 1、0 からメジャーが考慮すると、モデルが存在するが返されませんが、アルゴリズムによって学習します。  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>例 1:最も可能性の高いクラスターにクラスターの距離を取得します。  
 次の例は、ほとんどのケースが属するクラスターに、指定したケースからの距離を返します。  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 例の結果を次に示します。  
  
|式|  
|----------------|  
|0.0477390930705145|  
  
 これがどのクラスターであるかを確認するには、上記の例で `Cluster` の代わりに `ClusterDistance` を使用します。  
  
 例の結果を次に示します。  
  
|$CLUSTER|  
|--------------|  
|クラスター 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>例 2:指定したクラスターまでの距離を取得します。  
 次の構文では、マイニング モデル コンテンツ スキーマ行セットを使用して、マイニング モデル内のクラスターのノードの ID とノードのキャプションの一覧を返します。 クラスター id の引数としてノードのキャプションを使用することができますし、 **ClusterDistance**関数。  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 例の結果を次に示します。  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|クラスター 1|  
|002|Cluster 2|  
  
 次の構文例では、Cluster 2 というラベルの付いたクラスターから、指定したケースの距離を返します。  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 例の結果を次に示します。  
  
|Cluster 2 Distance|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>関連項目  
 [クラスター &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
