---
title: SQL Server&#39;2014 | の新機能Microsoft Docs
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
ms.openlocfilehash: f368da503c90595624f476344724719206cdb77c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893704"
---
# <a name="what39s-new-in-sql-server-2014"></a>SQL Server&#39;2014 の新機能
  このトピックで[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]は、の新機能に関する詳細なリンクと、のサービスパックの概要について説明します。[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**お試しください:** ![Azure の仮想マシン](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png)には azure アカウントがありますか?  次に、SQL Server 2014 Service Pack 1 (SP1) が既にインストールされている仮想マシンを起動するに **[は、ここ](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** にアクセスします。 
  
-   [新&#40;機能データベースエンジン&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Analysis Services とビジネスインテリジェンスの新機能](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)  
  
-   [SQL Server インストールの新機能](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]では、次のような重要な新機能は導入されていません。**  
  
-   [新&#40;機能 Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [新&#40;機能 Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)](SP1) では、重要な新機能は導入されませんでした。
-  [SQL Server 2014 Service Pack 1 のリリース情報](https://support.microsoft.com/en-us/kb/3058865)。
-  [![Microsoft の Service Pack 1 をダウンロードしますか?SQL Server しますか?](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) 2014[Microsoft の Service Pack 1 をダウンロードしますか?SQL Server しますか?2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694)。


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Service Pack 2 (SP2)
- [SQL Server 2014 Service Pack 2 リリース情報](https://support.microsoft.com/en-us/kb/3171021)。
-  [![Microsoft の Service Pack 2 をダウンロードしますか?SQL Server しますか?](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) 2014[Microsoft の Service Pack 2 をダウンロードしますか?SQL Server しますか?2014](https://go.microsoft.com/fwlink/?LinkID=821558)。
-  [![Download SQL Server 2014 SP2 Feature Pack をダウンロードします](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [Download SQL Server 2014 SP2 Feature Pack をダウンロードします](https://www.microsoft.com/en-us/download/details.aspx?id=53164)。

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SMSでは、次の点が改善されています。

### <a name="performance-and-scalability-improvements"></a>パフォーマンスとスケーラビリティの向上 
-   **ソフト NUMA の自動パーティション分割:** SP2 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]では、インスタンスの起動時にトレースフラグ8079が有効になっていると、自動ソフト NUMA が有効になります。 起動時にトレースフラグ8079が有効になっ[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]ている場合、SP2 はハードウェアレイアウトを調査し、numa ノードあたり8個以上の cpu を報告するシステムでソフト NUMA を自動的に構成します。 ソフト NUMA の自動動作は、ハイパースレッド (HT/論理プロセッサ) に対応しています。 パーティション分割と追加ノードの作成により、リスナーの数の増加、スケーリング、およびネットワークと暗号化機能の向上により、バックグラウンド処理が拡張されます。 まず、自動ソフト NUMA を使用してパフォーマンスワークロードをテストしてから、運用環境で有効にすることをお勧めします。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/)。 
-  **動的メモリオブジェクトのスケーリング:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 では、最新のハードウェアに拡張するために、ノードとコアの数に基づいてメモリオブジェクトを動的に分割します。 動的な昇格の目的は、スレッドセーフメモリオブジェクト (CMEMTHREAD) がボトルネックになった場合に、そのオブジェクトを自動的にパーティション分割することです。 パーティション分割されていないメモリオブジェクトは、ノードによってパーティション分割されるように動的に昇格できます (パーティションの数は NUMA ノードの数と等しくなります)。また、ノードによってパーティション分割されたメモリオブジェクトは、さらに上位の CPU によってパーティション分割されるようになります (パーティション数は、Cpu)。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/)。
-  **DBCC CHECK\*コマンドの MAXDOP ヒント:** この改善により、 [connect のフィードバック (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb)が解決します。 Sp_configure 値以外の MAXDOP 設定を使用して DBCC CHECKDB を実行できるようになりました。 MAXDOP では、Resource Governor で構成されている値を超えると、データベース エンジンは、「ALTER WORKLOAD GROUP (TRANSACT-SQL)」に記載のリソース ガバナーの MAXDOP 値を使用します。 MAXDOP クエリ ヒントを使用している場合は、max degree of parallelism 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、「 [DBCC CHECKDB (transact-sql)](https://msdn.microsoft.com/library/ms176064.aspx)」を参照してください。
-   **バッファープールの > 8 TB を有効にする:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 では、バッファープールの使用に対して、128 TB の仮想アドレス空間を使用できます。 この改善により、SQL Server バッファープールは、最新のハードウェアでは 8 TB を超える規模に拡張できます。
-   **SOS_RWLock スピンロックの向上:** SOS_RWLock は、SQL Server コードベースを通じてさまざまな場所で使用される同期プリミティブです。  名前が示すように、コードは複数の共有 (リーダー) または単一 (ライター) の所有権を持つことができます。 この改善により、SOS_RWLock のスピンロックが不要になり、代わりにインメモリ OLTP と同様のロックフリー手法が使用されます。 この変更により、多くのスレッドでは、相互にブロックせずに、SOS_RWLock によって保護されたデータ構造を同時に読み取ることができるため、スケーラビリティが向上します。 この変更の前に、スピンロックの実装では、データ構造を読み取る場合でも、一度に1つのスレッドしか SOS_RWLock を取得できませんでした。  [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/)。
-    **空間ネイティブ実装:** ネイティブ実装によって、SP2 で[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]は、空間クエリのパフォーマンスが大幅に向上しています。 詳細については、[サポート技術情報の記事 KB3107399](https://support.microsoft.com/en-us/kb/3107399)を参照してください。

### <a name="supportability-and-diagnostics-improvements"></a>サポートと診断の機能強化
-   **データベースの複製:** 複製データベースは、データなしでスキーマとメタデータを複製することで、既存の運用データベースのトラブルシューティングを強化する新しい DBCC コマンドです。 複製は、コマンド`DBCC clonedatabase('source_database_name', 'clone_database_name')`を使用して作成されます。  **注:** 複製されたデータベースは、実稼働環境では使用できません。 次のコマンドを使用して、複製されたデータベース`select DATABASEPROPERTYEX('clonedb', 'isClone')`からデータベースが生成されたかどうかを確認します。 戻り値**1**は、データベースが clonedatabase から作成されていることを示し、 **0**は複製ではないことを示します。
-   **Tempdb のサポート性:** Tempdb ファイルの数と、サーバーの起動時に存在する tempdb データファイルのサイズと自動拡張を示す新しいエラーログメッセージ。
-   **データベースのファイルの瞬時初期化ログ:** サーバーの状態を示す新しいエラーログメッセージ。データベースのファイルの瞬時初期化の状態 (有効/無効) が表示されます。
-   **呼び出し履歴のモジュール名:** Xevent の呼び出し履歴には、絶対アドレスではなく、モジュール名とオフセットが含まれるようになりました。
-   **増分統計用の新しい DMF:** この改善により、 [connect のフィードバック (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics)が、パーティションレベルで増分統計を追跡できるようになります。 新しい DMF _db_incremental_stats_properties は、増分統計のパーティションごとの情報を公開するために導入されました。
-   **インデックス使用状況 DMV の動作が更新されました:** この改善により、インデックスを再構築しても、そのインデックスの既存の行エントリが削除され*ない*ようにします[(739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) 。 動作は、SQL 2008 および SQL Server 2016 と同じになります。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/)。
-   **診断の XE と Dmv の相関関係が向上しました。** この改善により、 [connect のフィードバック (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types)が解決します。 Query_hash と query_plan_hash は、クエリを一意に識別するために使用されます。 DMV はこれらを varbinary(8) として定義するのに対し、XEvent は UINT64 として定義します。 SQL server には "unisigned bigint" がないため、キャストは常に機能しません。 この機能強化では、新しい XEvent アクション/フィルター列が導入されています。これは XE と DMV 間の関連付けクエリに役立つ INT64 として定義されている点を除き、query_hash と query_plan_hash と同等です。
-   **BULK INSERT および BCP での UTF-8 のサポート:** この改善により、BULK INSERT と BCP で、UTF-8 文字セットでエンコードされたデータのエクスポートとインポートのサポートが有効になりました[(370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) 。
-   **操作ごとの軽量クエリ実行プロファイル:** クエリのパフォーマンスのトラブルシューティングでは、プランのクエリ実行プランと操作コストに関する情報が多数表示されますが、(CPU、i/o 読み取り、スレッドあたりの経過時間などの) 実際の実行時の統計情報については制限があります。 SQL 2014 SP2 では、クエリのパフォーマンスのトラブルシューティングを支援するために、Showplan と XEvent (query_thread_profile) の各演算子に対して、これらの追加のランタイム統計情報が導入されています。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/)。
-   **Change Tracking のクリーンアップ:** 必要に応じて`sp_flush_CT_internal_table_on_demand` 、変更の追跡の内部テーブルをクリーンアップするために、新しいストアドプロシージャが導入されました。
-   **AlwaysON リースタイムアウトのログ**現在の時刻と予想される更新時刻がログに記録されるように、リースタイムアウトメッセージの新しいログ記録機能が追加されました。 また、タイムアウトに関して、SQL エラーログに新しいメッセージが導入されました。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/)。
-   **SQL Server で入力バッファーを取得するための新しい DMF。** セッション/要求の入力バッファーを取得するための新しい DMF (sys.dm_exec_input_buffer) を使用できるようになりました。 これは DBCC INPUTBUFFER と同等の機能です。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/)。
-   **過小使用および過剰推定メモリ許可の軽減策:** MIN_GRANT_PERCENT と MAX_GRANT_PERCENT を通じて Resource Governor の新しいクエリヒントが追加されました。 これにより、メモリの許可を上限にしてメモリの競合を防ぐことで、クエリの実行中にこれらのヒントを活用できます。 詳細については、[サポート技術情報の記事 KB310740](https://support.microsoft.com/en-us/kb/3107401)を参照してください。
-   **メモリ許可/使用量の診断の向上:** SQL Server (query_memory_grant_usage) のトレース機能の一覧に新しい拡張イベントが追加され、要求され、許可されたメモリ許可を追跡します。 これにより、メモリ許可に関連するクエリ実行の問題をトラブルシューティングするためのトレースと分析の機能が向上します。 詳細については、[サポート技術情報の記事 KB3107173](https://support.microsoft.com/en-us/kb/3107173)を参照してください。
-   **Tempdb 書き込みのクエリ実行診断:** -ハッシュ警告と並べ替えの警告に、物理 i/o 統計、メモリ使用量、および影響を受けた行数を追跡するための列が追加されるようになりました。 また、新しい hash_spill_details 拡張イベントも導入しました。 これで、ハッシュと並べ替えの警告 ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)) の詳細情報を追跡できるようになりました。 この改善は、SpillToTempDbType 複合型 ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)) に新しい属性の形式で XML クエリプランを通じて公開されるようになりました。 Set statistics on に並べ替え作業テーブルの統計情報が表示されるようになりました。 .
-   **残存述語のプッシュダウンが関係するクエリ実行プランの診断が向上しました。** クエリパフォーマンスのトラブルシューティングを向上させるために、クエリ実行プランに実際に読み取られた行が報告されるようになりました。 これにより、SET STATISTICS IO を個別にキャプチャする必要がなくなります。 これにより、クエリプランの残存述語プッシュダウンに関連する情報を表示できるようになりました。 詳細については、[サポート技術情報の記事 KB3107397](https://support.microsoft.com/en-us/kb/3107397)を参照してください。


## <a name="additional-information"></a>追加情報  
 [SQL Server 2014 のリソース](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 リリース ノート](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014 リソースセンター](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat Web サイト](https://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  
