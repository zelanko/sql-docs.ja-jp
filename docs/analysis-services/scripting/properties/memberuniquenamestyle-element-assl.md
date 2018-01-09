---
title: "MemberUniqueNameStyle 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MemberUniqueNameStyle Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MemberUniqueNameStyle element
ms.assetid: f0771c81-0127-4203-9501-ae4f864730fa
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dbe8b82f9f82327009875530e7750753705f48e8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="memberuniquenamestyle-element-assl"></a>MemberUniqueNameStyle 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]一意の名前が決定に含まれる階層のメンバーに対して生成される、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension>  
   ...  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ネイティブ*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*ネイティブ*|インスタンスによって、メンバーの一意の名前が自動的に決定されます。|  
|*NamePath*|インスタンスによって、メンバーの各レベルおよびキャプションで構成される複合名が生成されます。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**MemberUniqueNameStyle**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [Cube 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [CubeDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)  
  
  
