---
title: RootMemberIf 要素 (ASSL) |Microsoft ドキュメント
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a923b08efc636d2635d60b00f85c42dc00a312e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075352"
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
 値、`RootMemberIf`要素は親属性によってのみ使用 (つまり、他の値、[使用状況](usage-element-dimensionattribute-assl.md)の要素、`DimensionAttribute`に設定されている親要素*親*)、ルート (を決定するには親子階層の最上位) メンバー。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|説明の条件の 1 つ以上満たすメンバーだけ*ParentIsBlank*、 *ParentIsSelf*、または*ParentIsMissing*ルート メンバーとして扱われます。|  
|*ParentIsBlank*|Null、0、または空の文字列で表されるキー列でのメンバーのみ、 [KeyColumns](../collections/columns-element-assl.md)のコレクション`DimensionAttribute`ルート メンバーとして扱われます。|  
|*ParentIsSelf*|自分自身が親であるメンバーのみがルート メンバーとして扱われます。|  
|*ParentIsMissing*|親が見つからないメンバーのみがルート メンバーとして扱われます。|  
  
 許可される値に対応する列挙`RootMemberIf`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RootIfValue>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  