---
title: "変更データ キャプチャの管理と監視 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "変更データ キャプチャ [SQL Server], 監視"
  - "変更データ キャプチャ [SQL Server], 管理"
  - "変更データ キャプチャ [SQL Server], ジョブ"
ms.assetid: 23bda497-67b2-4e7b-8e4d-f1f9a2236685
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# 変更データ キャプチャの管理と監視 (SQL Server)
  このトピックでは、変更データ キャプチャを管理および監視する方法について説明します。  
  
##  <a name="Capture"></a> キャプチャ ジョブ  
 キャプチャ ジョブは、パラメーターなしのストアド プロシージャ **sp_MScdc_capture_job** を実行すると開始されます。 このストアド プロシージャは、msdb.dbo.cdc_jobs からキャプチャ ジョブの *maxtrans*、*maxscans*、*continuous*、および *pollinginterval* の構成値を抽出することによって開始されます。 これらの構成値は、パラメーターとしてストアド プロシージャ **sp_cdc_scan** に渡されます。 これは **sp_replcmds** を呼び出してログ スキャンを実行する場合に使用されます。  
  
### キャプチャ ジョブのパラメーター  
 キャプチャ ジョブの動作を理解するには、**sp_cdc_scan** における構成可能パラメーターの使用方法について理解する必要があります。  
  
#### maxtrans パラメーター  
 *maxtrans* パラメーターは、ログの単一のスキャン サイクルで処理できるトランザクションの最大数を指定します。 スキャン時に、処理するトランザクションの数がこの制限値に達すると、現在のスキャンにはそれ以上のトランザクションは含まれません。 スキャン サイクルの完了後は、処理されたトランザクションの数は常に *maxtrans*以下になります。  
  
#### maxscans パラメーター  
 *maxscans* パラメーターは、制御を返す前 (continuous = 0)、または waitfor を実行する前 (continuous = 1) に、ログを空にするために実行されるスキャン サイクルの最大数を指定します。  
  
#### continous パラメーター  
 *continuous* パラメーターは **sp_cdc_scan** が、ログを空にするか、最大数のスキャン サイクル (ワン ショット モード) を実行した後で制御を解放するかどうかを決定します。 また、明示的に停止されるまで、**sp_cdc_scan** の実行を継続するかどうかもこのパラメーターが制御します (連続モード)。  
  
##### ワン ショット モード  
 ワン ショット モードでは、キャプチャ ジョブは **sp_cdc_scan** が最大 *maxtrans* 回のスキャンを実行して、ログを空にして返すことを要求します。 ログに存在するトランザクションで *maxtrans* を超えた分は後のスキャンで処理されます。  
  
 ワン ショット モードは、処理するトランザクションのボリュームがわかっている、制御されたテストで使用され、完了時にジョブが自動的に終了するという利点があります。 ワン ショット モードは、実稼働環境用にはお勧めできません。 これは、このモードではジョブ スケジュールに依存してスキャン サイクル実行の頻度が管理されるためです。  
  
 ワン ショット モードでの実行時には、キャプチャ ジョブの予想スループットの上限を計算できます。これは次の計算式を使用して、1 秒あたりのトランザクション数として表します。  
  
 `(maxtrans * maxscans) / number of seconds between scans`  
  
 ログをスキャンして変更テーブルにデータを設定するために必要な時間が 0 とあまり変わらない場合でも、ジョブの平均スループットは、単一スキャンでのトランザクションの最大許容数にスキャンの最大許容数を掛け、それをログ処理間隔の秒数で割った値を超えることはできません。  
  
 ワン ショット モードでログ スキャンを制御する場合は、ログ処理間の秒数をジョブ スケジュールによって決める必要があります。 このような動作が必要な場合、ログ スキャンの再スケジュールの管理には、連続モードでのキャプチャ ジョブの実行がより適しています。  
  
