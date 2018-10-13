---
title: EXISTING キーワード (MDX) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d41b49e4585d2a256250a009b09ffa9ed94ea925
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906198"
---
# <a name="mdx-query---existing-keyword"></a>MDX クエリ - EXISTING キーワード
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指定されたセットを現在のコンテキストで評価するように設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 有効な多次元式 (MDX) セット式です。  
  
## <a name="remarks"></a>コメント  
 既定では、セットの評価は、そのセットのメンバーを含むキューブのコンテキストで実行されます。 **Existing** キーワードを指定すると、指定されているセットの評価が現在のコンテキストで行われます。  
  
## <a name="example"></a>例  
 次の例では、 **Aggregate** 関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。 Product ディメンションに含まれる製品カテゴリに関して減少した売上の値を返すために、 [Hierarchize (MDX)](../../../mdx/hierarchize-mdx.md) 関数および [DrilldownLevel (MDX)](../../../mdx/drilldownlevel-mdx.md) 関数を使用しています。 **既存**キーワードのセットを強制する、**フィルター** State-province 属性階層の Washington および Oregon メンバーには、現在のコンテキストで評価する関数。  
  
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
 [AddCalculatedMembers (MDX)](../../../mdx/addcalculatedmembers-mdx.md)   
 [Aggregate (MDX)](../../../mdx/aggregate-mdx.md)   
 [Filter (MDX)](../../../mdx/filter-mdx.md)   
 [Properties (MDX)](../../../mdx/properties-mdx.md)   
 [DrilldownLevel (MDX)](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize (MDX)](../../../mdx/hierarchize-mdx.md)   
 [MDX 関数リファレンス (MDX)](../../../mdx/mdx-function-reference-mdx.md)  
  
  
