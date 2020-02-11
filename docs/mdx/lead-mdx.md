---
title: 潜在顧客 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cc4d362fbc7656e9427548a352b32d5d8297071e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905740"
---
# <a name="lead-mdx"></a>潜在顧客 (MDX)


  メンバーのレベルに沿って指定されたメンバーの後に指定された位置の数であるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *化*  
 メンバーの位置の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 レベル内のメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定された潜在顧客がゼロ (0) の場合、 **lead**関数は、指定されたメンバーを返します。  
  
 指定された潜在顧客が負の場合、 **lead**関数は前のメンバーを返します。  
  
 `Lead(1)`は、 [Nextmember](../mdx/nextmember-mdx.md)関数と同じです。 `Lead(-1)`は、 [Prevmember](../mdx/prevmember-mdx.md)関数に相当します。  
  
 **Lead**関数は[lag](../mdx/lag-mdx.md)関数に似ていますが、 **lag**関数は、 **lead**関数に反対方向を検索します。 つまり、 `Lead(n)`はと同じです`Lag(-n)`。  
  
## <a name="example"></a>例  
 次の例では、2001年12月の値が返されます。  
  
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
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
