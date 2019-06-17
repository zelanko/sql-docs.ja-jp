---
title: 先祖 (MDX) |Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298498"
---
# <a name="ancestor-mdx"></a>先祖 (MDX)


  メンバーから指定したレベルまたは指定された距離にある指定したメンバーの先祖を返す関数。  
  
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
 レベルを返す有効な多次元式 (MDX) 式。  
  
 *距離*  
 指定されたメンバーからの距離を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **先祖**関数の場合、関数、MDX メンバー式を提供して指定メンバーの先祖であるレベルの MDX 式または数値式の上位のレベル数を表すそのメンバーです。 この情報により、**先祖**関数は、そのレベルの先祖メンバーを返します。  
  
> [!NOTE]  
>  先祖メンバーだけではなく、先祖メンバーを含むセットを返すを使用して、[先祖&#40;MDX&#41; ](../mdx/ancestors-mdx.md)関数。  
  
 レベル式が指定されている場合、**先祖**関数は、指定されたレベルで指定されたメンバーの先祖を返します。 指定されたレベルと同じ階層内で指定されたメンバーでない場合、関数はエラーを返します。  
  
 距離が指定されている場合、**先祖**関数は、メンバー式で指定された階層内で指定されたステップ数は、指定されたメンバーの先祖を返します。 メンバーには、属性階層、ユーザー定義階層、または場合によっては親子階層のメンバーを指定できます。 番号 1 は、メンバーの親を返し、数値として 2 が (存在する場合、メンバーの親の親を返します。 数値として 0 が指定された場合はそのメンバー自体を返します。  
  
> [!NOTE]  
>  この形式の使用、**先祖**関数の場合、親のレベルが不明またはということはできません。  
  
## <a name="examples"></a>使用例  
 次の例では、レベル式を使用し、オーストラリアとその % オーストラリア合計 Internet Sales Amount の State-province ごとの Internet Sales Amount を返します。  
  
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
  
 次の例では、数値式を使用し、オーストラリアとその %、合計の Internet Sales Amount のすべての国の State-province ごとの Internet Sales Amount を返します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
