---
title: "TopCount (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: TOPCOUNT
dev_langs: kbMDX
helpviewer_keywords: TopCount function
ms.assetid: 15026a8f-35c5-4307-8856-348f5c44bfd5
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 597faa6bfe343a0a1329dfc0dd75be5a1f785491
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="topcount-mdx"></a>TopCount (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットを降順に並べ替え、値の大きい方から指定された数の要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **TopCount**関数、順序、指定されたセットに対して評価された数値式で指定された値に従って、指定されたセットで指定されたセット内の組を降順で並べ替えます。 セットの並べ替えの後に、 **TopCount**関数では、指定した数の組の最も大きい値を返します。  
  
> [!IMPORTANT]  
>  同様に、 [BottomCount](../mdx/bottomcount-mdx.md) 、関数、 **TopCount**関数が常に階層を解除します。  
  
 数値式が指定されていない場合、関数のセットを返しますメンバー、自然な順序で、並べ替えを行わずと同様の動作、 [Head (MDX)](../mdx/head-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次の例では、Internet Sales Amount の上位 10 日を返します。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の例では、Bike カテゴリについて、Geography ディメンションの Geography 階層にある City レベルのメンバーのすべての組み合わせと Date ディメンションの Fiscal 階層のすべての会計年度を含んでいるセットを、Reseller Sales Amount メジャーで (最も売上が多いメンバーが 1 番目になるように) 並べ替えて、最初の 5 つのメンバーを返します。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
