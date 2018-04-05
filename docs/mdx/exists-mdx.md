---
title: (MDX) が存在する |Microsoft ドキュメント
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
- Exists function
ms.assetid: 1e1d93b5-5be6-421c-b82b-839538ea50b1
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 2adc9ae709257cc3d44496e9ad4c7d078b76cb92
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="exists-mdx"></a>Exists (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 番目に指定されている組のセットのうち、2 番目に指定されているセットの 1 つ以上の組と共存する組のセットを返します。 この関数は、autoexist によって自動的に実行される操作を手動で実行するために使用します。 詳細については自動が存在するを参照してください[MDX &#40; の主な概念Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
 場合、省略可能な\<メジャー グループ名 > は、提供された場合、2 番目のセットと指定されたメジャー グループのファクト テーブルの行に関連付けられている組の 1 つまたは複数の組と存在する組を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *MeasureGroupName*  
 メジャー グループ名を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
  
1.  Null 値を含んでいるメジャー、メジャー グループ行**Exists** MeasureGroupName 引数が指定されている場合。 これが、この形式の Exists 関数と Nonempty 関数の違いです。これらのメジャーの NullProcessing プロパティが Preserve に設定されている場合、クエリがキューブのその部分に対して実行されると、メジャーは NULL 値を表示します。NonEmpty は常に NULL メジャー値を持つセットから組を削除しますが、MeasureGroupName 引数を持つ Exists は、メジャー値が NULL である場合でも、メジャー グループ行に関連付けられている組をフィルター処理しません。  
  
2.  場合*MeasureGroupName*パラメーターを使用すると、結果は、参照されているメジャー グループ内に表示されるメジャーがあるかどうか以外の場合は、参照されているメジャー グループに表示されるメジャーがないかどうかは、EXISTS は空のセットの値に関係なく、常に返しますに依存は*Set_Expression1*と*Set_Expression2*です。  
  
## <a name="examples"></a>使用例  
 カリフォルニア在住の顧客  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
) ON 1   
FROM [Adventure Works]  
  
```  
  
 売上があったカリフォルニア在住の顧客  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 売上があった顧客  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, , "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 自転車を購入した顧客  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Product].[Product Categories].[Category].&[1]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [クロス結合 &#40;です。MDX と #41 です。](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;です。MDX と #41 です。](../mdx/nonemptycrossjoin-mdx.md)   
 [空でない &#40;です。MDX と #41 です。](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;です。MDX と #41 です。](../mdx/isempty-mdx.md)  
  
  
