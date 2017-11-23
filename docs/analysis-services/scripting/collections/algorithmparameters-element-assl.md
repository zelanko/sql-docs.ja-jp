---
title: "AlgorithmParameters 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AlgorithmParameters Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AlgorithmParameters
helpviewer_keywords: AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1470ce42b2dada9d96c61e34716800b71fb63f26
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="algorithmparameters-element-assl"></a>AlgorithmParameters 要素 (ASSL)
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
 [Algorithm 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
