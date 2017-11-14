---
title: "DeleteWithDescendants 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DeleteWithDescendants Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d0a75a3cb5de9aba6cd6aeccd90d8342442847c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deletewithdescendants-element-xmla"></a>DeleteWithDescendants 要素 (XMLA)
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
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

