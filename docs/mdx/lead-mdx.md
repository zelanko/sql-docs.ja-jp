---
title: Lead (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d72af1bf0b671eeb2bd4b84c194f129ed1ce6bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205436"
---
# <a name="lead-mdx"></a>Lead (MDX)


  次のメンバーのレベルにある指定されたメンバーの位置の指定した数であるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 メンバーの位置の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 レベル内でメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定したの潜在顧客がゼロ (0) の場合、**リード**関数は、指定されたメンバーを返します。  
  
 指定したの潜在顧客が負の場合、**リード**関数は後方のメンバーを返します。  
  
 `Lead(1)` 同じですが、 [NextMember](../mdx/nextmember-mdx.md)関数。 `Lead(-1)` 同じですが、 [PrevMember](../mdx/prevmember-mdx.md)関数。  
  
 **リード**機能に似ています、 [Lag](../mdx/lag-mdx.md)関数点を除いて、 **Lag**関数は方向が逆になります、**リード**関数。 つまり、`Lead(n)`と等価`Lag(-n)`します。  
  
## <a name="example"></a>例  
 次の例では、2001 年 12 月の値を返します。  
  
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
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
