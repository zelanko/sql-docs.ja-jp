---
title: "パブリケーションとアーティクルの作成、変更、および削除 (レプリケーション) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
ms.assetid: e66d06ec-a12b-444d-875b-77f958af2f21
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e8edc949b81a6b8c6d336ecaf3fd955d406a3648
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-modify-and-delete-publications-and-articles-replication"></a>パブリケーションとアーティクルの作成、変更、および削除 (レプリケーション)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] ここでは、パブリケーションの作成とアーティクルの定義に関連する作業の手順について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [アーティクルの定義](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [パブリケーション プロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [アーティクルのプロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
-   [パブリケーションの削除](../../../relational-databases/replication/publish/delete-a-publication.md)  
  
-   [アーティクルの削除](../../../relational-databases/replication/publish/delete-an-article.md)  
  
-   [Oracle データベースからのパブリケーションの作成](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)  
  
-   [サブスクリプションの有効期限の設定](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md)  
  
-   [スキーマ オプションの指定](../../../relational-databases/replication/publish/specify-schema-options.md)  
  
-   [スキーマ変更のレプリケート](../../../relational-databases/replication/publish/replicate-schema-changes.md)  
  
-   [ID 列の管理](../../../relational-databases/replication/publish/manage-identity-columns.md)  
  
-   [マージ パブリケーションの互換性レベルの設定](../../../relational-databases/replication/publish/set-the-compatibility-level-for-merge-publications.md)  
  
## <a name="snapshot-options"></a>スナップショット オプション  
  
-   [スナップショットの形式の指定 (SQL Server Management Studio)](../../../relational-databases/replication/publish/specify-snapshot-format-sql-server-management-studio.md)  
  
-   [代替スナップショット フォルダーの場所の指定 (SQL Server Management Studio)](../../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   [スナップショット ファイルの圧縮 (SQL Server Management Studio)](../../../relational-databases/replication/publish/compress-snapshot-files-sql-server-management-studio.md)  
  
-   [スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [スナップショット適用前および適用後のスクリプトの実行 (SQL Server Management Studio)](../../../relational-databases/replication/execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [FTP でのスナップショットの配信](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)  
  
## <a name="filtering-data"></a>データのフィルター処理  
  
-   [列フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)  
  
-   [静的行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)  
  
-   [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [パラメーター化された行フィルターの最適化](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md)  
  
-   [マージ アーティクル間の結合フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
-   [マージ アーティクル間の一連の結合フィルターを自動的に生成する (SQL Server Management Studio)](../../../relational-databases/replication/publish/automatically-generate-join-filters-between-merge-articles.md)  
  
## <a name="transactional-replication-options"></a>トランザクション レプリケーション オプション  
  
-   [データの変更をトランザクション アーティクルに反映する方法の設定](../../../relational-databases/replication/publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
-   [キュー更新の競合解決オプションの設定 (SQL Server Management Studio)](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)  
  
-   [トランザクション パブリケーションでのストアド プロシージャの実行のパブリッシュ (SQL Server Management Studio)](../../../relational-databases/replication/publish/publish-execution-of-stored-procedure-in-transactional-publication.md)  
  
## <a name="merge-replication-options"></a>マージ レプリケーション オプション  
  
-   [マージ テーブル アーティクル間に論理レコード リレーションシップを定義する](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [マージ テーブル アーティクルの処理順序の指定 (レプリケーション Transact-SQL プログラミング)](../../../relational-databases/replication/publish/specify-the-processing-order-of-merge-table-articles.md)  
  
-   [マージ テーブル アーティクルをダウンロード専用に指定する](../../../relational-databases/replication/publish/specify-that-a-merge-table-article-is-download-only.md)  
  
-   [マージ アーティクルに対して削除を追跡しないように指定する (レプリケーション Transact-SQL プログラミング)](../../../relational-databases/replication/publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [マージ アーティクルの競合追跡と競合解決のレベルの指定](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [マージ アーティクル競合回避モジュールの指定](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
-   [マージ アーティクルのインタラクティブな競合回避の指定](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
