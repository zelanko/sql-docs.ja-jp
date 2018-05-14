---
title: 属性の要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5c798d389608b19a888e0161bddda64a35e736bf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-element-assl"></a>Attribute 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  属性の説明を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attributes>  
   <Attribute xsi:type="AggregationAttribute">...</Attribute> <!-- ancestor: AggregationDimension -->  
   <!-- or -->  
   <Attribute xsi:type="AggregationDesignAttribute">...</Attribute> <!-- ancestor: AggregationDesignDimension -->  
   <!-- or -->  
   <Attribute xsi:type="AggregationInstanceAttribute">...</Attribute> <!-- ancestor: AggregationInstanceCubeDimension -->  
   <!-- or -->  
   <Attribute xsi:type="CubeAttribute">...</Attribute> <!--ancestor:  CubeDimension -->  
   <!-- or -->  
   <Attribute xsi:type="DimensionAttribute">...</Attribute> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <Attribute xsi:type="MeasureGroupAttribute">...</Attribute> <!-- ancestor: RegularMeasureGroupDimension -->  
   <!-- or -->  
   <Attribute xsi:type="PerspectiveAttribute">...</Attribute> <!-- ancestor: PerspectiveDimension -->  
   <!-- or -->  
   <Attribute>  
      <AttributeID>...</AttributeID>  
   </Attribute> <!-- ancestor: RelationshipEnd -->  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)|[AggregationDesignAttribute](../../../analysis-services/scripting/data-type/aggregationdesignattribute-data-type-assl.md)|  
|[AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md)|[AggregationAttribute](../../../analysis-services/scripting/data-type/aggregationattribute-data-type-assl.md)|  
|[AggregationInstanceCubeDimension](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)|[AggregationInstanceAttribute](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)|  
|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)|  
|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|[RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|  
|[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|[PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|[RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|\<属性 ><br />      \<[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)>.\</AttributeID >\<属性/>|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデル内の対応する要素が<xref:Microsoft.AnalysisServices.AggregationDesignAttribute>、 <xref:Microsoft.AnalysisServices.AggregationAttribute>、 <xref:Microsoft.AnalysisServices.CubeAttribute>、 <xref:Microsoft.AnalysisServices.DimensionAttribute>、 <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>、および<xref:Microsoft.AnalysisServices.PerspectiveAttribute>です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
