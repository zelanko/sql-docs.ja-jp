---
title: "Database 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Database Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DATABASE
helpviewer_keywords: Database element
ms.assetid: c3bc7eaf-ed0d-4395-a3b7-8d9cfacfe911
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 89c6170386d75d25abcebab7b1f61de29160b002
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="database-element-assl"></a>Database 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Databases>  
   <Database>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastUpdate>...</LastUpdate>  
      <Description>...</Description>  
      <State>   </State>  
      <AggregationPrefix>...</AggregationPrefix>  
      <EstimatedSize>...</EstimatedSize>  
      <LastProcessed>...</LastProcessed>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <Visible>...</Visible>  
      <MasterDatasourceID>...</MasterDataSourceID>  
      <Accounts>...</Accounts>  
      <DataSources>...</DataSources>  
      <DataSourceViews>...</DataSourceViews>  
      <Dimensions>...</Dimensions>  
      <Cubes>...</Cubes>  
      <MiningStructures>...</MiningStructures>  
            <Roles>...</Roles>  
      <Assemblies>...</Assemblies>  
      <DatabasePermissions>...</DatabasePermissions>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Database>  
</Databases>  
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
|親要素|[データベース](../../../analysis-services/scripting/collections/databases-element-assl.md)|  
|子要素|[アカウント](../../../analysis-services/scripting/collections/accounts-element-assl.md)、 [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[アセンブリ](../../../analysis-services/scripting/collections/assemblies-element-assl.md)、[照合](../../../analysis-services/scripting/properties/collation-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、[キューブ](../../../analysis-services/scripting/collections/cubes-element-assl.md)、 [DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)、 [DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md)、 [DataSourceViews](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [EstimatedSize](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[言語](../../../analysis-services/scripting/properties/language-element-assl.md)、 [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [LastUpdate](../../../analysis-services/scripting/properties/lastupdate-element-assl.md)、 [MasterDatasourceID](../../../analysis-services/scripting/properties/masterdatasourceid-element-assl.md)、 [MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[ロール](../../../analysis-services/scripting/collections/roles-element-assl.md)、[状態](../../../analysis-services/scripting/properties/state-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Database>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
