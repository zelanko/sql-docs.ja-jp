---
title: BottomCount (MDX) |Microsoft ドキュメント
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
- BOTTOMCOUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomCount function
ms.assetid: 1441dab3-7885-4e92-9d48-21d832286677
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8e86dcb2428468e7f187638efa03252489974a08
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットを昇順に並べ替え、指定されたセット内の組を、値の小さい方から指定された数だけ返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、指定されたセットに対して評価した、指定された数値式の値に基づいて、セット内の組を昇順で並べ替えます。 **BottomCount**関数し、指定した数の最小値で組を返します。  
  
> [!IMPORTANT]  
>  **BottomCount**関数は、like、 [TopCount](../mdx/topcount-mdx.md)関数を常に階層を解除します。  
  
 数値式が指定されていない場合、関数のセットを返しますメンバー、自然な順序で、並べ替えを行わずと同様の動作、 [Tail (MDX)](../mdx/tail-mdx.md)関数。  
  
## <a name="example"></a>例  
 次の例では、Product SubCategory のメンバーを Reseller Sales Amount メジャーに基づいて並べ替え、売上金額が下から 5 番目までのメンバーについて、年度ごとの Reseller Order Quantity メジャーを返しています。  
  
```  
SELECT BottomCount([Product].[Product Categories].[Subcategory].Members  
   , 10  
   , [Measures].[Reseller Sales Amount]) ON 0,  
   [Date].[Calendar].[Calendar Year].Members ON 1  
  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Reseller Order Quantity]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
