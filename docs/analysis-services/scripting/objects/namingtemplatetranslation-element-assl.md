---
title: "NamingTemplateTranslation 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NamingTemplateTranslation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa966a46acf8f6ce0c40b7c2ffb341552afa4e99
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="namingtemplatetranslation-element-assl"></a>NamingTemplateTranslation 要素 (ASSL)
  ローカライズされた翻訳を提供、 [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)要素の親を[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[NamingTemplateTranslations](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **NamingTemplateTranslation**要素は親属性によってのみ使用 (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の要素、 **DimensionAttribute**設定されている親*親*) のローカライズされた翻訳を格納する、 **NamingTemplate**特定の言語の値。  
  
 親に対応する要素**NamingTemplateTranslations**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [NamingTemplate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
