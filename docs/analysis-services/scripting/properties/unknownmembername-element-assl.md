---
title: "UnknownMemberName 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: UnknownMemberName Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: UnknownMemberName
helpviewer_keywords: UnknownMemberName element
ms.assetid: 54271336-ea9b-4270-ac3a-9658a5cff77b
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f8c0ef48c999e2a541c8e7d0177dde728c81478e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="unknownmembername-element-assl"></a>UnknownMemberName 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ディメンションの不明なメンバーのディメンションの既定の言語で、キャプションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMemberName>...</UnknownMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|*Unknown*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **UnknownMemberName**要素が不明なメンバーに使用されるキャプションを提供します。 不明なメンバーのメンバーの ID が*ディメンション*です。UnknownMember、場所*ディメンション*ディメンションの一意の名前は、変更できません。  
  
 親に対応する要素**UnknownMemberName**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
