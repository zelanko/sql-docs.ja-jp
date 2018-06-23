---
title: StorageEngineUsed 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- StorageEngineUsed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
ms.assetid: 98895c10-f3c2-4d8a-be94-6128c828561d
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 608ebcbb1252b4fafa44bf242a83418cc6b3d053
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177397"
---
# <a name="storageengineused-element-xmla"></a>StorageEngineUsed 要素 (XMLA)
  現在のデータベースの種類を示す読み取り専用の値を格納します。  
  
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
            <StorageEngineUsed >...</StorageEngineUsed>  
   </Database>  
</Databases>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[database](../objects/database-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*従来*|データベース モデルは、MOLAP、ROLAP、または HOLAP ストレージ モードに対応します。|  
|*InMemory*|データベース モデルは、IMBI ストレージ モードに対応します。|  
|*混在*|データベース モデルは、IMBI と、MOLAP、ROLAP、または HOLAP ストレージ モードを組み合わせます。|  
  
 許可される値に対応する列挙`StorageEngineUsed`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.StorageEngineUsed>します。  
  
 親に対応する要素`StorageEngineUsed`分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Database>します。  
  
  