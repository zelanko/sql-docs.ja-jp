---
title: BottomCount (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 424c928f64b784070520f4cebe450dd5465fea41
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739781"
---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)


  セットを昇順に並べ替え、指定されたセット内の組を、値の小さい方から指定された数だけ返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 数値式が指定されている場合、指定されたセットに対して評価した、指定された数値式の値に基づいて、セット内の組を昇順で並べ替えます。 **BottomCount**関数し、指定した数の最小値で組を返します。  
  
> [!IMPORTANT]  
>  **BottomCount**関数は、like、 [TopCount](../mdx/topcount-mdx.md)関数を常に階層を解除します。  
  
 数値式が指定されていない場合、関数のセットを返しますメンバー、自然な順序で、並べ替えを行わずと同様の動作、 [Tail (MDX)](../mdx/tail-mdx.md)関数。  
  
## <a name="example"></a>例  
 次の例では、Product SubCategory のメンバーを Reseller Sales Amount メジャーに基づいて並べ替え、売上金額が下から 5 番目までのメンバーについて、年度ごとの Reseller Order Quantity メジャーを返しています。  
  
```  
SELECT BottomCount([Product].[Product Categories].[Subcategory].Members  
   , 10  
   , [Measures].[Reseller Sales Amount]) ON 0,  
   [Date].[Calendar].[Calendar Year].Members ON 1  
  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Reseller Order Quantity]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
