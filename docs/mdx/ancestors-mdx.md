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
manager: kfile
ms.openlocfilehash: 0c108ea102e03000481d18bfc69f657e6bd8a0ce
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313732"
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)


  メンバーから指定したレベルまたは指定された距離にある指定したメンバーのすべての先祖のセットを返す関数。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、返されるセットは常に - 1 つのメンバーで構成されている[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は、1 つのメンバーの複数の親をサポートしていません。  
  
## <a name="syntax"></a>構文  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式。  
  
 *距離*  
 指定されたメンバーからの距離を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **先祖**関数の場合、関数、MDX メンバー式を提供して指定のメンバーの先祖であるレベルの MDX 式または数値式のレベル数を表すそのメンバー上。 この情報により、**先祖**関数は、そのレベル (される 1 つのメンバーで構成されるセット) のメンバーのセットを返します。  
  
> [!NOTE]  
>  先祖のセットではなく先祖メンバーを使用して返される、[先祖](../mdx/ancestor-mdx.md)関数。  
  
 レベル式が指定されている場合、**先祖**関数は、指定されたレベルで指定されたメンバーのすべての先祖のセットを返します。 指定されたレベルと同じ階層内で指定されたメンバーでない場合、関数はエラーを返します。  
  
 距離が指定されている場合、**先祖**関数は、メンバー式で指定された階層内で指定されたステップ数であるすべてのメンバーのセットを返します。 メンバーは、メンバーの属性階層、ユーザー定義階層の場合、または場合によっては、親子階層として指定する場合があります。 番号 1 は、親レベルでメンバーのセットを返し、(存在する場合に、数値として 2 が、親の親レベルでメンバーのセットを返します。 数値として 0 が指定された場合はそのメンバー自体のみを含むセットを返します。  
  
> [!NOTE]  
>  この形式の使用、**先祖**関数の場合、親のレベルが不明またはということはできません。  
  
## <a name="examples"></a>使用例  
 次の例では、**先祖**関数、メンバー、親、およびその親の親の Internet Sales Amount メジャーを返します。 この例では、レベル式を使用して、返すレベルを指定します。 レベルは、メンバー式で指定されたメンバーと同じ階層には。  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、**先祖**関数、メンバー、親、およびその親の親の Internet Sales Amount メジャーを返します。 この例では、数値式を使用して、返されるレベルを指定します。 レベルは、メンバー式で指定されたメンバーと同じ階層には。  
  
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
  
 次の例では、**先祖**関数 Internet Sales Amount メジャー、属性階層のメンバーの親を返します。 この例では、数値式を使用して、返されるレベルを指定します。 メンバー式に含まれるメンバーは、属性階層のメンバーであるために、その親は、[All] レベルになります。  
  
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
  
  
