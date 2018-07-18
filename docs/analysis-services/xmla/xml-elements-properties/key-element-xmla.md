---
title: キーの要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bea00c5b5fdff010d667db19ef3af28284ce3ed9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036920"
---
# <a name="key-element-xmla"></a>Key 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  属性メンバーのメンバー キー値を含みます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Any|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キー](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素で使用するデータ型は、指定される属性の適切なキー列のデータ型と一致する必要があります。 場合**キー**親要素が指定されていない**属性**要素、 **AttributeName**と**名前**で指定した要素、親**属性**要素が変更される属性メンバーを識別するために使用されます。  
  
## <a name="see-also"></a>参照
 [要素の属性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [AttributeName 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Drop 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [要素を挿入&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [KeyColumn 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Update 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [場所要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
