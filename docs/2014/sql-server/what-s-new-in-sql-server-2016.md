---
title: どのような&#39;SQL Server 2014 の |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 70
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9144eeb653649e36cfed3551e4ec465d403ffdcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074970"
---
# <a name="what39s-new-in-sql-server-2014"></a>どのような&#39;SQL Server 2014 の
  このトピックの新機能の詳細へのリンクをまとめたもの[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]と用のサービス パックの概要を示します [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**お試しください:** ![Azure の仮想マシンの小さな](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png)Azure アカウントをお持ちですか?  次いで**[ここ](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** に既にインストールされている SQL Server 2014 Service Pack 1 (SP1) を持つバーチャル マシンを動かします。 
  
-   [新機能&#40;データベース エンジン&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Analysis Services と Business Intelligence の新機能](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [SQL Server インストールの新機能](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 次に重要な新機能が導入されていません。**  
  
-   [新機能&#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [新機能&#40;レプリケーション&#41;](../relational-databases/replication/what-s-new-replication.md)  
  
-   [新機能&#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) は、重要な新機能を挿入しないでした。
-  [SQL Server 2014 Service Pack 1 リリース情報](https://support.microsoft.com/en-us/kb/3058865)です。
-  [![Service Pack 1 Microsoft® SQL Server® 2014 のダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [Microsoft® SQL Server® 2014 の Service Pack 1 をダウンロード](https://www.microsoft.com/en-us/download/details.aspx?id=46694)です。


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 2 (SP2)
- [SQL Server 2014 Service Pack 2 リリース情報](https://support.microsoft.com/en-us/kb/3171021)です。
-  [![Service Pack 2 Microsoft® SQL Server® 2014 のダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](http://go.microsoft.com/fwlink/?LinkID=821558) [Microsoft® SQL Server® 2014 の Service Pack 2 をダウンロード](http://go.microsoft.com/fwlink/?LinkID=821558)です。
-  [![SQL Server 2014 SP2 用 Feature Pack のダウンロード](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [、SQL Server 2014 SP2 用 Feature Pack のダウンロード](https://www.microsoft.com/en-us/download/details.aspx?id=53164)です。

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2)次の機能強化が含まれています。

### <a name="performance-and-scalability-improvements"></a>パフォーマンスとスケーラビリティの向上 
-   **自動ソフト NUMA のパーティション分割:** で[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2、自動ソフト NUMA は有効になっているインスタンスの起動中に、トレース フラグ 8079 がオンにするとします。 スタートアップ中に、トレース フラグ 8079 が有効になっているときに[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 はハードウェアのレイアウトを調査し、システムの NUMA ノードあたり 8 個以上の Cpu をレポートのソフト NUMA を自動的に構成します。 自動ソフト NUMA 動作がハイパー (HT/論理プロセッサ) に注意してください。 パーティション分割と追加ノードの作成により、リスナーの数の増加、スケーリング、およびネットワークと暗号化機能の向上により、バックグラウンド処理が拡張されます。 お勧め最初のテストを自動ソフト NUMA のパフォーマンス負荷実稼働環境で有効にします。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/)です。 
-  **動的メモリ オブジェクトの規模の調整:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 は、ノードと最新のハードウェア上でスケール アップするコアの数に基づくメモリ オブジェクトを動的にパーティション分割します。 動的な昇格の目的は、ボトルネックとなる場合に、スレッド セーフ メモリ オブジェクト (CMEMTHREAD) を自動的に分割します。 パーティションを設定するノード (NUMA ノード数のパーティション equals 数)、によって、パーティション分割されていないメモリ オブジェクトを動的に昇格でき、オブジェクト ノードでパーティション分割されていることができますをさらにメモリが CPU (の等しい数のパーティションの数がパーティション分割に昇格Cpu)。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/)です。
-  **DBCC CHECK で MAXDOP ヒント\*コマンド:** この改善アドレス[connect フィードバック (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb)です。 指定した DBCC CHECKDB を実行して、sp_configure 値以外 MAXDOP に設定します。 MAXDOP では、リソース ガバナーで構成されている値を超えると、データベース エンジンは、ALTER WORKLOAD GROUP (TRANSACT-SQL)」に記載のリソース ガバナーの MAXDOP 値を使用します。 MAXDOP クエリ ヒントを使用している場合は、max degree of parallelism 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、次を参照してください。 [DBCC CHECKDB (TRANSACT-SQL)](https://msdn.microsoft.com/library/ms176064.aspx)です。
-   **有効にする > バッファー プールに 8 TB:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 128 TB のバッファー プールの使用率の仮想アドレス領域を有効にします。 この機能強化には、最新のハードウェアに 8 TB を超えるスケール アウトする SQL Server のバッファー プールが有効にします。
-   **SOS_RWLock スピンロック向上:** SOS_RWLock は SQL Server コード ベースのさまざまな場所で使用される同期プリミティブです。  名前が示すように、コードは複数の共有 (リーダー) または 1 つ (ライター) の所有権を持つことができます。 この機能強化では、SOS_RWLock のスピンロックの必要性を削除し、代わりに、インメモリ OLTP のようなロック制御不要の手法を使用します。 この変更により、多くのスレッドが互いをブロックしたり、スケーラビリティの向上を提供することがなく、並列で SOS_RWLock によって保護するデータ構造体を読み取ることができます。 この変更前に、スピンロックの実装は、データ構造体を読み取る場合にも、時、SOS_RWLock を取得する 1 つのスレッドを使用できます。  [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/)です。
-    **空間のネイティブ実装:** 空間クエリのパフォーマンスを大幅に向上がで導入された[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]ネイティブの実装を通して SP2。 詳細については、次を参照してください。、[サポート技術情報の記事 KB3107399](https://support.microsoft.com/en-us/kb/3107399)です。

### <a name="supportability-and-diagnostics-improvements"></a>サポートおよび診断機能の強化
-   **データベースの複製:** クローン データベースは、スキーマとデータがないメタデータを複製することによって既存の実稼働データベースのトラブルシューティングを強化する新しい DBCC コマンド。 コマンドを使用して、複製が作成された`DBCC clonedatabase(‘source_database_name’, ‘clone_database_name’)`です。  **注:** クローン データベースは、実稼働環境では使用できません。 データベースが複製されたデータベースから生成されたかどうかを決定する、次のコマンドを使用して:`select DATABASEPROPERTYEX('clonedb', 'isClone')`です。 戻り値**1** clonedatabase 中から、データベースが作成されたことを示します**0**クローンではないことを示します。
-   **Tempdb のサポート:** tempdb ファイルの数、および tempdb のデータのサイズと自動拡張を新しいエラー ログ メッセージはファイル サーバーの起動時に存在します。
-   **データベース インスタント ファイルの初期化のログ:** をサーバーのスタートアップ、データベース ファイルの瞬時初期化 (有効/無効) の状態を示す新しいエラー ログ メッセージ。
-   **呼び出し履歴内のモジュール名:** Xevent callstack にはモジュール名 + 絶対アドレスではなくオフセットが含まれています。
-   **増分統計の新しい DMF:** この改善アドレス[connect フィードバック (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics)パーティション レベルで増分統計情報の追跡を有効にします。 情報ごとのパーティションの増分統計を公開する新しい DMF sys.dm_db_incremental_stats_properties が導入されました。
-   **更新インデックス使用状況の DMV 現象:** この改善アドレス[connect フィードバック (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats)顧客のインデックスを再構築されるはどこから*いない*sys.dm_db から既存の行エントリをクリアそのインデックスの _index_usage_stats します。 動作は SQL 2008 および SQL Server 2016 のものと同じなります。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/)です。
-   **診断 XE および Dmv の間の相関関係の向上:** この改善アドレス[connect フィードバック (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types)です。 Query_hash と query_plan_hash は、クエリを一意に識別するために使用されます。 DMV はこれらを varbinary(8) として定義するのに対し、XEvent は UINT64 として定義します。 SQL server に"unisigned bigint"がないのでキャスト常に機能しません。 この機能強化では、新しい XEvent アクション/フィルター列が導入されています。これは XE と DMV 間の関連付けクエリに役立つ INT64 として定義されている点を除き、query_hash と query_plan_hash と同等です。
-   **BULK insert ステートメントおよび BCP では、utf-8 のサポート:** この改善アドレス[connect フィードバック (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) utf-8 文字セットでエンコードされたデータのエクスポートとインポートのサポート BULK insert ステートメントおよび BCP になりました。
-   **クエリの実行プロファイルのオペレーターごとの軽量:** プラン表示、クエリ実行プランと演算子のコストの計画に多くの情報を提供するが、実際の情報に制限されていますが、クエリのパフォーマンスをトラブルシューティングするときに(CPU、I/O の読み取り、経過時間あたりのスレッド) などのランタイム統計情報です。 SQL 2014 SP2 には、演算子、プラン表示だけでなく、XEvent (query_thread_profile) クエリのパフォーマンスのトラブルシューティングを支援するために別のこれらの追加のランタイム統計情報が導入されています。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/)です。
-   **変更の追跡のクリーンアップ:** 新しいストアド プロシージャ`sp_flush_CT_internal_table_on_demand`クリーンアップ変更の要求時に内部テーブルを追跡するが導入されました。
-   **AlwaysON のリース タイムアウトをログ記録**予期された更新時刻と現在の時刻をログに記録されるように、リース タイムアウト メッセージの新しいログ機能を追加します。 また、新しいメッセージは、タイムアウトについては、SQL エラー ログで導入されました。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/)です。
-   **SQL Server でのバッファーの入力を取得するための新しい DMF:** セッション/要求 (sys.dm_exec_input_buffer) が使用できるようになりました、入力バッファーを取得するための新しい DMF です。 これは DBCC INPUTBUFFER と同等の機能です。 [詳細については、ブログを参照してください](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/)です。
-   **過小評価されると、あまりメモリ許可の軽減策:** MIN_GRANT_PERCENT および MAX_GRANT_PERCENT を介してリソース ガバナーの新しいクエリ ヒントを追加します。 これにより、メモリの競合を防ぐためにメモリ許可の上限によってクエリの実行中にこれらのヒントを活用することができます。 詳細については、次を参照してください[サポート技術情報の記事 KB310740。](https://support.microsoft.com/en-us/kb/3107401)
-   **メモリ許可/使用状況の診断の向上:** メモリ許可の要求および付与を追跡するために SQL Server (query_memory_grant_usage) のトレース機能の一覧に追加された新しい拡張イベント。 これは、メモリ許可のクエリの実行に関する問題のトラブルシューティングの向上のトレースと分析機能を提供します。 詳細については、次を参照してください。[サポート技術情報の記事 KB3107173](https://support.microsoft.com/en-us/kb/3107173)です。
-   **クエリ実行の診断 tempdb オーバーフローを:**-Hash Warning および Sort Warnings 物理 I/O の統計情報、使用されるメモリおよび影響を受ける行を追跡する追加の列があるようになりました。 新しい hash_spill_details 拡張イベントを紹介します。 これより詳細な情報を追跡するには、ハッシュおよび並べ替えの警告 ([KB3107172](https://support.microsoft.com/en-us/kb/3107172))。 この機能強化が SpillToTempDbType 複合型に新しい属性の形式で XML のクエリ プランによって公開されるようになりました ([KB3107400](https://support.microsoft.com/en-us/kb/3107400))。 これで、表示の並べ替えの作業テーブルの統計情報で統計情報を設定します。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。
-   **残余述語のプッシュ ダウンが関係するクエリ実行プランの診断の向上:** 読み取られた実際の行は、クエリ パフォーマンスのトラブルシューティングを向上させるクエリ実行プランでは報告ようになりました。 SET STATISTICS IO を個別にキャプチャする必要があるこの必要があります。 今すぐを使用すると、クエリ プランの残余述語のプッシュ ダウンに関連する情報を表示できます。 詳細については、次を参照してください。[サポート技術情報の記事 KB3107397](https://support.microsoft.com/en-us/kb/3107397)です。


## <a name="additional-information"></a>追加情報  
 [SQL Server 2014 リソース](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 リリース ノート](http://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014 リソース センター](http://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat Web サイト](http://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  