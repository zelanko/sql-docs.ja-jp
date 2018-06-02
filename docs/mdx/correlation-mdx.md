---
title: 相関関係 (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e4b53ff01dc6cf0d62b334e95ac8a474f969f5f9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577454"
---
# <a name="correlation-mdx"></a>Correlation (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットに対して評価される X と Y の値の組の相関係数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Correlation( Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **相関**関数は、最初に、y 軸の値を取得する最初の数値式に対して指定されたセットを評価することによって 2 組の値の相関係数を計算します。 次に、2 番目の数値式が指定されている場合は、指定されたセットをその式に対して評価し、X 軸の値のセットを取得します。 2 番目の数値式が指定されていない場合、関数では、値として指定されたセット内のセルの現在のコンテキストを x 軸の使用します。  
  
> [!NOTE]  
>  **相関**関数は空のセルまたはテキストや論理値を含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
