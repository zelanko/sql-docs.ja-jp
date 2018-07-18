---
title: MoveWithDescendants 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MoveWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.movewithdescendants
- http://schemas.microsoft.com/analysisservices/2003/engine#MoveWithDescendants
- urn:schemas-microsoft-com:xml-analysis#MoveWithDescendants
helpviewer_keywords:
- MoveWithDescendants element
ms.assetid: d02285b6-1801-4da9-8e2b-9ab008e25558
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b75fffd4d923b7593f403ae2268b980a5ab6de6f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332572"
---
# <a name="movewithdescendants-element-xmla"></a>MoveWithDescendants 要素 (XMLA)
  属性メンバーの子孫が親によっても更新するかどうかを示します[Update](../xml-elements-commands/update-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Update](../xml-elements-commands/update-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `MoveWithDescendants`要素を決定するかどうか、`Update`コマンドによって識別される属性メンバーをのみ更新する必要がありますできません、[属性](attributes-element-xmla.md)要素もするそれらの属性メンバーの子孫の場合は同様に更新します。  
  
> [!NOTE]  
>  この要素は、親子階層内の属性メンバーにのみ適用されます。  
  
 メンバーの更新の詳細については、次を参照してください。[挿入、更新、および削除するメンバー &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
