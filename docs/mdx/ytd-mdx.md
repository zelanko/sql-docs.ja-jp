---
title: Ytd (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 33deba1261ad6c2afcf44854b0590c978683f08b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581894"
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
  
## <a name="remarks"></a>コメント  
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
  
 **Ytd**はでよく使用の組み合わせでパラメーターを指定せず、つまり、 [CurrentMember &#40;MDX&#41; ](../mdx/currentmember-mdx.md)関数で示すように、レポートでは、年度累計の累積合計を表示は、次のクエリ:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
