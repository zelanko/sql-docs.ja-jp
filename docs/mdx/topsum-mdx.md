---
title: TopSum (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 853390f99f02352fd7814fcec208bba1508c03a7
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743411"
---
# <a name="topsum-mdx"></a>TopSum (MDX)


  セットを並べ替え、累積合計が指定された値以上になる最上位の要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Value*  
 各組の比較の基準値を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、メジャーを返す多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **TopSum**関数セットを降順で並べ替え、指定されたセットに対して評価される指定メジャーの合計を計算します。 次に、値の大きい方から、指定した数値式の合計が指定値以上になるように要素のセットを作成して返します。 この関数は、累積合計が指定値以上になるセットの最小サブセットを返します。 要素は大きい方から順に返されます。  
  
> [!IMPORTANT]  
>  同様に、 [BottomSum](../mdx/bottomsum-mdx.md) 、関数、 **TopSum**関数が常に階層を解除します。  
  
## <a name="example"></a>例  
 次の例では、Bike カテゴリについて、Reseller Sales Amount メジャーを使用した累積合計が 6,000,000 以上になる、Geography ディメンションの Geography 階層にある City レベルの最小のメンバーのセットを返します (最も売り上げが多いメンバーを 1 番目に返します)。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
