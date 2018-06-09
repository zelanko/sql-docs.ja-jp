---
title: プロパティ (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c29d9b29078d6097b512acb93ff47eef018592c8
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742701"
---
# <a name="properties-mdx"></a>Properties (MDX)


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
  
## <a name="remarks"></a>コメント  
 **プロパティ**関数は、指定したメンバー プロパティの指定されたメンバーの値を返します。 メンバー プロパティがする固有メンバー プロパティのいずれかのように**名前**、 **ID**、**キー**、または**キャプション**、またはユーザー定義メンバー プロパティを指定できます。 詳細については、次を参照してください。[固有メンバー プロパティ&#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md)と[ユーザー定義メンバー プロパティ&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md)です。  
  
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
 [メンバー プロパティを使用して&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
