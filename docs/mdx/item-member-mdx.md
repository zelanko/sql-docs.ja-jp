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
manager: kfile
ms.openlocfilehash: 92745085a408503a2b435eb160daf431c7fdaa32
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63272842"
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
  
 *Index*  
 返される組内の位置によって、特定のメンバーを指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **項目**関数が、指定された組からメンバーを返します。 指定した 0 から始まる位置にあるメンバーを返します*インデックス*します。  
  
## <a name="example"></a>例  
 次の例では、列の `[2003]` 組に含まれる最初のアイテムである `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` メンバーを返します。  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
