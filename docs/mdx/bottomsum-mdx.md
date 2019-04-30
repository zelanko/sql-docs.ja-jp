---
title: BottomSum (MDX) |Microsoft Docs
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63306718"
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)


  指定したセットを昇順で並べ替え、最も低い値の合計が同じか、または指定した値よりも小さい組のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *[値]*  
 各組の比較対象となる値を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式は、通常、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **BottomSum**関数セットを昇順を並べ替え、指定されたセットに対して評価される指定メジャーの合計を計算します。 関数は、指定された数値式の合計は、(sum) の指定した値では少なくとも最小値を持つ要素を返します。 この関数は、累積合計が指定値以上になるセットの最小サブセットを返します。 返される要素は小さい方から順します。  
  
> [!IMPORTANT]  
>  **BottomSum**関数は、このような[TopSum](../mdx/topsum-mdx.md)関数を常に階層を解除します。  
  
## <a name="examples"></a>使用例  
 次の例を返します、Bike カテゴリについて、最小設定市区町村のメンバーの Geography ディメンションの Geography 階層のレベル、2003 会計年度のされ、Reseller Sales Amount メジャーを使用して、累積合計が、少なくともの合計50,000 (販売数の最小セットのメンバーで始まる)。  
  
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
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
