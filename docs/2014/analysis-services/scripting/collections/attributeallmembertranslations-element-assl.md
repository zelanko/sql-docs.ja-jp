---
title: AttributeAllMemberTranslations 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeAllMemberTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeAllMemberTranslations
helpviewer_keywords:
- AttributeAllMemberTranslations element
ms.assetid: 1a0d86ea-d95d-4d93-b321-acd35ed4ac26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f9a5d8e2427534c100f303a4dadda968327107b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121562"
---
# <a name="attributeallmembertranslations-element-assl"></a>AttributeAllMemberTranslations 要素 (ASSL)
  ディメンションの All メンバーのキャプションに対する翻訳のコレクションを格納します。  
  
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
|親要素|[Dimension](../objects/dimension-element-assl.md)|  
|子要素|[AttributeAllMemberTranslation](../objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`AttributeAllMemberTranslations`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [Translation 要素&#40;ASSL&#41;](translations-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
