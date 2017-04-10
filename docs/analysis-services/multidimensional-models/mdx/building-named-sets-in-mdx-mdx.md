---
title: "MDX での名前付きセットの作成 (MDX) | Microsoft Docs"
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
helpviewer_keywords: 
  - "多次元式 [Analysis Services], 名前付きセット"
  - "名前付きセット [MDX]"
  - "セット [MDX]"
  - "MDX [Analysis Services], 名前付きセット"
  - "クエリ [MDX], 名前付きセット"
  - "セット式 [MDX]"
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# MDX での名前付きセットの作成 (MDX)
  セット式は、長く複雑な宣言になることがあり、そのような場合は読みにくく、理解するのが難しい式になります。 また、同じセット式を頻繁に使用する場合に、その同じセットを繰り返し定義しなければならないのは面倒です。 長く複雑な式や頻繁に使用する式の取り扱いを簡略化するために、多次元式 (MDX) では、そのような式を*名前付きセット*として定義できるようになっています。  
  
 基本的に、名前付きセットとは、別名を割り当てたセット式です。 名前付きセットには、通常 1 つのセットに組み込めるメンバーや関数を任意に組み込めます。 MDX では、名前付きセットの別名をセット式として取り扱うので、セット式を使用できる場所であればどこででもその別名を使用できます。  
  
 名前付きセットの定義では、以下のいずれかのコンテキストを設定できます。  
  
-   **クエリ スコープ** MDX クエリの一部として定義される名前付きセットを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 その名前付きセットは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した名前付きセットを、SELECT ステートメントを修正せずに変更できます。  
  
     WITH キーワードを使用して名前付きセットを作成する方法の詳細については、「[クエリ スコープの名前付きセットの作成 (MDX)](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-named-sets-mdx.md)」を参照してください。  
  
-   **セッション スコープ** クエリのコンテキストよりも広いスコープを設定して名前付きセットを作成する場合 (つまり、スコープを MDX セッションの有効期間全体とする場合) は、CREATE SET ステートメントを使用します。 CREATE SET ステートメントで定義した名前付きセットは、そのセッションのすべての MDX クエリで使用できます。 CREATE SET ステートメントを使用する方法は、たとえば、さまざまなクエリで 1 つのセットを使い回すクライアント アプリケーションで役立ちます。  
  
     CREATE SET ステートメントを使用してセッションでの名前付きセットを作成する方法の詳細については、「[セッション スコープの名前付きセットの作成 (MDX)](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-named-sets-mdx.md)」を参照してください。  
  
## 参照  
 [SELECT ステートメント (MDX)](../Topic/SELECT%20Statement%20\(MDX\).md)   
 [CREATE SET ステートメント (MDX)](../Topic/CREATE%20SET%20Statement%20\(MDX\).md)   
 [MDX クエリの基礎 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  