---
title: "ClusterProbability (DMX) |Microsoft ドキュメント"
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
- ClusterProbability
dev_langs:
- DMX
helpviewer_keywords:
- ClusterProbability function
ms.assetid: a6447b3c-94ce-4122-a3eb-6f3827598d8f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b7f68000caa8fd90dd2a2396ff17f0fd701b96d2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  入力ケースが指定されたクラスターに所属する確率を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>適用対象  
 この関数は、基本となるデータ マイニング モデルがクラスターをサポートする場合にのみ使用できます。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>解説  
 次の構文は、マイニング モデル コンテンツ スキーマ行セットを使用して、マイニング モデルに存在するノードのキャプションを返します。  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 詳細については、この構文を使用して、次を参照してください。 [SELECT FROM &#60; モデル &#62;。コンテンツ &#40;DMX"&"#41;](../dmx/select-from-model-content-dmx.md). マイニング モデル コンテンツ スキーマ行セットの詳細については、次を参照してください。 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)です。  
  
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
 [クラスター &#40;DMX"&"#41;](../dmx/cluster-dmx.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

