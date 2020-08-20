---
description: セット式の使用
title: Set 式を使用する |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d47372f2e90f96aca99eb05bd6a2565c08567611
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491386"
---
# <a name="using-set-expressions"></a>セット式の使用


  セットは、0個以上の組の順序付きリストで構成されます。 組を 1 つも含まないセットは、空のセットと呼ばれます。  
  
 セットの完全な式は、中かっこで囲まれた0個以上の明示的に指定された組で構成されます。  
  
 {[{ *Tuple_expression*  |  *Member_expression* } [, { *Tuple_expression*  |  *Member_expression* }]...]}  
  
 セット式で指定されたメンバー式は、1つのメンバーのタプル式に変換されます。  
  
## <a name="example"></a>例  
 次の例では、クエリの列軸と行軸で使用される2つのセット式を示します。  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Columns 軸のセット  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 Measures ディメンションの2つのメンバーで構成されます。 ROWS 軸のセットを次に示します。  
  
 {([Product]。[製品カテゴリ]。[Category] です。 & [4]、[Date] です。[カレンダー]。[Calendar Year] & [2004])、  
  
 ([Product]。[製品カテゴリ]。[Category] です。 & [1]、[Date] です。[カレンダー]。[Calendar Year] & [2003])、  
  
 ([Product]。[製品カテゴリ]。[Category] です。 & [3]、[Date] です。[カレンダー]。[Calendar Year] です。 & [2004])}  
  
 このセットは 3 つの組で構成されており、それぞれの組には、Product ディメンションの Product Categories 階層のメンバーと Date ディメンションの Calendar 階層のメンバーへの、2 つの明示的な参照が含まれています。  
  
 セットを返す関数の例については、「 [MDX&#41;&#40;メンバー、組、およびセットの操作 ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX &#40;式&#41;](../mdx/expressions-mdx.md)  
  
  
