---
title: NamingTemplateTranslation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NamingTemplateTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7689c1b2d83abb7673253550e133cd0fa0ea5e20
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086259"
---
# <a name="namingtemplatetranslation-element-assl"></a>NamingTemplateTranslation 要素 (ASSL)
  ローカライズされた翻訳を提供します、 [NamingTemplate](../properties/namingtemplate-element-assl.md)親要素[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](translation-element-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[NamingTemplateTranslations](../collections/translations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値、`NamingTemplateTranslation`要素の親属性によってのみ使用されます (つまり、他の値、[使用状況](../properties/usage-element-dimensionattribute-assl.md)の要素、`DimensionAttribute`に親が設定されている*親*) ローカライズ バージョンを格納するには変換、`NamingTemplate`特定の言語の値。  
  
 親に対応する要素`NamingTemplateTranslations`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [NamingTemplate 要素&#40;ASSL&#41;](../properties/namingtemplate-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
