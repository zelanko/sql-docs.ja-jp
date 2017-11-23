---
title: "Item (メンバー) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ITEM
dev_langs: kbMDX
helpviewer_keywords: Item function
ms.assetid: 71cca249-910b-4ecd-9097-1a17b224e219
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6f35b9e90c01f55e66045ae54d6f8c3b8e2166e0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="item-member-mdx"></a>Item (メンバー) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された組からメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
 *Index*  
 返す組内の特定のメンバーを位置で指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 **項目**関数は、指定された組からメンバーを返します。 指定された 0 から始まる位置で見つかるメンバーを返します*インデックス*です。  
  
## <a name="example"></a>例  
 次の例では、列の `[2003]` 組に含まれる最初のアイテムである `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` メンバーを返します。  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
