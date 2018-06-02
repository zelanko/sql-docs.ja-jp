---
title: ClosingPeriod (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3d082ec7958ab1b29b5b42108d6f9c5c78fc3470
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577364"
---
# <a name="closingperiod-mdx"></a>ClosingPeriod (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたレベルの指定されたメンバーの子孫の中から、最後の兄弟を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ClosingPeriod( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 この関数は、Time 型のディメンションに対して使用することを主目的としていますが、どのディメンションでも使用できます。  
  
-   レベル式が指定されている場合、 **ClosingPeriod**関数は、ディメンションでは、指定されたレベルを含み、指定されたレベルで既定のメンバーの子孫のうち、最後の兄弟を返しますを使用します。  
  
-   レベル式もメンバー式が指定されている場合、 **ClosingPeriod**関数は、指定されたレベルで指定されたメンバーの子孫のうち、最後の兄弟を返します。  
  
-   レベル式もメンバー式が指定されている場合、 **ClosingPeriod**関数を使用して、既定のレベルと、ディメンションのメンバー (存在する場合) 時間の種類を使用してキューブにします。  
  
 **ClosingPeriod**関数は、次の MDX ステートメントに相当します。  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`。  
  
> [!NOTE]  
>  [OpeningPeriod](../mdx/openingperiod-mdx.md)関数がに似ていますが、 **ClosingPeriod**関数点を除いて、 **OpeningPeriod**関数は、最後の兄弟ではなく、最初の兄弟を返します。  
  
## <a name="examples"></a>使用例  
 次の例では、(意味上の型が Time 型と同じである) Date ディメンションの FY2007 メンバーの既定のメジャーに対応する値が返されます。 このメンバーが返されるのは、[All] レベルの最初の子孫が Fiscal Year レベルであるためです。Fiscal 階層は、階層コレクション内の最初のユーザー定義階層であるため既定の階層です。また、FY 2007 メンバーはこの階層内のこのレベルにある最後の兄弟です。  
  
```  
SELECT ClosingPeriod() ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、Date.Date 属性階層の Date.Date.Date レベルにある November 30, 2006 メンバーの既定のメジャーの値を返します。 このメンバーは、Date.Date 属性階層内で [All] レベルの子孫の最後の兄弟です。  
  
```  
SELECT ClosingPeriod ([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、December, 2003 メンバーの既定のメジャーに対応する値が返されます。これは、Calendar ユーザー定義階層の Year レベルにある 2003 メンバーの子孫の最後の兄弟です。  
  
```  
SELECT ClosingPeriod ([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、June, 2003 メンバーの既定のメジャーに対応する値が返されます。これは、Fiscal ユーザー定義階層の Year レベルにある 2003 メンバーの子孫の最後の兄弟です。  
  
```  
SELECT ClosingPeriod ([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [OpeningPeriod &#40;MDX&#41;](../mdx/openingperiod-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40;MDX&#41;](../mdx/lastsibling-mdx.md)  
  
  
