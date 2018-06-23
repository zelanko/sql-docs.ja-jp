---
title: セルの要素 (XMLA) |Microsoft ドキュメント
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
- Cell Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: 88daba54-89e9-423f-8d12-8de80cf52d6b
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: be00f4ae61817143cc986e69d543eaf4201bbe87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165092"
---
# <a name="cell-element-xmla"></a>Cell 要素 (XMLA)
  [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md) コマンドによって更新されるセルについての情報を含みます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<UpdateCells>  
   ...  
   <Cell CellOrdinal="Long">  
      <Value>...</Value>  
   </Cell>  
   ...  
</UpdateCells>  
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
|親要素|[UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)|  
|子要素|[Value](value-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|CellOrdinal|必要な`Long`属性。 更新するセルの位置を示す 0 から始まる序数を含みます。|  
  
## <a name="remarks"></a>コメント  
 セルの更新の詳細については、「[セルの更新 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  