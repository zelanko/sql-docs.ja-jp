---
title: Binding データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14b216fbc9dffd4cbaade3fd9106e824eebb55c4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="binding-data-type-assl"></a>Binding データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  あるオブジェクトのデータまたはメタデータがバインド対象オブジェクトのデータまたはメタデータに依存している 2 つのオブジェクト間の依存関係を表す抽象プリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)、 [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、 [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)、 [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)、 [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)、 [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)、 [ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)、 [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)、 [TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)、 [TimeAttributeBinding](../../../analysis-services/scripting/data-type/timeattributebinding-data-type-assl.md)、 [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)、 [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Binding>します。  
  
 データ バインディングの詳細については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Binding 型の要素  
 次の表に、型の要素**バインド**です。  
  
|親要素|型の要素**バインド**|コメント|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)の[CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md) (型の[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|型、**バインド**する必要があります[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)または[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (不一致)](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|型、**バインド**する必要があります[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|**バインド**任意の型の場合があります|  
|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)、 [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、または[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)または[UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|[列](../../../analysis-services/scripting/objects/column-element-assl.md)|型、**バインド**する必要があります[CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)または[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)(型の[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|型、**バインド**する必要があります[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)、 [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)、または[RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|  
|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)の[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) (型の[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|型、**バインド**する必要があります[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)または[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、または[InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|型、**バインド**する必要があります[MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|型、**バインド**する必要があります[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|型、**バインド**する必要があります[PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (不一致)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)、 [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)、または[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|  
|[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|型、**バインド**する必要があります[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [CubeAttributeBinding データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)、または[MeasureBinding データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[SourceMeasureGroup](../../../analysis-services/scripting/objects/sourcemeasuregroup-element-assl.md)|型、**バインド**する必要があります[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
