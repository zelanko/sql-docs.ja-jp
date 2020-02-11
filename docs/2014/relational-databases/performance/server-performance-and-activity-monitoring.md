---
title: サーバーのパフォーマンスと利用状況の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7289c18fac421bbdb5ccc0e00a3bea60b7a22d9e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150615"
---
# <a name="server-performance-and-activity-monitoring"></a>サーバーのパフォーマンスと利用状況の監視
  データベースを監視する目的は、サーバーのパフォーマンスを評価することです。 適切な監視には、現在のパフォーマンスのスナップショットを定期的にキャプチャして問題の原因となっているプロセスを特定したり、長期にわたって継続的にデータを採取してパフォーマンスの傾向を追跡する作業が必要です。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]および Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)]オペレーティングシステムには、データベースの現在の状態を表示したり、状態の変化に伴うパフォーマンスを追跡するためのユーティリティが用意されています。  
  
 次のセクションには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Windows のパフォーマンスと利用状況の監視ツールの使用方法を説明するトピックが含まれています。 ここで説明する内容は次のとおりです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 **Windows ツールで監視タスクを実行するには**  
  
-   [Windows&#41;&#40;システムモニターを起動する](start-system-monitor-windows.md)  
  
-   [Windows アプリケーション ログの表示 &#40;Windows&#41;](view-the-windows-application-log-windows-10.md)  
  
 **Windows ツールを使用して SQL Server データベースの警告を作成するには**  
  
-   [Windows&#41;&#40;SQL Server データベースの警告を設定する](set-up-a-sql-server-database-alert-windows.md)  
  
 **SQL Server Management Studio で監視タスクを実行するには**  
  
-   [SQL Server のエラーログ &#40;SQL Server Management Studio を表示&#41;](../../ssms/sql-server-management-studio-ssms.md)  
  
-   [利用状況モニターを開く方法 &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)  
  
 **Transact-sql ストアドプロシージャを使用して SQL トレースで監視タスクを実行するには**  
  
-   [Transact-sql&#41;&#40;トレースを作成する](../sql-trace/create-a-trace-transact-sql.md)  
  
-   [Transact-sql&#41;&#40;トレースフィルターを設定する](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
-   [既存のトレース &#40;Transact-sql&#41;の変更](../sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [保存されているトレース &#40;Transact-sql&#41;を表示する](../sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [Transact-sql&#41;&#40;フィルター情報を表示する](../sql-trace/view-filter-information-transact-sql.md)  
  
-   [Transact-sql&#41;のトレース &#40;の削除](../sql-trace/delete-a-trace-transact-sql.md)  
  
 **SQL Server プロファイラーを使用してトレースを作成および変更するには**  
  
-   [トレースの作成 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [グローバルトレースオプション &#40;SQL Server プロファイラー&#41;を設定します](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [トレースファイルのイベントとデータ列を指定する &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [トレース &#40;SQL Server プロファイラーを実行するための Transact-sql スクリプトを作成&#41;](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [トレース結果をファイル &#40;SQL Server プロファイラーに保存&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [トレースファイル &#40;SQL Server プロファイラーの最大ファイルサイズを設定&#41;](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [トレース結果をテーブル &#40;SQL Server プロファイラー&#41;に保存する](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [トレーステーブルの最大テーブルサイズを設定する &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [トレース内のイベントへのフィルターの適用 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [フィルター情報の表示 &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [フィルター &#40;SQL Server プロファイラーの変更&#41;](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [イベントの開始時刻 &#40;SQL Server プロファイラーに基づいてイベントをフィルター処理し&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [イベントの終了時刻 &#40;SQL Server プロファイラーに基づいてイベントをフィルター処理し&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [トレース &#40;SQL Server プロファイラー内の Spid&#41; &#40;サーバープロセス Id をフィルター処理し&#41;](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [トレース &#40;SQL Server プロファイラーに表示される列の構成&#41;](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
 **SQL Server プロファイラーを使用してトレースを開始、一時停止、および停止するには**  
  
-   [サーバーへの接続後の自動的なトレースの開始 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [トレースの一時停止 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [トレースの停止 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [一時停止または停止したトレースの再開 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
 **トレースを開き、SQL Server プロファイラーを使用してトレースを表示する方法を構成するには**  
  
-   [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [トレース ウィンドウの消去 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [トレースウィンドウを閉じる &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [トレース定義の既定値の設定 &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [トレース表示の既定値の設定 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **SQL Server プロファイラーを使用してトレースを再生するには**  
  
-   [トレースファイル &#40;SQL Server プロファイラーを再生する&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [トレーステーブル &#40;SQL Server プロファイラーの再生&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [一度に1つのイベントを再生 &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [ブレークポイントまでの再生 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [カーソルまでの再生 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [Transact-sql スクリプトの再生 &#40;SQL Server プロファイラー&#41;](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
 **を使用してトレーステンプレートを作成、変更、および使用するには SQL Server プロファイラー**  
  
-   [トレース テンプレートの作成 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [トレース テンプレートの変更 &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
-   [実行中のトレースからのテンプレートの作成 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [トレース ファイルまたはトレース テーブルからのテンプレートの作成 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [トレース テンプレートのエクスポート &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [トレーステンプレート &#40;SQL Server プロファイラーをインポートする&#41;](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
 **SQL Server プロファイラートレースを使用して、サーバーのパフォーマンスを収集および監視するには**  
  
-   [&#40;SQL Server プロファイラーのトレース中に値列またはデータ列を検索&#41;](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [デッドロックグラフを保存 &#40;SQL Server プロファイラー&#41;](save-deadlock-graphs-sql-server-profiler.md)  
  
-   [Showplan XML イベントを個別に保存 &#40;SQL Server プロファイラー&#41;](save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [Showplan XML Statistics Profile イベントを個別に保存 &#40;SQL Server プロファイラー&#41;](save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [トレース &#40;SQL Server プロファイラーからのスクリプトの抽出&#41;](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [トレースと Windows パフォーマンスログデータ &#40;の関連付け SQL Server プロファイラー&#41;](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
