---
title: Aggregate (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 11e10d5a03702329a5ed59ed42acee0abc2d27c8
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740571"
---
# <a name="aggregate-mdx"></a>Aggregate (MDX)


  セット式から返されたセルを集計することによって計算した数値を返します。 数値式が指定されていない場合は、メジャーごとに指定されている既定の集計演算子を使用して、現在のクエリ コンテキスト内で各メジャーを集計します。 数値式が指定されている場合は、指定されたセット内のセルごとに数値式を評価してから、合計を算出します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Aggregate(Set_Expression [ ,Numeric_Expression ])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 空の組のセットまたは空のセットを指定した場合、この関数は空の値を返します。  
  
 次の表方法、**集計**各種集計関数の関数の動作です。  
  
|集計演算子|結果|  
|--------------------------|------------|  
|Sum|セット全体の値の合計を返します。|  
|Count|セット全体の値の数を返します。|  
|Max|セット全体の最大値を返します。|  
|Min|セット全体の最小値を返します。|  
|準加法集計関数|時間軸に図形を投影してから、準加法動作の計算結果を返します。|  
|Distinct Count|スライサー軸にセットが含まれている場合、サブキューブに関与するファクト データ全体で集計を行います。<br /><br /> セットのメンバーごとに個別のカウントを返します。 その結果は、計算に必要なセルのセキュリティではなく、集計対象のセルのセキュリティによって異なります。 セットにセル セキュリティが指定されているとエラーが生成されますが、指定されているセットの粒度より下位のセル セキュリティは無視されます。 セットに関する計算はエラーになります。 セットの粒度よりも下位の計算は無視されます。 1 つのメンバーとそのメンバーの子が 1 つ以上含まれているセット全体に対する個別カウントは、子メンバーに関与するファクト全体の個別カウントになります。|  
|集計できない属性|値の合計を返します。|  
|集計関数の混合|サポートされていないので、エラーになります。|  
|単項演算子|影響しません。値は合計を算出することによって集計されます。|  
|計算されるメジャー|計算されるメジャーを確保するために設定された解決順序が適用されます。|  
|計算されるメンバー|通常の規則が適用されます。つまり、最後の解決順序が優先されます。|  
|代入|代入により、メジャー集計関数に従って集計が行われます。 メジャー集計関数が個別カウントの場合、代入の合計が算出されます。|  
  
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
  
 次の例では、Aggregate 関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。 **Hierarchize**と**DrillDownLevel** Product ディメンションに製品カテゴリに関して減少した売上の値を返す関数を使用します。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>参照  
 [PeriodsToDate &#40;MDX&#41;](../mdx/periodstodate-mdx.md)   
 [子&#40;MDX&#41;](../mdx/children-mdx.md)   
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [カウント&#40;設定&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [フィルター &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [プロパティ&#40;MDX&#41;](../mdx/properties-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
