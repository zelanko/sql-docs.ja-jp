---
title: EXISTING キーワード (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8431c4b29f20b3c87e3b944736612d009426900a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106552"
---
# <a name="existing-keyword-mdx"></a>EXISTING キーワード (MDX)
  指定されたセットを現在のコンテキストで評価するように設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 有効な多次元式 (MDX) セット式です。  
  
## <a name="remarks"></a>コメント  
 既定では、セットの評価は、そのセットのメンバーを含むキューブのコンテキストで実行されます。 `Existing`キーワードには、代わりに、現在のコンテキスト内で評価される指定されたセットが行われます。  
  
## <a name="example"></a>例  
 次の例では、`Aggregate`  関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。 [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) 関数および [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) 関数を使用しています。 `Existing`キーワード力のセット、 `Filter` State-province 属性階層の Washington および Oregon メンバーには、現在のコンテキストで評価する関数。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>参照  
 [カウント&#40;設定&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [集計&#40;MDX&#41;](/sql/mdx/aggregate-mdx)   
 [フィルター &#40;MDX&#41;](/sql/mdx/filter-mdx)   
 [プロパティ&#40;MDX&#41;](/sql/mdx/properties-mdx)   
 [DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx)   
 [MDX 関数リファレンス&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
