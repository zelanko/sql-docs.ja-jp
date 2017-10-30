---
title: "相関関係 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CORRELATION
dev_langs:
- kbMDX
helpviewer_keywords:
- Correlation function
ms.assetid: 9b3662c9-95a1-4644-b952-9460fe0cf160
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 00f2e3380c1706805e111edbc24423ae49e3ab97
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="correlation-mdx"></a>Correlation (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>解説  
 **相関**関数は、最初に、y 軸の値を取得する最初の数値式に対して指定されたセットを評価することによって 2 組の値の相関係数を計算します。 次に、2 番目の数値式が指定されている場合は、指定されたセットをその式に対して評価し、X 軸の値のセットを取得します。 2 番目の数値式が指定されていない場合、関数では、値として指定されたセット内のセルの現在のコンテキストを x 軸の使用します。  
  
> [!NOTE]  
>  **相関**関数は空のセルまたはテキストや論理値を含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

