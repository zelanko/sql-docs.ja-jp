---
title: Lag (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3c5479aa3ce855b554f34f72c5c86aa86eb04b9f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740881"
---
# <a name="lag-mdx"></a>Lag (MDX)


  レベル内の指定されたメンバーより指定された数だけ後退した位置にあるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 メンバー位置を後退させる数を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 レベル内のメンバーの位置は、属性階層の自然な順序によって決まります。 メンバーの位置の基点は 0 です。  
  
 指定した間隔が 0 の場合、 **Lag**関数は、指定されたメンバー自体を返します。  
  
 指定した間隔が負の場合、 **Lag**関数は、後続のメンバーを返します。  
  
 `Lag(1)` 等価の[PrevMember](../mdx/prevmember-mdx.md)関数。 `Lag(-1)` 等価の[NextMember](../mdx/nextmember-mdx.md)関数。  
  
 **Lag**関数がに似ていますが、[リード](../mdx/lead-mdx.md)関数点を除いて、**潜在顧客**関数は方向が逆になります、 **Lag**関数。 つまり、`Lag(n)`は等価`Lead(-n)`です。  
  
## <a name="example"></a>例  
 次の例では、2001 年 12 月の値が返されます。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
