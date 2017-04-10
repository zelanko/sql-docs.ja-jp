---
title: "MDX 内でのメジャーの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# MDX 内でのメジャーの作成
  多次元式 (MDX) では、メジャーは、テーブル モデルで値を返す式を計算することで解決される名前付き DAX 式です。 これは一見なにげない定義ですが、非常に広範囲に影響を及ぼします。 MDX クエリでメジャーを作成して使用する機能によって、テーブル データの操作能力が大幅に向上します。  
  
> [!WARNING]  
>  メジャーは、テーブル モデルでのみ定義できます。データベースが多次元モードに設定されている場合、メジャーを作成するとエラーになります。  
  
 MDX クエリの一部として定義されるメジャーを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 そのメジャーは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した計算されるメンバーを、SELECT ステートメントを修正せずに変更できます。 ただし、MDX では、DAX 式とは異なる方法でメジャーを参照します。メジャーを参照するには、[Measures] ディメンションのメンバーとして指定します。次の MDX の例を参照してください。  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 これを実行すると、次のデータが返されます。  
  
||Total Sales Amount||  
|-|------------------------|-|  
|2001|11331808.96||  
|2002|30674773.18||  
|2003|41993729.72||  
|2004|25808962.34||  
  
## 参照  
 [CREATE MEMBER ステートメント &#40;MDX&#41;](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [SELECT ステートメント &#40;MDX&#41;](../Topic/SELECT%20Statement%20\(MDX\).md)  
  
  