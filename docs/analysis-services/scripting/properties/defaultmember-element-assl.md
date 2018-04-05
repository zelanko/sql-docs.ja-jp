---
title: DefaultMember 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DefaultMember Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3559aafd4fc5b31b1cfc73bdf7dc75a9d6821b84
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="defaultmember-element-assl"></a>DefaultMember 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素の既定のメンバーを識別する多次元式 (MDX) 式が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、 [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md)、 [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DefaultMember**要素は親要素の既定のメンバーを定義します。 場合**DefaultMember**が指定されていないか、空の文字列に設定されている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]既定のメンバーとして使用するメンバーを選択します。  
  
 **ManyToManyMeasureGroupDimension** 、要素、 **DefaultMember**要素にはで識別されたディメンションのメンバーを指定する MDX 式が含まれています、 **CubeDimensionID**の要素、 **ManyToManyMeasureGroupDimension**です。 MDX 式がに似ていますが、 [StrToMember](../../../mdx/strtomember-mdx.md) MDX の関数、CONSTRAINED キーワードを使用で MDX またはユーザー定義関数に含めることはできません。  
  
 詳細については、「 [既定メンバーの定義](../../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)」を参照してください。  
  
 親に対応する要素**DefaultMember**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AttributePermission>、 <xref:Microsoft.AnalysisServices.DimensionAttribute>、および<xref:Microsoft.AnalysisServices.PerspectiveAttribute>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
