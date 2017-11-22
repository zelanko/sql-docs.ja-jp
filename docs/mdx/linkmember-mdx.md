---
title: "LinkMember (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: LINKMEMBER
dev_langs: kbMDX
helpviewer_keywords: LinkMember function
ms.assetid: b9106f07-8ea2-4933-aed3-ee9c63acf7ac
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b9122e0ae4aec51fe2e554f4e5d667fb9225e4d0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された階層の指定されたメンバーと等価のメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **LinkMember**関数は、関連する階層で指定されたメンバーの各レベルでキー値に一致する指定された階層からメンバーを返します。 各レベルの属性では、キーの基数およびデータ型が同じである必要があります。 不自然階層では、属性のキー値が複数一致する場合、結果はエラーまたは不確定になります。  
  
## <a name="examples"></a>使用例  
 次の例では、 **LinkMember**関数を Calendar 階層にある Date.Date 属性階層の July 1, 2002年メンバーの先祖の Adventure Works キューブ内の既定のメジャーを返します。  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Hierarchize (& a) #40 です。MDX と #41 です。](../mdx/hierarchize-mdx.md)   
 [先祖と #40 です。MDX と #41 です。](../mdx/ascendants-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
