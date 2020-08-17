---
description: IsAncestor (MDX)
title: IsAncestor (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ccc61de94c87972eda3dbebdba798f9b1c4028b1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341488"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  指定されたメンバーが別の指定されたメンバーの先祖であるかどうかを示す値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression1*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Member_Expression2*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Isancestor**関数は、指定された最初のメンバーが2番目に指定されたメンバーの先祖である場合に**true**を返します。 それ以外の場合、関数は **false**を返します。  
  
## <a name="example"></a>例  
 次の例では、[Date] の場合に **true** を返します。[会計]。CurrentMember は2003年1月の先祖です。  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [先祖 &#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
