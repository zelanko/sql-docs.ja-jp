---
title: MembersWithData 要素 (ASSL) |Microsoft ドキュメント
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
- MembersWithData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5c0311a774b225234aeb63d4d67680e12b693b0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176034"
---
# <a name="memberswithdata-element-assl"></a>MembersWithData 要素 (ASSL)
  親属性内の非リーフ メンバーのデータ メンバーを表示するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*NonLeafDataVisible*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値、`MembersWithData`要素は親属性によってのみ使用 (つまり、他の値、[使用状況](usage-element-dimensionattribute-assl.md)の要素、`DimensionAttribute`に設定されている親要素*親*) を決定するかどうか親属性の非リーフ メンバーのデータ メンバーを表示します。 データ メンバーの詳細については、「 [親子階層の属性](../../multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*NonLeafDataHidden*|非リーフ データは表示されません。|  
|*NonLeafDataVisible*|非リーフ データは表示されます。|  
  
 許可される値に対応する列挙`MembersWithData`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MembersWithData>します。  
  
## <a name="see-also"></a>参照  
 [MembersWithDataCaption 要素&#40;ASSL&#41;](caption-element-assl.md)   
 [DimensionAttribute データ型&#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  