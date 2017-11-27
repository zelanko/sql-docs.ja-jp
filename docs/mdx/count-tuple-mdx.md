---
title: "Count (組) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.assetid: c8f4a570-54a8-4c00-ac4b-eef0ebdb353c
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f25899c01bfd30fa5868fa01487d16efa6ff03da
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="count-tuple-mdx"></a>Count (組) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  組内のディメンション数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 組内のディメンション数を返します。  
  
## <a name="example"></a>例  
 次のクエリで計算されるメジャー値 2 を返します、階層、組にある数である`([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])`:  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [カウント (&) #40";"ディメンション"&"#41;& #40 です。MDX と #41 です。](../mdx/count-dimension-mdx.md)   
 [カウント & #40 です。階層レベルが"&"#41;& #40 です。MDX と #41 です。](../mdx/count-hierarchy-levels-mdx.md)   
 [カウント & #40 です。セット &#41;& #40 です。MDX と #41 です。](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

