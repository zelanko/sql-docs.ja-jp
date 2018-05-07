---
title: FirstChild (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FIRSTCHILD
dev_langs:
- kbMDX
helpviewer_keywords:
- FirstChild function
ms.assetid: 3c19a169-7658-4b31-93a9-85f74225ba05
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f4ac1f7b1c0a8b3a399ab1eaf5f193a3b9572d5d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="firstchild-mdx"></a>FirstChild (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
