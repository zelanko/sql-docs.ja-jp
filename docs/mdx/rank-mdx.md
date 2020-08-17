---
description: Rank (MDX)
title: Rank (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 391ba9d805684a9fd469d8e6c66727caba71ce70
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341338"
---
# <a name="rank-mdx"></a>Rank (MDX)


  指定されたセット内の指定された組の1から始まる順位を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Rank(Tuple_Expression, Set_Expression [ ,Numeric Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **Rank** 関数は、組に対して指定された数値式を評価することによって、指定された組の1から始まる順位を決定します。 数値式が指定されている場合、 **rank** 関数は、セット内の重複する値を持つ組に同じランクを割り当てます。 このように重複する値に同じランクを割り当てる動作は、セット内の後続の組のランクに影響を与えます。 たとえば、セットは次の組で構成さ `{(a,b), (e,f), (c,d)}` れます。 タプルは `(a,b)` 組と同じ値を持ち `(c,d)` ます。 組の `(a,b)` ランクが1の場合、 `(a,b)` との両方に `(c,d)` ランクが1になります。 ただし、`(e,f)` のランクは 3 になります。 ランクが 2 の組はこのセットには存在できません。  
  
 数値式が指定されていない場合、 **Rank** 関数は、指定された組の1から始まる序数位置を返します。  
  
 Rank 関数では、セットは順序 **付け** されません。  
  
## <a name="example"></a>例  
 次の例では、各顧客が購入した最後の日付を検索するために、 **Filter**、 **空**でない、 **Item**、および **Rank** 関数を使用して、顧客と購入日を含む組のセットを返します。  
  
```  
WITH SET MYROWS AS FILTER  
   (NONEMPTY  
      ([Customer].[Customer Geography].MEMBERS  
         * [Date].[Date].[Date].MEMBERS  
         , [Measures].[Internet Sales Amount]  
      ) AS MYSET  
   , NOT(MYSET.CURRENT.ITEM(0)  
      IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))  
   )  
SELECT [Measures].[Internet Sales Amount] ON 0,  
MYROWS ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、 **rank**関数ではなく**order**関数を使用して、再販業者の Sales Amount メジャーに基づいて City 階層のメンバーにランクを付け、順位付きで表示します。 **Order**関数を使用して City 階層のメンバーのセットを最初に並べ替えると、並べ替えは一度だけ実行された後、線形スキャンが行われてから、並べ替えられた順序で表示されます。  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#40;順序 ](../mdx/order-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
