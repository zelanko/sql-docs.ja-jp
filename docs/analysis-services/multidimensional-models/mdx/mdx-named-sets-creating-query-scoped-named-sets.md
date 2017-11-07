---
title: "名前付きセット (MDX) のクエリ スコープを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06751ad71a12e537728167d4d8a9cdec0a870962
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-named-sets---creating-query-scoped-named-sets"></a>名前付きセットの名前付きセットのクエリ スコープを作成する MDX
  1 つの多次元式 (MDX) クエリでのみ名前付きセットが必要な場合は、WITH キーワードを使用してその名前付きセットを定義できます。 WITH キーワードを使用して作成した名前付きセットは、そのクエリの実行が終了した時点で存在しなくなります。  
  
 このトピックで説明するように、WITH キーワードの構文は非常に柔軟なので、名前付きセットを定義するための関数も使用できます。  
  
> [!NOTE]  
>  名前付きセットの詳細については、「[MDX での名前付きセットの作成 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)」を参照してください。  
  
## <a name="with-keyword-syntax"></a>WITH キーワードの構文  
 MDX の SELECT ステートメントに WITH キーワードを追加するための構文は、以下のとおりです。  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 WITH キーワードの構文で使用する `Set_Identifier` パラメーターには、名前付きセットの別名を指定します。 `Set_Expression` パラメーターには、名前付きセットの別名が参照するセット式を指定します。  
  
## <a name="with-keyword-example"></a>WITH キーワードの例  
 以下に示すのは、Microsoft SQL Server 2000 Analysis Services のサンプル データベース **FoodMart 2000**に登録されている Chardonnay ワインと Chablis ワインの売上数量を調べる MDX クエリです。 このクエリは、結果セットという観点からすれば非常にシンプルですが、クエリの管理という観点から見ると長すぎて扱いが厄介です。  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 この MDX クエリを管理しやすくするために、WITH キーワードを使用してこのクエリのための名前付きセットを作成できます。 以下に示すのは、WITH キーワードを使用して `[ChardonnayChablis]`という名前付きセットを作成し、その名前付きセットを使用して SELECT ステートメントを短くする方法を示したコードです。  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a>WITH キーワードで関数を使用する方法  
 名前付きセットの各メンバーを明示的に定義することもできますが、その場合はステートメントが長くなってしまうことがあります。 名前付きセットの作成と管理を簡略化するために、MDX 関数を使用してメンバーを定義できます。  
  
 たとえば、次に示す MDX クエリでは、 [Filter](../../../mdx/filter-mdx.md)、 [CurrentMember](../../../mdx/currentmember-mdx.md)、 [Name](../../../mdx/name-mdx.md) の各 MDX 関数と VBA の InStr 関数を使用して名前付きセット `[ChardonnayChablis]` を作成しています。 この名前付きセット `[ChardonnayChablis]` は、明示的に定義した上記の名前付きセットと同じです。  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a>参照  
 [SELECT ステートメント (MDX)](../../../mdx/mdx-data-manipulation-select.md)   
 [名前付きセット &#40; のセッション スコープの作成MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  

