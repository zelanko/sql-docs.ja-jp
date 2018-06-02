---
title: 潜在顧客 (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e9faf5d0f7b549887c6aa4a12e4c502c2663ce3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578994"
---
# <a name="lead-mdx"></a>Lead (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  レベル内の指定されたメンバーから指定された数だけ前進した位置にあるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 メンバー位置を数値で指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 レベル内のメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定したの潜在顧客がゼロ (0) の場合、**リード**関数は、指定されたメンバーを返します。  
  
 指定したの潜在顧客が負の場合、**リード**関数は後方のメンバーを返します。  
  
 `Lead(1)` 等価の[NextMember](../mdx/nextmember-mdx.md)関数。 `Lead(-1)` 等価の[PrevMember](../mdx/prevmember-mdx.md)関数。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
