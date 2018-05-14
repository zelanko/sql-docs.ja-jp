---
title: Algorithm 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d60c8416ef530014ee996f57b321f46ffbb2e436
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="algorithm-element-assl"></a>Algorithm 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  によって使用されるアルゴリズムを定義、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、**アルゴリズム**要素は、アルゴリズムを識別する文字列。 たとえば、文字列がなります*Microsoft_Naive_Bayes*、 *Microsoft_Decision_Trees*、または*Microsoft_Clustering です。* によって提供されるアルゴリズムを識別する、文字列[!INCLUDE[msCoName](../../../includes/msconame-md.md)]と、ユーザーが指定したカスタム アルゴリズムです。 使用できる値を**アルゴリズム**の SERVICE_NAME 列から要素を取得できる、 [DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)スキーマ行セット。  
  
 親に対応する要素**アルゴリズム**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningModel>します。 AMO オブジェクト モデルの中で、関連性の高い要素は <xref:Microsoft.AnalysisServices.MiningModelAlgorithms> です。  
  
## <a name="see-also"></a>参照  
 [AlgorithmParameter 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)   
 [AlgorithmParameters 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
