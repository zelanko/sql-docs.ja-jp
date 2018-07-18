---
title: 要素 (XMLA) の名前を付けます |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 088dd6aa9ce8d9ecae3e3a8f293f64b3ddc93c70
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194232"
---
# <a name="name-element-xmla"></a>Name 要素 (XMLA)
  親の属性メンバーの名前を含む[属性](attribute-element-xmla.md)または[翻訳](translation-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|先祖または親。|Cardinality|  
|[属性](attribute-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|[翻訳](translation-element-xmla.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](attribute-element-xmla.md)、[翻訳](translation-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Attribute` 要素の場合、`Name` 要素は、`Insert` または `Update` コマンドの実行時に挿入または更新される属性メンバーの名前を含みます。  
  
 `Translation` 要素の場合、`Name` 要素は、親オブジェクト `Language` の `Translation` 要素で指定された言語で、属性メンバーのキャプションを含みます。 `Name` 要素が指定されない場合、または空の文字列を含む場合には、`Name` 要素を含んでいる `Attribute` 要素の `Translation` 要素の値が使用されます。  
  
## <a name="see-also"></a>参照  
 [要素を挿入&#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [言語要素&#40;XMLA&#41;](language-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
