---
title: AlgorithmParameters 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7444fd5cd5792a2e5b8ee6bfbd74eddf343d0900
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="algorithmparameters-element-assl"></a>AlgorithmParameters 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  使用されるアルゴリズムのパラメーターのコレクションが含まれています、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし (コレクション型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|子要素|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **AlgorithmParameters**コレクションには、拡張可能なマイニング モデル アルゴリズムの名前と値のペアとして表されるパラメーターのセットが含まれています。 適用可能なパラメーターのセットはアルゴリズムによって異なります。 特定のアルゴリズムのアルゴリズム パラメーターの詳細については、そのアルゴリズムに関するドキュメントを参照してください。  
  
 検証や表示情報を含む使用可能なアルゴリズム パラメーターは、DMSCHEMA_MINING_SERVICE_PARAMETERS スキーマ行セットから取得できます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>します。  
  
## <a name="see-also"></a>参照  
 [Algorithm 要素&#40;ASSL&#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
