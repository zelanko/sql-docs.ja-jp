---
title: LastChild (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 08f1f71497861ee1a946019ed547f40a0d6037ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68098539"
---
# <a name="lastchild-mdx"></a>LastChild (MDX)


  指定されたメンバーの最後の子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.LastChild   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="example"></a>例  
 次の例では、2002年の最初の会計四半期の最後の子である2001年9月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002].LastChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [FirstChild &#40;MDX&#41;](../mdx/firstchild-mdx.md)   
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
