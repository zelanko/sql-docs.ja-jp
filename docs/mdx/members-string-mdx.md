---
title: "Members (String) (MDX) |Microsoft ドキュメント"
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
- Members
dev_langs:
- kbMDX
helpviewer_keywords:
- Members function
ms.assetid: 21fca354-448b-4b05-93f4-111bde1568f1
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 14ab54616fdfeb85cb5b45f1e6d77b8e5c475c41
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="members-string-mdx"></a>Members (文字列) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  文字列式で指定されたメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Name*  
 メンバー名を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **Members (String)**関数を指定する名前を持つ 1 つのメンバーを返します。 通常、使用して、 **Members (String)**を提供する外部の関数と併用、 **Members (String)**関数、メンバーを識別する文字列と**Members (String)**関数がその指定したメンバーについて、値を返します。  
  
## <a name="example"></a>例  
 次の例では、 **Members (String)**関数の有効なメンバーに、指定した文字列を変換して、文字列で指定されたメンバーの既定のメジャーを返します。 指定の文字列は単一引用符で囲まれています。 既定のメジャーは Reseller Sales Amount メジャーです。  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

