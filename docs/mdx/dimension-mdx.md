---
title: "ディメンション (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Dimension
dev_langs: kbMDX
helpviewer_keywords: Dimension function
ms.assetid: 0e3ce539-1d34-45ca-8342-67796e11b730
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 74c5beec4459c1d261a1850b9888a6a0906e9900
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="dimension-mdx"></a>Dimension (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたメンバー、レベル、または階層を含む階層を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.Dimension  
  
Level syntax  
Level_Expression.Dimension  
  
Member syntax  
Member_Expression.Dimension  
  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="examples"></a>使用例  
 次の例では、**ディメンション**と組み合わせて、関数、**名前**を指定されたメンバーの階層の名前を返す関数。  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 次の例では、Dimension 関数を Levels 関数および Count 関数と併用して、指定されたメンバーを含む階層内のレベル数を返しています。  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 次の例で、**ディメンション**と組み合わせて、関数、**メンバー**と**カウント**関数を指定されたメンバーを含む階層でメンバーの数を返します。  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [カウント &#40;です。階層レベルが&#41;&#40;です。MDX と #41 です。](../mdx/count-hierarchy-levels-mdx.md)   
 [カウント &#40;です。セット &#41;&#40;です。MDX と #41 です。](../mdx/count-set-mdx.md)   
 [レベル &#40;です。MDX と #41 です。](../mdx/levels-mdx.md)   
 [メンバーと #40 です。セット &#41;&#40;です。MDX と #41 です。](../mdx/members-set-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
