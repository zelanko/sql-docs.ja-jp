---
title: ParallelPeriod (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c1f495ce1fad9a318ea5e6c1f3fadd88f8313cd6
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742371"
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (MDX)


  前の期間から、指定されたメンバーと同じ相対位置にあるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 さかのぼる並列期間の数を指定する有効な数値式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 似ていますが、 [Cousin](../mdx/cousin-mdx.md) 、関数、 **ParallelPeriod**関数はタイム シリーズをより密接に関連します。 **ParallelPeriod**関数が指定されたレベルで指定されたメンバーの先祖を受け取り、指定した間隔、先祖の兄弟を検索および最後に、兄弟の子孫のうち、指定されたメンバーの並列期間を返します。  
  
 **ParallelPeriod**関数には、次の既定値。  
  
-   既定のメンバー値の型を持つ最初のディメンションの最初の階層の現在のメンバーは、レベル式もメンバー式が指定されている場合*時間*メジャー グループにします。  
  
-   既定のメンバー値は、レベル式を指定すると、メンバー式が指定されていない場合、 *Level_Expression*.**Hierarchy.CurrentMember**です。  
  
-   既定のインデックス値は 1 です。  
  
-   既定のレベルは、指定されたメンバーの親のレベルです。  
  
 **ParallelPeriod**関数は、次の MDX ステートメントに相当します。  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>例  
 次の例では、Quarter レベルを基準として、2003 年 10 月から 3 期間さかのぼった並列期間を返します。つまり、2003 年 1 月が返されます。  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 次の例では、Semester  レベルを基準として、2003 年 10 月から 3 期間さかのぼった並列期間を返します。つまり、2002 年 4 月が返されます。  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
