---
title: "AttributeAllMemberTranslations 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname: AttributeAllMemberTranslations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AttributeAllMemberTranslations
helpviewer_keywords: AttributeAllMemberTranslations element
ms.assetid: 1a0d86ea-d95d-4d93-b321-acd35ed4ac26
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 520b2e016c91d899d2b740b8c5bf07ea02dd18d1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="attributeallmembertranslations-element-assl"></a>AttributeAllMemberTranslations 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ディメンションの All メンバーのキャプションに対する翻訳のコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
   ...  
   <AttributeAllMemberTranslations>  
      <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
   </AttributeAllMemberTranslations>  
      ...  
</Dimension>  
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
|親要素|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|[AttributeAllMemberTranslation](../../../analysis-services/scripting/objects/attributeallmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**AttributeAllMemberTranslations**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [Translation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
