---
title: MoveWithDescendants 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a61c8f56ae41d7fd1f58f394ea9adaca4a82ceb
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="movewithdescendants-element-xmla"></a>MoveWithDescendants 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
 メンバーの更新の詳細については、次を参照してください。[挿入、更新、および削除するメンバー &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
