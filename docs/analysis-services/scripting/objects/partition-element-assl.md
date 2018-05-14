---
title: 要素 (ASSL) をパーティション分割 |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cacc02776c1886caf4a8a46557ac01d2d33257c5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="partition-element-assl"></a>Partition 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  パーティションを定義、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)要素またはの行外でのパーティション バインド[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Partitions>  
      <Partition> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Source>...</Source>  
      <ProcessingPriority>...</ProcessingPriority>  
      <AggregationPrefix>...</AggregationPrefix>  
      <StorageMode>...</StorageMode>  
      <ProcessingMode>...</ProcessingMode>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <StorageLocation>...</StorageLocation>  
      <RemoteDatasourceID>...</RemoteDatasourceID>  
      <Slice>...</Slice>  
      <ProactiveCaching>...</ProactiveCaching>  
      <Type>...</Type>  
      <EstimatedSize>...</EstimatedSize>  
      <EstimatedRows>...</EstimatedRows>  
      <CurrentStorageMode>...</CurrentStorageMode>  
      <AggregationDesignID>...</AggregationDesignID>  
      <AggregationInstances>...</AggregationInstances>  
      <AggregationInstanceSource>...</AggregationInstanceSource>  
      <LastProcessed>...</LastProcessed>  
      <State>...</State>  
      <Annotations>.../Annotations>  
   </Partition>  
   <!-- or -->  
   <Partition xsi:type="PartitionBinding"> <!-- ancestor: MeasureGroupBinding -->  
   </Partition>  
</Partitions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|なし|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パーティション](../../../analysis-services/scripting/collections/partitions-element-assl.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[AggregationDesignID](../../../analysis-services/scripting/properties/aggregationdesignid-element-assl.md)、 [AggregationInstances](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)、 [AggregationInstanceSource](../../../analysis-services/scripting/properties/aggregationinstancesource-element-assl.md)、 [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [CurrentStorageMode](../../../analysis-services/scripting/properties/currentstoragemode-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)、 [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md)、 [EstimatedSize](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)、 [ProcessingMode](../../../analysis-services/scripting/properties/processingmode-element-assl.md)、 [ProcessingPriority](../../../analysis-services/scripting/properties/processingpriority-element-assl.md)、 [RemoteDatasourceID](../../../analysis-services/scripting/properties/remotedatasourceid-element-assl.md)、[スライス](../../../analysis-services/scripting/properties/slice-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)、[状態](../../../analysis-services/scripting/properties/state-element-assl.md)、 [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)、 [StorageMode](../../../analysis-services/scripting/properties/storagemode-element-assl.md)、[型](../../../analysis-services/scripting/properties/type-element-partition-assl.md)|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|なし|  
  
## <a name="remarks"></a>解説  
 この要素は、DeploymentMode の値が 2 (テーブル サーバー モード) の下にある次の検証には。  
  
-   次の子要素は、サポートされていないため、使用できません。  
  
    -   [ProcessingPriority](../../../analysis-services/scripting/properties/processingpriority-element-assl.md)  
  
    -   [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)  
  
    -   [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)  
  
    -   [ProcessingMode](../../../analysis-services/scripting/properties/processingmode-element-assl.md)  
  
    -   [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
    -   [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)  
  
    -   [RemoteDatasourceID](../../../analysis-services/scripting/properties/remotedatasourceid-element-assl.md)  
  
    -   [スライス](../../../analysis-services/scripting/properties/slice-element-assl.md)  
  
    -   [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)  
  
    -   [型](../../../analysis-services/scripting/properties/type-element-partition-assl.md)  
  
    -   [CurrentStorageMode](../../../analysis-services/scripting/properties/currentstoragemode-element-assl.md)  
  
    -   [AggregationDesignID](../../../analysis-services/scripting/properties/aggregationdesignid-element-assl.md)  
  
    -   [AggregationInstances](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)  
  
    -   [AggregationInstanceSource](../../../analysis-services/scripting/properties/aggregationinstancesource-element-assl.md)  
  
     上記の要素のいずれかを使用すると、エラーがスローされます。  
  
-   [ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)要素のみを受け入れる**クエリ**バインドします。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Partition>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
