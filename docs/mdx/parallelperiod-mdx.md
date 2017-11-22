---
title: "ParallelPeriod (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PARALLELPERIOD
dev_langs: kbMDX
helpviewer_keywords: ParallelPeriod function
ms.assetid: 9c87f5a6-5694-46f1-9890-bd9705190ea7
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 93f1133779ec210979f0d819e612111b97050096
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  前の期間から、指定されたメンバーと同じ相対位置にあるメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 さかのぼる並列期間の数を指定する有効な数値式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 似ていますが、 [Cousin](../mdx/cousin-mdx.md) 、関数、 **ParallelPeriod**関数はタイム シリーズをより密接に関連します。 **ParallelPeriod**関数が指定されたレベルで指定されたメンバーの先祖を受け取り、指定した間隔、先祖の兄弟を検索および最後に、兄弟の子孫のうち、指定されたメンバーの並列期間を返します。  
  
 **ParallelPeriod**関数には、次の既定値。  
  
-   既定のメンバー値の型を持つ最初のディメンションの最初の階層の現在のメンバーは、レベル式もメンバー式が指定されている場合*時間*メジャー グループにします。  
  
-   既定のメンバー値は、レベル式を指定すると、メンバー式が指定されていない場合、 *Level_Expression*.**Hierarchy.CurrentMember**です。  
  
-   既定のインデックス値は 1 です。  
  
-   既定のレベルは、指定されたメンバーの親のレベルです。  
  
 **ParallelPeriod**関数は、次の MDX ステートメントに相当します。  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>例  
 次の例では、Quarter レベルを基準として、2003 年 10 月から 3 期間さかのぼった並列期間を返します。つまり、2003 年 1 月が返されます。  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 次の例では、Semester  レベルを基準として、2003 年 10 月から 3 期間さかのぼった並列期間を返します。つまり、2002 年 4 月が返されます。  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
