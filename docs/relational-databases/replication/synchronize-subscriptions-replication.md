---
title: "サブスクリプションの同期 (レプリケーション) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dbd10248c5a6c358e6e8e6c64b0db355fc4ed66d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="synchronize-subscriptions-replication"></a>サブスクリプションの同期 (レプリケーション)
  サブスクリプションはレプリケーション エージェントにより同期されます。 ディストリビューション エージェントによりサブスクリプションがトランザクション パブリケーションおよびスナップショット パブリケーションと同期され、マージ エージェントによりサブスクリプションがマージ パブリケーションと同期されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レプリケーション ストアド プロシージャ、およびレプリケーション管理オブジェクト (RMO) を使用して、サブスクリプションを同期したり、同期の動作を制御できます。 次のトピックでは、サブスクリプションの同期方法と同期オプションの指定方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/enable-initialization-with-backup-for-transactional-publications.md)  
  
-   [トランザクション サブスクリプションのバックアップからの初期化 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [手動によるサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-manually.md)  
  
-   [プル サブスクリプションの同期](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [プッシュ サブスクリプションの同期](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [スナップショット適用前および適用後のスクリプトの実行 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [同期中のスクリプトの実行 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Windows 同期マネージャーを使用したサブスクリプションの同期 &#40;Windows 同期マネージャー&#41;](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md)  
  
-   [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [ビジネス ロジック ハンドラーのデバッグ&#40;レプリケーション プログラミング&#41;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [同期中にトリガーと制約の動作を制御する &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [マージ アーティクルのカスタム競合回避モジュールの実装](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>参照  
 [データベースの同期](../../relational-databases/replication/synchronize-data.md)  
  
  
