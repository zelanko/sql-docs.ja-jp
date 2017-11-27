---
title: "OpeningPeriod (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENINGPERIOD
dev_langs:
- kbMDX
helpviewer_keywords:
- OpeningPeriod function
ms.assetid: bebf55cf-e5c6-42b1-98f2-1d6e54093d4c
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 30100b2762d3365c1599e665db54e2446e392fb3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>解説  
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
 [TopCount & #40 です。MDX と #41 です。](../mdx/topcount-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling & #40 です。MDX と #41 です。](../mdx/firstsibling-mdx.md)  
  
  

