---
title: 親 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9449c81e9f8e8de0c21d96062337e91b2f56398d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037199"
---
# <a name="parent-mdx"></a>親 (MDX)


  メンバーの親メンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **親**関数は、指定されたメンバーの親メンバーを返します。  
  
## <a name="examples"></a>使用例  
 次の 2 つの例では、July 1, 2001 メンバーの親メンバーを返しています。 この例では、Date 属性階層のコンテキストでこのメンバーを指定して、All Periods メンバーを返します。  
  
```  
SELECT [Date].[Date].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、Calendar 階層のコンテキストで2001年7月1日のメンバーを指定しています。  
  
```  
SELECT [Date].[Calendar].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
