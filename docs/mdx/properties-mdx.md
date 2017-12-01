---
title: "プロパティ (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Properties
dev_langs: kbMDX
helpviewer_keywords: Properties function
ms.assetid: 2d8442c5-30c4-4fd1-99ea-9845b6533e41
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1177ef96713961af17a7c76b1f3bce01a8089688
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="properties-mdx"></a>Properties (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  メンバー プロパティ値を含む文字列または厳密に型指定された値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Property_Name*  
 メンバー プロパティの名前を表す有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **プロパティ**関数は、指定したメンバー プロパティの指定されたメンバーの値を返します。 メンバー プロパティがする固有メンバー プロパティのいずれかのように**名前**、 **ID**、**キー**、または**キャプション**、またはユーザー定義メンバー プロパティを指定できます。 詳細については、次を参照してください。[固有メンバー プロパティ &#40;です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md)と[ユーザー定義メンバー プロパティ &#40;です。MDX と #41 です;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md)。  
  
 既定では、強制的に文字列型の値が返されます。 場合**型指定された**を指定すると、戻り値が厳密に型指定します。  
  
-   プロパティの型が組み込み型の場合、この関数はメンバーの元の型を返します。  
  
-   戻り値の型と同じ戻り値の型は、プロパティの型が定義されているユーザーの場合、 **MemberValue**関数。  
  
> [!NOTE]  
>  Key プロパティは、複合キーを除いて Key0 と同じ結果を返します。 Key プロパティは、複合キーに関しては NULL を返します。 キーを使用して*x*の例のように、複合キーの構文。 Key0 プロパティ、Key1 プロパティ、Key2 プロパティなどは、全体として複合キーを形成します。  
  
## <a name="example"></a>例  
 次の例では、固有メンバー プロパティとユーザー定義メンバー プロパティを返しています。Day Name メンバー プロパティについては TYPED 引数を使用して、戻り値の型を厳密に指定しています。  
  
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
  
SELECT {Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  ON 0  
FROM [Adventure Works]  
```  
  
 次の例は、キーの使用を示しています。*x*プロパティです。  
  
```  
WITH   
MEMBER Measures.MemberKey AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key')  
MEMBER Measures.MemberKey0 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key0')  
MEMBER Measures.MemberKey1 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key1')  
  
SELECT {Measures.MemberKey  
   , Measures.MemberKey0  
   , Measures.MemberKey1     
   }  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [メンバーのプロパティ &#40; を使用します。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
