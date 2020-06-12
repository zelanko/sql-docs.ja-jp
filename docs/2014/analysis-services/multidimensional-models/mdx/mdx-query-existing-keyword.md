---
title: EXISTING キーワード (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546214"
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
  
## <a name="remarks"></a>Remarks  
 既定では、セットの評価は、そのセットのメンバーを含むキューブのコンテキストで実行されます。 `Existing` キーワードを指定すると、指定されているセットの評価が現在のコンテキストで行われます。  
  
## <a name="example"></a>例  
 次の例では、`Aggregate`  関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。 Product ディメンションに含まれる製品カテゴリに関して減少した売上の値を返すために、 [Hierarchize (MDX)](/sql/mdx/hierarchize-mdx) 関数および [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) 関数を使用しています。 キーワードを使用 `Existing` すると、関数内のセットが `Filter` 現在のコンテキストで評価されるようになります。つまり、ワシントンおよびオレゴン州の属性階層のオレゴンメンバーに対して評価されます。  
  
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
 [MDX&#41;&#41; &#40;設定 &#40;数](/sql/mdx/count-set-mdx)   
 [MDX&#41;&#40;の Add演算メンバー](/sql/mdx/addcalculatedmembers-mdx)   
 [MDX&#41;の集計 &#40;](/sql/mdx/aggregate-mdx)   
 [MDX&#41;のフィルター処理 &#40;](/sql/mdx/filter-mdx)   
 [MDX&#41;&#40;プロパティ](/sql/mdx/properties-mdx)   
 [MDX&#41;&#40;ドリルダウンレベル](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx)   
 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
