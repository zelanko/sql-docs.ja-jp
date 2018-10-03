---
title: Insert 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Insert Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Insert
- http://schemas.microsoft.com/analysisservices/2003/engine#Insert
- microsoft.xml.analysis.insert
helpviewer_keywords:
- Insert command
ms.assetid: d1137033-cc19-4bcb-b93d-8575f17bea6b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a077a263a66c4684279be6e2f353348f451d5435
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120932"
---
# <a name="insert-element-xmla"></a>Insert 要素 (XMLA)
  属性メンバーをディメンションに挿入します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Insert>  
      <Object>...</Object>  
      <Attributes>...</Attributes>  
   </Insert>  
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
|子要素|[属性](../xml-elements-properties/attributes-element-xmla.md)、[オブジェクト](../xml-elements-properties/object-element-dimension-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Insert` コマンドは、書き込み許可ディメンションの中に新しい属性メンバーを挿入します。  
  
 メンバーを削除する方法についての詳細については、次を参照してください。[挿入、更新、および削除するメンバー &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [Drop 要素&#40;XMLA&#41;](drop-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](update-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
