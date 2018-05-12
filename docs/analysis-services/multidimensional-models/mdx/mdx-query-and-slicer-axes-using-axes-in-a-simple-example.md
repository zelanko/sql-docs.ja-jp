---
title: クエリ軸とスライサー軸を使用して、簡単な例 (MDX) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fce95d7e51c17f6e8a0fedbec01eccf7bd8ec8c4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-query-and-slicer-axes---using-axes-in-a-simple-example"></a>MDX クエリ軸とスライサー軸 - 軸を使用して簡単な例
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  このトピックでは、簡単な例を使って、クエリ軸とスライサー軸の基本的な指定方法および使用方法を示します。  
  
## <a name="the-cube"></a>キューブ  
 Route と Time という 2 つの単純なディメンションを持つ TestCube という名前のキューブがあるとします。 各ディメンションには、それぞれ Route および Time という名前のユーザー階層が 1 つずつあります。 キューブのメジャーは Measures ディメンションの一部なので、このキューブには全部で 3 つのディメンションがあります。  
  
## <a name="the-query"></a>クエリ  
 クエリでは、Packages メジャーを各 Route や Time と比較できるマトリックスが用意されます。  
  
 以下の MDX クエリの例では、Route および Time 階層がクエリ軸で、Measures ディメンションがスライサー軸です。 [Members](../../../mdx/members-set-mdx.md) 関数は、MDX が階層またはレベルのメンバーを使ってセットを構築することを示します。 **Members** 関数を使用する場合、特定の階層またはレベルの各メンバーを MDX クエリ内で明示的に記述する必要はありません。  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>結果  
 結果は、COLUMNS 軸ディメンションと ROWS 軸ディメンションの各交差部分に Packages メジャーの値を表示するグリッドになります。 このグリッドは、以下の表のようになります。  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## <a name="see-also"></a>参照  
 [クエリ軸 & #40; の内容の指定MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [スライサー軸 & #40; の内容の指定MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
