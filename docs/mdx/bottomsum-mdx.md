---
title: BottomSum (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f923761144389a97962f7269cc5164d0dbdbf51
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739611"
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)


  指定されたセットを昇順で並べ替え、合計が指定された値以下になるように、値の小さい方から組のセットを作成して返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Value*  
 各組の比較の基準値を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **BottomSum**関数セットを昇順で並べ替え、指定されたセットに対して評価される指定メジャーの合計を計算します。 次に、値の小さい方から、指定された数値式の合計が指定値以上になるように要素のセットを作成して返します。 この関数は、累積合計が指定値以上になるセットの最小サブセットを返します。 要素は小さい方から順に返されます。  
  
> [!IMPORTANT]  
>  **BottomSum**関数は、like、 [TopSum](../mdx/topsum-mdx.md)関数を常に階層を解除します。  
  
## <a name="examples"></a>使用例  
 次の例では、Bike カテゴリについて、Reseller Sales Amount メジャーを使用して累積合計が 50,000 以上になるような、2003 会計年度の Geography ディメンションの Geography 階層にある City レベルの最小のメンバーのセットを返します (最も売上が少ないメンバーを 1 番目に返します)。  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
