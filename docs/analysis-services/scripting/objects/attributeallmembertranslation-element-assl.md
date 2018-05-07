---
title: AttributeAllMemberTranslation 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fc51d29f908728dae2dc5f7e4c98802a1b122ef1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="attributeallmembertranslation-element-assl"></a>AttributeAllMemberTranslation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  キャプションの翻訳が含まれています、**すべて**のメンバー、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeAllMemberTranslations>  
   <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
</AttributeAllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeAllMemberTranslations](../../../analysis-services/scripting/collections/attributeallmembertranslations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素、 **AttributeAllMemberTranslations**分析管理オブジェクト (AMO) オブジェクト モデルのコレクションが<xref:Microsoft.AnalysisServices.Dimension>です。  
  
## <a name="see-also"></a>参照  
 [Translation 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
