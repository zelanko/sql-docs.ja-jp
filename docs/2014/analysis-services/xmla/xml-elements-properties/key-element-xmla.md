---
title: キーの要素 (XMLA) |Microsoft Docs
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
- Key Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1f98ae6863f0aab25149ee4f8a69ef13b65da974
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213762"
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
|親要素|[キー](keys-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素で使用するデータ型は、指定される属性の適切なキー列のデータ型と一致する必要があります。 親要素 `Key` で `Attribute` 要素が指定されない場合、変更対象の属性メンバーを識別するために、親要素 `AttributeName` 内で指定された `Name` および `Attribute` 要素が使用されます。  
  
## <a name="see-also"></a>参照  
 [要素の属性&#40;XMLA&#41;](attribute-element-xmla.md)   
 [AttributeName 要素&#40;XMLA&#41;](name-element-xmla.md)   
 [Drop 要素&#40;XMLA&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [要素を挿入&#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [KeyColumn 要素&#40;ASSL&#41;](../../scripting/objects/column-element-assl.md)   
 [Update 要素&#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [場所要素&#40;XMLA&#41;](where-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
