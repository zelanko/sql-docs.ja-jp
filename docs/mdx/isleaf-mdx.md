---
title: IsLeaf (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 400c55cdfcea35ae60859fb66489384870172744
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905942"
---
# <a name="isleaf-mdx"></a>IsLeaf (MDX)


  指定されたメンバーがリーフメンバーであるかどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsLeaf(Member_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **Isleaf**関数は、指定されたメンバーがリーフメンバーである場合に**true**を返します。 それ以外の場合、関数は**false**を返します。  
  
## <a name="example"></a>例  
 次の例では、[Date] の場合に TRUE を返します。[会計]。CurrentMember はリーフメンバーです。  
  
 `WITH MEMBER MEASURES.ISLEAFDEMO AS`  
  
 `IsLeaf([Date].[Fiscal].CURRENTMEMBER)`  
  
 `SELECT {MEASURES.ISLEAFDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
