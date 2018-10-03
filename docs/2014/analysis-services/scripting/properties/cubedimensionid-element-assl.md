---
title: CubeDimensionID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeDimensionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimensionID
helpviewer_keywords:
- CubeDimensionID element
ms.assetid: d1341fb2-9afe-40f1-a704-ce548bce48fc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e50506439d5820bee62015805a19323a20134e55
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076272"
---
# <a name="cubedimensionid-element-assl"></a>CubeDimensionID 要素 (ASSL)
  識別、 [CubeDimension](../data-type/dimension-data-type-assl.md)親要素に関連付けられた要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationDesignDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <CubeDimensionID>...</CubeDimensionID>  
   ...  
</AggregationDesignDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationDesignDimension](../data-type/aggregationdesigndimension-data-type-assl.md)、 [AggregationDimension](../data-type/aggregationdimension-data-type-assl.md)、 [AggregationInstanceCubeDimension](../data-type/aggregationinstancecubedimension-data-type-assl.md)、 [CubeAttributeBinding](../data-type/binding-data-type-assl.md)、 [CubeDimensionBinding](../data-type/dimensionbinding-data-type-assl.md)、 [CubeDimensionPermission](../data-type/permission-data-type-assl.md)、 [MeasureGroupDimension](../data-type/measuregroupdimension-data-type-assl.md)、 [MeasureGroupDimensionBinding](../data-type/measuregroupdimensionbinding-data-type-assl.md)、 [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで `CubeDimensionID` の親に対応する要素は、<xref:Microsoft.AnalysisServices.AggregationDesignDimension>、<xref:Microsoft.AnalysisServices.AggregationDimension>、<xref:Microsoft.AnalysisServices.CubeAttributeBinding>、<xref:Microsoft.AnalysisServices.CubeDimensionBinding>、<xref:Microsoft.AnalysisServices.CubeDimensionPermission>、<xref:Microsoft.AnalysisServices.MeasureGroupDimension>、<xref:Microsoft.AnalysisServices.MeasureGroupDimensionBinding>、および <xref:Microsoft.AnalysisServices.PerspectiveDimension> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
