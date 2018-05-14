---
title: RootMemberIf 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0a738d6d859a74430d50439ebcee3d4aab8d031c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="rootmemberif-element-assl"></a>RootMemberIf 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **RootMemberIf**要素は親属性によってのみ使用 (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の要素、 **DimensionAttribute**親要素設定*親*)、親子階層のルート (最上位) メンバーを判断します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|説明の条件の 1 つ以上満たすメンバーだけ*ParentIsBlank*、 *ParentIsSelf*、または*ParentIsMissing*ルート メンバーとして扱われます。|  
|*ParentIsBlank*|Null、0、または空の文字列で表されるキー列でのメンバーのみ、 [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)のコレクション**DimensionAttribute**ルート メンバーとして扱われます。|  
|*ParentIsSelf*|自分自身が親であるメンバーのみがルート メンバーとして扱われます。|  
|*ParentIsMissing*|親が見つからないメンバーのみがルート メンバーとして扱われます。|  
  
 許可される値に対応する列挙**RootMemberIf**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RootIfValue>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
