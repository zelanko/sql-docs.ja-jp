---
title: IsSibling (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d86c96686357533aa1217571f3c199ec8ddff508
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739641"
---
# <a name="issibling-mdx"></a>IsSibling (MDX)


  指定されたメンバーが指定された別のメンバーの兄弟かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsSibling(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression1*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Member_Expression2*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **IsSibling**関数が返される**true**メンバーは、2 番目の指定されたメンバーの兄弟、最初に指定した場合。 関数を返しますそれ以外の場合、 **false**です。  
  
## <a name="example"></a>例  
 次の例では、Date ディメンションの Fiscal 階層の現在のメンバーが July 2002 の兄弟である場合、TRUE を返します。  
  
 `WITH MEMBER MEASURES.ISSIBLINGDEMO AS`  
  
 `IsSibling([Date].[Fiscal].CURRENTMEMBER, [Date].[Fiscal].[Month].&[2002]&[7])`  
  
 `SELECT {MEASURES.ISSIBLINGDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
