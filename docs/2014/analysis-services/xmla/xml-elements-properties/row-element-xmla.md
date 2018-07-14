---
title: row 要素 (XMLA) |Microsoft Docs
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
- row Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords:
- row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17bc202bb7e1d2c0701b478409b02f4bbb160958
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223992"
---
# <a name="row-element-xmla"></a>row 要素 (XMLA)
  データの 1 つの行が含まれています、[ルート](root-element-xmla.md)によって返される表形式のデータを含む要素、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッドの呼び出し。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
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
|親要素|[ルート](root-element-xmla.md)(を使用して、[行セット](../xml-data-types/rowset-data-type-xmla.md)データ型)|  
|子要素|1 つ以上の列要素|  
  
## <a name="remarks"></a>コメント  
 表形式データを含む `root` 要素によって返される各行ごとに、対応する `row` 要素が存在します。 `root` 要素内のそれぞれの列は、個別の XML 要素によって表されます。 `row` 要素の列の値は XML 要素に含まれるデータで、列の名前は XML 要素の名前に対応します。  
  
 行の中の列に NULL 値を指定する方法は、次の 2 つです。  
  
-   列要素が欠落している場合、その列が NULL であることを暗黙に意味します。  
  
-   列要素で `xsi:nil='true'` 属性を使用することにより、その列が NULL 値を持つことを示せます。  
  
 たとえば、ある行に Store_Name という単一の列が含まれ、その値が NULL の場合、以下のいずれかの方法で表せます。  
  
```  
<row>  
</row>  
```  
  
 または。  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 列要素にエラーが含まれる場合、次の例のように、エラーに関する情報が `Error` 要素によって提供されます。  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 詳細とスキーマについては、表形式のデータの列の名前付けについては、次を参照してください。[行セットのデータ型&#40;XMLA&#41;](../xml-data-types/rowset-data-type-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
