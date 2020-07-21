---
title: 先祖 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8551e6fdac54b3eb4c20f13f6722936df1c92feb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017103"
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)


  指定されたレベルまたはメンバーから指定された距離にある、指定されたメンバーのすべての先祖のセットを返す関数。 で[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は、返されるセットは常に1つのメンバー [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]で構成されます。1つのメンバーに対して複数の親はサポートされません。  
  
## <a name="syntax"></a>構文  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *距離*  
 指定されたメンバーからの距離を指定する有効な数値式です。  
  
## <a name="remarks"></a>Remarks  
 **先祖**関数では、mdx メンバー式を使用して関数を指定し、そのメンバーの先祖であるレベルの mdx 式、またはそのメンバーの上位レベルの数を表す数値式のいずれかを指定します。 この情報を使用すると、**先祖**関数は、そのレベルでメンバーのセット (1 つのメンバーで構成されるセット) を返します。  
  
> [!NOTE]  
>  先祖のセットではなく先祖メンバーを返すには、[先祖](../mdx/ancestor-mdx.md)関数を使用します。  
  
 レベル式が指定されている場合、**先祖**関数は、指定されたレベルにある指定されたメンバーのすべての先祖のセットを返します。 指定したメンバーが指定したレベルと同じ階層内にない場合、関数はエラーを返します。  
  
 距離が指定されている場合、**先祖**関数は、メンバー式で指定された階層内で指定されたステップ数であるすべてのメンバーのセットを返します。 メンバーは、属性階層、ユーザー定義階層、または場合によっては親子階層のメンバーとして指定することができます。 1を指定すると、親レベルでメンバーのセットが返され、2を指定すると、親レベル (存在する場合) のメンバーのセットが返されます。 数値として 0 が指定された場合はそのメンバー自体のみを含むセットを返します。  
  
> [!NOTE]  
>  この形式の**先祖**関数は、親のレベルが不明な場合、または名前を指定できない場合に使用します。  
  
## <a name="examples"></a>使用例  
 次の例では、**先祖**関数を使用して、メンバー、その親、およびその親の親の Internet Sales Amount メジャーを返します。 この例では、レベル式を使用して、返すレベルを指定します。 レベルは、メンバー式で指定されたメンバーと同じ階層にあります。  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、**先祖**関数を使用して、メンバー、その親、およびその親の親の Internet Sales Amount メジャーを返します。 この例では、数値式を使用して、返されるレベルを指定します。 レベルは、メンバー式で指定されたメンバーと同じ階層にあります。  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 次の例では、**先祖**関数を使用して、属性階層のメンバーの親の Internet Sales Amount メジャーを返します。 この例では、数値式を使用して、返されるレベルを指定します。 メンバー式のメンバーは属性階層のメンバーであるため、その親は [All] レベルです。  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
