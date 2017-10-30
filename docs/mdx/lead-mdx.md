---
title: "潜在顧客 (MDX) |Microsoft ドキュメント"
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
- LEAD
dev_langs:
- kbMDX
helpviewer_keywords:
- Lead function
ms.assetid: f3250092-7b98-40b5-8dca-77e3b50734a0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 127c84f38fe85453fa3da7ae2b1c9752b05b6ba7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="lead-mdx"></a>Lead (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レベル内の指定されたメンバーから指定された数だけ前進した位置にあるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *インデックス*  
 メンバー位置を数値で指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 レベル内のメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定したの潜在顧客がゼロ (0) の場合、**リード**関数は、指定されたメンバーを返します。  
  
 指定したの潜在顧客が負の場合、**リード**関数は後方のメンバーを返します。  
  
 `Lead(1)`等価の[NextMember](../mdx/nextmember-mdx.md)関数。 `Lead(-1)`等価の[PrevMember](../mdx/prevmember-mdx.md)関数。  
  
 **リード**関数がに似ていますが、 [Lag](../mdx/lag-mdx.md)関数点を除いて、 **Lag**関数は方向が逆になります、**潜在顧客**関数。 つまり、`Lead(n)`は等価`Lag(-n)`です。  
  
## <a name="example"></a>例  
 次の例では、2001 年 12 月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2002 年 3 月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

