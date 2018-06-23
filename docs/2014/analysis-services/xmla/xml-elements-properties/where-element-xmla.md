---
title: 場所要素 (XMLA) |Microsoft ドキュメント
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
- Where Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Where
- microsoft.xml.analysis.where
- http://schemas.microsoft.com/analysisservices/2003/engine#Where
helpviewer_keywords:
- Where element
ms.assetid: 81fb4190-3379-4ddf-8795-a0772f3b92bb
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4e63d2ecd6f20d374c6746c7d3bc77ad455f1ef6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178745"
---
# <a name="where-element-xmla"></a>Where 要素 (XMLA)
  親コマンド [Drop](../xml-elements-commands/drop-element-xmla.md) または [Update](../xml-elements-commands/update-element-xmla.md) で使用されるフィルター条件を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Drop> <!-- or Update -->  
   ...  
   <Where>  
      <Attributes>...</Attributes>  
   </Where>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Drop](../xml-elements-commands/drop-element-xmla.md)、 [Update](../xml-elements-commands/update-element-xmla.md)|  
|子要素|[Attributes](attributes-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Drop`コマンド、`Where`と組み合わせて、要素、 [DeleteWithDescendants](deletewithdescendants-element-xmla.md)要素を削除する属性メンバーのスコープを識別します。  
  
 `Update` コマンドの場合、`Where` 要素は更新対象の属性メンバーのスコープを識別します。 複数の属性メンバーを更新するには、親コマンド `Attributes` の `Update` コレクション内と、`Attributes` 要素の `Where` コレクション内で、属性の組み合わせを指定します。  
  
 属性メンバーの削除と更新の詳細については、「[メンバーの挿入、更新、および削除 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  