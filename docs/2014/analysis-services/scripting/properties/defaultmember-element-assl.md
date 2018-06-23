---
title: DefaultMember 要素 (ASSL) |Microsoft ドキュメント
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
- DefaultMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 71b8b2ecd1d5cd46ea50cceebe2a0105d9b7311f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083510"
---
# <a name="defaultmember-element-assl"></a>DefaultMember 要素 (ASSL)
  親要素の既定のメンバーを識別する多次元式 (MDX) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
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
|親要素|[AttributePermission](../objects/attributepermission-element-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、 [ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md)、 [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DefaultMember` 要素は、親要素の既定のメンバーを定義します。 場合`DefaultMember`が指定されていないか、空の文字列に設定されている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]既定のメンバーとして使用するメンバーを選択します。  
  
 `ManyToManyMeasureGroupDimension` 要素の場合、`DefaultMember` 要素には、`CubeDimensionID` の `ManyToManyMeasureGroupDimension` 要素で識別されたディメンション内のメンバーを指定する MDX 式が格納されます。 MDX 式がに似ていますが、 [StrToMember](/sql/mdx/strtomember-mdx) MDX の関数、CONSTRAINED キーワードを使用で MDX またはユーザー定義関数に含めることはできません。  
  
 詳細については、「 [既定メンバーの定義](../../multidimensional-models/attribute-properties-define-a-default-member.md)」を参照してください。  
  
 親に対応する要素`DefaultMember`分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AttributePermission>、 <xref:Microsoft.AnalysisServices.DimensionAttribute>、および<xref:Microsoft.AnalysisServices.PerspectiveAttribute>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
