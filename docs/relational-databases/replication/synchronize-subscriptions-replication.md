---
title: "サブスクリプションの同期 (レプリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "同期 [SQL Server レプリケーション]、サブスクリプション"
  - "サブスクリプション [SQL Server レプリケーション], 同期"
  - "レプリケーション [SQL Server], 同期"
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# サブスクリプションの同期 (レプリケーション)
  サブスクリプションはレプリケーション エージェントにより同期されます。 ディストリビューション エージェントによりサブスクリプションがトランザクション パブリケーションおよびスナップショット パブリケーションと同期され、マージ エージェントによりサブスクリプションがマージ パブリケーションと同期されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レプリケーション ストアド プロシージャ、およびレプリケーション管理オブジェクト (RMO) を使用して、サブスクリプションを同期したり、同期の動作を制御できます。 次のトピックでは、サブスクリプションの同期方法と同期オプションの指定方法について説明します。  
  
## このセクションの内容  
  
-   [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [トランザクション パブリケーションと #40; のバックアップの初期化を有効にします。SQL Server Management Studio と #41 です。](../../relational-databases/replication/enable initialization with backup for transactional publications.md)  
  
-   [バックアップと #40; からトランザクション パブリケーションに対するサブスクリプションを初期化します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/initialize a transactional subscription from a backup.md)  
  
-   [Initialize a Subscription Manually](../../relational-databases/replication/initialize-a-subscription-manually.md)  
  
-   [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [スナップショットが適用される前後にスクリプトの実行 (& a) #40 です。SQL Server Management Studio と #41 です。](../../relational-databases/replication/execute scripts before and after a snapshot is applied.md)  
  
-   [同期および #40; 時にスクリプトを実行します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [表示してマージ パブリケーションおよび #40; のデータの競合を解決します。SQL Server Management Studio と #41 です。](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   [トランザクション パブリケーションおよび #40; のデータの競合の表示SQL Server Management Studio と #41 です。](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Windows 同期マネージャーおよび #40; を使用してサブスクリプションを同期します。Windows 同期マネージャーと #41 です。](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)  
  
-   [マージ アーティクルのビジネス ロジック ハンドラーの実装](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [#40; (&)、ビジネス ロジック ハンドラーをデバッグします。レプリケーション プログラミングと #41 です。](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [同期および #40; 時にトリガーと制約の動作を制御します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/control behavior of triggers and constraints in synchronization.md)  
  
-   [マージ アーティクルのカスタム競合回避モジュールの実装](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## 参照  
 [データの同期](../../relational-databases/replication/synchronize-data.md)  
  
  