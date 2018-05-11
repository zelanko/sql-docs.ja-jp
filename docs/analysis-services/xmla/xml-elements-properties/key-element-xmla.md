---
title: キーの要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cd43ad594acb118be0e7fb8d39cb34f2ae3e6ef6
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キー](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素で使用するデータ型は、指定される属性の適切なキー列のデータ型と一致する必要があります。 場合**キー**親の要素が指定されていない**属性**要素、 **AttributeName**と**名前**で指定した要素、親**属性**要素を使用して変更する属性メンバーを識別します。  
  
## <a name="see-also"></a>参照  
 [Attribute 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [AttributeName 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Drop 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [要素 & #40; を挿入します。XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [KeyColumn 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Update 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [場所要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
