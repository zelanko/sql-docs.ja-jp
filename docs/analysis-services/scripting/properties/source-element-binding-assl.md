---
title: Source 要素 (バインド) (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Source Element (Binding)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 1032558c-7546-4ca7-888d-8139df23cb62
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ad14293322c4d41e7161c9114e707af19f32e3d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="source-element-binding-assl"></a>Source 要素 (バインド) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素がバインドされているデータのソースを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationInstance> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Source>...</Source>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|[AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/aggregationinstancemeasure-data-type-assl.md)|[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)|  
|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|派生した任意のデータ型[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)の親に応じて、 **DataItem**です。 詳細については、「解説」を参照してください。|  
|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、 [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|[MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|  
|[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|派生した任意のデータ型[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)の親によって使用される処理と通知のオプションによって、 **ProactiveCaching**要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)、 [AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/aggregationinstancemeasure-data-type-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、 [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)です。|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **ソース**要素では、派生した**バインド**で許可されるデータ型、 **DataItem**要素の親によって異なります、 **DataItem**要素。  
  
|DataItem の親|許可されるデータ型|  
|---------------------|------------------------|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [TimeAttributeBinding](../../../analysis-services/scripting/data-type/timeattributebinding-data-type-assl.md) (に対してのみ[KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md))。|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)です。|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[データ型のバインド&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)です。  
  
 ASSL でのデータ バインドの詳細については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
