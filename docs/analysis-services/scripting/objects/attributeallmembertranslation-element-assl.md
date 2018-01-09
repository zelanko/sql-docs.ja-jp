---
title: "AttributeAllMemberTranslation 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AttributeAllMemberTranslation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AttributeAllMemberTranslation
helpviewer_keywords: AttributeAllMemberTranslation element
ms.assetid: 4b0c61dd-6666-4bf4-9b23-c9d8e315c414
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9f7bb320ebbd371a06c078578947848740a607ce
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="attributeallmembertranslation-element-assl"></a>AttributeAllMemberTranslation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]キャプションの翻訳が含まれています、**すべて**のメンバー、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeAllMemberTranslations>  
   <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
</AttributeAllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeAllMemberTranslations](../../../analysis-services/scripting/collections/attributeallmembertranslations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素、 **AttributeAllMemberTranslations**分析管理オブジェクト (AMO) オブジェクト モデルのコレクションが<xref:Microsoft.AnalysisServices.Dimension>です。  
  
## <a name="see-also"></a>参照  
 [Translation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
