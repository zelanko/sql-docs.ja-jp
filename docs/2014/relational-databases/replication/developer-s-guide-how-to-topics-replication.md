---
title: '開発者ガイド : 操作方法に関するトピック (レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- replication
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c6c15ae6-da52-4638-93d3-61c7242e8a0b
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: fc3eeb21918886c1b738891b7b0453cbc5712212
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285128"
---
# <a name="developer39s-guide-how-to-topics-replication"></a>開発者ガイド : 操作方法に関するトピック (レプリケーション)
  このトピックでは、レプリケーション関連タスクをプログラムで実行する方法に関する情報へのリンクを示します。  
  
## <a name="securing-a-replication-topology"></a>レプリケーション トポロジのセキュリティ保護  
  
-   [レプリケーションのセキュリティ設定の表示および変更](security/view-and-modify-replication-security-settings.md)  
  
-   [パブリケーション アクセス リストのログインの管理](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="configuring-modifying-and-disabling-publishing-and-distribution-replication"></a>パブリッシングとディストリビューションの構成、変更、および無効化 (レプリケーション)  
  
-   [パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)  
  
-   [パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)  
  
-   [パブリッシングおよびディストリビューションの無効化](disable-publishing-and-distribution.md)  
  
## <a name="creating-modifying-and-deleting-publications-and-articles"></a>パブリケーションおよびアーティクルの作成、変更、削除  
  
-   [パブリケーションの作成](publish/create-a-publication.md)  
  
-   [Define an Article](publish/define-an-article.md)  
  
-   [パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)  
  
-   [アーティクルのプロパティの表示と変更](publish/view-and-modify-article-properties.md)  
  
-   [パブリケーションの削除](publish/delete-a-publication.md)  
  
-   [アーティクルの削除](publish/delete-an-article.md)  
  
-   [Oracle データベースからのパブリケーションの作成](publish/create-a-publication-from-an-oracle-database.md)  
  
-   [サブスクリプションの有効期限の設定](publish/set-the-expiration-period-for-subscriptions.md)  
  
-   [スキーマ オプションの指定](publish/specify-schema-options.md)  
  
-   [スキーマ変更のレプリケート](publish/replicate-schema-changes.md)  
  
-   [ID 列の管理](publish/manage-identity-columns.md)  
  
-   [マージ パブリケーションの互換性レベルの設定](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a>スナップショット オプション  
  
-   [スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [FTP でのスナップショットの配信](publish/deliver-a-snapshot-through-ftp.md)  
  
### <a name="filtering-data"></a>データのフィルター処理  
  
-   [列フィルターの定義および変更](publish/define-and-modify-a-column-filter.md)  
  
-   [静的行フィルターの定義および変更](publish/define-and-modify-a-static-row-filter.md)  
  
-   [マージ アーティクルのパラメーター化された行フィルターの定義および変更](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [パラメーター化された行フィルターの最適化](merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [マージ アーティクル間の結合フィルターの定義および変更](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a>トランザクション レプリケーション オプション  
  
-   [データの変更をトランザクション アーティクルに反映する方法の設定](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a>マージ レプリケーション オプション  
  
-   [マージ テーブル アーティクル間に論理レコード リレーションシップを定義する](publish/define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [マージ テーブル アーティクルの処理順序の指定 (レプリケーション Transact-SQL プログラミング)](publish/specify-the-processing-order-of-merge-table-articles.md)  
  
-   [マージ テーブル アーティクルをダウンロード専用に指定する](publish/specify-that-a-merge-table-article-is-download-only.md)  
  
-   [マージ アーティクルに対して削除を追跡しないように指定する (レプリケーション Transact-SQL プログラミング)](publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [マージ アーティクルの競合追跡と競合解決のレベルの指定](publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [マージ アーティクル競合回避モジュールの指定](publish/specify-a-merge-article-resolver.md)  
  
-   [マージ アーティクルのインタラクティブな競合回避の指定](publish/specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="creating-modifying-and-deleting-subscriptions"></a>サブスクリプションの作成、変更、および削除  
  
-   [プル サブスクリプションの作成](create-a-pull-subscription.md)  
  
-   [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)  
  
-   [プル サブスクリプションの削除](delete-a-pull-subscription.md)  
  
-   [プッシュ サブスクリプションの作成](create-a-push-subscription.md)  
  
-   [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)  
  
-   [プッシュ サブスクリプションの削除](delete-a-push-subscription.md)  
  
-   [同期スケジュールの指定](specify-synchronization-schedules.md)  
  
-   [トランザクション パブリケーションの更新可能なサブスクリプションの作成](create-updatable-subscription-transactional-publication-transact-sql.md)  
  
-   [SQL Server 以外のサブスクライバーのサブスクリプションの作成](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronizing-subscriptions"></a>サブスクリプションの同期  
  
-   [初期スナップショットの作成および適用](create-and-apply-the-initial-snapshot.md)  
  
-   [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [手動によるサブスクリプションの初期化](initialize-a-subscription-manually.md)  
  
-   [プル サブスクリプションの同期](synchronize-a-pull-subscription.md)  
  
-   [プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md)  
  
-   [サブスクリプションの再初期化](reinitialize-a-subscription.md)  
  
-   [同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [マージ アーティクルのビジネス ロジック ハンドラーの実装](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [ビジネス ロジック ハンドラーのデバッグ&#40;レプリケーション プログラミング&#41;](debug-a-business-logic-handler-replication-programming.md)  
  
-   [同期中にトリガーと制約の動作を制御する &#40;レプリケーション Transact-SQL プログラミング&#41;](control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [マージ アーティクルのカスタム競合回避モジュールの実装](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administering-a-replication-topology"></a>レプリケーション トポロジの管理  
  
-   [レプリケーション エージェント プロファイルの操作](agents/replication-agent-profiles.md)  
  
-   [サブスクライバーでのデータの検証](validate-data-at-the-subscriber.md)  
  
-   [パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [マージ レプリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-SQL プログラミング)](bulk-load-data-into-tables-in-a-merge-publication.md)  
  
-   [マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング)](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)  
  
-   [マージ アーティクルのダミー更新の実行 (レプリケーション Transact-SQL プログラミング)](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)  
  
-   [レプリケートされたコマンドなどディストリビューション データベースに格納されている情報を表示する (レプリケーション Transact-SQL プログラミング)](monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [トランザクション レプリケーションの連携バックアップの有効化 (レプリケーション Transact-SQL プログラミング)](administration/enable-coordinated-backups-for-transactional-replication.md)  
  
-   [ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング)](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)  
  
-   [レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング)](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)  
  
-   [Oracle パブリッシャー用のトランザクション セット ジョブの構成 (レプリケーション Transact-SQL プログラミング)](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  
  
-   [レプリケーション スクリプトのアップグレード (レプリケーション Transact-SQL プログラミング)](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitoring-a-replication-topology"></a>レプリケーション トポロジの監視  
  
-   [管理者以外のユーザーがレプリケーション モニターを使用できるようにする](monitor/allow-non-administrators-to-use-replication-monitor.md)  
  
-   [プログラムによるレプリケーションの監視](monitor/monitoring-replication-overview.md)  
  
-   [レプリケートされたコマンドなどディストリビューション データベースに格納されている情報を表示する (レプリケーション Transact-SQL プログラミング)](monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](view-conflict-information-for-merge-publications.md)  
  
-   [トランザクション レプリケーションの待機時間の計測および接続の検証](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
