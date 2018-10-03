---
title: Translation データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Translation data type
ms.assetid: d40039e1-3ff6-4e20-8d8b-5baf501f726f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d6bf4fe33120a102239ccd54e7032e98719d0789
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213694"
---
# <a name="translation-data-type-assl"></a>Translation データ型 (ASSL)
  ローカライズされた翻訳を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Translation>  
   <Language>...</Language>  
   <Caption>...</Caption>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Annotations>...</Annotations>  
</Translation>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[AttributeTranslation](translation-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、[キャプション](../properties/caption-element-assl.md)、[説明](../properties/description-element-assl.md)、 [DisplayFolder](../properties/displayfolder-element-assl.md)、[言語](../properties/language-element-assl.md)|  
|派生要素|[AllMemberTranslation](../objects/translation-element-assl.md)、 [AttributeAllMemberTranslation](../objects/attributeallmembertranslation-element-assl.md)、 [NamingTemplateTranslation](../objects/namingtemplatetranslation-element-assl.md)、 [UnknownMemberTranslation](../objects/unknownmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Translation>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
