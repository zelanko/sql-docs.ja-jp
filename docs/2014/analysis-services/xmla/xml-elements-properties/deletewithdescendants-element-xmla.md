---
title: DeleteWithDescendants 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DeleteWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93a6d92e675e0ae016327e064fabb6ec2c012aac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199942"
---
# <a name="deletewithdescendants-element-xmla"></a>DeleteWithDescendants 要素 (XMLA)
  属性メンバーの子孫が親によっても削除するかどうかを示す[ドロップ](../xml-elements-commands/drop-element-xmla.md)コマンド。  
  
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
|親要素|[ドロップ](../xml-elements-commands/drop-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DeleteWithDescendants`要素を決定かどうか、`Drop`コマンドによって識別される属性メンバーを削除する必要があります、[場所](where-element-xmla.md)要素もそれらの属性メンバーの子孫がも削除されます。  
  
> [!NOTE]  
>  この要素は、親子階層内の属性メンバーにのみ適用されます。  
  
 属性メンバーの削除と更新の詳細については、「[メンバーの挿入、更新、および削除 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
