---
title: RootMemberIf 要素 (ASSL) |Microsoft Docs
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
- RootMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7ac45d2111b8d3631160ce78f131f98d53230e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280298"
---
# <a name="rootmemberif-element-assl"></a>RootMemberIf 要素 (ASSL)
  親属性のルート メンバーまたはメンバーを識別する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ParentIsBlankSelfOrMissing*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値、`RootMemberIf`要素の親属性によってのみ使用されます (つまり、他の値、[使用状況](usage-element-dimensionattribute-assl.md)の要素、`DimensionAttribute`に設定されている親要素*親*) ルート (を判断するには親子階層の最上位) メンバー。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|説明されている条件の 1 つ以上満たすメンバーのみ*ParentIsBlank*、 *ParentIsSelf*、または*ParentIsMissing*がルート メンバーとして扱われます。|  
|*ParentIsBlank*|Null、0、または空の文字列で表されるキー列を持つメンバーのみ、 [KeyColumns](../collections/columns-element-assl.md)のコレクション`DimensionAttribute`がルート メンバーとして扱われます。|  
|*ParentIsSelf*|自分自身が親であるメンバーのみがルート メンバーとして扱われます。|  
|*ParentIsMissing*|親が見つからないメンバーのみがルート メンバーとして扱われます。|  
  
 許容された値に対応する列挙体`RootMemberIf`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RootIfValue>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
