---
title: 先祖 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 464f8504850c6aa13f1cf040f9429be56f7181be
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739321"
---
# <a name="ancestor-mdx"></a>Ancestor (MDX)


  指定メンバーの先祖のうち、指定したレベル、またはメンバーから指定された距離だけ離れた位置にある先祖を返す関数です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *距離*  
 指定されたメンバーからの距離を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **先祖**関数、MDX メンバー式で、関数を提供し、提供するメンバーの先祖であるレベルの MDX 式または数値式をそのメンバー上のレベルの数を表すのいずれか。 この情報により、**先祖**関数は、そのレベルの先祖メンバーを返します。  
  
> [!NOTE]  
>  先祖メンバーだけではなく、先祖メンバーを含むセットを返すには使用、[先祖&#40;MDX&#41; ](../mdx/ancestors-mdx.md)関数。  
  
 レベル式が指定されている場合、**先祖**関数は、指定されたレベルで指定されたメンバーの先祖を返します。 指定したメンバーが指定されたレベルと同じ階層内でない場合、関数はエラーを返します。  
  
 距離が指定されている場合、**先祖**関数は、メンバー式で指定された階層内で指定されたステップ数は、指定されたメンバーの先祖を返します。 メンバーには、属性階層、ユーザー定義階層、または場合によっては親子階層のメンバーを指定できます。 数値として 1 が指定された場合はメンバーの親を返し、数値として 2 が指定された場合はメンバーの親より 1 つ上の先祖 (存在する場合) を返します。 数値として 0 が指定された場合はそのメンバー自体を返します。  
  
> [!NOTE]  
>  この形式の使用、**先祖**関数の場合、親のレベルが不明または名前を付けることはできません。  
  
## <a name="examples"></a>使用例  
 次の例では、レベル式を使用して、Australia の State-Province ごとの Internet Sales Amount と、Australia 全体における合計 Internet Sales Amount に対するその売上金額の割合を返しています。  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
   [Measures].[Internet Sales Amount],    
      Ancestor   
         (  
         [Customer].[Customer Geography].CurrentMember,  
            [Customer].[Customer Geography].[Country]  
         )  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
        [Customer].[Customer Geography].[Country].&[Australia],  
           [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、数値式を使用して、Australia の State-Province ごとの Internet Sales Amount と、すべての国の Internet Sales Amount の合計に対する割合をそれぞれ返します。  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
      [Measures].[Internet Sales Amount],  
         Ancestor   
            ([Customer].[Customer Geography].CurrentMember, 2)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
         [Customer].[Customer Geography].[Country].&[Australia],  
            [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
