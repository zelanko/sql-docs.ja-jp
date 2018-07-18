---
title: Source 要素 (Binding) (ASSL) |Microsoft Docs
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
- Source Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 1032558c-7546-4ca7-888d-8139df23cb62
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 54257415a19530a82b27e759dea03a4e41dcb0cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257244"
---
# <a name="source-element-binding-assl"></a>Source 要素 (バインド) (ASSL)
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
|データ型と長さ|次の参照データ型表|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
 **データ型と長さ**  
  
|||  
|-|-|  
|先祖または親|データ型|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[AggregationInstanceMeasure](../data-type/columnbinding-data-type-assl.md)|  
|[Cube](../data-type/datasourceviewbinding-data-type-assl.md)|  
|[DataItem](../data-type/dataitem-data-type-assl.md)|任意のデータ型から派生した[バインド](../data-type/binding-data-type-assl.md)の親に応じて、`DataItem`します。 詳細については、「解説」を参照してください。|  
|[ディメンション](../data-type/dimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../data-type/datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md)、 [TimeBinding](../data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../data-type/attributebinding-data-type-assl.md)、 [UserDefinedGroupBinding](../data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[メジャー グループ](../data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupDimension](../data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[CubeDimensionBinding](../data-type/cubedimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../data-type/datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md)|  
|[パーティション](../data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|任意のデータ型から派生した[ProactiveCachingBinding](../data-type/proactivecachingbinding-data-type-assl.md)の親で使用される処理と通知オプションに応じて、`ProactiveCaching`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstance](../objects/aggregationinstance-element-assl.md)、 [AggregationInstanceMeasure](../data-type/aggregationinstancemeasure-data-type-assl.md)、[キューブ](../objects/cube-element-assl.md)、 [DataItem](../data-type/dataitem-data-type-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、 [MeasureGroupDimension](../data-type/dimension-data-type-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)、[パーティション](../objects/partition-element-assl.md)、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)します。|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Source` 要素では、`Binding` 要素で使用できる `DataItem` 派生データ型は、`DataItem` 要素の親によって異なります。  
  
|DataItem の親|許可されるデータ型|  
|---------------------|------------------------|  
|[DimensionAttribute](../data-type/attributebinding-data-type-assl.md)、 [ColumnBinding](../data-type/columnbinding-data-type-assl.md)、 [TimeAttributeBinding](../data-type/timeattributebinding-data-type-assl.md) (に対してのみ[KeyColumns](../collections/columns-element-assl.md))。|  
|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|[AttributeBinding](../data-type/attributebinding-data-type-assl.md)、 [ColumnBinding](../data-type/columnbinding-data-type-assl.md)、 [InheritedBinding](../data-type/inheritedbinding-data-type-assl.md)します。|  
|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[ColumnBinding](../data-type/columnbinding-data-type-assl.md)|  
  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](../data-type/binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
