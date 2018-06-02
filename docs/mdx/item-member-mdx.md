---
title: Item (メンバー) (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cb7c3825f2a319282788c222a7ebb46cec2b532
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578834"
---
# <a name="item-member-mdx"></a>Item (メンバー) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>コメント  
 **項目**関数は、指定された組からメンバーを返します。 指定された 0 から始まる位置で見つかるメンバーを返します*インデックス*です。  
  
## <a name="example"></a>例  
 次の例では、列の `[2003]` 組に含まれる最初のアイテムである `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` メンバーを返します。  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
