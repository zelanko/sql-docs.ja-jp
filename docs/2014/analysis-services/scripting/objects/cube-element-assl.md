---
title: キューブ要素 (ASSL) |Microsoft Docs
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
- Cube Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Cube
helpviewer_keywords:
- Cube element
ms.assetid: 2d801066-6cca-4a99-bbd8-56a38d762108
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eab8cc56de346540491664a60c644ef868b02a25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165263"
---
# <a name="cube-element-assl"></a>Cube 要素 (ASSL)
  通常、仮想、またはリンク キューブを定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [データベース](database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cubes>  
   <Cube>  
            <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
            <Description>...</Description>  
            <Language>...</Language>  
            <Collation>...</Collation>  
            <Translations>...</Translations>  
      <Dimensions>...</Dimensions>  
            <CubePermissions>...</CubePermissions>  
      <MdxScripts>...</MdxScripts>  
      <Perspectives>...</Perspectives>  
      <State>...</State>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Visible>...</Visible>  
      <MeasureGroups>...</MeasureGroups>  
      <DataSourceView >...</Source>  
      <AggregationPrefix>...</AggregationPrefix>  
      <ProcessingPriority>...</ProcessingPriority>  
            <StorageMode>...</StorageMode>  
      <ProcessingMode>...</ProcessingMode>  
      <ScriptCacheProcessingMode>...</ScriptCacheProcessingMode>  
      <ProactiveCaching>...</ProactiveCaching>  
            <Kpis>...</Kpis>  
            <ErrorConfiguration>...</ErrorConfiguration>  
            <Actions>...</Actions>  
      <StorageLocation>...</StorageLocation>  
      <EstimatedRows>...</EstimatedRows>  
      <LastProcessed>...</LastProcessed>  
      <Annotations>...</Annotations>  
   </Cube>  
</Cubes>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../collections/cubes-element-assl.md)|  
|子要素|[アクション](../collections/actions-element-assl.md)、 [AggregationPrefix](../properties/aggregationprefix-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、[照合](../properties/collation-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [CubePermissions](../collections/cubepermissions-element-assl.md)、 [DefaultMeasure](measure-element-assl.md)、[説明](../properties/description-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、 [ErrorConfiguration](errorconfiguration-element-assl.md)、 [EstimatedRows](../properties/estimatedrows-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [Kpi](../collections/kpis-element-assl.md)、[言語](../properties/language-element-assl.md)、 [LastProcessed](../properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [MdxScripts](../collections/mdxscripts-element-assl.md)、 [MeasureGroups](../collections/groups-element-assl.md)、[名前](../properties/name-element-assl.md)、[パースペクティブ](../collections/perspectives-element-assl.md)、 [ProactiveCaching](proactivecaching-element-assl.md)、 [ProcessingMode](../properties/processingmode-element-assl.md)、 [ProcessingPriority](../properties/processingpriority-element-assl.md)、 [ScriptCacheProcessingMode](../properties/scriptcacheprocessingmode-element-assl.md)、[状態](../properties/state-element-assl.md)、 [StorageLocation](../properties/storagelocation-element-assl.md)、 [StorageMode](../properties/storagemode-element-assl.md)、[翻訳](../collections/translations-element-assl.md)、[表示](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Cube>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
