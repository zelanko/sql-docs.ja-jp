---
title: Server 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d9715dd8e6ebd5c080362004850674adc3113c8c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030573"
---
# <a name="server-element-assl"></a>Server 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [ProductName](../../../analysis-services/scripting/properties/productname-element-assl.md)、[エディション](../../../analysis-services/scripting/properties/edition-element-assl.md)、 [EditionId](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md)、[バージョン](../../../analysis-services/scripting/properties/version-element-assl.md)、 [ServerMode](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md)、 [ProductLevel](../../../analysis-services/xmla/xml-elements-properties/productlabel-element.md)、[データベース](../../../analysis-services/scripting/collections/databases-element-assl.md)、[アセンブリ](../../../analysis-services/scripting/collections/assemblies-element-assl.md)、[トレース](../../../analysis-services/scripting/collections/traces-element-assl.md)、[ロール](../../../analysis-services/scripting/collections/roles-element-assl.md)、[ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)>|  
  
## <a name="remarks"></a>解説  
 **サーバー**要素のインスタンスを表す[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、Analysis Services スクリプト言語 (ASSL) ノード階層の最上位ノードとして機能します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Server>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
