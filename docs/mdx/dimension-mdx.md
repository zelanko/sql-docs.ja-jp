---
title: ディメンション (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cee82f3baa95df1d8636e314bfbb0798efe9527a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741671"
---
# <a name="dimension-mdx"></a>Dimension (MDX)


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
 [カウント&#40;階層レベル&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [カウント&#40;設定&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [レベル&#40;MDX&#41;](../mdx/levels-mdx.md)   
 [メンバー&#40;設定&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
