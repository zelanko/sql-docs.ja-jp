---
title: "Count (ディメンション) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COUNT
dev_langs: kbMDX
helpviewer_keywords: Count function [MDX]
ms.assetid: 4b9c52f6-5bb0-401a-947c-e14134558b4a
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7c75e556f86ad2c433e97e44474048e042603861
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="count-dimension-mdx"></a>Count (ディメンション) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [カウント &#40;です。組と #41 です。&#40;です。MDX と #41 です。](../mdx/count-tuple-mdx.md)   
 [カウント &#40;です。階層レベルが&#41;&#40;です。MDX と #41 です。](../mdx/count-hierarchy-levels-mdx.md)   
 [カウント &#40;です。セット &#41;&#40;です。MDX と #41 です。](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
