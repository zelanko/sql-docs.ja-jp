---
title: SetToArray (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e545cb4b41f1a0d60e471c15753a82079978ee5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149297"
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)


  1 つまたは複数のセットをユーザー定義関数で使用する配列に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式は、通常、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **SetToArray**関数は、1 つまたは複数のセットをユーザー定義関数で使用する配列に変換します。 結果の配列内のディメンションの数は、指定されたセットの数と同一になります。  
  
 省略可能な数値式には、配列のセルに値を指定できます。 数値式が指定されていない場合は、現在のコンテキストでセットのクロス結合が評価されます。  
  
 この結果作成される配列では、セルの座標がセットの並び順に対応します。 たとえば、`SA`、`SB`、`SC` という 3 つのセットがあるとします。 それぞれのセットには 2 つの要素があります。 MDX ステートメントで`SetToArray(SA, SB, SC)`、次の 3 次元の配列を作成します。  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  戻り値の型、 **SetToArray**関数は、VARIANT 型の vt_array です。 そのための出力、 **SetToArray**関数は、ユーザー定義関数への入力としてのみ使用する必要があります。  
  
## <a name="example"></a>例  
 次の例では、配列を返します。  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
