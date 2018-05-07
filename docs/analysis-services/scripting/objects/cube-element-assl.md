---
title: キューブ要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c946e1700b28d1e70dac837b91350f37621178e9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cube-element-assl"></a>Cube 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  通常、仮想、またはリンク キューブを定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
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
|親要素|[キューブ](../../../analysis-services/scripting/collections/cubes-element-assl.md)|  
|子要素|[アクション](../../../analysis-services/scripting/collections/actions-element-assl.md)、 [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[照合](../../../analysis-services/scripting/properties/collation-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [CubePermissions](../../../analysis-services/scripting/collections/cubepermissions-element-assl.md)、 [DefaultMeasure](../../../analysis-services/scripting/properties/defaultmeasure-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)、 [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [Kpi](../../../analysis-services/scripting/collections/kpis-element-assl.md)、[言語](../../../analysis-services/scripting/properties/language-element-assl.md)、 [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [MdxScripts](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)、 [MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[パースペクティブ](../../../analysis-services/scripting/collections/perspectives-element-assl.md)、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)、 [ProcessingMode](../../../analysis-services/scripting/properties/processingmode-element-assl.md)、 [ProcessingPriority](../../../analysis-services/scripting/properties/processingpriority-element-assl.md)、 [ScriptCacheProcessingMode](../../../analysis-services/scripting/properties/scriptcacheprocessingmode-element-assl.md)、[状態](../../../analysis-services/scripting/properties/state-element-assl.md)、 [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)、 [StorageMode](../../../analysis-services/scripting/properties/storagemode-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Cube>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
