---
title: 中央値 (MDX) |Microsoft ドキュメント
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
- MEDIAN
dev_langs:
- kbMDX
helpviewer_keywords:
- Median function
ms.assetid: 7a326a3f-0123-45c4-9b18-31f83b90d986
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3cfa0b03deae60d9354e2e7056e0725125355ff4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="median-mdx"></a>Median (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットに対して評価される数値式の中央値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Median(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式を指定した場合、この数値式がセットに対して評価されてから、その評価で得られる中央値が返されます。 数値式を指定しなかった場合、指定したセットがそのセットのメンバーの現在のコンテキストで評価されてから、その評価で得られる中央値が返されます。  
  
 中央値とは、順番に並べられた数値のセットの中央に位置する値です  (セット内の数値の合計を、セット内にある数値の数で除算する平均値とは異なります)。 中央値は、セット内の値の少なくとも半数が、その値以下になるような最小の値を選択することによって決まります。 セット内の値の数が奇数の場合、中央値は 1 つの値になります。 セット内の値の数が偶数の場合は、中央に位置する 2 つの値の合計を 2 で除算した値が返されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、数値セットの中央値が計算される際、NULL 値は無視されます。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブ内の四半期、サブカテゴリ、および国ごとの毎月の売上高の中央値を返します。  
  
```  
WITH MEMBER Measures.x AS Median   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
