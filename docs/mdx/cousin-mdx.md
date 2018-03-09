---
title: "子メンバー (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COUSIN
dev_langs: kbMDX
helpviewer_keywords: Cousin function
ms.assetid: 9a416685-d35d-4d9c-a9f6-4574cbe59aea
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b1f7374d18c2d9e8695d243f50b7eeca9c654e24
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cousin-mdx"></a>Cousin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
