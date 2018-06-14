---
title: 子メンバー (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad604900ac31cbcfb7e9a68fba4241c5f539b491
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740031"
---
# <a name="cousin-mdx"></a>Cousin (MDX)


  親メンバーからの相対位置が、指定された子メンバーと同じ子メンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cousin( Member_Expression , Ancestor_Member_Expression )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Ancestor_Member_Expression*  
 先祖メンバーを 1 つ返す有効な多次元式 (MDX) メンバー式です。  
  
## <a name="remarks"></a>コメント  
 この関数は、複数レベル内のメンバーの順序と位置を算出します。 2 つの階層が存在し、一方の階層に 4 つ、他方の階層に 5 つのレベルがあるとすると、一方の階層の 3 番目のレベルに対応する "いとこ" の位置関係に当たる子メンバーは他方の階層の 3 番目のレベルです。  
  
## <a name="examples"></a>使用例  
 次の例では、先祖である 2003 会計年度の Year レベルを基準として、2002 会計年度の第 4 四半期に対応する "いとこ" の位置関係に当たる子メンバーを取得します。 取得される子メンバーは、2003 会計年度の第 4 四半期です。  
  
```  
SELECT Cousin   
   ( [Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002],  
     [Date].[Fiscal].[FY 2003]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、先祖である 2004 会計年度の第 2 四半期の Quarter レベルを基準として、2002 会計年度の 7 月に対応する "いとこ" の位置関係に当たる子メンバーを取得します。 取得される子メンバーは、2003 年の 10 月です。  
  
```  
SELECT Cousin   
   ([Date].[Fiscal].[Month].[July 2002] ,  
    [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2004]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
