---
title: 兄弟 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a4414e134d3b837406c3cb72566084029cf522c9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742851"
---
# <a name="siblings-mdx"></a>Siblings (MDX)


  指定されたメンバー自体を含めて、メンバーの兄弟を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="example"></a>例  
 次の例では、March 2003 の兄弟 (January 2003 と February 2003、および March 2003 自体も含む) の既定のメジャーが返されます。  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
