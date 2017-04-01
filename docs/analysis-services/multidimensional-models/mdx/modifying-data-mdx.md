---
title: "データの変更 (MDX) | Microsoft Docs"
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
  - "データの変更 [MDX]"
  - "多次元式 [Analysis Services], データの変更"
  - "MDX [Analysis Services], データの変更"
  - "データ変更 [MDX]"
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# データの変更 (MDX)
  多次元式 (MDX) は、ディメンションやキューブのデータの取得や操作を行うためだけでなく、ディメンションやキューブのデータの更新、つまり*書き戻し*を行うためにも使用できます。 これらの更新は、推測分析または "what-if" 分析の場合のように一時的なものであることも、データ分析に基づいて変更を加える必要がある場合のように永続的なものになることもあります。  
  
 データの更新は、ディメンション レベルまたはキューブ レベルで実行できます。  
  
 **ディメンションの書き戻し**  
 書き込み可能なディメンションのデータを変更するには、[ALTER CUBE ステートメント (MDX)](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md) を使用します。属性値の削除、作成、更新を反映するには、[REFRESH CUBE ステートメント (MDX)](../Topic/REFRESH%20CUBE%20Statement%20\(MDX\).md) を使用します。 ALTER CUBE ステートメントを使用すると、階層内のサブツリー全体を削除したり、削除されたメンバーの子を昇格させるなど、複雑な操作を実行することもできます。  
  
 **キューブの書き戻し**  
 書き込み可能なキューブに対する更新を実行するには、[UPDATE CUBE](../Topic/UPDATE%20CUBE%20Statement%20\(MDX\).md) ステートメントを使用します。 UPDATE CUBE ステートメントを使用すると、特定の値で組を更新できます。 サーバーにある更新されたデータをクライアント セッションのデータに適用するには、[REFRESH CUBE ステートメント (MDX)](../Topic/REFRESH%20CUBE%20Statement%20\(MDX\).md) を使用します。  
  
 詳細については、「[キューブの書き戻しの使用 (MDX)](../../../analysis-services/multidimensional-models/mdx/using-cube-writebacks-mdx.md)」を参照してください。  
  
## 「  
 [MDX クエリの基礎 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  