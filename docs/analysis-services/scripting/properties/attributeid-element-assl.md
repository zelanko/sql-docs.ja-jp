---
title: "AttributeID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AttributeID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeID
helpviewer_keywords:
- AttributeID element
ms.assetid: 13d2e92b-e4bf-4f2d-b34c-a6f483da3a9e
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a1973319f3fdf66a7602ac201bd1748936cd96e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="attributeid-element-assl"></a>AttributeID 要素 (ASSL)
  親要素に関連付けられている属性の ID を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationAttribute> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <AttributeID>...</AttributeID>  
   ...  
</AggregationAttribute>  
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
|親要素|[AggregationAttribute](../../../analysis-services/scripting/data-type/aggregationattribute-data-type-assl.md)、 [AggregationDesignAttribute](../../../analysis-services/scripting/data-type/aggregationdesignattribute-data-type-assl.md)、 [AggregationInstanceAttribute](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)、 [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)、 [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)、 [CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)、 [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)、 [DimensionAttributeBinding](../../../analysis-services/scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md)、 [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)、 [MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)、 [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)、 [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**AttributeID**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AggregationAttribute>、 <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>、 <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>、 <xref:Microsoft.AnalysisServices.AttributeBinding>、 <xref:Microsoft.AnalysisServices.AttributePermission>、 <xref:Microsoft.AnalysisServices.AttributeRelationship>、 <xref:Microsoft.AnalysisServices.CubeAttribute>、 <xref:Microsoft.AnalysisServices.CubeAttributeBinding>、 <xref:Microsoft.AnalysisServices.PerspectiveAttribute>、および<xref:Microsoft.AnalysisServices.UserDefinedGroupBinding>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

