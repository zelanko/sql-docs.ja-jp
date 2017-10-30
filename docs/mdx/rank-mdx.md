---
title: "順位 (MDX) |Microsoft ドキュメント"
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
- RANK
dev_langs:
- kbMDX
helpviewer_keywords:
- Rank function [MDX]
ms.assetid: 3cea35ed-57c4-4b47-a736-cee00275509b
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 89983af39b21ee508a0ddea06bbe953c1cb68b5a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="rank-mdx"></a>Rank (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したセット内の指定した組の 1 から始まる順位付けを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Rank(Tuple_Expression, Set_Expression [ ,Numeric Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、**ランク**関数が、組に対して指定された数値式を評価することによって、指定された組のランクを決定します。 数値式が指定されている場合、**ランク**関数は、セットで重複する値を持つタプルに同じランクを割り当てます。 このように重複する値に同じランクを割り当てる動作は、セット内の後続の組のランクに影響を与えます。 たとえば、次の組は、セット`{(a,b), (e,f), (c,d)}`です。 タプル`(a,b)`組と同じ値を持つ`(c,d)`します。 場合、組`(a,b)`ランクが 1 の場合は、両方の`(a,b)`と`(c,d)`ランクは 1 を必要があります。 ただし、`(e,f)` のランクは 3 になります。 ランクが 2 の組はこのセットには存在できません。  
  
 数値式が指定されていない場合、**ランク**関数は、指定された組の 1 から始まる序数位置を返します。  
  
 **ランク**関数には、セットが順序付けしません。  
  
## <a name="example"></a>例  
 次の例を使用して、顧客と購入日を含む組のセットを返します、**フィルター**、 **NonEmpty**、**項目**、および**ランク**関数を最後の日付を確認するには、各顧客が購入を行うことです。  
  
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
  
 次の例では、**順序**関数ではなく、**ランク**City 階層のメンバーにランクの関数は、Reseller Sales Amount メジャーに基づいており、ランクの順序で表示されます。 使用して、**順序**City 階層のメンバーのセットを関数の最初の注文を 1 回だけ行われ、その後で線形スキャン並べ替えた順で表示される前に並べ替えを行います。  
  
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
 [順序と #40 です。MDX と #41 です。](../mdx/order-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

