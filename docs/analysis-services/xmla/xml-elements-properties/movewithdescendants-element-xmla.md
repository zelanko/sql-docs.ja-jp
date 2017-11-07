---
title: "MoveWithDescendants 要素 (XMLA) |Microsoft ドキュメント"
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
- MoveWithDescendants Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.movewithdescendants
- http://schemas.microsoft.com/analysisservices/2003/engine#MoveWithDescendants
- urn:schemas-microsoft-com:xml-analysis#MoveWithDescendants
helpviewer_keywords:
- MoveWithDescendants element
ms.assetid: d02285b6-1801-4da9-8e2b-9ab008e25558
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdbacbaa6de4d175d5a1c0223a12a89911ba557a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="movewithdescendants-element-xmla"></a>MoveWithDescendants 要素 (XMLA)
  属性メンバーの子孫が親によっても更新するかどうかを示す[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)コマンド。  
  
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
|親要素|[Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **MoveWithDescendants**要素を決定するかどうか、**更新**コマンドによって識別される属性メンバーをだけ更新する必要がありますいない、[属性](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)要素が、同様に更新するそれらの属性メンバーの子孫であります。  
  
> [!NOTE]  
>  この要素は、親子階層内の属性メンバーにのみ適用されます。  
  
 メンバーの更新の詳細については、次を参照してください。[挿入、更新、およびメンバーの削除 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

