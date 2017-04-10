---
title: "クエリ軸とスライサー軸を使用する簡単な例 (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スライサー軸"
  - "クエリ軸 [MDX]"
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# クエリ軸とスライサー軸を使用する簡単な例 (MDX)
  このトピックでは、簡単な例を使って、クエリ軸とスライサー軸の基本的な指定方法および使用方法を示します。  
  
## キューブ  
 Route と Time という 2 つの単純なディメンションを持つ TestCube という名前のキューブがあるとします。 各ディメンションには、それぞれ Route および Time という名前のユーザー階層が 1 つずつあります。 キューブのメジャーは Measures ディメンションの一部なので、このキューブには全部で 3 つのディメンションがあります。  
  
## クエリ  
 クエリでは、Packages メジャーを各 Route や Time と比較できるマトリックスが用意されます。  
  
 以下の MDX クエリの例では、Route および Time 階層がクエリ軸で、Measures ディメンションがスライサー軸です。 [Members](../../../mdx/members-set-mdx.md) 関数は、MDX が階層またはレベルのメンバーを使ってセットを構築することを示します。 **Members** 関数を使用する場合、特定の階層またはレベルの各メンバーを MDX クエリ内で明示的に記述する必要はありません。  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## 結果  
 結果は、COLUMNS 軸ディメンションと ROWS 軸ディメンションの各交差部分に Packages メジャーの値を表示するグリッドになります。 このグリッドは、以下の表のようになります。  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## 参照  
 [クエリ軸の内容の指定 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md)   
 [スライサー軸の内容の指定 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-slicer-axis-mdx.md)  
  
  