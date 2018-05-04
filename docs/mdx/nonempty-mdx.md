---
title: NonEmpty (MDX) |Microsoft ドキュメント
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
dev_langs:
- kbMDX
helpviewer_keywords:
- NonEmpty function
ms.assetid: dfbfa747-3175-405c-aa5b-15c187b06338
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d533d6e5e0d62219f144b325b97142039e4eb5bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="nonempty-mdx"></a>NonEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセットと 2 番目のセットのクロス積に基づいて、指定されたセットから空ではない組のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>引数  
 *set_expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *set_expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>解説  
 この関数は、指定されている 1 番目のセット内の組のうち、2 番目のセット内のすべての組に対して評価した際に空でなかった組を返します。 **NonEmpty**関数は計算を考慮し、重複する組を保持します。 2 番目のセットが指定されなかった場合、属性階層のメンバーとキューブ内のメジャーの現在の座標のコンテキストで式が評価されます。  
  
> [!NOTE]  
>  非推奨ではなくこの関数を使用して[NonEmptyCrossjoin &#40;MDX&#41; ](../mdx/nonemptycrossjoin-mdx.md)関数。  
  
> [!IMPORTANT]  
>  空ではないという特性は、組自体ではなく、組から参照されるセルの特性です。  
  
## <a name="examples"></a>使用例  
 次のクエリは、簡単な例を示しています。 **NonEmpty**、年 7 月 1 日の 2001 年に Internet Sales Amount の null 以外の値を持っている顧客をすべて返します。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の例は、顧客と購入日を使用する組のセットを返します、**フィルター**関数および**NonEmpty**する最後の日付を確認するには、各顧客が購入を行う関数。  
  
 `WITH SET MYROWS AS FILTER`  
  
 `(NONEMPTY`  
  
 `([Customer].[Customer Geography].[Customer].MEMBERS`  
  
 `* [Date].[Date].[Date].MEMBERS`  
  
 `, [Measures].[Internet Sales Amount]`  
  
 `) AS MYSET`  
  
 `, NOT(MYSET.CURRENT.ITEM(0)`  
  
 `IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))`  
  
 `)`  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `MYROWS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [DefaultMember &#40;MDX&#41;](../mdx/defaultmember-mdx.md)   
 [フィルターと #40 です。MDX と #41 です。](../mdx/filter-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
