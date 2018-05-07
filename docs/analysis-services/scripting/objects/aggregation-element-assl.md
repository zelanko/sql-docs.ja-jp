---
title: Aggregation 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a8da8515142988fcc625e2800178e6b3aa4d2482
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="aggregation-element-assl"></a>Aggregation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  1 つの集計を定義、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Aggregations>  
      <Aggregation>  
      <ID>...</ID>  
      <Name>...</Name>  
      <Dimensions>...</Dimensions>  
            <Annotations>...</Annotations>  
      <Description>...</Description>  
   </Aggregation>  
</Aggregations>  
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
|親要素|[集計](../../../analysis-services/scripting/collections/aggregations-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[名](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Aggregation>します。  
  
## <a name="see-also"></a>参照  
 [要素をパーティション分割&#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [AggregationDesign 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [MeasureGroup 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
