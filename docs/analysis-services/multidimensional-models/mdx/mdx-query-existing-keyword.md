---
title: "EXISTING キーワード (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5078aa14be3c476e8b89545ed1541f12b7686f4e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-query---existing-keyword"></a>MDX クエリ - EXISTING キーワード
  指定されたセットを現在のコンテキストで評価するように設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 有効な多次元式 (MDX) セット式です。  
  
## <a name="remarks"></a>解説  
 既定では、セットの評価は、そのセットのメンバーを含むキューブのコンテキストで実行されます。 **Existing** キーワードを指定すると、指定されているセットの評価が現在のコンテキストで行われます。  
  
## <a name="example"></a>例  
 次の例では、 **Aggregate** 関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。 Product ディメンションに含まれる製品カテゴリに関して減少した売上の値を返すために、 [Hierarchize (MDX)](../../../mdx/hierarchize-mdx.md) 関数および [DrilldownLevel (MDX)](../../../mdx/drilldownlevel-mdx.md) 関数を使用しています。 **Existing** キーワードを指定すると、 **Filter** 関数内のセット (State-Province 属性階層の Washington メンバーと Oregon メンバー) の評価が現在のコンテキストで行われます。  
  
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
 [Count (セット) (MDX)](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers & #40 です。MDX と #41 です。](../../../mdx/addcalculatedmembers-mdx.md)   
 [集計 & #40 です。MDX と #41 です。](../../../mdx/aggregate-mdx.md)   
 [フィルターと #40 です。MDX と #41 です。](../../../mdx/filter-mdx.md)   
 [プロパティ & #40 です。MDX と #41 です。](../../../mdx/properties-mdx.md)   
 [DrilldownLevel & #40 です。MDX と #41 です。](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize (& a) #40 です。MDX と #41 です。](../../../mdx/hierarchize-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../../../mdx/mdx-function-reference-mdx.md)  
  
  

