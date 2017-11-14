---
title: "値の要素 (XMLA) |Microsoft ドキュメント"
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
- Value Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61a5fa276918a176eb60340fce44e5dfdae0d4da
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-xmla"></a>Value 要素 (XMLA)
  目的の値が含まれています、[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)で追加する要素、[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)コマンド、または[セル](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)要素で更新する、 [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Any|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)、[セル](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **属性**、要素、**値**要素には、後に、メンバーが含む目的の値が含まれています、**挿入**コマンドがコミットされました。 メンバーの挿入の詳細については、次を参照してください。[挿入、更新、およびメンバーの削除 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 **セル**、要素、**値**要素には、後に、セルが含む目的の値が含まれています、 **UpdateCells**コマンドがコミットされました。 そのセルの書き戻しテーブルに格納される実際の値は、セルの元の値と目的の値との差異です。  
  
 この要素が使用するデータ型は、更新対象のセルのデータ型と一致している必要があります。  
  
 セルの更新の詳細については、「[セルの更新 &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CellOrdinal 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [要素 &#40; を挿入します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [UpdateCells 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

