---
title: "PrevMember (MDX) |Microsoft ドキュメント"
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
- PREVMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- PrevMember function
ms.assetid: 4d8c9c6b-13b6-4baf-bd1b-8e8f89187080
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fbf6613bc3524bd2a460828acdd764cc60d6cbd5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="prevmember-mdx"></a>PrevMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたメンバーを含むレベルにある直前のメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.PrevMember   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **PrevMember**関数は、指定されたメンバーと同じレベルに前のメンバーを返します。  
  
## <a name="example"></a>例  
 次の例では、簡単なクエリを使用して、 **PrevMember**行軸に現在のメンバーの直前のメンバーの名前を表示する関数。  
  
 `WITH MEMBER MEASURES.PREVMEMBERDEMO AS`  
  
 `[Date].[Calendar].CURRENTMEMBER.PREVMEMBER.NAME`  
  
 `SELECT MEASURES.PREVMEMBERDEMO ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の例では、Aggregate 関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。 **Hierarchize**と**DrillDownLevel** Product ディメンションに製品カテゴリに関して減少した売上の値を返す関数を使用します。 **PrevMember**関数を使用して、前の期と現在の期と比較します。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

