---
title: Drop 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Drop Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Drop
- microsoft.xml.analysis.drop
- http://schemas.microsoft.com/analysisservices/2003/engine#Drop
helpviewer_keywords:
- Drop element
ms.assetid: a5d21db3-743a-4958-b16d-b6816a5ee787
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b723e6ae10ae045ce43c7138ce481ffdab3955bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194942"
---
# <a name="drop-element-xmla"></a>Drop 要素 (XMLA)
  属性メンバーをディメンションから削除します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Drop>  
      <Object>...</Object>  
      <DeleteWithDescendants>...</DeleteWithDescendants>  
      <Where>...</Where>  
   </Drop>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[DeleteWithDescendants](../xml-elements-properties/deletewithdescendants-element-xmla.md)、[オブジェクト](../xml-elements-properties/object-element-dimension-xmla.md)、[場所](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Drop` コマンドは、書き込み許可ディメンションから属性メンバーを削除します。  
  
 メンバーを削除する方法についての詳細については、次を参照してください。[挿入、更新、および削除するメンバー &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [要素を挿入&#40;XMLA&#41;](insert-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](update-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
