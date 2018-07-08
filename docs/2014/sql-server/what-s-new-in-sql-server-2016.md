---
title: どのような&#39;SQL Server 2014 の新 |Microsoft Docs
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- database-engine
- integration-services
- master-data-services
- replication
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 70
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 5845455529c1b7d2cec25e7407ac8425a0a0e4a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150153"
---
# <a name="what39s-new-in-sql-server-2014"></a>どのような&#39;s SQL Server 2014 の新機能
  このトピックでは、新機能の詳細なリンクをまとめたものです[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]しのサービス パックの概要を示します。 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**試してみる:** ![Azure Virtual Machine のアイコン](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png)Azure アカウントを持っているでしょうか。  やがて**[ここ](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** 既にインストールされている SQL Server 2014 Service Pack 1 (SP1) の仮想マシンを作成します。 
  
-   [新機能については&#40;データベース エンジン&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [新しい Analysis Services と Business Intelligence の新機能](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [SQL Server インストールの新機能](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 次に重要な新機能が導入されていません。**  
  
-   [新機能については&#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [新機能については&#40;レプリケーション&#41;](../relational-databases/replication/what-s-new-replication.md)  
  
-   [新機能については&#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) は重要な新機能を含めていません。
-  [SQL Server 2014 Service Pack 1 リリース情報](https://support.microsoft.com/en-us/kb/3058865)します。
-  [![Microsoft® SQL Server® 2014 用 Service Pack 1 をダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [Microsoft® SQL Server® 2014 用 Service Pack 1 をダウンロード](https://www.microsoft.com/en-us/download/details.aspx?id=46694)します。


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 2 (SP2)
- [SQL Server 2014 Service Pack 2 リリース情報](https://support.microsoft.com/en-us/kb/3171021)します。
-  [![Microsoft® SQL Server® 2014 の Service Pack 2 をダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](http://go.microsoft.com/fwlink/?LinkID=821558) [Microsoft® SQL Server® 2014 の Service Pack 2 をダウンロード](http://go.microsoft.com/fwlink/?LinkID=821558)します。
-  [![SQL Server 2014 SP2 Feature Pack ダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [SQL Server 2014 SP2 Feature Pack ダウンロード](https://www.microsoft.com/en-us/download/details.aspx?id=53164)します。

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2)次の機能強化が含まれています。

### <a name="performance-and-scalability-improvements"></a>パフォーマンスとスケーラビリティの向上 
-   **自動ソフト NUMA のパーティション分割:** で[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]インスタンスの起動中にトレース フラグ 8079 が有効にしたときに SP2 で自動ソフト NUMA を有効にします。 起動時に、トレース フラグ 8079 が有効にすると[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 はハードウェア レイアウトを問い合わせて、NUMA ノードあたり 8 個以上の Cpu をレポートするシステムのソフト NUMA を自動的に構成します。 自動的に、ソフト NUMA の動作は、ハイパー スレッド (HT/論理プロセッサ) に注意してください。 パーティション分割と追加ノードの作成により、リスナーの数の増加、スケーリング、およびネットワークと暗号化機能の向上により、バックグラウンド処理が拡張されます。 お勧めの最初のテストをパフォーマンス ワークロード自動ソフト NUMA を実稼働環境でこれを有効にする前にします。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/)します。 
-  **メモリ オブジェクトの動的スケーリング:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 は、最新のハードウェア上でスケール アップするノードとコアの数に基づくメモリ オブジェクトを動的にパーティション分割します。 動的な昇格の目的は、ボトルネックとなる場合、スレッド セーフ メモリ オブジェクト (CMEMTHREAD) を自動的に分割します。 ノード (NUMA ノード数のパーティションと等しい数)、パーティションに分割するパーティション分割されていないメモリ オブジェクトを動的に昇格し、(の等しい数のパーティションの数を CPU によってパーティションに分割する昇格させたノードでパーティション分割されたオブジェクトが、さらにメモリCpu)。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/)します。
-  **DBCC CHECK の MAXDOP ヒント\*コマンド:** この機能強化がアドレス[connect フィードバック (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb)します。 指定した DBCC CHECKDB を実行して、sp_configure 値以外の MAXDOP 設定します。 MAXDOP では、リソース ガバナーで構成されている値を超えると、データベース エンジンは、ALTER WORKLOAD GROUP (TRANSACT-SQL)」に記載のリソース ガバナーの MAXDOP 値を使用します。 MAXDOP クエリ ヒントを使用している場合は、max degree of parallelism 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、次を参照してください。 [DBCC CHECKDB (TRANSACT-SQL)](https://msdn.microsoft.com/library/ms176064.aspx)します。
-   **有効にする > のバッファー プールの 8 TB:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 により、バッファー プールの使用の仮想アドレス空間の 128 TB です。 この機能強化では、最新のハードウェアで 8 TB を超えてスケールする SQL Server バッファー プールを使用できます。
-   **SOS_RWLock スピンロックの向上:** SOS_RWLock は同期プリミティブの SQL Server のコード ベース全体でさまざまな場所で使用します。  名前が示すように、コードは、複数の共有 (リーダー) または 1 つ (ライター) 所有権ことができます。 この機能強化は SOS_RWLock スピンロックの必要を削除し、代わりに、インメモリ OLTP のようなロック制御不要の手法を使用します。 この変更により、多数のスレッドが互いをブロックして、それによってスケーラビリティの向上を提供することがなく SOS_RWLock で並列で保護されたデータ構造を読み取ることができます。 今回の変更前は、スピンロックの実装は、データ構造の読み取りにも、時、SOS_RWLock を取得する 1 つのスレッドを許可します。  [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/)します。
-    **空間のネイティブ実装:** 空間クエリのパフォーマンスが大幅に向上がで導入された[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 ネイティブ実装から。 詳細については、次を参照してください。、[サポート技術情報記事 KB3107399](https://support.microsoft.com/en-us/kb/3107399)します。

### <a name="supportability-and-diagnostics-improvements"></a>サポート性と診断機能の強化
-   **データベースの複製:** クローン データベースは、スキーマとデータなしのメタデータを複製することにより既存の運用データベースのトラブルシューティングを強化する新しい DBCC コマンド。 コマンドを使用して、複製が作成された`DBCC clonedatabase(‘source_database_name’, ‘clone_database_name’)`します。  **注:** 運用環境で、複製されたデータベースを使用しない必要があります。 特定のデータベースが複製されたデータベースから生成されたかどうか、次のコマンドを使用して:`select DATABASEPROPERTYEX('clonedb', 'isClone')`します。 戻り値**1** clonedatabase 中から、データベースが作成されたことを示します**0**複製ではないことを示します。
-   **Tempdb のサポート性:** tempdb ファイルの数および tempdb のデータのサイズと自動拡張を示す新しいエラー ログ メッセージはファイル サーバーの起動時に存在します。
-   **データベースのインスタント ファイル初期化ログ:** でサーバーのスタートアップ、データベース ファイルの瞬時初期化 (有効/無効) の状態を示す新しいエラー ログ メッセージ。
-   **呼び出し履歴内のモジュール名:** Xevent の呼び出し履歴には今すぐモジュール名 + 絶対アドレスではなくオフセットが含まれています。
-   **増分統計の新しい DMF:** この機能強化がアドレス[connect フィードバック (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics)パーティション レベルで増分統計情報の追跡を有効にします。 情報 - パーティションの増分統計を公開する新しい DMF sys.dm_db_incremental_stats_properties が導入されました。
-   **更新インデックス使用状況の DMV の動作:** この機能強化がアドレス[connect フィードバック (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats)顧客がインデックスを再構築するはどこから*いない*sys.dm_db から既存の行エントリをクリアそのインデックスに対する _index_usage_stats します。 動作では、SQL 2008 および SQL Server 2016 と同じではようになりました。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/)します。
-   **診断 XE および Dmv 間の相関関係の向上:** この機能強化がアドレス[connect フィードバック (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types)します。 クエリを一意に識別するため、Query_hash と query_plan_hash が使用されます。 DMV はこれらを varbinary(8) として定義するのに対し、XEvent は UINT64 として定義します。 SQL server に"unisigned bigint"がないのでキャストが機能しません。 この機能強化では、新しい XEvent アクション/フィルター列が導入されています。これは XE と DMV 間の関連付けクエリに役立つ INT64 として定義されている点を除き、query_hash と query_plan_hash と同等です。
-   **BULK INSERT と BCP では、utf-8 のサポート:** この機能強化がアドレス[connect フィードバック (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001)文字セットを utf-8 でエンコードされたデータのエクスポートとインポートのサポート BULK INSERT と BCP になりました。
-   **演算子ごとの軽量なクエリの実行プロファイル:** プラン表示プランで、クエリ実行プランと演算子のコストで多くの情報を提供しますが、実際の情報が限られていますが、クエリのパフォーマンスをトラブルシューティングするときに(CPU、I/O の読み取り、経過時間あたりのスレッド) などのランタイム統計情報。 SQL 2014 SP2 では、プラン表示だけでなく、XEvent (query_thread_profile) クエリのパフォーマンスのトラブルシューティングを支援するために、演算子ごとのこれらの追加のランタイム統計情報について説明します。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/)します。
-   **変更の追跡のクリーンアップ:** 新しいストアド プロシージャ`sp_flush_CT_internal_table_on_demand`オンデマンド追跡の内部テーブルのクリーンアップの変更が導入されました。
-   **AlwaysON のリース タイムアウトをログ記録**リース タイムアウト メッセージに対する新しいログ機能を追加して、現在の時刻と予想される更新時刻をログに記録できるようにします。 また、新しいメッセージは、タイムアウトに関する SQL エラー ログで導入されました。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/)します。
-   **SQL Server でのバッファーの入力を取得するための新しい DMF:** セッション/要求 (sys.dm_exec_input_buffer) が使用できるようになりました、入力バッファーを取得するための新しい DMF します。 これは DBCC INPUTBUFFER と同等の機能です。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/)します。
-   **過小評価されると、あまりメモリ許可の軽減策:** MIN_GRANT_PERCENT および MAX_GRANT_PERCENT をリソース ガバナーの新しいクエリ ヒントを追加します。 これにより、メモリの競合を防ぐためにメモリ許可を制限してクエリを実行中にこれらのヒントを活用することができます。 詳細については、次を参照してください[サポート技術情報記事 KB310740。](https://support.microsoft.com/en-us/kb/3107401)
-   **メモリ許可/使用状況の診断の向上:** メモリ許可の要求および付与を追跡する SQL Server (query_memory_grant_usage) のトレース機能の一覧に追加された新しい拡張イベント。 これは、メモリ許可のクエリの実行に関する問題のトラブルシューティングの強化されたトレースと分析機能を提供します。 詳細については、次を参照してください。[サポート技術情報記事 KB3107173](https://support.microsoft.com/en-us/kb/3107173)します。
-   **クエリ実行の診断の tempdb の書き込み:**-Hash Warning および Sort Warnings 物理 I/O の統計情報、使用されるメモリと影響を受ける行を追跡する追加の列があるようになりました。 新しい hash_spill_details 拡張イベントも導入されています。 ハッシュと並べ替えの警告についてより詳細な情報を追跡するようになりました ([KB3107172](https://support.microsoft.com/en-us/kb/3107172))。 この機能強化が SpillToTempDbType 複合型に新しい属性の形式での XML クエリ プランを介して公開されるようになりました ([KB3107400](https://support.microsoft.com/en-us/kb/3107400))。 表示は、作業テーブルの統計情報を並べ替えるようになりましたの統計情報を設定します。 .
-   **残余述語のプッシュ ダウンに関連するクエリ実行プランの診断の強化:** 読み取られた実際の行は、クエリ パフォーマンスのトラブルシューティングを向上させるクエリ実行プランでは報告ようになりました。 これは、SET STATISTICS IO を個別にキャプチャする必要を負数化する必要があります。 これでを使用すると、クエリ プランの残余述語のプッシュ ダウンに関連する情報を参照してください。 詳細については、次を参照してください。[サポート技術情報記事 KB3107397](https://support.microsoft.com/en-us/kb/3107397)します。


## <a name="additional-information"></a>追加情報  
 [SQL Server 2014 リソース](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 リリース ノート](http://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014 リソース センター](http://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat Web サイト](http://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  
