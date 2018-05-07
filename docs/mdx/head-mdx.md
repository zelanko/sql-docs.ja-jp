---
title: Head (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- HEAD
dev_langs:
- kbMDX
helpviewer_keywords:
- Head function
ms.assetid: 2a909bda-1366-4537-93b0-c089554fc11f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b0e25718c55dbe433bd34438b459aed31b2097f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="head-mdx"></a>Head (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットの先頭から、指定された数の要素を返します (重複要素も保持します)。  
  
## <a name="syntax"></a>構文  
  
```  
  
Head(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Count*  
 返す組の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 **ヘッド**関数は、指定されたセットの先頭から指定数の組を返します。 要素の順序は保持されます。 Count の既定値は 1 です。 指定した数の組が 1 より小さい場合、**ヘッド**関数は、空のセットを返します。 指定された組数がセット内の組数を超える場合は、元のセットを返します。  
  
## <a name="example"></a>例  
 次の例では、階層とは無関係に、Reseller Gross Profit に基づいて、売上が上位 5 番目までの製品のサブカテゴリを返します。 **ヘッド**関数を使用してを使用して結果を並べ替えてから、結果の最初の 5 つのセットのみを返す、**順序**関数。  
  
```  
SELECT   
[Measures].[Reseller Gross Profit] ON 0,  
Head  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,5  
   ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [末尾&#40;MDX&#41;](../mdx/tail-mdx.md)   
 [項目&#40;組&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)   
 [項目&#40;メンバー&#41; &#40;MDX&#41;](../mdx/item-member-mdx.md)   
 [ランク&#40;MDX&#41;](../mdx/rank-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
