---
title: (MDX) が存在する |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7237a4023bf9ad67f0050951b60b1ee33db4a53f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740611"
---
# <a name="exists-mdx"></a>Exists (MDX)


  1 番目に指定されている組のセットのうち、2 番目に指定されているセットの 1 つ以上の組と共存する組のセットを返します。 この関数は、autoexist によって自動的に実行される操作を手動で実行するために使用します。 詳細については自動が存在するを参照してください[MDX の主な概念&#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)です。  
  
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
  
## <a name="remarks"></a>コメント  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin &#40;MDX&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [空でない&#40;MDX&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)  
  
  
