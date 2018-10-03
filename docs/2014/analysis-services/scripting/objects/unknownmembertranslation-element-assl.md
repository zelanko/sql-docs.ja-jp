---
title: UnknownMemberTranslation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- UnknownMemberTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- UnknownMemberTranslation
helpviewer_keywords:
- UnknownElementTranslation element
ms.assetid: a4b8cdac-b065-4a44-b251-c5ac1cfe5e6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7fa7aacc82e91396496a0fd5405c70e9643372c2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125302"
---
# <a name="unknownmembertranslation-element-assl"></a>UnknownMemberTranslation 要素 (ASSL)
  キャプションの翻訳が含まれています、 [UnknownMember](member-element-assl.md)の要素を[ディメンション](dimension-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<UnknownMemberTranslations>  
   <UnknownMemberTranslation xsi:type="Translation">...</UnknownMemberTranslation>  
</UnknownMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](../data-type/translation-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[UnknownMemberTranslations](../collections/translations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 親に対応する要素`UnknownMemberTranslation`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>関連項目  
 [Translation 要素&#40;ASSL&#41;](translation-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
