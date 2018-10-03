---
title: MeasureGroup 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroup
helpviewer_keywords:
- MeasureGroup element
ms.assetid: 7aa099db-5dc7-4cac-b437-f73fc0921b24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 84186a736f7d3e17587a3a5457b1c7850c02f12b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089712"
---
# <a name="measuregroup-element-assl"></a>MeasureGroup 要素 (ASSL)
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
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|なし|  
|[CubeBinding](../data-type/binding-data-type-assl.md)|  
|[パースペクティブ](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../collections/groups-element-assl.md)|  
|子要素||  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[キューブ](../collections/aggregationdesigns-element-assl.md)、 [AggregationPrefix](../properties/aggregationprefix-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [DataAggregation](aggregation-element-assl.md)、 [説明](../properties/description-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、 [ErrorConfiguration](errorconfiguration-element-assl.md)、 [EstimatedRows](../properties/estimatedrows-element-assl.md)、 [EstimatedSize](../properties/estimatedsize-element-assl.md)、[ID](../properties/id-element-assl.md)、 [IgnoreUnrelatedDimensions](../properties/ignoreunrelateddimensions-element-assl.md)、 [LastProcessed](../properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [MeasureQualification](../properties/measurequalificaton-element-assl.md)、[メジャー](../collections/measures-element-assl.md)、[名前](../properties/name-element-assl.md)、[パーティション](../collections/partitions-element-assl.md)、 [ProactiveCaching](proactivecaching-element-assl.md)、 [ProcessingMode](../properties/processingmode-element-assl.md)、 [ProcessingPriority](../properties/processingpriority-element-assl.md)、[ソース](../properties/source-element-measure-assl.md)、[状態](../properties/state-element-assl.md)、 [StorageLocation](../properties/storagelocation-element-assl.md)、 [StorageMode](../properties/storagemode-element-assl.md)、[翻訳](../collections/translations-element-assl.md)、[型](../properties/type-element-measuregroup-assl.md)|  
|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)|なし|  
|[パースペクティブ](perspective-element-assl.md)|なし|  
  
## <a name="remarks"></a>コメント  
 メジャー グループのすべてのメジャーは、1 つのテーブルをソースとする必要があります。 メジャー グループでは、パーティションごとにオーバーライドできる既定のバインドを定義できます。  
  
 `MeasureGroup` 要素は、標準キューブおよび仮想キューブのメジャー グループに共通する詳細を定義します。 個々のサブタイプは、各種類に固有の詳細を定義します。  
  
 `State` の `MeasureGroup` プロパティは、次の値をとります。  
  
-   すべてのパーティションが処理される場合、*FullyProcessed*   
  
-   少なくとも 1 つのパーティションが処理される場合、*PartiallyProcessed*   
  
-   パーティションが処理されない場合、*Unprocessed*   
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.MeasureGroup> と <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup> です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
