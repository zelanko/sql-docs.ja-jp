---
title: "Hierarchize (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: HIERARCHIZE
dev_langs: kbMDX
helpviewer_keywords: Hierarchize function
ms.assetid: e9795003-70e7-4b4c-9074-45b5b9b817fa
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 14719e4ec362b140cee189231f983ac772a567af
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="hierarchize-mdx"></a>Hierarchize (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットのメンバーを階層化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>Remarks  
 **Hierarchize**関数は階層の順序に指定されたセットのメンバーを編成します。 この関数は、常に重複部分を保持します。  
  
-   場合**POST**が指定されていない、関数は、自然な順序でレベル内のメンバーを並べ替えます。 自然な順序とは、他の並べ替え条件が指定されていない場合の、階層に沿ったメンバーの既定の順序です。 子メンバーは親メンバーの直後になります。  
  
-   場合**POST**を指定すると、 **Hierarchize**関数は、後の自然な順序を使用して、レベル内のメンバーを並べ替えます。 つまり、子メンバーは親メンバーの前になります。  
  
## <a name="example"></a>例  
 次の例では、Canada メンバーに対してドリル アップを行っています。 **Hierarchize**関数を使用して必要な階層の順序で指定されたセット メンバーを整理、 **DrillUpMember**関数。  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 次の例は、の合計を返して、`Measures.[Order Quantity]`集計に含まれている 2003年の 9 か月の最初のメンバー、`Date`ディメンションから、 **Adventure Works**キューブ。 **PeriodsToDate**関数、集計関数演算対象となるセット内の組を定義します。 **Hierarchize**関数は、階層の順序で、Product ディメンションのメンバーの指定されたセットのメンバーを編成します。  
  
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
  
  
