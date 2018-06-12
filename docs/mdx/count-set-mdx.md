---
title: Count (セット) (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31e048329fde26d947b7d7978ee2d364d4901b34
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740551"
---
# <a name="count-set-mdx"></a>Count (セット) (MDX)


  セット内のセル数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>コメント  
 **Count (セット)** 関数を追加または使用する構文に応じて、空のセルを除外します。 空のセルの除外またはを使用して含まれている標準の構文を使用する場合、 **EXCLUDEEMPTY**または**INCLUDEEMPTY**フラグにより、それぞれします。 代替構文を使用した場合、空白セルは常に対象に含められます。  
  
 空のセル セットの数に、除外する、標準の構文と省略可能なを使用して**EXCLUDEEMPTY**フラグ。  
  
> [!NOTE]  
>  **Count (セット)** 関数は、既定では空のセルをカウントします。 これに対し、**カウント**セットをカウントする OLE DB 内の関数は、既定で空白セルを除外します。  
  
## <a name="examples"></a>使用例  
 次の例では、Product ディメンションの Model Name 属性階層の子で構成されるメンバーのセットに含まれるセル数をカウントします。  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、Product ディメンションに製品の数をカウントを使用して、 **DrilldownLevel**関数と組み合わせて、**カウント**関数。  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 次の例を使用して、前のカレンダー四半期と比べて売上が減少した再販業者を返して、**カウント**関数と組み合わせて、**フィルター**関数およびその他の関数の数。 このクエリを使用して、**集計**など、クライアント アプリケーションでドロップダウン リストから選択のため、複数の地理的なメンバーの選択をサポートする関数。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
   (Filter  
      (Existing(Reseller.Reseller.Reseller),  
         [Measures].[Reseller Sales Amount]   
         < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
      )  
   )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate  
   ( {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
   )  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})  
      })  
   ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,  
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
   ,[Measures].[Declining Reseller Sales])  
  
```  
  
## <a name="see-also"></a>参照  
 [カウント&#40;ディメンション&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [カウント&#40;階層レベル&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [カウント&#40;組&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [プロパティ&#40;MDX&#41;](../mdx/properties-mdx.md)   
 [集計&#40;MDX&#41;](../mdx/aggregate-mdx.md)   
 [フィルター &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
