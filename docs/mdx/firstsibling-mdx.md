---
title: FirstSibling (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 671dd0b2b400362fe3a2274c4687f93192f04da4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68105449"
---
# <a name="firstsibling-mdx"></a>FirstSibling (MDX)


  メンバーの親の最初の子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.FirstSibling   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="example"></a>例  
 次のクエリでは、会計年度2002の会計年度2003の最初の兄弟が返されます。これは会計年度です。  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstSibling ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
