---
title: Server 要素 (ASSL) |Microsoft Docs
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
- Server Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- server
helpviewer_keywords:
- Server element
ms.assetid: 92ca67f6-817e-4a75-9244-8f8bcf412190
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d5ae1dc9c10bce01cb9b0f90da2ef25b023392f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319232"
---
# <a name="server-element-assl"></a>Server 要素 (ASSL)
  インスタンスを記述[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Server>  
   <!—These elements are common to each major object -->  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <Description>...</Description>  
   <Annotations>...</Annotations>  
   <!-- server elements or properties -->  
   <ProductName>...</ProductName>  
   <Edition>...</Edition>  
   <EditionId>...</Edition>  
   <Version>...</Version>  
   <ServerMode>...</ServerMode>  
   <ProductLevel>...</Databases>  
   <Databases>...</Databases>  
   <Assemblies>...</Assemblies>  
   <Traces>...</Traces>  
   <Roles>...</Roles>  
   <ServerProperties>...</ServerProperties>  
</Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[名前](../properties/name-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[説明](../properties/description-element-assl.md)、 [注釈](../collections/annotations-element-assl.md)、 [ProductName](../properties/productname-element-assl.md)、 [Edition](../properties/edition-element-assl.md)、 [EditionId](../../xmla/xml-elements-properties/editionid-element.md)、[バージョン](../properties/version-element-assl.md)、 [ServerMode](../../xmla/xml-elements-properties/editionid-element.md)、 [ProductLevel](../../xmla/xml-elements-properties/productlabel-element.md)、[データベース](../collections/databases-element-assl.md)、[アセンブリ](../collections/assemblies-element-assl.md)、[トレース](../collections/traces-element-assl.md)、[ロール](../collections/roles-element-assl.md)、[ServerProperties](../collections/serverproperties-element-assl.md)>|  
  
## <a name="remarks"></a>コメント  
 `Server` 要素は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを表し、Analysis Services スクリプト言語 (ASSL) ノード階層の最上位ノードとして使用できます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Server>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
