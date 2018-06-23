---
title: AttributeName 要素 (XMLA) |Microsoft ドキュメント
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
- AttributeName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AttributeName
- http://schemas.microsoft.com/analysisservices/2003/engine#AttributeName
- microsoft.xml.analysis.attributename
helpviewer_keywords:
- AttributeName element
ms.assetid: 4dc8260b-522e-46d9-9bd8-22a5a0068982
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1251de0a3f81a0b3a25d44de5bfbe2e41fa0f90a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085295"
---
# <a name="attributename-element-xmla"></a>AttributeName 要素 (XMLA)
  親によって表される属性の名前を含む[属性](attribute-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute>  
   ...  
   <AttributeName>...</AttributeName>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](attribute-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [Drop 要素&#40;XMLA&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [要素を挿入&#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [場所要素&#40;XMLA&#41;](where-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  