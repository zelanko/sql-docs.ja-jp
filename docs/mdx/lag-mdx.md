---
title: Lag (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c7e95af96249b64f86bb1466283e8a1a38a32d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905774"
---
# <a name="lag-mdx"></a>Lag (MDX)


  メンバーのレベルで指定されたメンバーの前に指定された位置の数であるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *化*  
 遅延するメンバーの位置の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 レベル内のメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定された lag が0の場合、 **lag**関数は、指定されたメンバー自体を返します。  
  
 指定された lag が負の場合、 **lag**関数は後続のメンバーを返します。  
  
 `Lag(1)`は、 [Prevmember](../mdx/prevmember-mdx.md)関数に相当します。 `Lag(-1)`は、 [Nextmember](../mdx/nextmember-mdx.md)関数と同じです。  
  
 **Lag**関数は[、lead 関数](../mdx/lead-mdx.md)に似ています。ただし、 **lead**関数は、 **lag**関数と逆方向に見えます。 つまり、 `Lag(n)`はと同じです`Lead(-n)`。  
  
## <a name="example"></a>例  
 次の例では、2001年12月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(2) ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2002 年 3 月の値が返されます。  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(-1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
