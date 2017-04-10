---
title: "MDX での計算されるメンバーの作成 (MDX) | Microsoft Docs"
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
  - "MDX [Analysis Services], 計算されるメンバー"
  - "計算されるメンバー [MDX]"
  - "多次元式 [Analysis Services], 計算されるメンバー"
  - "クエリ [MDX], 計算されるメンバー"
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# MDX での計算されるメンバーの作成 (MDX)
  多次元式 (MDX) では、値を返す MDX 式の計算によって解決されるメンバーのことを、計算されるメンバーといいます。 これは一見なにげない定義ですが、非常に広範囲に影響を及ぼします。 MDX クエリで計算されるメンバーを作成して使用する機能によって、多次元データの操作能力が大幅に向上するからです。  
  
 計算されるメンバーは、階層内のどこにでも作成できます。 また、キューブ内の既存のメンバーだけでなく、同じ MDX 式で定義された他の計算されるメンバーにも依存するように、計算されるメンバーを作成することもできます。  
  
 計算されるメンバーの定義では、以下のいずれかのコンテキストを設定できます。  
  
-   **クエリ スコープ** MDX クエリの一部として定義する、計算されるメンバーを作成する場合 (スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 その計算されるメンバーは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した計算されるメンバーを、SELECT ステートメントを修正せずに変更できます。  
  
     WITH キーワードを使用して計算されるメンバーを作成する方法の詳細については、「[クエリ スコープの計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-calculated-members-mdx.md)」を参照してください。  
  
-   **セッション スコープ** クエリのコンテキストよりも広いスコープを設定して計算されるメンバーを作成する場合 (スコープを MDX セッションの有効期間全体とする場合) は、CREATE MEMBER ステートメントを使用します。 CREATE MEMBER ステートメントで定義した計算されるメンバーは、そのセッションのすべての MDX クエリで使用できます。 CREATE MEMBER ステートメントを使用する方法は、たとえば、さまざまなクエリで同じセットを使い回すクライアント アプリケーションで役立ちます。  
  
     CREATE MEMBER ステートメントを使用してセッションでの計算されるメンバーを作成する方法の詳細については、「[セッション スコープの計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-calculated-members-mdx.md)」を参照してください。  
  
## 参照  
 [CREATE MEMBER ステートメント &#40;MDX&#41;](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [SELECT ステートメント &#40;MDX&#41;](../Topic/SELECT%20Statement%20\(MDX\).md)  
  
  