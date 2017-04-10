---
title: "マージ レプリケーションの競合の検出と解決 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション], 競合回避について"
  - "既定の競合回避モジュール"
  - "競合解決 [SQL Server レプリケーション]"
  - "マージ レプリケーションの競合の表示"
  - "マージ レプリケーションの競合解決"
  - "アーティクル [SQL Server レプリケーション], 競合回避"
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション]"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ レプリケーションの競合の検出と解決
  パブリッシャーとサブスクライバーが接続され、同期が発生すると、マージ エージェントによって競合の検出が行われます。 競合が検出された場合、マージ エージェントは競合回避モジュールを使用して、どのデータを受け入れて他のサイトに反映するかを決定します。  
  
> [!NOTE]  
>  サブスクライバーがパブリッシャーと同期している場合でも、サブスクライバーとパブリッシャーでの更新よりも、別のサブスクライバーの更新で競合が発生することがよくあります。  
  
 マージ レプリケーションでは、競合を検出して解決するためのさまざまなメソッドが用意されています。 ほとんどのアプリケーションの場合、次の既定のメソッドが適切です。  
  
-   競合がパブリッシャーとサブスクライバーの間で発生した場合、パブリッシャーの変更は保存され、サブスクライバーの変更は破棄されます。  
  
-   クライアント サブスクリプション (プル サブスクリプションの既定の種類) を使用している 2 つのサブスクライバー間で競合が発生した場合は、パブリッシャーと同期する最初のサブスクライバーからの変更が保存され、2 番目のサブスクライバーからの変更は破棄されます。 クライアントとサーバーのサブスクリプションを指定する方法の詳細については、次を参照してください。 [指定マージ サブスクリプションの種類と競合解決の優先度と #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)します。  
  
-   サーバー サブスクリプション (プッシュ サブスクリプションの既定の種類) を使用している 2 つのサブスクライバー間で競合が発生した場合は、優先度が高い方のサブスクライバーからの変更が保存され、2 番目のサブスクライバーからの変更は破棄されます。 優先度値が同じである場合は、パブリッシャーと同期する最初のサブスクライバーからの変更が保存されます。  
  
 競合の検出とマージ レプリケーションの解決方法の詳細については、次を参照してください。 [高度なマージ レプリケーションの競合の検出および解決](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)します。  
  
## 参照  
 [マージ レプリケーションのアーティクルのオプション](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [パブリケーションのサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  