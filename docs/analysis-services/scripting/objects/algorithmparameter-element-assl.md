---
title: "AlgorithmParameter 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AlgorithmParameter Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AlgorithmParameter
helpviewer_keywords:
- AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33ef60da325d605250b5a429bc3fac14e8da01d7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="algorithmparameter-element-assl"></a>AlgorithmParameter 要素 (ASSL)
  使用されるアルゴリズムのパラメーターを定義、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AlgorithmParameters](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|  
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[値](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **AlgorithmParameter**マイニング モデル アルゴリズムのパラメーターです。 **AlgorithmParameter**名前/値のペアとしてこのパラメーターを表します。 適用可能なパラメーターのセットを**AlgorithmParameter**できます表すはアルゴリズムによって異なります。 特定のアルゴリズムのアルゴリズム パラメーターの詳細については、そのアルゴリズムに関するドキュメントを参照してください。  
  
 検証や表示の情報を含む使用可能なアルゴリズム パラメーターから取得できる、 [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)スキーマ行セット。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AlgorithmParameter>します。  
  
## <a name="see-also"></a>参照  
 [MiningModel 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Algorithm 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

