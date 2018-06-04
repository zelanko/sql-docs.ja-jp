---
title: 集合関数の使用 |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a042092cfcddb985b29e7b0c98612f07c68ac2d0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582284"
---
# <a name="using-set-functions"></a>集合関数の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  集合関数は、ディメンション、階層、レベルからセットを取得します。あるいは、それらのオブジェクト内でのメンバーの絶対位置および相対位置をトラバースすることにより、さまざまな方法でセットを構築します。  
  
 集合関数は、メンバー関数や組関数と同様に、Analysis Services で使用される多次元構造を操作するために不可欠です。 さらに、セット式が多次元式 (MDX) クエリの軸を定義するため、集合関数は MDX クエリから結果を得るうえでも不可欠です。  
  
 最も一般的な集合関数の 1 つは、[Member&#40;セット&#41; &#40;MDX&#41; ](../mdx/members-set-mdx.md)関数で、すべてのディメンション、階層、またはレベルからメンバーを含むセットを取得します。 クエリ内でのこの関数の使用例を次に示します。  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns all of the members on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 一般的に使用される別の関数は、 [Crossjoin &#40;MDX&#41; ](../mdx/crossjoin-mdx.md)関数。 この関数は、パラメーターとして渡されるセットのデカルト積を表す組のセットを返します。 つまり、この関数を使用すると、クエリに "入れ子になった" 軸または "クロス集計された" 軸を作成できます。  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns a set containing every combination of all of the members`  
  
 `//on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension and all of the members on the Category level`  
  
 `//of the Category hierarchy on the Product dimension`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 [Descendants&#40;MDX&#41; ](../mdx/descendants-mdx.md)関数は似ています、**Child**機能しますより強力です。 この関数は、階層内の 1 つ以上のレベルにある任意のメンバーの子孫を返します。  
  
 SELECT  
  
 [Measures].[Internet Sales Amount]  
  
 ON Columns,  
  
 //Returns a set containing all of the Dates beneath Calendar Year  
  
 //2004 in the Calendar hierarchy of the Date dimension  
  
 DESCENDANTS(  
  
 [Date].[Calendar].[Calendar Year].&[2004]  
  
 , [Date].[Calendar].[Date])  
  
 ON Rows  
  
 FROM [Adventure Works]  
  
 [Order&#40;MDX&#41; ](../mdx/order-mdx.md)関数では、昇順または降順の特定の数値式に従って順序でセットの内容を注文することができます。 次のクエリでは、上記のクエリと同じ、行のメンバーを返しますが、ここでは Internet Sales Amount メジャーでこのメンバーを並べ替えます。  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//ordered by Internet Sales Amount`  
  
 `ORDER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount], BDESC)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 このクエリでは、集合関数 Descendants から返されたセットをパラメーターとして別の集合関数 Order に渡す方法も示しています。  
  
 特定の条件に従ってセットをフィルター選択非常に便利です、クエリを記述する場合は、この目的で使用することができます、[Filter &#40;MDX&#41; ](../mdx/filter-mdx.md)関数は、次の例で示すようにします。  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//where Internet Sales Amount is greater than $70000`  
  
 `FILTER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount]>70000)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 また、他の方法でセットにフィルターを適用できるようにする、さらに高度な関数もあります。 たとえば、次のクエリの表示、 [TopCount &#40;MDX&#41; ](../mdx/topcount-mdx.md)関数がセット内の最上位の n 個のアイテムを返します。  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing the top 10 Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension by Internet Sales Amount`  
  
 `TOPCOUNT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,10, [Measures].[Internet Sales Amount])`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 最後に、多数のなどの関数を使用して論理セットの操作を実行することは[Intersect &#40;MDX&#41;](../mdx/intersect-mdx.md)、[Union&#40;MDX&#41; ](../mdx/union-mdx.md)と[Except&#40;MDX&#41; ](../mdx/except-mdx-function.md)関数。 次のクエリでは、後者 2 つの関数の例を示します。  
  
 `SELECT`  
  
 `//Returns a set containing the Measures Internet Sales Amount, Internet Tax Amount and`  
  
 `//Internet Total Product Cost`  
  
 `UNION(`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}`  
  
 `, {[Measures].[Internet Total Product Cost]}`  
  
 `)`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//except the January 1st 2004`  
  
 `EXCEPT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,{[Date].[Calendar].[Date].&[915]})`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [関数&#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)   
 [メンバー関数の使用](../mdx/using-member-functions.md)   
 [組関数の使用](../mdx/using-tuple-functions.md)  
  
  
