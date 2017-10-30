---
title: "Avg (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AVG
dev_langs:
- kbMDX
helpviewer_keywords:
- Avg function [MDX]
ms.assetid: efe61272-c3eb-4a33-b231-e00c30be16aa
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a0393bc578fd7c4f5b470ced1bb682755483f448
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="avg-mdx"></a>Avg (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セットを評価し、セット内のセルの空でない値の平均値を返します。セット内のメジャーまたは指定されたメジャーに対して平均値が求められます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Avg( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 一連の空の組または空のセットが指定されている場合、 **Avg**関数は、空の値を返します。  
  
 **Avg**関数は、最初に、指定されたセット内のセル値の合計を計算し、指定されたセット内の空でないセルの数で割って計算された合計で指定されたセット内のセルの空でない値の平均を計算します。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、数値セットの平均値が計算される際、NULL 値は無視されます。  
  
 特定の数値式 (通常はメジャー) が指定されていない場合、 **Avg**関数、現在のクエリ コンテキスト内の各メジャーの平均を計算します。 特定のメジャーを指定する場合、 **Avg**関数はまず、セットに対してメジャーを評価し、関数は、指定されたメジャーに基づいて平均値を計算し、します。  
  
> [!NOTE]  
>  使用する場合、 **CurrentMember**関数ステートメントでは、計算されるメンバー、そのようなクエリのコンテキストでは、現在の座標に対する既定のメジャーが存在しないために、数値式を指定する必要があります。  
  
 空のセルを含めるには、アプリケーションを使用する必要があります、 [CoalesceEmpty](../mdx/coalesceempty-mdx.md)関数かを指定する有効な*Numeric_Expression*空の値のゼロ (0) の値を指定します。 空のセルの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、指定されたセットに対するメジャーの平均値を返しています。 メジャーは、指定されたセットのメンバーの既定のメジャーか、指定されたメジャーのどちらかになります。  
  
 `WITH SET [NW Region] AS`  
  
 `{[Geography].[State-Province].[Washington]`  
  
 `, [Geography].[State-Province].[Oregon]`  
  
 `, [Geography].[State-Province].[Idaho]}`  
  
 `MEMBER [Geography].[Geography].[NW Region Avg] AS`  
  
 `AVG ([NW Region]`  
  
 `--Uncomment the line below to get an average by Reseller Gross Profit Margin`  
  
 `--otherwise the average will be by whatever the default measure is in the cube,`  
  
 `--or whatever measure is specified in the query`  
  
 `--, [Measures].[Reseller Gross Profit Margin]`  
  
 `)`  
  
 `SELECT [Date].[Calendar Year].[Calendar Year].Members ON 0`  
  
 `FROM [Adventure Works]`  
  
 `WHERE ([Geography].[Geography].[NW Region Avg])`  
  
 次の例は、の日次平均を返します、`Measures.[Gross Profit Margin]`から、2003年会計年度の各月の日間にわたって計算、メジャー、 **Adventure Works**キューブ。 **Avg**の各月に含まれている日のセットから平均を計算、`[Ship Date].[Fiscal Time]`階層。 計算の 1 つ目のバージョンでは、売上が記録されなかった日を平均から除く、Avg の既定の動作を示します。2 番目のバージョンでは、売上のない日を平均に含める方法を示します。  
  
 `WITH MEMBER Measures.[Avg Gross Profit Margin] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `Measures.[Gross Profit Margin]`  
  
 `), format_String='percent'`  
  
 `MEMBER Measures.[Avg Gross Profit Margin Including Empty Days] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `CoalesceEmpty(Measures.[Gross Profit Margin],0)`  
  
 `), Format_String='percent'`  
  
 `SELECT`  
  
 `{Measures.[Avg Gross Profit Margin],Measures.[Avg Gross Profit Margin Including Empty Days]} ON COLUMNS,`  
  
 `[Ship Date].[Fiscal].[Fiscal Year].Members ON ROWS`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Product].&[344])`  
  
 次の例は、の日次平均を返します、`Measures.[Gross Profit Margin]`から、2003年会計年度の各半期に関して日間にわたって計算、メジャー、 **Adventure Works**キューブ。  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS  
   Avg(  
      Descendants(  
         [Ship Date].[Fiscal].CurrentMember,   
            [Ship Date].[Fiscal].[Date]  
      ),   
      Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
      [Ship Date].[Fiscal].[Fiscal Year].[FY 2003].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

