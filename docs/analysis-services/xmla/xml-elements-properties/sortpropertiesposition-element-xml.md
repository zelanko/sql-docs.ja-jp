---
title: "SortPropertiesPosition 要素 (XML) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 68b040a7-ab16-46f5-8610-21db07df9181
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b4579aa9873c23ad3490763ce5c5900dcc8158aa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sortpropertiesposition-element-xml"></a>SortPropertiesPosition 要素 (XML)
  要素のコレクション内での要素の位置についての情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|-1|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **RelationshipEndVisualizationProperties** 、要素、 **SortPropertiesPosition**要素には詳細のコレクション内の並べ替えプロパティ要素の位置が含まれています。 既定値は、使用する並べ替えプロパティがないことを示します。  
  
  

