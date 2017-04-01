---
title: "セッション スコープの計算されるメンバーの作成 (MDX) | Microsoft Docs"
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
  - "CREATE MEMBER ステートメント"
  - "セッション スコープの計算されるメンバー [MDX]"
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# セッション スコープの計算されるメンバーの作成 (MDX)
  多次元式 (MDX) セッション全体で使用できる計算されるメンバーを作成するには、[CREATE MEMBER](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md) ステートメントを使用します。 CREATE MEMBER ステートメントを使用して作成された計算されるメンバーは、MDX セッションが閉じるまで削除されません。  
  
 このトピックで説明するように、CREATE MEMBER ステートメントの構文は非常に単純で使いやすいものです。  
  
> [!NOTE]  
>  計算されるメンバーの詳細については、「[Building Calculated Members in MDX (MDX)](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md)」(MDX での計算されるメンバーの作成 (MDX))を参照してください。  
  
## CREATE MEMBER の構文  
 MDX ステートメントに CREATE MEMBER ステートメントを追加するための構文は、以下のとおりです。  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 CREATE MEMBER ステートメントの構文で使用する `fully-qualified-member-name` の値は、計算されるメンバーの完全修飾名です。 完全修飾名には、計算されるメンバーを関連付けるディメンションまたはレベルが含まれます。 `expression` の値は、その式の値が評価された後の計算されるメンバーの値を返します。  
  
## CREATE MEMBER の例  
 以下の例では、CREATE MEMBER ステートメントを使用して、計算されるメンバー `LastFourStores` を作成しています。 この計算されるメンバーは、販売した単位の合計を最後の 4 つのストアに関して返します。このメンバーは、このキューブのセッション全体で使用できます。  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## 参照  
 [クエリ スコープの計算されるメンバーの作成 (MDX)](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-calculated-members-mdx.md)  
  
  