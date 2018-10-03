---
title: AllMemberTranslation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllMemberTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllMemberTranslation
helpviewer_keywords:
- AllMemberTranslation element
ms.assetid: 31ec0c44-8f1d-457c-9e8b-61dd5bc468f7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2453a6a41fbafd35b952017fca9e04e8858713fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121802"
---
# <a name="allmembertranslation-element-assl"></a>AllMemberTranslation 要素 (ASSL)
  すべてのメンバーのキャプションの翻訳が含まれています、[階層](hierarchy-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AllMemberTranslations>  
   <AllMemberTranslation xsi:type="Translation">...  
   </AllMemberTranslation>  
</AllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](translation-element-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AllMemberTranslations](../collections/translations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで `AllMemberTranslations` コレクションの親に対応する要素は、<xref:Microsoft.AnalysisServices.Hierarchy> です。  
  
## <a name="see-also"></a>参照  
 [Translation 要素&#40;ASSL&#41;](translation-element-assl.md)   
 [Hierarchy 要素&#40;ASSL&#41;](hierarchy-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
