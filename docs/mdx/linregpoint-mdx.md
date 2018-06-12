---
title: LinRegPoint (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cc47b5910f0d5323b1b7e29cd3313b36d615265c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741131"
---
# <a name="linregpoint-mdx"></a>LinRegPoint (MDX)


  セットの線形回帰を計算しの値を返します、 *y 切片*回帰直線 y = ax+b x の特定の値。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Slice_Expression_x*  
 有効な数値式です。通常は、スライサー軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 最小ニ乗法による線型回帰では、回帰直線 (点の連続に最も適合する直線) の式を計算します。 回帰直線では次の式では、ここは傾き、b は切片は。  
  
 y = ax+b  
  
 **LinRegPoint**関数は、y 軸の値を取得する 2 番目の数値式に対して指定されたセットを評価します。 次に、3 番目の数値式が指定されている場合は、指定されているセットをその式に対して評価し、X 軸の値を取得します。 3 番目の数値式が指定されていない場合は、指定されたセット内のセルの現在のコンテキストを X 軸の値として使用します。 X 軸の引数を指定しない方法は、時間ディメンションでよく使用されます。   
  
 線型回帰直線が計算された後、1 番目の数値式に対して回帰直線式の値が計算され、返されます。  
  
> [!NOTE]  
>  **LinRegPoint**関数は空のセルまたはテキストを含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="example"></a>例  
 次の例では、売上数量と店舗売上の統計的関係に基づいて、過去 10 期間の予測売上数量を返しています。  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
