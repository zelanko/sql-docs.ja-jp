---
title: AllMemberTranslations 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AllMemberTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllMemberTranslations
helpviewer_keywords:
- AllMemberTranslations element
ms.assetid: 982ee2bf-c88d-4da5-a679-7a6b08a48a0d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b2a1a8b9b72895c69cb8d415d00d633be99ebc99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175241"
---
# <a name="allmembertranslations-element-assl"></a>AllMemberTranslations 要素 (ASSL)
  コレクションを格納[翻訳](../objects/translation-element-assl.md)要素の All メンバーのキャプションに対する、[階層](../objects/hierarchy-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Hierarchy>  
   ...  
   <AllMemberTranslations>  
      <AllMemberTranslation xsi:type="Translation">...  
            </AllMemberTranslation>  
   </AllMemberTranslations>  
      ...  
</Hierarchy>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし (コレクション型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|子要素|[AllMemberTranslation](../objects/allmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`AllMemberTranslations`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Hierarchy>します。  
  
## <a name="see-also"></a>参照  
 [Translation 要素&#40;ASSL&#41;](../objects/translation-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  