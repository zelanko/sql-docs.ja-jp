---
title: DeleteWithDescendants 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 16731018ec2f8414f2431ff4a3c04f4f554ff592
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="deletewithdescendants-element-xmla"></a>DeleteWithDescendants 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  属性メンバーの子孫が親によっても削除するかどうかを示す[ドロップ](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
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
|親要素|[ドロップ](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DeleteWithDescendants**要素を決定するかどうか、**ドロップ**コマンドによって識別される属性メンバーを削除する必要があります、[場所](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)要素も、それらの属性メンバーの子孫も削除されます。  
  
> [!NOTE]  
>  この要素は、親子階層内の属性メンバーにのみ適用されます。  
  
 属性メンバーの削除と更新の詳細については、「[メンバーの挿入、更新、および削除 &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
