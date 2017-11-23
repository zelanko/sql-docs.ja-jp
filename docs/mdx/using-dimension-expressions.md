---
title: "ディメンション式の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], dimensions
- dimensions [Analysis Services], MDX
ms.assetid: 1d40cffb-e88f-4284-93cf-d62ab4f08395
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c48cf34963f4fb496537cf1573cd4974949a672e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-dimension-expressions"></a>ディメンション式の使用
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  ディメンション式と階層式は通常、階層からメンバー、セット、または組を返すために多次元式 (MDX) 内で関数にパラメーターを渡す場合に使用します。  
  
 ディメンション式はオブジェクト識別子なので、単純式のみを指定できます。 参照してください[式 &#40;です。MDX と #41 です。](../mdx/expressions-mdx.md)単純式と複合式の説明。  
  
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
  
 階層識別子は*Dimension_Name**.**Hierarchy_Name* MDX ステートメントの記述に使用される BNF 表記でします。  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。MDX と #41 です。](../mdx/expressions-mdx.md)  
  
  
