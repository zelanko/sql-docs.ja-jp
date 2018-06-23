---
title: AggregationDesign 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationDesign Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesign
helpviewer_keywords:
- AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c8b02460500a79d1ff98dfac84a07782c388ef10
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074674"
---
# <a name="aggregationdesign-element-assl"></a>AggregationDesign 要素 (ASSL)
  データベース内の複数のパーティションで共有できる一連の集計定義を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationDesigns>  
   <AggregationDesign>  
      <ID>...</ID>  
      <Name>...</Name>  
            <Description>...</Description>  
      <EstimatedRows>...</EstimatedRows>  
      <Dimensions>...</Dimensions>  
            <Aggregations>...</Aggregation>  
      <EstimatedPerformanceGain>...</EstimatedPerformanceGain>  
      <Annotations>...</Annotations>  
   </AggregationDesign>  
</AggregationDesigns>  
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
|親要素|[AggregationDesigns](../collections/aggregationdesigns-element-assl.md)|  
|子要素|[集計](../collections/aggregations-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、[説明](../properties/description-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、 [EstimatedPerformanceGain](../properties/estimatedperformancegain-element-assl.md)、 [EstimatedRows](../properties/estimatedrows-element-assl.md)、 [ID](../properties/id-element-assl.md)、[名](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationDesign>します。  
  
## <a name="see-also"></a>参照  
 [要素をパーティション分割&#40;ASSL&#41;](partition-element-assl.md)   
 [Aggregation 要素&#40;ASSL&#41;](aggregation-element-assl.md)   
 [Aggregations 要素&#40;ASSL&#41;](../collections/aggregations-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  