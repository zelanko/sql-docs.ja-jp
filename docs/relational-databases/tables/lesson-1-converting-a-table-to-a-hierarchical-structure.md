---
title: "レッスン 1:テーブルの階層構造への変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# レッスン 1:テーブルの階層構造への変換
階層リレーションシップを表すために自己結合を使っているテーブルがある場合、このレッスンの説明に従って、それらのテーブルを階層構造に変換できます。 現在の表示から、 **hierarchyid**を使用した表示に移行するのは比較的簡単です。 移行後は、コンパクトで理解しやすい階層表示が可能になるため、ユーザーはさまざまな方法でインデックスを作成して効率的なクエリを実現できます。  
  
このレッスンでは、既存のテーブルを検証した後、 **hierarchyid** 列を含む新しいテーブルを作成し、そのテーブルにソース テーブルのデータを取り込みます。さらに、3 とおりのインデックス作成方法を紹介します。 このレッスンの内容は次のとおりです。  
  
-   [Employee テーブルの現在の構造の確認](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
-   [既存の階層データを使用したテーブルの設定](../../relational-databases/tables/populating-a-table-with-existing-hierarchical-data.md)  
  
-   [NewOrg テーブルの最適化](../../relational-databases/tables/optimizing-the-neworg-table.md)  
  
-   [まとめ : テーブルの階層構造への変換](../../relational-databases/tables/summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## 前提条件  
このレッスンを学習するには、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースが必要です。  
  
## このレッスンの次の作業  
[Employee テーブルの現在の構造の確認](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
## 次のレッスン  
[レッスン 2 : 階層テーブルでのデータの作成と管理](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
