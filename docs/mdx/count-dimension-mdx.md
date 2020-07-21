---
title: Count (ディメンション) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b84c5a1902e80f8abe3828f4be1b5d570ec026ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68104812"
---
# <a name="count-dimension-mdx"></a>Count (ディメンション) (MDX)


  キューブ内の階層数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Remarks  
 `[Measures].[Measures]` 階層も含めて、キューブ内の階層数を返します。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブ内の階層数を返します。  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#41; &#40;組 &#40;数](../mdx/count-tuple-mdx.md)   
 [MDX&#41;&#41; &#40;&#40;階層レベルのカウント](../mdx/count-hierarchy-levels-mdx.md)   
 [MDX&#41;&#41; &#40;設定 &#40;数](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
