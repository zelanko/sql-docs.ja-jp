---
title: ClosingPeriod (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CLOSINGPERIOD
dev_langs:
- kbMDX
helpviewer_keywords:
- ClosingPeriod function
ms.assetid: ae709017-219d-43e1-a98a-a85bd365b4cd
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d53c0686742f096f49519da93e64ea2b6706d056
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>解説  
 この関数は、Time 型のディメンションに対して使用することを主目的としていますが、どのディメンションでも使用できます。  
  
-   レベル式が指定されている場合、 **ClosingPeriod**関数は、ディメンションでは、指定されたレベルを含み、指定されたレベルで既定のメンバーの子孫のうち、最後の兄弟を返しますを使用します。  
  
-   レベル式もメンバー式が指定されている場合、 **ClosingPeriod**関数は、指定されたレベルで指定されたメンバーの子孫のうち、最後の兄弟を返します。  
  
-   レベル式もメンバー式が指定されている場合、 **ClosingPeriod**関数を使用して、既定のレベルと、ディメンションのメンバー (存在する場合) 時間の種類を使用してキューブにします。  
  
 **ClosingPeriod**関数は、次の MDX ステートメントに相当します。  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`」を参照してください。  
  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40;MDX&#41;](../mdx/lastsibling-mdx.md)  
  
  
