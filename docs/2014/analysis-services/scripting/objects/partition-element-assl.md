---
title: 要素 (ASSL) をパーティション分割 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Partition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PARTITION
helpviewer_keywords:
- Partition element
ms.assetid: 40020840-1bb7-478f-9017-1a30342ac4c6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ad06de27b07ab58df2d5357b960906093daa5f5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198802"
---
# <a name="partition-element-assl"></a>Partition 要素 (ASSL)
  パーティションを定義、 [MeasureGroup](group-element-assl.md)要素またはの行外でのパーティション バインド[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)要素。  
  
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
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[メジャー グループ](group-element-assl.md)|なし|  
|[MeasureGroupBinding](../data-type/binding-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パーティション](../collections/partitions-element-assl.md)|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[MeasureGroup](../properties/id-element-assl.md)、 [AggregationInstances](../collections/aggregationinstances-element-assl.md)、 [AggregationInstanceSource](../properties/aggregationinstancesource-element-assl.md)、 [AggregationPrefix](../properties/aggregationprefix-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [CurrentStorageMode](../properties/storagemode-element-assl.md)、[説明](../properties/description-element-assl.md)、 [ErrorConfiguration](errorconfiguration-element-assl.md)、 [EstimatedRows](../properties/estimatedrows-element-assl.md)、 [EstimatedSize](../properties/estimatedsize-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [LastProcessed](../properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[名前](../properties/name-element-assl.md)、 [ProactiveCaching](proactivecaching-element-assl.md)、 [ProcessingMode](../properties/processingmode-element-assl.md)、 [ProcessingPriority](../properties/processingpriority-element-assl.md)、 [RemoteDatasourceID](../properties/datasourceid-element-assl.md)、[スライス](../properties/slice-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)、[状態](../properties/state-element-assl.md)、 [StorageLocation](../properties/storagelocation-element-assl.md)、 [StorageMode](../properties/storagemode-element-assl.md)、[型](../properties/type-element-partition-assl.md)|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)|なし|  
  
## <a name="remarks"></a>コメント  
 この要素には、DeploymentMode の値 2 (表形式サーバー モード)、次の検証があります。  
  
-   次の子要素は、サポートされていないため、使用できません。  
  
    -   [ProcessingPriority](../properties/processingpriority-element-assl.md)  
  
    -   [AggregationPrefix](../properties/aggregationprefix-element-assl.md)  
  
    -   [StorageLocation](../properties/storagelocation-element-assl.md)  
  
    -   [ProcessingMode](../properties/processingmode-element-assl.md)  
  
    -   [ErrorConfiguration](errorconfiguration-element-assl.md)  
  
    -   [StorageLocation](../properties/storagelocation-element-assl.md)  
  
    -   [RemoteDatasourceID](../properties/datasourceid-element-assl.md)  
  
    -   [スライス](../properties/slice-element-assl.md)  
  
    -   [ProactiveCaching](proactivecaching-element-assl.md)  
  
    -   [型](../properties/type-element-partition-assl.md)  
  
    -   [CurrentStorageMode](../properties/storagemode-element-assl.md)  
  
    -   [AggregationDesignID](../properties/aggregationdesignid-element-assl.md)  
  
    -   [AggregationInstances](../collections/aggregationinstances-element-assl.md)  
  
    -   [AggregationInstanceSource](../properties/aggregationinstancesource-element-assl.md)  
  
     上記の要素のいずれかを使用すると、エラーがスローされます。  
  
-   [ソース](../properties/source-element-binding-assl.md)要素のみを受け入れる**クエリ**バインドします。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Partition>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
