---
title: ClusterDistance (DMX) |Microsoft ドキュメント
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
- ClusterDistance
dev_langs:
- DMX
helpviewer_keywords:
- ClusterDistance function
ms.assetid: a13152b3-4cd1-4c79-8a3e-207624198330
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 03e85862a5fc8a1a9daae56282294d9addad53f0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  **ClusterDistance**関数では、入力したケースの距離を返します、指定されたクラスターまたはクラスターが指定されていない場合、最も可能性の高いクラスターから入力したケースの距離。  
  
## <a name="syntax"></a>構文  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>適用対象  
 この関数は、基本となるデータ マイニング モデルがクラスターをサポートする場合にのみ使用できます。 この関数はどの種類のクラスター モデル (EM、K-Means など) でも使用できますが、アルゴリズムによって結果が異なります。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>解説  
 **ClusterDistance**関数が、入力したケースと入力したケースの確率の高いクラスター間の距離を返します。  
  
 K-Means クラスタリングの場合、どのケースも所属できるのは、メンバーシップの重みが 1.0 のクラスター 1 つだけなので、クラスターの距離は常に 0 になります。 ただし、K-Means では、各クラスターに重心があると想定されています。 マイニング モデル コンテンツ内の入れ子になったテーブル NODE_DISTRIBUTION をクエリしたり参照したりして、重心の値を取得できます。 詳細については、「[クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)」を参照してください。  
  
 既定の EM クラスタリング手法の場合、クラスター内のすべてのポイントは同程度であると見なされるため、仕様上、クラスターには重心がありません。 値**ClusterDistance** 、特定のケースと特定のクラスター間で*N*次のように計算されます。  
  
 ClusterDistance(N) =1–(membershipWeight(N))  
  
 または。  
  
 ClusterDistance(N) = 1 – ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>関連する予測関数  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] クラスタ リング モデルを照会するためには、次の追加機能を提供します。  
  
-   使用して、[クラスター &#40;DMX&#41; ](../dmx/cluster-dmx.md)関数最も可能性の高いクラスターを返します。  
  
-   使用して、 [ClusterProbability &#40;DMX&#41; ](../dmx/clusterprobability-dmx.md)ケースが特定のクラスターに所属する確率を取得します。 この値は、クラスターとの距離とは逆の関係になります。  
  
-   使用して、 [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md)関数、入力ケース既存のモデルのクラスターの各確率値のヒストグラムを返します。  
  
-   使用して、 [PredictCaseLikelihood &#40;DMX&#41; ](../dmx/predictcaselikelihood-dmx.md)を考慮すると、モデルが存在するは、入力したケース可能性を示す 1、0 からメジャーを返す関数は、アルゴリズムによって学習します。  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>例 1: 最も可能性の高いクラスターまでのクラスターの距離の取得  
 次の例は、指定したケースから、そのケースが最も所属している可能性の高いクラスターまでの距離を返します。  
  
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
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>例 2: 指定したクラスターまでの距離の取得  
 次の構文では、マイニング モデル コンテンツ スキーマ行セットを使用して、マイニング モデル内のクラスターのノードの ID とノードのキャプションの一覧を返します。 クラスター id の引数としてのノードのキャプションを行うこともできますし、 **ClusterDistance**関数。  
  
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
  
 次の構文例では、Cluster 2 というラベルが付いたクラスターから、指定されたケースまでの距離が返されます。  
  
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
  
## <a name="see-also"></a>参照  
 [クラスター &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [クラスタ リング モデル & #40; のマイニング モデル コンテンツAnalysis Services - データ マイニング & #41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
