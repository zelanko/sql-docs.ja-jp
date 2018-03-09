---
title: "セット式の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ba59d13932b4d93f7d4992b8f26b6830ba67b395
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="using-set-expressions"></a>セット式の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットは、0 個以上の組の順序付けされた一覧で構成されます。 組を 1 つも含まないセットは、空のセットと呼ばれます。  
  
 完全なセット式は、中かっこの中に 0 個以上の組を明示的に指定して表します。  
  
 {[{ *Tuple_expression* | *メンバー式*} [、{ *Tuple_expression* | *メンバー式*}]...]}  
  
 セット式の中で指定されたメンバー式は、1 つのメンバーのみの組式に変換されます。  
  
## <a name="example"></a>例  
 次の例では、クエリの COLUMNS 軸と ROWS 軸で使用される 2 つのセット式を示します。  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 COLUMNS 軸のセットを次に示します。  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 このセットは、Measures ディメンションの 2 つのメンバーで構成されています。 ROWS 軸のセットを次に示します。  
  
 {([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),  
  
 ([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),  
  
 ([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}  
  
 このセットは 3 つの組で構成されており、それぞれの組には、Product ディメンションの Product Categories 階層のメンバーと Date ディメンションの Calendar 階層のメンバーへの、2 つの明示的な参照が含まれています。  
  
 セットを返す関数の例については、次を参照してください[メンバー、組、およびセット &#40; の操作。MDX と #41 です](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)。  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。MDX と #41 です](../mdx/expressions-mdx.md)  
  
  
