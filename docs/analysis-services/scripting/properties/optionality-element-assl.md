---
title: "Optionality 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Optionality Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Optionality element
ms.assetid: 6cd2ef0a-6fbe-4462-ab27-4cdfeb33f8ab
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8649ff45c9c6982361098d2643f7d4bc00cdf663
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="optionality-element-assl"></a>Optionality 要素 (ASSL)
  メンバーがオプションかどうかを示す、 [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*必須*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*必須*|関連属性内の各メンバーが所有している属性の少なくとも 1 つのメンバーに関連するが、 **AttributeRelationship**要素。|  
|*省略可*|関連属性内の各メンバーが所有している属性の少なくとも 1 つのメンバーと関連付けられる、 **AttributeRelationship**要素。|  
  
 許可される値に対応する列挙**基数**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Optionality>します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

