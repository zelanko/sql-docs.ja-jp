---
title: "Ytd (MDX) |Microsoft ドキュメント"
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
f1_keywords: YTD
dev_langs: kbMDX
helpviewer_keywords: Ytd function
ms.assetid: b77fdba2-d4a9-4271-8c21-c1f12eba526d
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 8f9d95aca057801c924ceec962f818c7e6f27869
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="ytd-mdx"></a>Ytd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  以降では最初の兄弟、制約の中で指定されたメンバーで終わると、特定のメンバーと同じレベルからメンバーの兄弟のセットを返します、*年*時間ディメンション内のレベルです。  
  
## <a name="syntax"></a>構文  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 既定値は型のレベルを持つ最初の階層の現在のメンバーではメンバー式が指定されていない場合*年*型の最初の次元の*時間*メジャー グループにします。  
  
 **Ytd**関数のショートカット関数では、 [PeriodsToDate](../mdx/periodstodate-mdx.md)関数レベルの基になる属性階層の Type プロパティに設定されている*年*です。 つまり、`Ytd(Member_Expression)`は等価`PeriodsToDate(Year_Level_Expression,Member_Expression)`です。 Type プロパティ設定されている場合、この関数は機能しないことに注意してください*FiscalYears*です。  
  
## <a name="example"></a>例  
 次の例は、の合計を返して、`Measures.[Order Quantity]`集計に含まれている 2003 年の最初の 8 月のメンバー、`Date`ディメンションから、 **Adventure Works**キューブ。  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **Ytd**はでよく使用の組み合わせでパラメーターを指定せず、つまり、 [CurrentMember (& a) #40 です。MDX と #41 です。](../mdx/currentmember-mdx.md)関数は、次のクエリで示すように、レポートでは、年度累計の累積合計が表示されます。  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
