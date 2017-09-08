---
title: "Server 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Server Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- server
helpviewer_keywords:
- Server element
ms.assetid: 92ca67f6-817e-4a75-9244-8f8bcf412190
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8de09f74b1d9b7a6ded780f416201116c17a5667
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="server-element-assl"></a>Server 要素 (ASSL)
  インスタンスを記述[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
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
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [ProductName](../../../analysis-services/scripting/properties/productname-element-assl.md)、[エディション](../../../analysis-services/scripting/properties/edition-element-assl.md)、 [EditionId](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md)、[バージョン](../../../analysis-services/scripting/properties/version-element-assl.md)、 [ServerMode](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md)、 [ProductLevel](../../../analysis-services/xmla/xml-elements-properties/productlabel-element.md)、[データベース](../../../analysis-services/scripting/collections/databases-element-assl.md)、[アセンブリ](../../../analysis-services/scripting/collections/assemblies-element-assl.md)、[トレース](../../../analysis-services/scripting/collections/traces-element-assl.md)、[ロール](../../../analysis-services/scripting/collections/roles-element-assl.md)、 [ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)>|  
  
## <a name="remarks"></a>解説  
 **サーバー**要素のインスタンスを表す[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、Analysis Services スクリプト言語 (ASSL) ノード階層の最上位ノードとして機能します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Server>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
