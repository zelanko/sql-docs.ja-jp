---
title: "キーの要素 (XMLA) |Microsoft ドキュメント"
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
- Key Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 00c7e159e919afe608a9d55c70485592c4b7003d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="key-element-xmla"></a>Key 要素 (XMLA)
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
 [Attribute 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [AttributeName 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Drop 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [要素 &#40; を挿入します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [KeyColumn 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Update 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [場所要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
