---
title: "Count (ディメンション) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 4b9c52f6-5bb0-401a-947c-e14134558b4a
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 42c607f44e10c35c41e302b858406f0dafc57c9c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="count-dimension-mdx"></a>Count (ディメンション) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キューブ内の階層数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>解説  
 `[Measures].[Measures]` 階層も含めて、キューブ内の階層数を返します。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブ内の階層数を返しています。  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [カウント & #40 です。組と #41 です。& #40 です。MDX と #41 です。](../mdx/count-tuple-mdx.md)   
 [カウント & #40 です。階層レベルが"&"#41;& #40 です。MDX と #41 です。](../mdx/count-hierarchy-levels-mdx.md)   
 [カウント & #40 です。セット &#41;& #40 です。MDX と #41 です。](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

