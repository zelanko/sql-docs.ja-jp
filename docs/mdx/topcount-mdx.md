---
title: TopCount (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fa8edcf8af510a41affdcbcc9924edf69cf4c220
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743221"
---
# <a name="topcount-mdx"></a>TopCount (MDX)


  セットを降順に並べ替え、値の大きい方から指定された数の要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 数値式が指定されている場合、 **TopCount**関数、順序、指定されたセットに対して評価された数値式で指定された値に従って、指定されたセットで指定されたセット内の組を降順で並べ替えます。 セットの並べ替えの後に、 **TopCount**関数では、指定した数の組の最も大きい値を返します。  
  
> [!IMPORTANT]  
>  同様に、 [BottomCount](../mdx/bottomcount-mdx.md) 、関数、 **TopCount**関数が常に階層を解除します。  
  
 数値式が指定されていない場合、関数のセットを返しますメンバー、自然な順序で、並べ替えを行わずと同様の動作、 [Head (MDX)](../mdx/head-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次の例では、Internet Sales Amount の上位 10 日を返します。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
