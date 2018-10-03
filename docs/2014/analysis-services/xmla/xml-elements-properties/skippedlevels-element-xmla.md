---
title: SkippedLevels 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SkippedLevels Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#SkippedLevels
- microsoft.xml.analysis.skippedlevels
- urn:schemas-microsoft-com:xml-analysis#SkippedLevels
helpviewer_keywords:
- SkippedLevels element
ms.assetid: 4887b557-0ffc-4f42-b6b9-c98ad1208ca5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb76860b4f022bf076e7d5ccaed2234c917e3f73
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049412"
---
# <a name="skippedlevels-element-xmla"></a>SkippedLevels 要素 (XMLA)
  親によって表される属性メンバーがスキップするレベルの数を含む[属性](attribute-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute>  
   ...  
   <SkippedLevels>...</SkippedLevels>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|0|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](attribute-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `SkippedLevels` 要素は、親要素 `Attribute` によって定義される属性メンバーがスキップするレベルの数を決定します。  
  
## <a name="see-also"></a>参照  
 [要素を挿入&#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