##### 連続モードとポーリング間隔  
 連続モードでは、キャプチャ ジョブは **sp_cdc_scan** が継続的に実行されることを要求します。 これにより、ストアド プロシージャは、maxtrans と maxscans だけではなく、ログ処理間 (ポーリング間隔) の秒数の値を指定することにより、独自の wait ループを管理できます。 このモードを実行すると、キャプチャ ジョブはアクティブな状態を維持し、ログ スキャン間に **WAITFOR** を実行します。  
  
> [!NOTE]  
>  ポーリング間隔の値が 0 より大きい場合、定期的なワン ショット ジョブのスループットと同じ上限が連続モードのジョブ操作にも適用されます。 つまり、(*maxtrans* \* *maxscans*) をゼロ以外のポーリング間隔で割ると、キャプチャ ジョブで処理できる平均トランザクション数の上限が決まります。  
  
### キャプチャ ジョブのカスタマイズ  
 キャプチャ ジョブでは、追加のロジックを適用することにより、固定したポーリング間隔に依存せずに、新しいスキャンをすぐに開始するか、スリープ状態を経てから新しいスキャンを開始するかを決定できます。 この決定は単に時刻に基づきます。たとえば、アクティビティのピーク時に非常に長いスリープを強制したり、その日の処理を完了し、夜間の運用に備えることが重要な 1 日の終わりにポーリング間隔を 0 にしたりします。 また、キャプチャ プロセスの進捗状態を監視して、午前零時までにコミットされたすべてのトランザクションのスキャンが完了して変更テーブルに格納された時刻を判断することもできます。 これにより、キャプチャ ジョブを終了して、毎日 1 回のスケジュールで再起動することが可能になります。 **sp_cdc_scan** を呼び出すジョブ ステップを、ユーザーが作成した **sp_cdc_scan** のラッパーの呼び出しに置き換えることにより、付加的な労力はほとんどなしで、高度にカスタマイズされた動作を簡単に実現できます。  
  
##  <a name="Cleanup"></a> クリーンアップ ジョブ  
 ここでは、変更データ キャプチャのクリーンアップ ジョブの仕組みについて説明します。  
  
