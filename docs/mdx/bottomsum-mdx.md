---
title: "BottomSum (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: BOTTOMSUM
dev_langs: kbMDX
helpviewer_keywords: BottomSum function
ms.assetid: b3b10e68-2a36-4c38-85f4-3bb7917d5ae8
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e7175a655406dd27f11c2594ad53dfc233a6c1a9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたセットを昇順で並べ替え、合計が指定された値以下になるように、値の小さい方から組のセットを作成して返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *値*  
 各組の比較の基準値を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
