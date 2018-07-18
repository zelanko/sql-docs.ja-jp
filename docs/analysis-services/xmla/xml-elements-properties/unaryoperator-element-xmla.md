---
title: UnaryOperator 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 062cf977e04eabfc09e6598167bc7530f1254436
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051580"
---
# <a name="unaryoperator-element-xmla"></a>UnaryOperator 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親によって表される属性メンバーの単項演算子を含む[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute>  
   ...  
   <UnaryOperator>...</UnaryOperator>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **UnaryOperator**要素には、親によって定義される属性メンバーの単項演算子を定義する多次元式 (MDX) 式が含まれています。**属性**要素。  
  
 MDX 式の詳細については、次を参照してください。[式&#40;MDX&#41;](../../../mdx/expressions-mdx.md)します。  
  
## <a name="see-also"></a>参照
 [要素を挿入&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
