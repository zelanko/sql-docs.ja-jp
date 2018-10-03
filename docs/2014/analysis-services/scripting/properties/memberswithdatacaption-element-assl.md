---
title: MembersWithDataCaption 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MembersWithDataCaption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithDataCaption
helpviewer_keywords:
- MembersWithDataCaption element
ms.assetid: a5d59efd-5d67-485b-a360-67d54a1fe394
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 847a355f2517a5a630096e2617a27bdae396e565
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103902"
---
# <a name="memberswithdatacaption-element-assl"></a>MembersWithDataCaption 要素 (ASSL)
  システムによって生成されるデータ メンバーのキャプションを作成するためのテンプレート文字列を提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeTranslation](../data-type/translation-data-type-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値、`MembersWithDataCaption`要素の親属性によってのみ使用されます (つまり、他の値、[使用状況](usage-element-dimensionattribute-assl.md)の要素、`DimensionAttribute`に設定されている親要素*親*) を判断、親属性内のデータ メンバーのキャプション。 データ メンバーの詳細については、「 [親子階層の属性](../../multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
 親に対応する要素`MembersWithDataCaption`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.AttributeTranslation>と<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [MembersWithData 要素&#40;ASSL&#41;](../objects/data-element-assl.md)   
 [AttributeTranslation データ型&#40;ASSL&#41;](../data-type/translation-data-type-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
