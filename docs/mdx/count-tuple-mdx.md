---
title: Count (組) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3775af63181489b982778d40ddd69ebc12872271
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285035"
---
# <a name="count-tuple-mdx"></a>Count (組) (MDX)


  組の次元数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 組の次元数を返します。  
  
## <a name="example"></a>例  
 次のクエリで計算されるメジャーが、組にある階層の数は、値 2 を返します`([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])`:  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [カウント&#40;ディメンション&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [カウント&#40;階層レベル&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Set&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
