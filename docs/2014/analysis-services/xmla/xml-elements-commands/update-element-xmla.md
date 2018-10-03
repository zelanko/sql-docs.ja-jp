---
title: Update 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Update Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Update
- microsoft.xml.analysis.update
- http://schemas.microsoft.com/analysisservices/2003/engine#Update
helpviewer_keywords:
- Update command [XMLA]
ms.assetid: 324dcc16-865d-4d0a-b393-2b06c18ac807
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b9663fa3d44b91f53ac20a5a1b1dba117f7a2574
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200132"
---
# <a name="update-element-xmla"></a>Update 要素 (XMLA)
  ディメンション内の属性メンバーを更新します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Update>  
      <Object>...</Object>  
      <MoveWithDescendants>...</MoveWithDescendants>  
      <Attributes>...</Attributes>  
      <Where>...</Where>  
   </Update>  
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
|子要素|[属性](../xml-elements-properties/attributes-element-xmla.md)、 [MoveWithDescendants](../xml-elements-properties/movewithdescendants-element-xmla.md)、[オブジェクト](../xml-elements-properties/object-element-dimension-xmla.md)、[場所](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 `Update` コマンドは、書き込み許可ディメンション内の属性メンバーを移動します。  
  
 メンバーの更新の詳細については、次を参照してください。[挿入、更新、および削除するメンバー &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Drop 要素&#40;XMLA&#41;](drop-element-xmla.md)   
 [要素を挿入&#40;XMLA&#41;](insert-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
