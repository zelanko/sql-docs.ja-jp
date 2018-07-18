---
title: Database 要素 (ASSL) |Microsoft Docs
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
- Database Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DATABASE
helpviewer_keywords:
- Database element
ms.assetid: c3bc7eaf-ed0d-4395-a3b7-8d9cfacfe911
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 56efc69c0e8f7f0e3e008aa5ea769774ee5014af
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332822"
---
# <a name="database-element-assl"></a>Database 要素 (ASSL)
  定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。  
  
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
|親要素|[データベース](../collections/databases-element-assl.md)|  
|子要素|[アカウント](../collections/accounts-element-assl.md)、 [AggregationPrefix](../properties/aggregationprefix-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、[アセンブリ](../collections/assemblies-element-assl.md)、[照合](../properties/collation-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[キューブ](../collections/cubes-element-assl.md)、 [DatabasePermissions](../collections/databasepermissions-element-assl.md)、[データソース](../collections/datasources-element-assl.md)、 [DataSourceViews](../collections/datasourceviews-element-assl.md)、[説明](../properties/description-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、 [EstimatedSize](../properties/estimatedsize-element-assl.md)、 [ID](../properties/id-element-assl.md)、[言語](../properties/language-element-assl.md)、 [LastProcessed](../properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [LastUpdate](../properties/lastupdate-element-assl.md)、 [MasterDatasourceID](../properties/datasourceid-element-assl.md)、 [MiningStructures](../collections/miningstructures-element-assl.md)、[名前](../properties/name-element-assl.md)、[ロール](../collections/roles-element-assl.md)、[状態](../properties/state-element-assl.md)、[翻訳](../collections/translations-element-assl.md)、[表示](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Database>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素&#40;ASSL&#41;](server-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
