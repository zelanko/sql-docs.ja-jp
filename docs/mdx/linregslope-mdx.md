---
title: LinRegSlope (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 108156c215840162bc93152db20a35f666c093bf
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579034"
---
# <a name="linregslope-mdx"></a>LinRegSlope (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットの線型回帰を計算し、回帰直線の傾きの値を返す y ax+b の a を = です。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinRegSlope(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 最小ニ乗法による線型回帰では、回帰直線 (点の連続に最も適合する直線) の式を計算します。 回帰直線では次の式では、ここは傾き、b は切片は。  
  
 y = ax+b  
  
 **LinRegSlope**関数は、y 軸の値を取得する最初の数値式に対して指定されたセットを評価します。 次に、2 番目の数値式が指定されている場合は、指定されているセット式をその数値式に対して評価し、X 軸の値を取得します。 2 番目の数値式が指定されていない場合、関数では、値として指定されたセット内のセルの現在のコンテキストを x 軸の使用します。 X 軸の引数を指定しない方法は、時間ディメンションでよく使用されます。   
  
 、点のセットを取得した後に、 **LinRegSlope**関数は、回帰直線の傾きを返します (、上記の式)。  
  
> [!NOTE]  
>  **LinRegSlope**関数は空のセルまたはテキストや論理値を含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="example"></a>例  
 次の例では、売上数量と店舗売上のメジャーに関する回帰直線の傾きを返しています。  
  
```  
LinRegSlope(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
