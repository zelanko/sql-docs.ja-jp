---
title: ディメンション式の使用 |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a5e26d56a52c8c922c43325bd2267fa623dc0e19
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743911"
---
# <a name="using-dimension-expressions"></a>ディメンション式の使用


  ディメンション式と階層式は通常、階層からメンバー、セット、または組を返すために多次元式 (MDX) 内で関数にパラメーターを渡す場合に使用します。  
  
 ディメンション式はオブジェクト識別子なので、単純式のみを指定できます。 参照してください[式&#40;MDX&#41; ](../mdx/expressions-mdx.md)単純式と複合式の説明。  
  
## <a name="dimension-expressions"></a>ディメンション式  
 ディメンション式には、ディメンション識別子またはディメンション関数のいずれかが含まれます。  
  
 ディメンション式は、ほとんど単独では使用しません。 代わりに、通常はディメンションの階層を指定します。 唯一の例外は、Measures ディメンションを操作している場合です。このディメンションには階層がありません。  
  
 次の例では、式 [Measures] を .Members 関数および Count() 関数と共に使用して Measures ディメンションのメンバー数を返す、計算されるメンバーを示しています。  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 ディメンションの識別子は*Dimension_Name* MDX ステートメントの記述に使用される BNF 表記でします。  
  
## <a name="hierarchy-expressions"></a>階層式  
 階層式にも同様に、階層識別子または階層関数のいずれかが含まれます。 次の例では、階層式 [Date].[Calendar] を .Levels 関数および .Count 関数と共に使用して、Date ディメンションの Calendar 階層のレベル数を返す方法を示しています。  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 階層式を使用する最も一般的なシナリオでは、.Members 関数と組み合わせて階層のすべてのメンバーを返します。 次の例では、行軸の [Date].[Calendar] のすべてのメンバーを返します。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 階層識別子は*Dimension_Name **.** Hierarchy_Name* MDX ステートメントの記述に使用される BNF 表記でします。  
  
## <a name="see-also"></a>参照  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
