---
title: BottomSum (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- BOTTOMSUM
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomSum function
ms.assetid: b3b10e68-2a36-4c38-85f4-3bb7917d5ae8
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f2080c608bc80f9d86f9b74e3ba2deebff8f837d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
