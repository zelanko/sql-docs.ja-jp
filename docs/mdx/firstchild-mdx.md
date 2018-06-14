---
title: FirstChild (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed769da991c54b4ae7bc85091a652a27f5399a73
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740381"
---
# <a name="firstchild-mdx"></a>FirstChild (MDX)


  指定されたメンバーの 1 つ目の子メンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.FirstChild   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="example"></a>例  
 次のクエリでは、Fiscal 階層内の 2003 会計年度の 1 つ目の子を返しています。返されるメンバーは、2003 会計年度の上半期です。  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [LastChild &#40;MDX&#41;](../mdx/lastchild-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
