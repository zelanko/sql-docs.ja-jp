---
title: サブスクリプションの同期 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1c24eee2e720e9a2a7098875f6255e08817cdabc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319882"
---
# <a name="synchronize-subscriptions-replication"></a>サブスクリプションの同期 (レプリケーション)
  サブスクリプションはレプリケーション エージェントにより同期されます。 ディストリビューション エージェントによりサブスクリプションがトランザクション パブリケーションおよびスナップショット パブリケーションと同期され、マージ エージェントによりサブスクリプションがマージ パブリケーションと同期されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レプリケーション ストアド プロシージャ、およびレプリケーション管理オブジェクト (RMO) を使用して、サブスクリプションを同期したり、同期の動作を制御できます。 次のトピックでは、サブスクリプションの同期方法と同期オプションの指定方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [初期スナップショットの作成および適用](create-and-apply-the-initial-snapshot.md)  
  
-   [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする &#40;SQL Server Management Studio&#41;](enable-initialization-with-backup-for-transactional-publications.md)  
  
-   [トランザクション サブスクリプションのバックアップからの初期化 &#40;レプリケーション Transact-SQL プログラミング&#41;](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [手動によるサブスクリプションの初期化](initialize-a-subscription-manually.md)  
  
-   [プル サブスクリプションの同期](synchronize-a-pull-subscription.md)  
  
-   [プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md)  
  
-   [サブスクリプションの再初期化](reinitialize-a-subscription.md)  
  
-   [スナップショット適用前および適用後のスクリプトの実行 &#40;SQL Server Management Studio&#41;](execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [同期中のスクリプトの実行 &#40;レプリケーション Transact-SQL プログラミング&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Windows 同期マネージャーを使用したサブスクリプションの同期 &#40;Windows 同期マネージャー&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)  
  
-   [マージ アーティクルのビジネス ロジック ハンドラーの実装](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [ビジネス ロジック ハンドラーのデバッグ&#40;レプリケーション プログラミング&#41;](debug-a-business-logic-handler-replication-programming.md)  
  
-   [同期中にトリガーと制約の動作を制御する &#40;レプリケーション Transact-SQL プログラミング&#41;](control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [マージ アーティクルのカスタム競合回避モジュールの実装](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>参照  
 [データの同期](synchronize-data.md)  
  
  
