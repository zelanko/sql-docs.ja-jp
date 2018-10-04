---
title: Binding データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Binding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- BINDING
helpviewer_keywords:
- Binding data type
ms.assetid: 0a777219-b885-4961-ac66-b76faeb520db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e46d48f94035a59c54a3e9bb9c8ccb087226660
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135902"
---
# <a name="binding-data-type-assl"></a>Binding データ型 (ASSL)
  あるオブジェクトのデータまたはメタデータがバインド対象オブジェクトのデータまたはメタデータに依存している 2 つのオブジェクト間の依存関係を表す抽象プリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[AttributeBinding](binding-data-type-assl.md)、 [ColumnBinding](columnbinding-data-type-assl.md)、 [CubeAttributeBinding](cubeattributebinding-data-type-assl.md)、 [CubeDimensionBinding](dimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](dimensionbinding-data-type-assl.md)、 [InheritedBinding](inheritedbinding-data-type-assl.md)、 [MeasureBinding](measurebinding-data-type-assl.md)、 [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)、 [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)、 [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)、 [RowBinding](rowbinding-data-type-assl.md)、 [TabularBinding](tabularbinding-data-type-assl.md)、 [TimeAttributeBinding](timeattributebinding-data-type-assl.md)、 [TimeBinding](timebinding-data-type-assl.md)、 [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Binding>します。  
  
 データ バインディングの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
## <a name="elements-of-type-binding"></a>Binding 型の要素  
 次の表は、`Binding` 型の要素を示しています。  
  
|親要素|`Binding` 型の要素|コメント|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../properties/source-element-binding-assl.md)の[CaptionColumn](../objects/column-element-assl.md) (型の[DataItem](dataitem-data-type-assl.md))|型、`Binding`あります[AttributeBinding](binding-data-type-assl.md)または[ColumnBinding](columnbinding-data-type-assl.md)|  
|[Cube](../objects/cube-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (不一致)](../objects/group-element-assl.md)|型、`Binding`あります[MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[DataItem](dataitem-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|`Binding` は、任意の型にすることができます。|  
|[Dimension](../objects/dimension-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[CubeDimensionBinding](dimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](dimensionbinding-data-type-assl.md)、または[TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](dimensionattribute-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[AttributeBinding](binding-data-type-assl.md)または[UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](action-data-type-assl.md)|[列](../objects/column-element-assl.md)|型、`Binding`あります[CubeAttributeBinding](cubeattributebinding-data-type-assl.md)または[MeasureBinding](measurebinding-data-type-assl.md)|  
|[メジャー](../objects/measure-element-assl.md)|[ソース](../properties/source-element-binding-assl.md)(型の[DataItem](dataitem-data-type-assl.md))|型、`Binding`あります[ColumnBinding](columnbinding-data-type-assl.md)、 [CubeDimensionBinding](dimensionbinding-data-type-assl.md)、 [MeasureBinding](measurebinding-data-type-assl.md)、または[RowBinding](rowbinding-data-type-assl.md)|  
|[メジャー グループ](../objects/measuregroup-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[ソース](../properties/source-element-binding-assl.md)の[KeyColumn](../objects/keycolumn-element-assl.md) (型の[DataItem](dataitem-data-type-assl.md))|型、`Binding`あります[AttributeBinding](binding-data-type-assl.md)または[ColumnBinding](columnbinding-data-type-assl.md)、または[InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../objects/dimension-element-assl.md)|型、`Binding`あります[MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](measuregroupbinding-data-type-out-of-line-assl.md)|[メジャー](../objects/measure-element-assl.md)|型、`Binding`あります[MeasureBinding](measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](../objects/partition-element-assl.md)|型、`Binding`あります[PartitionBinding](partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](measuregroupbinding-data-type-out-of-line-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[TableBinding](tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](dimension-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[CubeDimensionBinding](dimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)、または[DimensionBinding](dimensionbinding-data-type-assl.md)|  
|[パーティション](../objects/partition-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[TabularBinding](tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|型、`Binding`あります[AttributeBinding](binding-data-type-assl.md)、 [CubeAttributeBinding データ型&#40;ASSL&#41;](cubeattributebinding-data-type-assl.md)、または[MeasureBinding データ型&#40;ASSL&#41;](measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/sourcemeasuregroup-element-assl.md)|型、`Binding`あります[MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
