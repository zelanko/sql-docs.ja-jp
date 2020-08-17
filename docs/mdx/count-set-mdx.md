---
description: Count (セット) (MDX)
title: Count (セット) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3a8760d4df4aa1479aaa9ad365c92a5168eb3869
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341528"
---
# <a name="count-set-mdx"></a>Count (セット) (MDX)


  セット内のセルの数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Count (セット)** 関数は、使用する構文に応じて、空のセルを含めたり除外したりします。 標準構文を使用する場合は、 **Excludeempty** または **includeempty** フラグを使用して、空のセルを除外または含めることができます。 代替構文を使用する場合、関数には常に空のセルが含まれます。  
  
 セットの数に含まれる空のセルを除外するには、標準の構文とオプションの **Excludeempty** フラグを使用します。  
  
> [!NOTE]  
>  **Count (セット)** 関数は、既定では空のセルをカウントします。 これに対して、セットをカウントする OLE DB の **Count** 関数は、既定では空のセルを除外します。  
  
## <a name="examples"></a>例  
 次の例では、Product ディメンションのモデル名属性階層の子で構成されるメンバーのセットに含まれるセルの数をカウントします。  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、**カウント**関数と共に**ドリルダウンレベル**関数を使用して、Product ディメンション内の製品の数をカウントします。  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 次の例では、 **Count** 関数を **フィルター** 関数およびその他の多くの関数と組み合わせて使用することによって、前の calendar quarter と比較して売上が減少している再販業者が返されます。 このクエリでは、 **集計** 関数を使用して、クライアントアプリケーションのドロップダウンリスト内から選択するなど、複数の geography メンバーの選択をサポートします。  
  
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
 [&#40;ディメンション&#41; &#40;MDX&#41;のカウント ](../mdx/count-dimension-mdx.md)   
 [MDX&#41;&#41; &#40;&#40;階層レベルのカウント ](../mdx/count-hierarchy-levels-mdx.md)   
 [MDX&#41;&#41; &#40;組 &#40;数 ](../mdx/count-tuple-mdx.md)   
 [MDX&#41;&#40;ドリルダウンレベル ](../mdx/drilldownlevel-mdx.md)   
 [MDX&#41;&#40;の Add演算メンバー ](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [MDX&#41;&#40;プロパティ ](../mdx/properties-mdx.md)   
 [MDX&#41;の集計 &#40;](../mdx/aggregate-mdx.md)   
 [MDX&#41;のフィルター処理 &#40;](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