### クリーンアップ ジョブの構造  
 変更データ キャプチャでは、保有期間に基づくクリーンアップ戦略を使用して変更テーブルのサイズを管理します。 クリーンアップ メカニズムは、最初のデータベース テーブルが有効になったときに作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント [!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブで構成されます。 単一のクリーンアップ ジョブがすべてのデータベース変更テーブルのクリーンアップを処理し、定義されたすべてのキャプチャ インスタンスに同じ保有期間値を適用します。  
  
 クリーンアップ ジョブは、パラメーターなしのストアド プロシージャ **sp_MScdc_cleanup_job** を実行すれば開始されます。 このストアド プロシージャは、構成された保有期間値およびしきい値をクリーンアップ ジョブのために **msdb.dbo.cdc_jobs** から抽出すると開始されます。 保有期間値は、変更テーブルの新しい低水位マークの計算に使用します。 **cdc.lsn_time_mapping** テーブルの *tran_end_time* の最大値から指定の分数を差し引き、datetime 値として表す新しい低水位マークを取得します。 その後、CDC.lsn_time_mapping テーブルを使用して、対応する **lsn** 値にこの datetime 値を変換します。 テーブル内の複数のエントリが同じコミット時刻を共有する場合は、最小の **lsn** を持つエントリに対応する **lsn** が新しい低水位マークとして選ばれます。 この **lsn** 値は **sp_cdc_cleanup_change_tables** に渡され、データベース変更テーブルから変更テーブル エントリが削除されます。  
  
> [!NOTE]  
>  最新のトランザクションのコミット時刻を、新しい低水位マークの計算のベースとして使用する利点は、変更を特定の時刻の変更テーブルに残せることです。 これは、キャプチャ プロセスが背後で実行されている場合でも同様です。 実際の低水位マークの共有コミット時刻を持つ最小の **lsn** を選ぶと、現在の低水位マークと同じコミット時刻を持つすべてのエントリは、変更テーブル内に引き続き表示されます。  
  
 クリーンアップが実行されると、すべてのキャプチャ インスタンスの低水位マークが単一のトランザクションで最初に更新されます。 その後、使用されなくなったエントリの変更テーブルおよび cdc.lsn_time_mapping テーブルからの削除が試みられます。 単一のステートメントで削除できるエントリの数は、構成可能なしきい値によって制限されます。 1 つのテーブルで削除が失敗しても、残りのテーブルで削除操作ができなくなるわけではありません。  
  
### クリーンアップ ジョブのカスタマイズ  
 クリーンアップ ジョブの場合、カスタマイズが可能なのは、破棄する変更テーブル エントリを決定する戦略です。 配布されたクリーンアップ ジョブでサポートされる唯一の戦略は時間ベースのものです。 この状況では、新しい低水位マークは最後に処理されたトランザクションのコミット時刻から許容保有期間を引いて計算します。 基になるクリーンアップ プロシージャは、時間ではなく **lsn** に基づいているため、変更テーブルに保持する最小の **lsn** を決定する戦略はいくつもあります。 厳密には時間ベースのものはそのうちの一部のみです。 たとえばクライアントに関する知識は、変更テーブルへのアクセスを必要とするダウンストリーム プロセスを実行できない場合にフェールセーフを提供するために使用できます。 また、既定の戦略ではすべてのデータベースの変更テーブルのクリーンアップに同じ **lsn** を使用しますが、基になるクリーンアップ プロシージャを呼び出してキャプチャ インスタンス レベルでクリーンアップすることもできます。  
  
##  <a name="Monitor"></a> 変更データ キャプチャ プロセスの監視  
 変更データ キャプチャ プロセスを監視すると、変更が変更テーブルに適切に書き込まれているかどうか、および書き込み時の待機時間が妥当かどうかを判断できます。 また、発生する可能性のあるエラーを特定することもできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  には、変更データ キャプチャの監視に役立つ 2 つの動的管理ビューが用意されています。[sys.dm_cdc_log_scan_sessions](../Topic/sys.dm_cdc_log_scan_sessions%20\(Transact-SQL\).md) と [sys.dm_cdc_errors](../Topic/sys.dm_cdc_errors%20\(Transact-SQL\).md) です。  
  
### 空の結果セットを含むセッションの特定  
 sys.dm_cdc_log_scan_sessions の各行はログ スキャン セッションを表します (ID が 0 の行を除く)。 ログ スキャン セッションは、[sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) の 1 回の実行に相当します。 セッション中、スキャンによって変更内容または空の結果のいずれかが返されます。 結果セットが空の場合、sys.dm_cdc_log_scan_sessions の empty_scan_count 列が 1 に設定されます。 空の結果セットが連続する場合 (キャプチャ ジョブを連続的に実行している場合など)、既存の最後の行の empty_scan_count が増分されます。 たとえば、変更内容を返したスキャンについて、sys.dm_cdc_log_scan_sessions に既に 10 行が格納されており、5 つの空の結果が行に含まれている場合、ビューには 11 行が格納され、 最後の行の empty_scan_count 列の値は 5 になります。 空のスキャンを含むセッションを確認するには、次のクエリを実行します。  
  
 `SELECT * from sys.dm_cdc_log_scan_sessions where empty_scan_count <> 0`  
  
### 待機時間の判断  
 sys.dm_cdc_log_scan_sessions 管理ビューには、各キャプチャ セッションの待機時間を記録する列があります。 待機時間は、トランザクションがソース テーブルにコミットされてから、最後にキャプチャされたトランザクションが変更テーブルにコミットされるまでの経過時間として定義されます。 待機時間列では、アクティブなセッションについてのみ値が設定されます。 empty_scan_count 列の値が 0 より大きいセッションについては、待機時間列は 0 に設定されます。 次のクエリは、最新のセッションの平均待機時間を返します。  
  
 `SELECT latency FROM sys.dm_cdc_log_scan_sessions WHERE session_id = 0`  
  
 待機時間データを使用すると、キャプチャ プロセスでのトランザクションの処理時間を確認できます。 このデータが最も役立つのは、キャプチャ プロセスを連続的に実行している場合です。 スケジュールに従ってキャプチャ プロセスを実行している場合、トランザクションがソース テーブルにコミットされてから、スケジュールされた時間にキャプチャ プロセスが実行されるまでの間に遅延が生じるため、待機時間が長くなる可能性があります。  
  
 キャプチャ プロセスに関するもう 1 つの重要な指標はスループットです。 これは、各セッション中に処理された 1 秒あたりの平均コマンド数です。 セッションのスループットを確認するには、command_count 列の値を実行時間列の値で除算します。 次のクエリは、最新のセッションの平均スループットを返します。  
  
 `SELECT command_count/duration AS [Throughput] FROM sys.dm_cdc_log_scan_sessions WHERE session_id = 0`  
  
### データ コレクターを使用したサンプル データの収集  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ コレクターを使用すると、任意のテーブルまたは動的管理ビューからデータのスナップショットを収集して、パフォーマンス データ ウェアハウスを構築することができます。 データベースで変更データ キャプチャが有効になっている場合、sys.dm_cdc_log_scan_sessions ビューおよび sys.dm_cdc_errors ビューのスナップショットを一定間隔で取得すると、後の分析に役立ちます。 次の手順では、sys.dm_cdc_log_scan_sessions 管理ビューからサンプル データを収集するデータ コレクターを設定します。  
  
 **データ コレクションの構成**  
  
1.  データ コレクターを有効にし、管理データ ウェアハウスを構成します。 詳細については、「[データ コレクションの管理](../../relational-databases/data-collection/manage-data-collection.md)」を参照してください。  
  
2.  次のコードを実行して、変更データ キャプチャ用のカスタム データ コレクターを作成します。  
  
    ```tsql  
    USE msdb;  
  
    DECLARE @schedule_uid uniqueidentifier;  
  
    -- Collect and upload data every 5 minutes  
    SELECT @schedule_uid = (  
    SELECT schedule_uid from sysschedules_localserver_view   
    WHERE name = N'CollectorSchedule_Every_5min')  
  
    DECLARE @collection_set_id int;  
  
    EXEC dbo.sp_syscollector_create_collection_set  
    @name = N' CDC Performance Data Collector',  
    @schedule_uid = @schedule_uid,          
    @collection_mode = 0,                   
    @days_until_expiration = 30,                
    @description = N'This collection set collects CDC metadata',  
    @collection_set_id = @collection_set_id output;  
  
    -- Create a collection item using statistics from   
    -- the change data capture dynamic management view.  
    DECLARE @paramters xml;  
    DECLARE @collection_item_id int;  
  
    SELECT @paramters = CONVERT(xml,   
        N'<TSQLQueryCollector>  
            <Query>  
              <Value>SELECT * FROM sys.dm_cdc_log_scan_sessions</Value>  
              <OutputTable>cdc_log_scan_data</OutputTable>  
            </Query>  
          </TSQLQueryCollector>');  
  
    EXEC dbo.sp_syscollector_create_collection_item  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = N'302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @name = ' CDC Performance Data Collector',  
    @frequency = 5,   
    @parameters = @paramters,  
    @collection_item_id = @collection_item_id output;  
  
    GO  
    ```  
  
3.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[管理]**、 **[データ コレクション]**の順に展開します。 **[CDC パフォーマンス データ コレクター]**を右クリックし、 **[データ コレクション セットの開始]**をクリックします。  
  
4.  手順 1. で構成したデータ ウェアハウスで、custom_snapshots.cdc_log_scan_data テーブルを検索します。 このテーブルには、ログ スキャン セッションのデータの履歴スナップショットが格納されています。 このデータを使用すると、待機時間やスループットなどのパフォーマンス指標を時系列で分析できます。  
  
## 参照  
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)   
 [変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [変更データ キャプチャの有効化と無効化 &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md)   
 [変更データの処理 &#40;SQL Server&#41;](../../relational-databases/track-changes/work-with-change-data-sql-server.md)  
  
  