---
title: MeasureGroup 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 30f076955259c343c0cb77de3b4829d36d45142c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="measuregroup-element-assl"></a>MeasureGroup 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  同じレベルの粒度でメジャーのセットを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroups>  
   <MeasureGroup> <!-- ancestor: Cube -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</<Create  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Type>...</Type>  
      <State>...</State>  
      <MeasureQualification>...</MeasureQualification>  
      <Measures>...</Measures>  
      <DataAggregation>...</DataAggregation>  
      <Source>...</Source>  
            <StorageMode>...</StorageMode>  
      <StorageLocation>...</StorageLocation>  
      <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
            <ProactiveCaching>...</ProactiveCaching>  
      <EstimatedRows>...</EstimatedRows>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <EstimatedSize>...</EstimatedSize>  
      <ProcessingMode>...</ProcessingMode>  
      <Dimensions>...</Dimensions>  
      <Partitions>...</Partitions>  
      <AggregationPrefix>...</AggregationPrefix>  
      <ProcessingPriority>...</ProcessingPriority>  
            <AggregationDesigns>...</AggregationDesigns>  
      <Annotations>...</Annotations>  
   </MeasureGroup>  
   <!-- or  -->  
   <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- ancestor: CubeBinding -->  
   <!-- or  -->  
   <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- ancestor: Perspective -->  
</MeasureGroups>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|なし|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[AggregationDesigns](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md)、 [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [DataAggregation](../../../analysis-services/scripting/properties/dataaggregation-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)、 [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md)、 [EstimatedSize](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [IgnoreUnrelatedDimensions](../../../analysis-services/scripting/properties/ignoreunrelateddimensions-element-assl.md)、 [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [MeasureQualification](../../../analysis-services/scripting/properties/measurequalificaton-element-assl.md)、[メジャー](../../../analysis-services/scripting/collections/measures-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[パーティション](../../../analysis-services/scripting/collections/partitions-element-assl.md)、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)、 [ProcessingMode](../../../analysis-services/scripting/properties/processingmode-element-assl.md)、 [ProcessingPriority](../../../analysis-services/scripting/properties/processingpriority-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-measure-assl.md)、[状態](../../../analysis-services/scripting/properties/state-element-assl.md)、 [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)、 [StorageMode](../../../analysis-services/scripting/properties/storagemode-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[型](../../../analysis-services/scripting/properties/type-element-measuregroup-assl.md)|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|なし|  
|[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)|なし|  
  
## <a name="remarks"></a>解説  
 メジャー グループのすべてのメジャーは、1 つのテーブルをソースとする必要があります。 メジャー グループでは、パーティションごとにオーバーライドできる既定のバインドを定義できます。  
  
 **MeasureGroup** 要素は、標準キューブおよび仮想キューブのメジャー グループに共通する詳細を定義します。 個々のサブタイプは、各種類に固有の詳細を定義します。  
  
 **State** の **MeasureGroup** プロパティは、次の値をとります。  
  
-   すべてのパーティションが処理される場合、*FullyProcessed*   
  
-   少なくとも 1 つのパーティションが処理される場合、*PartiallyProcessed*   
  
-   パーティションが処理されない場合、*Unprocessed*   
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.MeasureGroup> と <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup> です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
