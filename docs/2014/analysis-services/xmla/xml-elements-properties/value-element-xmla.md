---
title: 値の要素 (XMLA) |Microsoft ドキュメント
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
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 7a422298e8d1b77f3d036b4cea5761dc6dc6dde4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071954"
---
# <a name="value-element-xmla"></a>Value 要素 (XMLA)
  目的の値が含まれています、[属性](attribute-element-xmla.md)で追加する要素、[挿入](../xml-elements-commands/insert-element-xmla.md)コマンド、または[セル](cell-element-xmla.md)要素で更新する、 [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)コマンド。  
  
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
|親要素|[属性](attribute-element-xmla.md)、[セル](cell-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Attribute` 要素の場合、`Value` 要素は、`Insert` コマンドがコミットされた後にメンバーが含む値としての目的の値を含みます。 メンバーの挿入の詳細については、次を参照してください。[挿入、更新、および削除するメンバー &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)です。  
  
 `Cell` 要素の場合、`Value` 要素は、`UpdateCells` コマンドがコミットされた後にセルが含む値としての目的の値を含みます。 そのセルの書き戻しテーブルに格納される実際の値は、セルの元の値と目的の値との差異です。  
  
 この要素が使用するデータ型は、更新対象のセルのデータ型と一致している必要があります。  
  
 セルの更新の詳細については、「[セルの更新 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CellOrdinal 要素&#40;XMLA&#41;](cellordinal-element-xmla.md)   
 [要素を挿入&#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [UpdateCells 要素&#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  