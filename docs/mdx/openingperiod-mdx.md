---
title: OpeningPeriod (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 07f94c3ed850af10120b1de7d95941bc5c90e826
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088221"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)


  指定されたレベルの子孫の中で最初の兄弟を返します。オプションで、指定したメンバーでも取得できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 この関数は、主に時間ディメンションを使用することを目的としていますが、どのディメンションでも使用できます。  
  
-   レベル式が指定されている場合、 **OpeningPeriod**関数は、指定されたレベルを含む階層を使用して、指定したレベルの既定のメンバーの子孫の中から最初の兄弟を返します。  
  
-   レベル式とメンバー式の両方が指定されている場合、 **OpeningPeriod**関数は、指定されたレベルを含む階層内で、指定されたメンバーの子孫の中から、最初の兄弟を返します。  
  
-   レベル式もメンバー式も指定されていない場合、 **OpeningPeriod**関数では、Time 型の既定のレベルとディメンションのメンバーが使用されます。  
  
> [!NOTE]  
>  [Closingperiod](../mdx/closingperiod-mdx.md)関数は、 **OpeningPeriod**関数に似ていますが、 **closingperiod**関数は、最初の兄弟ではなく最後の兄弟を返す点が異なります。  
  
## <a name="examples"></a>例  
 次の例では、Date ディメンション (Time 型) の FY2002 メンバーの既定のメジャーの値を返します。 このメンバーが返されるのは、会計年度レベルが [All] レベルの最初の子孫であるためです。これは、会計階層が階層コレクション内の最初のユーザー定義階層であり、FY2002 メンバーがの最初の兄弟であるためです。このレベルの階層です。  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、date. date の属性階層の date. date. date レベルにある、2001年7月1日の既定のメジャーの値を返します。 このメンバーは、Date 属性階層の [All] レベルの子孫の最初の兄弟です。  
  
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
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)  
  
  
