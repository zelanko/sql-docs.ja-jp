---
title: "フィルター (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: filter
dev_langs: kbMDX
helpviewer_keywords: Filter function
ms.assetid: f2df51c8-6acb-4300-b71c-2a480c9fbdf8
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 7a29ceb5b62cfabf53084e3ad467161fbe86d9b7
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="filter-mdx"></a>Filter (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセットを検索条件に基づいて絞り込み、結果セットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Logical_Expression*  
 true または false に評価される有効な多次元式 (MDX) 論理式です。  
  
## <a name="remarks"></a>解説  
 **フィルター**関数は、指定されたセット内の各組に対して指定された論理式を評価します。 論理式の評価が、指定されたセット内の各組で構成されるセットを返します**true**です。 評価される組がない場合**true**空のセットが返されます。  
  
 **フィルター**関数の動作と同様の方法で、 [IIf](../mdx/iif-mdx.md)関数。 **IIf**関数では、2 つのオプションの 1 つだけを返しますは MDX 論理式の評価に基づき、while、**フィルター**関数を指定した検索条件を満たす組のセットを返します。 実際には、**フィルター**関数が実行される`IIf(Logical_Expression, Set_Expression.Current, NULL)`セット、および返します内の組ごとに、その結果セットです。  
  
## <a name="examples"></a>使用例  
 次の例では、クエリの行軸で Filter 関数を使用して、Internet Sales Amount が 10,000 米ドルを超える日付のみを返す方法を示します。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Filter 関数は、計算されるメンバーの定義内でも使用できます。 次の例は、の合計を返して、`Measures.[Order Quantity]`集計に含まれている 2003年の 9 か月の最初のメンバー、`Date`ディメンションから、 **Adventure Works**キューブ。 **PeriodsToDate**関数セット内の組の定義を**集計**関数は動作します。 **フィルター**関数は、前の期間の Reseller Sales Amount メジャーの値が小さいものに返される組を限定します。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
