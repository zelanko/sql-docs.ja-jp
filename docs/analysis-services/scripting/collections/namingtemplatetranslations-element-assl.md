---
title: "NamingTemplateTranslations 要素 (ASSL) |Microsoft ドキュメント"
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
- NamingTemplateTranslations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed377512b4d2e27e6f3ec0d85066ac72b9996499
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="namingtemplatetranslations-element-assl"></a>NamingTemplateTranslations 要素 (ASSL)
  ローカライズされた変換のコレクションを提供、 [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)要素は親の[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)型の[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|[NamingTemplateTranslation](../../../analysis-services/scripting/objects/namingtemplatetranslation-element-assl.md)型の[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 値、 **NamingTemplateTranslation**要素は親属性によってのみ使用 (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の親要素**DimensionAttribute**に設定されている*親*)。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

