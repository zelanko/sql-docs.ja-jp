---
title: ディメンション (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 58bee93a4cef37a8a5a71211b292a16392687f12
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67999961"
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
  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="examples"></a>使用例  
 次の例では、 **Name**関数と共に**Dimension**関数を使用して、指定されたメンバーの階層名を返します。  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 次の例では、ディメンション関数をレベルおよびカウント関数と組み合わせて使用して、指定されたメンバーを含む階層内のレベル数を返します。  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 次の例では、**ディメンション**関数を**メンバー**および**カウント**関数と共に使用して、指定されたメンバーを含む階層内のメンバーの数を返します。  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#41; &#40;&#40;階層レベルのカウント](../mdx/count-hierarchy-levels-mdx.md)   
 [MDX&#41;&#41; &#40;設定 &#40;数](../mdx/count-set-mdx.md)   
 [MDX&#41;&#40;レベル](../mdx/levels-mdx.md)   
 [メンバー &#40;設定&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
