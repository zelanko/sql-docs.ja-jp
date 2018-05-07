---
title: StripCalculatedMembers (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRIPCALCULATEDMEMBERS
dev_langs:
- kbMDX
helpviewer_keywords:
- StripCalculatedMembers function
ms.assetid: c71725df-f435-4454-9122-6729ddad8cc7
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 91724b263f658baed8715cf68be0c30d4bbd82c4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stripcalculatedmembers-mdx"></a>StripCalculatedMembers (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  計算されるメンバーを指定されたセットから削除して生成したセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StripCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>解説  
 **StripCalculatedMembers**関数は、セットから計算されるメンバーを削除します。 計算されるメンバーを使用してセットに追加することができます、 [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md)関数で、サーバーで定義されている計算されるメンバーまたは WITH MEMBER 構文を使用して、クエリ自体内で追加された計算されるメンバーを返します。  
  
## <a name="example"></a>例  
 次の例では、すべての計算されるメンバーがクエリから削除されます。  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT StripCalculatedMembers(  
   { Measures.DefaultMember  
   , Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  
   )  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
