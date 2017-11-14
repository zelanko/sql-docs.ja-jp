---
title: "AttributeTranslation データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AttributeTranslation Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeTranslation
helpviewer_keywords:
- AttributeTranslation data type
ms.assetid: a0e29941-ef08-42ad-ab9c-b2efd7910895
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c59eb5b832f4d00b8e651569065dbfbc1566033f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="attributetranslation-data-type-assl"></a>AttributeTranslation データ型 (ASSL)
  関連付けられている翻訳を表す派生データ型を定義、[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)要素  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeTranslation>  
   <!-- The following elements extend Translation -->  
   <CaptionColumn>...</CaptionColumn>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
</AttributeTranslation>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[翻訳](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md)、 [MembersWithDataCaption](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)|  
|派生要素|参照してください[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)([翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)のコレクション[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)または[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AttributeTranslation>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

