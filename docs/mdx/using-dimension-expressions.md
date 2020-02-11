---
title: ディメンション式の使用 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0373bbda2d0c97946f15e048b7cc49175ca66669
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097173"
---
# <a name="using-dimension-expressions"></a>ディメンション式の使用


  多次元式 (MDX) の関数にパラメーターを渡して、階層からメンバー、セット、または組を返す場合は、通常、ディメンション式と階層式を使用します。  
  
 ディメンション式は、オブジェクト識別子であるため、単純式だけにすることができます。 単純式と複合式の説明については、「 [MDX&#41;&#40;式](../mdx/expressions-mdx.md)」を参照してください。  
  
## <a name="dimension-expressions"></a>ディメンション式  
 ディメンション式には、ディメンション識別子またはディメンション関数のいずれかが含まれます。  
  
 ディメンション式は、実際にはほとんど使用されません。 代わりに、通常はディメンションの階層を指定します。 唯一の例外は、Measures ディメンションを操作している場合です。このディメンションには階層がありません。  
  
 次の例では、式 [Measures] を .Members 関数および Count() 関数と共に使用して Measures ディメンションのメンバー数を返す、計算されるメンバーを示しています。  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 ディメンション識別子は、MDX ステートメントの記述に使用される BNF 表記で*Dimension_Name*として表示されます。  
  
## <a name="hierarchy-expressions"></a>階層式  
 階層式にも同様に、階層識別子または階層関数のいずれかが含まれます。 次の例では、階層式 [Date].[Calendar] を .Levels 関数および .Count 関数と共に使用して、Date ディメンションの Calendar 階層のレベル数を返す方法を示しています。  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 階層式を使用する最も一般的なシナリオでは、.Members 関数と組み合わせて階層のすべてのメンバーを返します。 次の例では、[Date] のすべてのメンバーを返します。Rows 軸の [Calendar]:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 階層識別子は Dimension_Name として表示されます。 MDX ステートメントの記述に使用される BNF 表記法で*Hierarchy_Name ます。*  
  
## <a name="see-also"></a>参照  
 [MDX &#40;式&#41;](../mdx/expressions-mdx.md)  
  
  
