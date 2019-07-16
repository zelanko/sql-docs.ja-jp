---
title: Properties (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e7d6e072cd47233b6cb76c09fb3bc0e9b9b42604
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020653"
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
 メンバーのプロパティ名の有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 **Properties**関数は、指定したメンバー プロパティの指定されたメンバーの値を返します。 メンバー プロパティがする固有メンバー プロパティのいずれかなど、**名前**、 **ID**、**キー**、または**キャプション**、することもできます、ユーザー定義メンバー プロパティです。 詳細については、次を参照してください。[固有メンバー プロパティ&#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md)と[ユーザー定義メンバー プロパティ&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md)します。  
  
 既定では、値は、文字列に強制的に変換されます。 場合**型指定された**を指定すると、戻り値が厳密に型指定します。  
  
-   プロパティの型が組み込み型の場合、この関数はメンバーの元の型を返します。  
  
-   戻り値の型の戻り値の型と同じでは、プロパティの型が定義されているユーザーの場合、 **MemberValue**関数。  
  
> [!NOTE]  
>  プロパティ (キー) は、複合キーを除いて Key0 と同じ結果を返します。 (キー) のプロパティは複合キーの null を返します。 キーを使用して*x*の例に示すように、複合キーの構文。 プロパティ ('Key0')、Properties('Key1') Properties('Key2') など、複合キーを形成します。  
  
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
  
 次の例は、キーの使用を示しています。*x*プロパティ。  
  
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
 [メンバー プロパティの使用 &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
