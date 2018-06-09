---
title: OpeningPeriod (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01144d6a82319b7853ae60f901a5fc0ad3c78d6c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742441"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)


  指定したレベルの子孫で、最初の兄弟を返します。オプションでメンバーも指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 この関数は、時間ディメンションに対して使用することを主な目的としていますが、どのディメンションでも使用できます。  
  
-   レベル式が指定されている場合、 **OpeningPeriod**関数は、指定されたレベルを含み、指定されたレベルで既定のメンバーの子孫のうち最初の兄弟を返します。 階層を使用します。  
  
-   レベル式もメンバー式が指定されている場合、 **OpeningPeriod**関数は、指定されたレベルを含む階層内で指定されたレベルで指定されたメンバーの子孫のうち、最初の兄弟を返します。  
  
-   レベル式もメンバー式が指定されている場合、 **OpeningPeriod**関数と Time 型の既定のレベルと、ディメンションのメンバーを使用します。  
  
> [!NOTE]  
>  [ClosingPeriod](../mdx/closingperiod-mdx.md)関数がに似ていますが、 **OpeningPeriod**関数点を除いて、 **ClosingPeriod**関数は、最初の兄弟ではなく、最後の兄弟を返します。  
  
## <a name="examples"></a>使用例  
 次の例では、(意味上の型が Time 型と同じである) Date ディメンションの FY2002 メンバーの既定のメジャーに対応する値が返されます。 このメンバーが返されるのは、[All] レベルの最初の子孫が Fiscal Year レベルであるためです。Fiscal 階層は、階層コレクション内の最初のユーザー定義階層であるため既定の階層です。また、FY 2002 メンバーはこの階層内のこのレベルにある最初の兄弟です。  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、Date.Date 属性階層の Date.Date.Date レベルにある July 1, 2001 メンバーの既定のメジャーの値が返されます。 このメンバーは、Date.Date 属性階層内の [All] レベルの子孫の最初の兄弟です。  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、January, 2003 メンバーの既定のメジャーに対応する値が返されます。これは、Calendar ユーザー定義階層の Year レベルにある 2003 メンバーの子孫の最初の兄弟です。  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、July, 2002 メンバーの既定のメジャーに対応する値が返されます。これは、Fiscal ユーザー定義階層の Year レベルにある 2003 メンバーの子孫の最初の兄弟です。  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)  
  
  
