---
title: ClusterProbability (DMX) |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4d8ce16bb07af07bd2bfd651cf5fc1ae15b7e08
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841685"
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  入力ケースが指定されたクラスターに所属する確率を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>適用対象  
 この関数は、基本となるデータ マイニング モデルがクラスターをサポートする場合にのみ使用できます。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>コメント  
 次の構文は、マイニング モデル コンテンツ スキーマ行セットを使用して、マイニング モデルに存在するノードのキャプションを返します。  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 詳細については、この構文を使用して、次を参照してください。 [SELECT FROM&#60;モデル&#62;です。コンテンツ&#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)です。 マイニング モデル コンテンツ スキーマ行セットの詳細については、次を参照してください。 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)です。  
  
 場合、\<ノードのキャプション > が指定されていない、関数は、入力ケースが最も高いクラスターに所属する確率を返します。 使用して、**クラスター**関数最も可能性の高いクラスターを返します。  
  
## <a name="examples"></a>使用例  
 次の例は、指定したケースが Cluster 2 というラベルが付けられたクラスターに存在する確率を返します。  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [クラスター &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
