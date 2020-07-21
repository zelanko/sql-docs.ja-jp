---
title: TopCount (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0f607f3111c150bff3d5dc562c77901a381bedc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036604"
---
# <a name="topcount-mdx"></a>TopCount (MDX)


  セットを降順で並べ替え、最大値を持つ指定した数の要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Count*  
 返す組の数を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 数値式を指定した場合、 **TopCount**関数は、指定されたセットに対して評価されるように、数値式で指定された値に基づいて、指定されたセットの組を降順で並べ替えます。 セットを並べ替えた後、 **TopCount**関数は、最大値を持つ指定された数の組を返します。  
  
> [!IMPORTANT]  
>  下位[カウント](../mdx/bottomcount-mdx.md)関数と同様に、 **TopCount**関数は常に階層を解除します。  
  
 数値式が指定されていない場合、関数は、並べ替えを行わずに、 [Head (MDX)](../mdx/head-mdx.md)関数のような自然な順序でメンバーのセットを返します。  
  
## <a name="examples"></a>使用例  
 次の例では、Internet Sales Amount によって上位10件の日付が返されます。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の例では、Bike カテゴリについて、Geography ディメンションの Geography 階層にある City レベルのメンバーのすべての組み合わせと Date ディメンションの Fiscal 階層のすべての会計年度を含んでいるセットを、Reseller Sales Amount メジャーで (最も売上が多いメンバーが 1 番目になるように) 並べ替えて、最初の 5 つのメンバーを返します。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
