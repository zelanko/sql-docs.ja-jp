---
title: Item (組) (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58cb48c467bbd3ca1c929da1fdff4881086d2e1d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740911"
---
# <a name="item-tuple-mdx"></a>Item (組) (MDX)


  セットから組を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *String_Expression1*  
 有効な文字列式です。通常は、1 つの文字列で 1 つの組を表現します。  
  
 *String_Expression2*  
 有効な文字列式です。通常は、1 つの文字列で 1 つの組を表現します。  
  
 *Index*  
 返すセット内の特定の組を位置で指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **項目**関数は、指定したセットから組を返します。 呼び出す 3 つの方法がある、**項目**関数。  
  
-   1 つの文字列式が指定されている場合、**項目**関数は、指定された組を返します。 たとえば、"([2005].Q3, [Store05])" のような指定です。  
  
-   1 つ以上の文字列式が指定されている場合、**項目**関数は、指定された座標によって定義される組を返します。 文字列の数は軸の数と一致している必要があり、各文字列で一意の階層を識別しなければなりません。 たとえば、"[2005].Q3", "[Store05]" のような指定です。  
  
-   整数が指定されている場合、**項目**関数によって指定された 0 から始まる位置にある組を返します*インデックス*です。  
  
## <a name="examples"></a>使用例  
 次の例では、([1996],Sales) が返されます。  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 次の例では、レベル式を使用して、Australia の State-Province ごとの Internet Sales Amount と、Australia 全体における合計 Internet Sales Amount に対するその売上金額の割合を返しています。 この例では、Item 関数を使用して、によって返されるセットから最初 (と組のみ) を抽出、**先祖**関数。  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
