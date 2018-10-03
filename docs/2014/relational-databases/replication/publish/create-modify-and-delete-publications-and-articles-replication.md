---
title: パブリケーションとアーティクルの作成、変更、および削除 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
ms.assetid: e66d06ec-a12b-444d-875b-77f958af2f21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df06bcf5a5f1d43dff50009166279e6b2658790e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145432"
---
# <a name="create-modify-and-delete-publications-and-articles-replication"></a>パブリケーションとアーティクルの作成、変更、および削除 (レプリケーション)
  ここでは、パブリケーションの作成とアーティクルの定義に関連する作業の手順について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [パブリケーションの作成](create-a-publication.md)  
  
-   [Define an Article](define-an-article.md)  
  
-   [パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)  
  
-   [アーティクルのプロパティの表示と変更](view-and-modify-article-properties.md)  
  
-   [パブリケーションの削除](delete-a-publication.md)  
  
-   [アーティクルの削除](delete-an-article.md)  
  
-   [Oracle データベースからのパブリケーションの作成](create-a-publication-from-an-oracle-database.md)  
  
-   [サブスクリプションの有効期限の設定](set-the-expiration-period-for-subscriptions.md)  
  
-   [スキーマ オプションの指定](specify-schema-options.md)  
  
-   [スキーマ変更のレプリケート](replicate-schema-changes.md)  
  
-   [ID 列の管理](manage-identity-columns.md)  
  
-   [マージ パブリケーションの互換性レベルの設定](set-the-compatibility-level-for-merge-publications.md)  
  
## <a name="snapshot-options"></a>スナップショット オプション  
  
-   [スナップショットの形式の指定 (SQL Server Management Studio)](specify-snapshot-format-sql-server-management-studio.md)  
  
-   [代替スナップショット フォルダーの場所の指定 (SQL Server Management Studio)](specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   [スナップショット ファイルの圧縮 (SQL Server Management Studio)](compress-snapshot-files-sql-server-management-studio.md)  
  
-   [スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)](configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [スナップショット適用前および適用後のスクリプトの実行 (SQL Server Management Studio)](../execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [FTP でのスナップショットの配信](deliver-a-snapshot-through-ftp.md)  
  
## <a name="filtering-data"></a>データのフィルター処理  
  
-   [列フィルターの定義および変更](define-and-modify-a-column-filter.md)  
  
-   [静的行フィルターの定義および変更](define-and-modify-a-static-row-filter.md)  
  
-   [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [パラメーター化された行フィルターの最適化](../merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)  
  
-   [マージ アーティクル間の一連の結合フィルターを自動的に生成する (SQL Server Management Studio)](automatically-generate-join-filters-between-merge-articles.md)  
  
## <a name="transactional-replication-options"></a>トランザクション レプリケーション オプション  
  
-   [データの変更をトランザクション アーティクルに反映する方法の設定](set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](enable-updating-subscriptions-for-transactional-publications.md)  
  
-   [キュー更新の競合解決オプションの設定 (SQL Server Management Studio)](set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)  
  
-   [トランザクション パブリケーションでのストアド プロシージャの実行のパブリッシュ (SQL Server Management Studio)](publish-execution-of-stored-procedure-in-transactional-publication.md)  
  
## <a name="merge-replication-options"></a>マージ レプリケーション オプション  
  
-   [マージ テーブル アーティクル間に論理レコード リレーションシップを定義する](define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [マージ テーブル アーティクルの処理順序の指定 (レプリケーション Transact-SQL プログラミング)](specify-the-processing-order-of-merge-table-articles.md)  
  
-   [マージ テーブル アーティクルをダウンロード専用に指定する](specify-that-a-merge-table-article-is-download-only.md)  
  
-   [マージ アーティクルに対して削除を追跡しないように指定する (レプリケーション Transact-SQL プログラミング)](specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [マージ アーティクルの競合追跡と競合解決のレベルの指定](specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [マージ アーティクル競合回避モジュールの指定](specify-a-merge-article-resolver.md)  
  
-   [マージ アーティクルのインタラクティブな競合回避の指定](specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md)  
  
  
