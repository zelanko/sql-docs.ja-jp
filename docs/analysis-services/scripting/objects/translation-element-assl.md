---
title: "Translation 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
apiname: Translation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Translation
helpviewer_keywords: Translation element
ms.assetid: fe715bab-050d-49e6-8ba6-801d0fa379a4
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9eca2f049f59b3a3e1d5e35777a6f00366fc877f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="translation-element-assl"></a>Translation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親のローカライズされた翻訳を提供、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Translations>  
   <Translation xsi:type="Translation">...</Translation>  
   <!-- or -->  
   <Translation xsi:type="AttributeTranslation">...</Translation>  
</Translations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)、 [AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Translation>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
