---
title: IsAncestor (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8aacd6825a81ff172d8fdf79373f5b251d6e18b9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740622"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  指定されたメンバーが指定された別のメンバーの先祖かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression1*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Member_Expression2*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **IsAncestor**関数が返される**true**番目のメンバーが指定された 2 つ目のメンバーの先祖である場合。 関数を返しますそれ以外の場合、 **false**です。  
  
## <a name="example"></a>例  
 次の例を返します**true**場合 [Date] です [。Fiscal] です。CurrentMember では、2003 年 1 月の先祖を示します。  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [先祖&#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
