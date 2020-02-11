---
title: Item (メンバー) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d7afa88f9d6239c8da7cb9c406ef11f0764f8dcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905908"
---
# <a name="item-member-mdx"></a>Item (メンバー) (MDX)


  指定された組からメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
 *化*  
 返されるタプル内の位置によって特定のメンバーを指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 **Item**関数は、指定された組からメンバーを返します。 関数は、 *Index*で指定された0から始まる位置で見つかったメンバーを返します。  
  
## <a name="example"></a>例  
 次の例では、列の `[2003]` 組に含まれる最初のアイテムである `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` メンバーを返します。  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
