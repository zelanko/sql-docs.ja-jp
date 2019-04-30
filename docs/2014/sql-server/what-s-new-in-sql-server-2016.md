---
title: どのような&#39;SQL Server 2014 の新 |Microsoft Docs
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 26d0c84194f6f2aafb8bc499ff5404a1438ee577
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63295247"
---
# <a name="what39s-new-in-sql-server-2014"></a>どのような&#39;s SQL Server 2014 の新機能
  このトピックでは、新機能の詳細なリンクをまとめたものです[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]しのサービス パックの概要を示します。 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**お試しください:**![Azure Virtual Machine のアイコン](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png)Azure アカウントを持っているでしょうか。  やがて**[ここ](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** 既にインストールされている SQL Server 2014 Service Pack 1 (SP1) の仮想マシンを作成します。 
  
-   [新機能については&#40;データベース エンジン&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [新しい Analysis Services と Business Intelligence の新機能](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [SQL Server インストールの新機能](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 次に重要な新機能が導入されていません。**  
  
-   [新機能については&#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [新機能については&#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) は重要な新機能を含めていません。
-  [SQL Server 2014 Service Pack 1 リリース情報](https://support.microsoft.com/en-us/kb/3058865)します。
-  [![Microsoft Service Pack 1 をダウンロードしていますか。SQL Server??2014](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [microsoft Service Pack 1 をダウンロードします。SQL Server??2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 2 (SP2)
- [SQL Server 2014 Service Pack 2 リリース情報](https://support.microsoft.com/en-us/kb/3171021)します。
-  [![Microsoft の Service Pack 2 をダウンロードするには [概要] タブSQL Server??2014](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) [microsoft Service Pack 2 をダウンロードします。SQL Server??2014](https://go.microsoft.com/fwlink/?LinkID=821558).
-  [![SQL Server 2014 SP2 Feature Pack ダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [SQL Server 2014 SP2 Feature Pack ダウンロード](https://www.microsoft.com/en-us/download/details.aspx?id=53164)します。

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2)次の機能強化が含まれています。

### <a name="performance-and-scalability-improvements"></a>パフォーマンスとスケーラビリティの向上 
-   **自動ソフト NUMA のパーティション分割:**[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]インスタンスの起動中にトレース フラグ 8079 が有効にしたときに SP2 で自動ソフト NUMA を有効にします。 起動時に、トレース フラグ 8079 が有効にすると[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 はハードウェア レイアウトを問い合わせて、NUMA ノードあたり 8 個以上の Cpu をレポートするシステムのソフト NUMA を自動的に構成します。 自動的に、ソフト NUMA の動作は、ハイパー スレッド (HT/論理プロセッサ) に注意してください。 パーティション分割と追加ノードの作成により、リスナーの数の増加、スケーリング、およびネットワークと暗号化機能の向上により、バックグラウンド処理が拡張されます。 お勧めの最初のテストをパフォーマンス ワークロード自動ソフト NUMA を実稼働環境でこれを有効にする前にします。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/)します。 
-  **動的メモリ オブジェクトのスケーリングします。**[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 には、最新のハードウェア上でスケール アップするノードとコアの数に基づいて、オブジェクトのメモリが動的にパーティション分割します。 動的な昇格の目的は、ボトルネックとなる場合、スレッド セーフ メモリ オブジェクト (CMEMTHREAD) を自動的に分割します。 ノード (NUMA ノード数のパーティションと等しい数)、パーティションに分割するパーティション分割されていないメモリ オブジェクトを動的に昇格し、(の等しい数のパーティションの数を CPU によってパーティションに分割する昇格させたノードでパーティション分割されたオブジェクトが、さらにメモリCpu)。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/)します。
-  **DBCC CHECK の MAXDOP ヒント\*コマンド。** この機能強化がアドレス[connect フィードバック (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb)します。 指定した DBCC CHECKDB を実行して、sp_configure 値以外の MAXDOP 設定します。 MAXDOP では、Resource Governor で構成されている値を超えると、データベース エンジンは、「ALTER WORKLOAD GROUP (TRANSACT-SQL)」に記載のリソース ガバナーの MAXDOP 値を使用します。 MAXDOP クエリ ヒントを使用している場合は、max degree of parallelism 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、次を参照してください。 [DBCC CHECKDB (TRANSACT-SQL)](https://msdn.microsoft.com/library/ms176064.aspx)します。
-   **有効にする > のバッファー プールの 8 TB。**[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 では、128 TB のバッファー プールの使用の仮想アドレス空間を使用できます。 この機能強化では、最新のハードウェアで 8 TB を超えてスケールする SQL Server バッファー プールを使用できます。
-   **SOS_RWLock スピンロックの向上:** SOS_RWLock は、SQL Server のコード ベースのさまざまな場所で使用される同期プリミティブです。  名前が示すように、コードは、複数の共有 (リーダー) または 1 つ (ライター) 所有権ことができます。 この機能強化は SOS_RWLock スピンロックの必要を削除し、代わりに、インメモリ OLTP のようなロック制御不要の手法を使用します。 この変更により、多数のスレッドが互いをブロックして、それによってスケーラビリティの向上を提供することがなく SOS_RWLock で並列で保護されたデータ構造を読み取ることができます。 今回の変更前は、スピンロックの実装は、データ構造の読み取りにも、時、SOS_RWLock を取得する 1 つのスレッドを許可します。  [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/)します。
-    **空間のネイティブ実装。** 空間クエリのパフォーマンスが大幅に向上がで導入された[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 ネイティブ実装から。 詳細については、次を参照してください。、[サポート技術情報記事 KB3107399](https://support.microsoft.com/en-us/kb/3107399)します。

### <a name="supportability-and-diagnostics-improvements"></a>サポート性と診断機能の強化
-   **データベースのクローンを作成します。** 複製データベースは、スキーマとデータなしのメタデータを複製することにより既存の運用データベースのトラブルシューティングを強化する新しい DBCC コマンドです。 コマンドを使用して、複製が作成された`DBCC clonedatabase('source_database_name', 'clone_database_name')`します。  **注:** 複製されたデータベースは、実稼働環境では使用できません。 特定のデータベースが複製されたデータベースから生成されたかどうか、次のコマンドを使用して:`select DATABASEPROPERTYEX('clonedb', 'isClone')`します。 戻り値**1** clonedatabase 中から、データベースが作成されたことを示します**0**複製ではないことを示します。
-   **Tempdb のサポート:** Tempdb ファイルの数とサーバーの起動時に存在する tempdb データ ファイルのサイズと自動拡張を示す新しいエラー ログ メッセージ。
-   **データベース ファイルの瞬時初期化ログ:** サーバーのスタートアップ、データベース ファイルの瞬時初期化 (有効/無効) の状態を示す新しいエラー ログ メッセージ。
-   **呼び出し履歴内のモジュール名:** Xevent の呼び出し履歴には、モジュール名 + 絶対アドレスではなくオフセットが含まれています。
-   **増分統計の新しい DMF:** この機能強化がアドレス[connect フィードバック (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics)パーティション レベルで増分統計情報の追跡を有効にします。 情報 - パーティションの増分統計を公開する新しい DMF sys.dm_db_incremental_stats_properties が導入されました。
-   **インデックス使用状況の DMV の更新動作:** この機能強化がアドレス[connect フィードバック (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats)顧客がインデックスを再構築するはどこから*いない*そのインデックスに対する sys.dm_db_index_usage_stats から既存の行エントリをクリアします。 動作では、SQL 2008 および SQL Server 2016 と同じではようになりました。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/)します。
-   **診断 XE および Dmv 間の相関関係の向上:** この機能強化がアドレス[connect フィードバック (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types)します。 クエリを一意に識別するため、Query_hash と query_plan_hash が使用されます。 DMV はこれらを varbinary(8) として定義するのに対し、XEvent は UINT64 として定義します。 SQL server に"unisigned bigint"がないのでキャストが機能しません。 この機能強化では、新しい XEvent アクション/フィルター列が導入されています。これは XE と DMV 間の関連付けクエリに役立つ INT64 として定義されている点を除き、query_hash と query_plan_hash と同等です。
-   **BULK INSERT と BCP では、utf-8 のサポート:** この機能強化がアドレス[connect フィードバック (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001)文字セットを utf-8 でエンコードされたデータのエクスポートとインポートのサポート BULK INSERT と BCP になりました。
-   **演算子ごとの軽量なクエリの実行プロファイル:** プラン表示プランで、クエリ実行プランと演算子のコストで多くの情報を提供しますが、実際の情報が限られていますが、パフォーマンス、クエリのトラブルシューティング (CPU、I/O の読み取り、スレッドごとに経過時間) などのランタイム統計情報。 SQL 2014 SP2 では、プラン表示だけでなく、XEvent (query_thread_profile) クエリのパフォーマンスのトラブルシューティングを支援するために、演算子ごとのこれらの追加のランタイム統計情報について説明します。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/)します。
-   **変更追跡のクリーンアップ。** 新しいストアド プロシージャ`sp_flush_CT_internal_table_on_demand`オンデマンド追跡の内部テーブルのクリーンアップの変更が導入されました。
-   **AlwaysON のリース タイムアウトをログ記録**リース タイムアウト メッセージに対する新しいログ機能を追加して、現在の時刻と予想される更新時刻をログに記録できるようにします。 また、新しいメッセージは、タイムアウトに関する SQL エラー ログで導入されました。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/)します。
-   **SQL Server での入力バッファーを取得するための新しい DMF:** セッション/要求の入力バッファーを取得するための新しい DMF (sys.dm_exec_input_buffer) を使用できるようになりました。 これは DBCC INPUTBUFFER と同等の機能です。 [詳細については、ブログを参照してください。](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/)します。
-   **過小評価されると、あまりメモリ許可の軽減策:** 追加された新しいクエリ ヒント MIN_GRANT_PERCENT および MAX_GRANT_PERCENT をリソース ガバナーの。 これにより、メモリの競合を防ぐためにメモリ許可を制限してクエリを実行中にこれらのヒントを活用することができます。 詳細については、次を参照してください[サポート技術情報記事 KB310740。](https://support.microsoft.com/en-us/kb/3107401)
-   **メモリ許可/使用状況のより優れた診断:** 新しい拡張イベントは、メモリ許可の要求および付与を追跡するために SQL Server (query_memory_grant_usage) のトレース機能の一覧に追加されました。 これは、メモリ許可のクエリの実行に関する問題のトラブルシューティングの強化されたトレースと分析機能を提供します。 詳細については、次を参照してください。[サポート技術情報記事 KB3107173](https://support.microsoft.com/en-us/kb/3107173)します。
-   **クエリ実行の診断の tempdb の書き込み:**-Hash Warning および Sort Warnings 物理 I/O の統計情報、使用されるメモリと影響を受ける行を追跡する追加の列があるようになりました。 新しい hash_spill_details 拡張イベントも導入されています。 ハッシュと並べ替えの警告についてより詳細な情報を追跡するようになりました ([KB3107172](https://support.microsoft.com/en-us/kb/3107172))。 この機能強化が SpillToTempDbType 複合型に新しい属性の形式での XML クエリ プランを介して公開されるようになりました ([KB3107400](https://support.microsoft.com/en-us/kb/3107400))。 表示は、作業テーブルの統計情報を並べ替えるようになりましたの統計情報を設定します。 .
-   **残余述語のプッシュ ダウンに関連するクエリ実行プランの診断機能の向上:** 実際に読み取られた行は、クエリ パフォーマンスのトラブルシューティングを向上させるクエリ実行プランで今すぐ報告されます。 これは、SET STATISTICS IO を個別にキャプチャする必要を負数化する必要があります。 これでを使用すると、クエリ プランの残余述語のプッシュ ダウンに関連する情報を参照してください。 詳細については、次を参照してください。[サポート技術情報記事 KB3107397](https://support.microsoft.com/en-us/kb/3107397)します。


## <a name="additional-information"></a>追加情報  
 [SQL Server 2014 リソース](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 リリース ノート](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014 リソース センター](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat Web サイト](https://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  
