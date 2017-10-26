---
title: "Algorithm 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Algorithm Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fe1a9caffdff1de0dc62c4ddd696e1ec8b829bd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="algorithm-element-assl"></a>Algorithm 要素 (ASSL)
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
 [AlgorithmParameter 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)   
 [AlgorithmParameters 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

