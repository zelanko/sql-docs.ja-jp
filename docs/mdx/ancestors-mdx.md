---
title: 先祖 (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb15caffbe8461da0ce04385bc58d7f1815483b5
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577004"
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定メンバーの先祖のうち、指定されたレベルまたはメンバーから指定された距離だけ離れた位置にあるすべての先祖のセットを返す関数です。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、1 つのメンバーのセットが返されますでは常に[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]1 つのメンバーに複数の親をサポートしていません。  
  
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
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *距離*  
 指定されたメンバーからの距離を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **先祖**関数、MDX メンバー式で、関数を提供して、そのメンバーの先祖であるレベルの MDX 式または数値式をそのメンバー上のレベルの数を表すのいずれかを指定します。 この情報により、**先祖**関数は、そのレベル (される 1 つのメンバーで構成されるセット) のメンバーのセットを返します。  
  
> [!NOTE]  
>  先祖のセットではなく先祖メンバーを使用して返される、[先祖](../mdx/ancestor-mdx.md)関数。  
  
 レベル式が指定されている場合、**先祖**関数は、指定されたレベルで指定されたメンバーのすべての先祖のセットを返します。 指定されたメンバーが指定されたレベルと同じ階層内に存在しない場合、関数はエラーを返します。  
  
 距離が指定されている場合、**先祖**関数、メンバー式で指定された階層内で指定されたステップ数であるすべてのメンバーのセットを返します。 メンバーは、またはグループのメンバー、属性階層、ユーザー定義の階層、場合によっては、親子階層として指定することがあります。 数値として 1 が指定された場合は親レベルにあるメンバーのセットを返し、数値として 2 が指定された場合は親より 1 つ上のレベルにあるメンバーのセット (存在する場合) を返します。 数値として 0 が指定された場合はそのメンバー自体のみを含むセットを返します。  
  
> [!NOTE]  
>  この形式の使用、**先祖**関数の場合、親のレベルが不明または名前を付けることはできません。  
  
## <a name="examples"></a>使用例  
 次の例では、**先祖**関数、メンバー、親、およびその親の親の Internet Sales Amount メジャーを返します。 この例では、レベル式を使用して、返すレベルを指定します。 このレベルは、メンバー式で指定されたメンバーと同じ階層にあります。  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、**先祖**関数、メンバー、親、およびその親の親の Internet Sales Amount メジャーを返します。 この例では、数値式を使用して、返されるレベルを指定します。 このレベルは、メンバー式で指定されたメンバーと同じ階層にあります。  
  
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
  
 次の例では、**先祖**関数を属性階層のメンバーの親の Internet Sales Amount メジャーを返します。 この例では、数値式を使用して、返すレベルを指定します。 メンバー式内のメンバーは属性階層のメンバーであるため、その親は [All] レベルです。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
