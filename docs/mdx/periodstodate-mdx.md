---
title: PeriodsToDate (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PERIODSTODATE
dev_langs:
- kbMDX
helpviewer_keywords:
- PeriodsToDate function
ms.assetid: 43b9f69c-7b8c-4de0-9c4b-778ae766f74e
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: b24e57d8f682e21a6d561a4e3a426da85f5ceb17
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  時間ディメンションで指定されているレベル内で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 指定されたレベルのスコープ内で、 **PeriodsToDate**先頭期間から始まり、指定したメンバーで終わる、指定されたメンバーと同じレベルの期間のセットを返します。  
  
-   レベルが指定した場合、階層の現在のメンバーが推論*階層*.**CurrentMember**ここで、*階層*は、指定されたレベルの階層です。  
  
-   レベルもメンバーも指定されていない場合、レベルは、メジャー グループの Time 型の最初のディメンションにある最初の階層の現在のメンバーの親レベルになります。  
  
 `PeriodsToDate( Level_Expression, Member_Expression )` は、以下の MDX 式と機能的に等価です。  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>使用例  
 次の例は、の合計を返して、`Measures.[Order Quantity]`集計に含まれている 2003 年の最初の 8 月のメンバー、`Date`ディメンションから、 **Adventure Works**キューブ。  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 次の例では、2003 年下半期の最初の 2 か月を集計しています。  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>参照  
 [TopCount &#40;です。MDX と #41 です。](../mdx/topcount-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
