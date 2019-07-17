---
title: sys.dm_os_wait_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_wait_stats_TSQL
- dm_os_wait_stats
- sys.dm_os_wait_stats
- sys.dm_os_wait_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_wait_stats dynamic management view
ms.assetid: 568d89ed-2c96-4795-8a0c-2f3e375081da
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69e23838ed8b237c25bf7ec066e76ee685f25551
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262740"
---
# <a name="sysdmoswaitstats-transact-sql"></a>sys.dm_os_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

実行されたスレッドにより検出されたすべての待機に関する情報を返します。 この集計ビューを使って、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および特定のクエリとバッチに関するパフォーマンスの問題を診断できます。 [sys.dm_exec_session_wait_stats &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md)セッションによって同様の情報を提供します。  
  
> [!NOTE] 
> これから **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]** 、名前を使用して、 **sys.dm_pdw_nodes_os_wait_stats**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|wait_type|**nvarchar(60)**|待機の種類の名前。 詳細については、次を参照してください。[待機の種類](#WaitTypes)、このトピックで後述します。|  
|waiting_tasks_count|**bigint**|この待機の種類における待機の数。 このカウンターは、待機が開始するたび増加します。|  
|wait_time_ms|**bigint**|この待機の種類 (ミリ秒単位) の合計待機時間。 この時間には signal_wait_time_ms が含まれます。|  
|max_wait_time_ms|**bigint**|この待機の種類における最大待機時間。|  
|signal_wait_time_ms|**bigint**|待機スレッドがシグナルを受け取ってから実行を開始するまでの時間。|  
|pdw_node_id|**int**|この配布であるノードの識別子。 <br/> **適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] |  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

##  <a name="WaitTypes"></a> 待機の種類  
 **リソースの待機**リソース待機をワーカーが使用可能なリソースが他のワーカーによって使用されているかはまだ使用可能なリソースへのアクセスを要求する場合に発生します。 リソース待機の例としては、ロック、ラッチ、ネットワークおよびディクス I/O 待機があります。 ロック待機およびラッチ待機は、同期オブジェクトで発生する待機です。  
  
**キュー待機**  
 キュー待機は、ワーカーが作業割り当ての待機でアイドル状態となっている場合に発生します。 キュー待機は、デッドロック監視のようなシステム バックグラウンド タスクや、削除されたレコードのクリーンアップ タスクで最も多く発生します。 これらのタスクは、作業要求が作業キューに配置されるまで待機します。 キュー待機は、新しいパケットがキューに配置されていない場合でも、定期的にアクティブになることがあります。  
  
 **外部待機します。**  
 外部待機は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ワーカーが、拡張ストアド プロシージャ呼び出しやリンク サーバー クエリなどの外部イベントの終了を待機しているときに発生します。 ブロッキングの問題を診断するときには、外部待機が発生していてもワーカーがアイドル状態になっているとは限らないことに注意してください。ワーカーはアクティブ状態で外部コードを実行している可能性があるためです。  
  
 `sys.dm_os_wait_stats` では、既に終わった待機時間が示されます。 この動的管理ビューでは、現在待機中の待機時間は示されません。  
  
 次のいずれかに該当する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ワーカー スレッドは待機中とは見なされません。  
  
-   リソースが使用可能になった。  
  
-   キューが空でない。  
  
-   外部プロセスが終了した。  
  
 スレッドは、待機中でなくなってもすぐに実行を開始する必要はありません。 このようなスレッドは、最初に実行可能なワーカーのキューに配置された後、スケジューラに従って実行するために、クォンタムの間待機する必要があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]待機時間のカウンターは**bigint**値あり、カウンターのロール オーバーが発生しやすく、以前のバージョンの同等カウンタとして[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 クエリ実行中に発生している待機時間の種類によって、クエリにボトルネックや機能停止ポイントがあるかどうかを判断できます。 また、サーバー全体の待機時間や待機カウントが高い値を示している場合は、サーバー インスタンス内の対話型クエリの対話にボトルネックまたはホット スポットが存在していることを表しています。 たとえば、ロック待機の場合はクエリによるデータ競合、ページ I/O ラッチ待機の場合は遅い I/O 反応時間、ページ ラッチ更新待機の場合は不正なファイル レイアウトが存在していると判断できます。  
  
 この動的管理ビューの内容は、次のコマンドを実行してリセットできます。  
  
```sql  
DBCC SQLPERF ('sys.dm_os_wait_stats', CLEAR);  
GO  
```  
  
このコマンドではすべてのカウンターが 0 にリセットされます。  
  
> [!NOTE]
> これらの統計は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動すると消去されます。すべてのデータは、統計が最後にリセットされてから、またはサーバーが最後に起動されてからの累積データです。  
  
 次の表は、タスクで発生する待機の種類の一覧です。  

|type |説明| 
|-------------------------- |--------------------------| 
|ABR |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| | 
|AM_INDBUILD_ALLOCATION |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|AM_SCHEMAMGR_UNSHARED_CACHE |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ASSEMBLY_FILTER_HASHTABLE |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ASSEMBLY_LOAD |アセンブリ読み込みへの排他アクセス時に発生します。| 
|ASYNC_DISKPOOL_LOCK |ファイルの作成や初期化などのタスクを実行している並列スレッドを同期しようとすると発生します。| 
|ASYNC_IO_COMPLETION |タスクが I/O の終了を待機しているときに発生します。| 
|ASYNC_NETWORK_IO |ネットワークの書き込みでタスクがブロックされているときに発生します。 クライアントがサーバーからのデータを処理しているかどうかを確認してください。| 
|ASYNC_OP_COMPLETION |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ASYNC_OP_CONTEXT_READ |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ASYNC_OP_CONTEXT_WRITE |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ASYNC_SOCKETDUP_IO |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|AUDIT_GROUPCACHE_LOCK |特殊なキャッシュへのアクセスを制御するロックに待機があるときに発生します。 このキャッシュには、各監査アクション グループの監査に使用されている監査報告書についての情報が格納されます。| 
|AUDIT_LOGINCACHE_LOCK |特殊なキャッシュへのアクセスを制御するロックに待機があるときに発生します。 このキャッシュには、ログイン監査アクション グループの監査に使用されている監査報告書についての情報が格納されます。| 
|AUDIT_ON_DEMAND_TARGET_LOCK |ロックに待機があるときに発生します。このロックは、監査に関係する拡張イベントのターゲットを確実に単独で初期化できるようにするために使用されるものです。| 
|AUDIT_XE_SESSION_MGR |ロックに待機があるときに発生します。このロックは、監査に関係する拡張イベントのセッションの開始と終了を同期するために使用されるものです。| 
|BACKUP |バックアップ処理の一部としてタスクがブロックされているときに発生します。| 
|BACKUP_OPERATOR |タスクがテープのマウントを待機しているときに発生します。 テープの状態を表示するには、sys.dm_io_backup_tapes をクエリします。 マウント操作が保留中以外のときに、この待機が発生した場合は、テープ ドライブにハードウェア上の問題があると考えられます。| 
|BACKUPBUFFER |バックアップ タスクが、データまたはデータを格納するバッファーを待機しているときに発生します。 この待機は、タスクがテープのマウントを待機しているとき以外はほとんど発生しません。| 
|BACKUPIO |バックアップ タスクが、データまたはデータを格納するバッファーを待機しているときに発生します。 この待機は、タスクがテープのマウントを待機しているとき以外はほとんど発生しません。| 
|BACKUPTHREAD |タスクがバックアップ タスクの終了を待機しているときに発生します。 待機時間の長さは、数分から数時間に及ぶ場合があります。 待機中のタスクが I/O 処理中である場合は、この待機が発生しても問題はありません。| 
|BAD_PAGE_PROCESS |問題があると考えられるバックグラウンドのページ ロガーが、5 秒間隔より頻繁な実行を回避しようとする場合に発生します。 問題があると考えられるページが多くある場合、ロガーは頻繁に実行されます。| 
|BLOB_METADATA |内部使用のみです。 <br />**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BMPALLOCATION |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br />**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BMPBUILD |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br />**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BMPREPARTITION |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BMPREPLICATION |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BPSORT |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_CONNECTION_RECEIVE_TASK |接続エンドポイントでメッセージを受信するためアクセスを待機しているときに発生します。 エンドポイントへの受信アクセスはシリアル化されます。| 
|BROKER_DISPATCHER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_ENDPOINT_STATE_MUTEX |Service Broker の接続エンドポイントの状態へのアクセスの競合があるときに発生します。 変更の状態へのアクセスはシリアル化されます。| 
|BROKER_EVENTHANDLER |Service broker プライマリ イベント ハンドラーでタスクが待機しているときに発生します。 これは非常に簡単に発生する必要があります。| 
|BROKER_FORWARDER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_INIT |各アクティブ データベースで Service Broker を初期化するときに発生します。 この待機は、発生頻度の低い待機です。| 
|BROKER_MASTERSTART |開始する Service broker プライマリ イベント ハンドラーのタスクが待機しているときに発生します。 これは非常に簡単に発生する必要があります。| 
|BROKER_RECEIVE_WAITFOR |RECEIVE WAITFOR が待機しているときに発生します。 いずれか、キューで受信するメッセージがないか、ロックの競合が原因で、キューからメッセージを受信可能性があります。| 
|BROKER_REGISTERALLENDPOINTS |Service Broker の接続エンドポイントの初期化中に発生します。 これは非常に簡単に発生する必要があります。| 
|BROKER_SERVICE |ターゲット サービスに関連付けられている Service Broker のターゲット リストを更新または再優先順位を設定するときに発生します。| 
|BROKER_SHUTDOWN |Service Broker の計画されたシャット ダウンがある場合に発生します。 この待機は、非常に短い時間の待機です。| 
|BROKER_START |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_TASK_SHUTDOWN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_TASK_STOP |Service Broker キューのタスク ハンドラーでタスクをシャット ダウンを行うときに発生します。 ステート チェックがシリアル化されます。ステート チェックは事前に実行状態になっている必要があります。| 
|BROKER_TASK_SUBMIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_TO_FLUSH |Service Broker レイジー フラッシャ フラッシュ メモリ内転送オブジェクトを作業テーブルと発生します。| 
|BROKER_TRANSMISSION_OBJECT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_TRANSMISSION_TABLE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_TRANSMISSION_WORK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|BROKER_TRANSMITTER |Service Broker 送信機能が作業を待機しているときに発生します。 Service Broker では、1 つまたは複数の接続エンドポイントを介して、ネットワーク経由で送信する複数のダイアログからのメッセージをスケジュールする送信機と呼ばれるコンポーネントがあります。 送信機では、この目的の 2 つの専用スレッドがあります。 この待機の種類は、ダイアログのメッセージを送信するためにこれらの送信元のスレッドが待機しているときに課金されますがトランスポート接続を使用します。 Waiting_tasks_count この待機の種類の値が大きい場合は、それらのスレッドの送信機の断続的な作業をポイントし、パフォーマンス問題の兆候がないです。 Service broker はまったく使用しない場合は、waiting_tasks_count 必要があります (2 つの送信元のスレッド) の 2 といます。 インスタンスが開始されてから 2 回の期間をする必要があります。 参照してください[Service broker の待機統計](https://blogs.msdn.microsoft.com/sql_service_broker/2008/12/01/service-broker-wait-types)します。|
|BUILTIN_HASHKEY_MUTEX |この待機はインスタンスの起動後、内部データ構造の初期化中に発生することがあります。 データ構造がいったん初期化されると、それ以降に再発生することはありません。| 
|CHANGE_TRACKING_WAITFORCHANGES |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CHECK_PRINT_RECORD |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|CHECK_SCANNER_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CHECK_TABLES_INITIALIZATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CHECK_TABLES_SINGLE_SCAN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CHECK_TABLES_THREAD_BARRIER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CHECKPOINT_QUEUE |チェックポイント タスクが、次のチェックポイント要求を待機しているときに発生します。| 
|CHKPT |サーバー起動時に発生し、チェックポイント スレッドに開始できることを伝えます。| 
|CLEAR_DB |データベースの開閉など、データベースの状態を変更する操作時に発生します。| 
|CLR_AUTO_EVENT |タスクが共通言語ランタイム (CLR) を実行中で、特定の自動イベントが開始されるのを待機しているときに発生します。 待機は長時間になることが一般的で、問題はありません。| 
|CLR_CRST |タスクが CLR を実行中で、重大なセクションが別のタスクによって現在使用されている場合、そのセクションを待機しているときに発生します。| 
|CLR_JOIN |タスクが CLR を実行中で、別のタスクの終了を待機しているときに発生します。 また、この待機状態は、タスク間の結合があるときに発生します。| 
|CLR_MANUAL_EVENT |タスクが CLR を実行中で、特定の手動イベントが開始されるのを待機しているときに発生します。| 
|CLR_MEMORY_SPY |データ構造のロック取得での待機中に発生します。このデータ構造は、CLR に由来するすべての仮想メモリ割り当てを記録するために使用されます。 データ構造はロックされますが、それは並行アクセスがある場合でもデータの整合性を保持するためです。| 
|CLR_MONITOR |タスクが CLR を実行中で、モニターのロックの取得を待機しているときに発生します。| 
|CLR_RWLOCK_READER |タスクが CLR を実行中で、リーダー ロックを待機しているときに発生します。| 
|CLR_RWLOCK_WRITER |タスクが CLR を実行中で、ライター ロックを待機しているときに発生します。| 
|CLR_SEMAPHORE |タスクが CLR を実行中で、セマフォを待機しているときに発生します。| 
|CLR_TASK_START |CLR タスクが完全に開始されるのを待機しているときに発生します。| 
|CLRHOST_STATE_ACCESS |CLR ホストのデータ構造への排他アクセスを取得するのを待機する場合に発生します。 この待機の種類が発生するのは、CLR ランタイムの設定時か設定解除時です。| 
|CMEMPARTITIONED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CMEMTHREAD |タスクがスレッドセーフ メモリ オブジェクトで待機しているときに発生します。 複数のタスクが同じメモリ オブジェクトからメモリを割り当てようとして競合が発生している場合、待機時間は長くなる可能性があります。| 
|COLUMNSTORE_BUILD_THROTTLE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|COLUMNSTORE_COLUMNDATASET_SESSION_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|COMMIT_TABLE |内部使用のみです。| 
|CONNECTION_ENDPOINT_LOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|COUNTRECOVERYMGR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CREATE_DATINISERVICE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|CXCONSUMER |行を送信するプロデューサー スレッドのコンシューマー スレッドが待機する場合に、並列クエリ プランで発生します。 これは、クエリの並列実行の正常な処理です。 <br /> **適用対象**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP2、 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3)、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|
|CXPACKET |クエリ プロセッサ交換反復子に、同期を実行して、生成および行を使用する場合に、並列クエリ プランで発生します。 待機時間が長すぎて、クエリのチューニング (インデックスの追加など) を実行しても短くできない場合は、並列処理のコストしきい値を調整したり並列処理の次数を下げたりすることを検討してください。<br /> **注:** 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP2、 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3、および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]、クエリ プロセッサ交換反復子を同期して、コンシューマー スレッドの行を生成するのみ CXPACKET を参照します。 コンシューマー スレッドは、CXCONSUMER の待機の種類で個別に追跡されます。| 
|CXROWSET_SYNC |範囲の並列スキャン中に発生します。| 
|DAC_INIT |専用管理者接続の初期化中に発生します。| 
|DBCC_SCALE_OUT_EXPR_CACHE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DBMIRROR_DBM_EVENT |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|DBMIRROR_DBM_MUTEX |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|DBMIRROR_EVENTS_QUEUE |データベース ミラーリングがイベントの処理を待機しているときに発生します。| 
|DBMIRROR_SEND |タスクが、ネットワーク層の通信バックログが消去されメッセージ送信できるようになるのを待機しているときに発生します。 通信層が過負荷になり、データベース ミラーリング データのスループットに影響が生じ始めていることを表します。| 
|DBMIRROR_WORKER_QUEUE |データベース ミラーリング ワーカー タスクが、次の作業の実行を待機していることを表します。| 
|DBMIRRORING_CMD |タスクが、ログ レコードのディスクへのフラッシュを待機しているときに発生します。 この待機状態は、長時間続くことが予想されます。| 
|DBSEEDING_FLOWCONTROL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DBSEEDING_OPERATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DEADLOCK_ENUM_MUTEX |デッドロック モニターと sys.dm_os_waiting_tasks が SQL Server が同時で複数のデッドロック検索を実行されていないことを確認しようと発生します。| 
|DEADLOCK_TASK_SEARCH |このリソースでの待機時間が長い場合は、サーバーが sys.dm_os_waiting_tasks 上で複数のクエリを実行したことにより、デッドロック モニターでデッドロック検索を実行できなくなっていることを表します。 この待機の種類は、デッドロック モニターにのみ使用されます。 sys.dm_os_waiting_tasks の上部のクエリは、DEADLOCK_ENUM_MUTEX を使用します。| 
|DEBUG |Transact SQL と CLR のデバッグの内部同期中に発生します。| 
|DIRECTLOGCONSUMER_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DIRTY_PAGE_POLL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DIRTY_PAGE_SYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DIRTY_PAGE_TABLE_LOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DISABLE_VERSIONING |SQL Server バージョン トランザクション マネージャーは、最も古いアクティブなトランザクションのタイムスタンプが、状態が変化し始めたときのタイムスタンプより後かどうかをポーリングするときに発生します。 最初のトランザクションのタイムスタンプが状態変化のタイムスタンプより後の場合、ALTER DATABASE ステートメントの実行前に開始されたスナップショット トランザクションはすべて終了しています。 この待機状態は、SQL Server は、ALTER DATABASE ステートメントを使用してバージョン管理を無効にされた場合に使用されます。| 
|DISKIO_SUSPEND |外部バックアップがアクティブで、タスクがファイルへのアクセスを待機しているときに発生します。 これは、ユーザー プロセスの待機が発生するたびに報告されます。 1 つのユーザー プロセスの待機が 5 回を超えた場合は、外部バックアップの完了に時間がかかりすぎている可能性があります。| 
|DISPATCHER_PRIORITY_QUEUE_SEMAPHORE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DISPATCHER_QUEUE_SEMAPHORE |ディスパッチャー プールのスレッドが、まだ多くの作業の処理を待機しているときに発生します。 ディスパッチャーがアイドル状態の場合、この待機の種類の待機時間は長くなると予想されます。| 
|DLL_LOADING_MUTEX |XML パーサー DLL が読み込まれるのを待機しているときに 1 回発生します。| 
|DPT_ENTRY_LOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DROP_DATABASE_TIMER_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DROPTEMP |一時オブジェクトの削除を試行して失敗した場合に、次の削除を試行するまでの間に発生します。 この待機時間は、削除の試行が失敗するたびに指数関数的に増えます。| 
|DTC |タスクが、状態遷移の管理に使用されるイベントで待機しているときに発生します。 SQL Server は、MS DTC サービスが利用不可になったことの通知を受信した後、Microsoft 分散トランザクション コーディネーター (MS DTC) トランザクションの復旧が発生したときの状態制御します。| 
|DTC_ABORT_REQUEST |MS DTC ワーカー セッションが、MS DTC トランザクションの所有権取得を待機しているときに発生します。 MS DTC がトランザクションの所有権を取得した後、セッションはそのトランザクションをロールバックできます。 一般に、セッションが待機するのは、そのトランザクションが別のセッションで使用されている場合です。| 
|DTC_RESOLVE |複数のデータベースにまたがるトランザクションで、復旧タスクが、トランザクションの結果をクエリするため master データベースを待機しているときに発生します。| 
|DTC_STATE |内部の MS DTC グローバル状態オブジェクトに対する変更を保護するイベントで、タスクが待機しているときに発生します。 この待機状態は非常に短い時間保持されます。| 
|DTC_TMDOWN_REQUEST |SQL Server が、MS DTC サービスが使用できないことの通知を受信すると、MS DTC ワーカー セッションで発生します。 ワーカーはまず MS DTC 復旧プロセスの開始を待機し、 次に、ワーカーが操作している分散トランザクションの結果取得を待機します。 この待機は、MS DTC サービスとの接続が再度確立されるまで継続される場合があります。| 
|DTC_WAITFOR_OUTCOME |MS DTC がアクティブになり、準備されたトランザクションの解決が可能になるのを、復旧タスクが待機しているときに発生します。| 
|DTCNEW_ENLIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DTCNEW_PREPARE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DTCNEW_RECOVERY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DTCNEW_TM |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DTCNEW_TRANSACTION_ENLISTMENT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DTCPNTSYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|DUMP_LOG_COORDINATOR |メイン タスクが、サブタスクによるデータ生成を待機しているときに発生します。 通常、この待機状態は発生しません。 待機が長時間になる場合は、予期しないブロックが発生している可能性があり、 サブタスクを調査する必要があります。| 
|DUMP_LOG_COORDINATOR_QUEUE |内部使用のみです。| 
|DUMPTRIGGER |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|EC |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|EE_PMOLOCK |ステートメントの実行時、特定の種類のメモリ割り当てを同期するときに発生します。| 
|EE_SPECPROC_MAP_INIT |内部プロシージャ ハッシュ テーブルの作成における同期中に発生します。 この待機は、SQL Server インスタンスを起動した後、ハッシュ テーブルの初期にアクセス中にのみ実行できます。| 
|ENABLE_EMPTY_VERSIONING |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ENABLE_VERSIONING |すべての更新トランザクションが完了するまで、データベースのスナップショット分離が許可されている状態に移行する準備ができてを宣言するには、このデータベースでの SQL Server が待機する場合に発生します。 この状態は、SQL Server、ALTER DATABASE ステートメントを使用してスナップショット分離を使用するときに使用されます。| 
|ERROR_REPORTING_MANAGER |複数のエラー ログの初期化における同期中に発生します。| 
|EXCHANGE |並列クエリの実行時、クエリ プロセッサ交換反復子での同期中に発生します。| 
|EXECSYNC |並列クエリの実行時、交換反復子に関係のない領域での、クエリ プロセッサによる同期中に発生します。 このような領域の例としては、ビットマップ、ラージ バイナリ オブジェクト (LOB)、スプール反復子などがあります。 LOB では、この待機状態が頻繁に使用されることがあります。| 
|EXECUTION_PIPE_EVENT_INTERNAL |バッチ実行のプロデューサー部とコンシューマー部との間で同期しているときに発生します。これらの部は接続コンテキストを通じて送信されます。| 
|EXTERNAL_RG_UPDATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|EXTERNAL_SCRIPT_NETWORK_IO |内部使用のみです。 <br /> **適用対象**:[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]現在経由。| 
|EXTERNAL_SCRIPT_PREPARE_SERVICE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|EXTERNAL_SCRIPT_SHUTDOWN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|EXTERNAL_WAIT_ON_LAUNCHER、 |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FABRIC_HADR_TRANSPORT_CONNECTION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FABRIC_REPLICA_CONTROLLER_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FABRIC_REPLICA_CONTROLLER_STATE_AND_CONFIG |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FABRIC_REPLICA_PUBLISHER_EVENT_PUBLISH |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FABRIC_REPLICA_PUBLISHER_SUBSCRIBER_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FABRIC_WAIT_FOR_BUILD_REPLICA_EVENT_PROCESSING |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FAILPOINT |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|FCB_REPLICA_READ |スナップショット (または DBCC によって作成された一時スナップショット) のスパース ファイルの読み取りを同期するときに発生します。| 
|FCB_REPLICA_WRITE |スナップショット (または DBCC によって作成された一時スナップショット) のスパース ファイルに対するページのプッシュまたはプルを同期するときに発生します。| 
|FEATURE_SWITCHES_UPDATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_DB_KILL_FLAG |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_DB_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_FCB |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_FCB_FIND |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_FCB_PARENT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_FCB_RELEASE_CACHED_ENTRIES |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_FCB_STATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_FILEOBJECT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NSO_TABLE_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_NTFS_STORE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_RECOVERY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_RSFX_COMM |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_RSFX_WAIT_FOR_MEMORY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_STARTUP_SHUTDOWN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_STORE_DB |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_STORE_ROWSET_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FFT_STORE_TABLE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILE_VALIDATION_THREADS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILESTREAM_CACHE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILESTREAM_CHUNKER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILESTREAM_CHUNKER_INIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILESTREAM_FCB |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILESTREAM_FILE_OBJECT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILESTREAM_WORKITEM_QUEUE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FILETABLE_SHUTDOWN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FOREIGN_REDO |内部使用のみです。 <br /> **適用対象**:[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]現在経由。| 
|FORWARDER_TRANSITION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FS_FC_RWLOCK |FILESTREAM ガベージ コレクターが次のいずれかを実行するために待機しているときに発生します。| 
|FS_GARBAGE_COLLECTOR_SHUTDOWN |FILESTREAM ガベージ コレクターがクリーンアップ タスクの完了を待機しているときに発生します。| 
|FS_HEADER_RWLOCK |FILESTREAM データ コンテナーの FILESTREAM ヘッダーへのアクセスの取得を待機しているときに発生します。待機するのは、FILESTREAM ヘッダー ファイル (Filestream.hdr) の内容を読み取るかまたは更新するためです。| 
|FS_LOGTRUNC_RWLOCK |次のいずれかを実行するために、FILESTREAM ログの切り捨てへのアクセスの取得を待機しているときに発生します。| 
|FSA_FORCE_OWN_XACT |FILESTREAM ファイル I/O 操作が、関連付けられているトランザクションにバインドされる必要があるのに、別のセッションがそのトランザクションを現在所有している場合に発生します。| 
|FSAGENT |FILESTREAM ファイル I/O 操作が、FILESTREAM エージェント リソースを待機しているときに発生します。このリソースは別のファイル I/O 操作が使用中です。| 
|FSTR_CONFIG_MUTEX |別の FILESTREAM 機能の再構成が完了するのを待機しているときに発生します。| 
|FSTR_CONFIG_RWLOCK |FILESTREAM 構成パラメーターへのアクセスのシリアル化を待機しているときに発生します。| 
|FT_COMPROWSET_RWLOCK |フル テキストがフラグメントのメタデータの操作を待機しています。 単に情報を示すためだけに記述されます。 サポートされていません。 将来の互換性は保証されません。| 
|FT_IFTS_RWLOCK |フルテキストが内部同期を待機しています。 単に情報を示すためだけに記述されます。 サポートされていません。 将来の互換性は保証されません。| 
|FT_IFTS_SCHEDULER_IDLE_WAIT |フルテキストのスケジューラが待機の種類をスリープしています。 スケジューラはアイドル状態です。| 
|FT_IFTSHC_MUTEX |フルテキストが fdhost 制御操作を待機しています。 単に情報を示すためだけに記述されます。 サポートされていません。 将来の互換性は保証されません。| 
|FT_IFTSISM_MUTEX |フル テキストが通信操作を待機しています。 単に情報を示すためだけに記述されます。 サポートされていません。 将来の互換性は保証されません。| 
|FT_MASTER_MERGE |フル テキストがマスター マージ操作を待機しています。 単に情報を示すためだけに記述されます。 サポートされていません。 将来の互換性は保証されません。| 
|FT_MASTER_MERGE_COORDINATOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FT_METADATA_MUTEX |単に情報を示すためだけに記述されます。 サポートされていません。 将来の互換性は保証されません。| 
|FT_PROPERTYLIST_CACHE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|FT_RESTART_CRAWL |一時的なエラーから復旧するために、正常と認識されている最後の時点からフルテキスト クロールを再開する必要があるときに発生します。 この待機が発生した場合、その設定を現在処理中のワーカー タスクは、現在のステップを完了するか終了することを許可されます。| 
|FULLTEXT GATHERER |フルテキスト操作の同期中に発生します。| 
|GDMA_GET_RESOURCE_OWNER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GHOSTCLEANUP_UPDATE_STATS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GHOSTCLEANUPSYNCMGR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GLOBAL_QUERY_CANCEL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GLOBAL_QUERY_CLOSE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GLOBAL_QUERY_CONSUMER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GLOBAL_QUERY_PRODUCER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GLOBAL_TRAN_CREATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GLOBAL_TRAN_UCS_SESSION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|GUARDIAN |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|HADR_AG_MUTEX |Always On DDL ステートメント、または Windows Server フェールオーバー クラスタ リング コマンドが、可用性グループの構成への排他的読み取り/書き込みアクセスを待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_AR_CRITICAL_SECTION_ENTRY |Always On DDL ステートメント、または Windows Server フェールオーバー クラスタ リング コマンドが関連付けられている可用性グループのローカル レプリカのランタイム状態への排他的読み取り/書き込みアクセスを待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_AR_MANAGER_MUTEX |可用性レプリカのシャットダウンが起動完了を待機しているとき、または可用性レプリカの起動がシャットダウン完了を待機しているときに発生します。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_AR_UNLOAD_COMPLETED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_ARCONTROLLER_NOTIFICATIONS_SUBSCRIBER_LIST |可用性レプリカのイベント (状態の変更または構成の変更など) のパブリッシャーが、イベント サブスクライバーの一覧に対する排他的読み取り/書き込みアクセスを待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_BACKUP_BULK_LOCK |Always On プライマリ データベースからセカンダリ データベースをバックアップ要求を受信したを待つと、バック グラウンド スレッドを取得または BulkOp ロックの解放要求の処理を完了します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_BACKUP_QUEUE |Always On プライマリ データベースのバックアップ バック グラウンド スレッドは、セカンダリ データベースから新しい作業要求を待機しています。 (通常、プライマリ データベースが BulkOp ログを保持していると、プライマリ データベースがロックを解放できることを示すためにセカンダリ データベースが待機しているときに発生).、 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_CLUSAPI_CALL |Windows Server フェールオーバー クラスタ リング Api を呼び出すために (SQL Server でスケジュール済み)、非プリエンプティブ モードから (オペレーティング システムによってスケジュール済み) プリエンプティブ モードに切り替えるに SQL Server スレッドが待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_COMPRESSED_CACHE_SYNC |複数のセカンダリ データベースに送信されるログ ブロックの圧縮が冗長を避けるために使用される圧縮されたログ ブロックのキャッシュへのアクセスを待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_CONNECTIVITY_INFO |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DATABASE_FLOW_CONTROL |メッセージがキュー登録の最大数に達している場合に、パートナーにメッセージが送信されるのを待機しています。 ログ スキャンがネットワーク送信よりも高速に実行されていることを示します。 ネットワーク送信速度が想定よりも遅い場合にのみ問題になります、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DATABASE_VERSIONING_STATE |Always On セカンダリ データベースのバージョン管理の状態の変更時に発生します。 この待機は内部データ構造し、は、通常はごく短時間でデータ アクセスに直接影響はありません、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DATABASE_WAIT_FOR_RECOVERY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DATABASE_WAIT_FOR_RESTART |データベースの Always On 可用性グループの管理下にある再起動を待機しています。 通常の状況では、この問題ではない顧客待機はここで必要なためです、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DATABASE_WAIT_FOR_TRANSITION_TO_VERSIONING |Always On 可用性グループは、セカンダリ レプリカが読み取りワークロードに対して有効にすると、実行中だったすべてのトランザクションのコミットまたはロールバックを待機中に行のバージョン管理ブロックの読み取り可能なセカンダリ データベース内のオブジェクトに対するクエリ。 この待機の種類は、行バージョンはスナップショット分離下で、クエリの実行前に使用できることを保証します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DB_COMMAND |会話型メッセージ (が Alwayson 会話型メッセージ インフラストラクチャを使用して、相手側からの明示的な応答が必要) への応答を待機しています。 この待機の種類を使用して、さまざまなメッセージ型の数値、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DB_OP_COMPLETION_SYNC |会話型メッセージ (が Alwayson 会話型メッセージ インフラストラクチャを使用して、相手側からの明示的な応答が必要) への応答を待機しています。 この待機の種類を使用して、さまざまなメッセージ型の数値、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DB_OP_START_SYNC |Always On DDL ステートメントまたは Windows Server フェールオーバー クラスタ リングのコマンドは、可用性データベースとその実行時状態をシリアル化されたアクセスを待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DBR_SUBSCRIBER |可用性レプリカのイベント (状態の変更または構成の変更など) のパブリッシャーが、可用性データベースに対応するイベント サブスクライバーの実行時状態に対する排他的読み取り/書き込みアクセスを待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DBR_SUBSCRIBER_FILTER_LIST |可用性レプリカのイベント (状態の変更または構成の変更など) のパブリッシャーが、可用性データベースに対応するイベント サブスクライバーの一覧の実行時状態に対する排他的読み取り/書き込みアクセスを待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DBSEEDING |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DBSEEDING_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_DBSTATECHANGE_SYNC |データベース レプリカの内部状態を更新するための同時実行制御の待機します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FABRIC_CALLBACK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_BLOCK_FLUSH |FILESTREAM Alwayson トランスポート マネージャーは、ログ ブロックの処理が完了するまで待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_FILE_CLOSE |FILESTREAM Alwayson トランスポート マネージャーは、[次へ] の FILESTREAM ファイルが処理され、そのハンドルが閉じられるまで待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_FILE_REQUEST |元に戻す中にファイルを Alwayson セカンダリ レプリカがプライマリのレプリカから要求されたすべての FILESTREAM の送信を待機している、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_IOMGR |FILESTREAM Alwayson トランスポート マネージャーがスタートアップまたはシャット ダウン中に、FILESTREAM 常に I/O マネージャーを保護する R/W ロックを待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_IOMGR_IOCOMPLETION |FILESTREAM 常に I/O マネージャーが I/O 完了を待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_MANAGER |FILESTREAM Alwayson トランスポート マネージャーがスタートアップまたはシャット ダウン中に、FILESTREAM Alwayson トランスポート マネージャーを保護する R/W ロックを待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_FILESTREAM_PREPROC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_GROUP_COMMIT |トランザクション コミット処理が、複数のコミット ログ レコードを 1 つのログ ブロックに含めることができるグループ コミットの許可を待機しています。 この待機時間は、ログ、I/O を最適化する予期された状態、キャプチャ、および操作を送信します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_LOGCAPTURE_SYNC |スキャンを作成または破棄する場合の、キャプチャのログまたはオブジェクトの適用に関連するコンカレンシー制御です。 これは、パートナーの状態または接続状態を変更する場合の想定される待機です、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_LOGCAPTURE_WAIT |ログ レコードが使用可能になるのを待機しています。 接続によって新しいログ レコードが生成されるのを待機している場合、またはキャッシュにないログを読み取る際の I/O 完了を待機している場合に発生します。 これは、ログ スキャンがログの末尾に解消またはディスクから読み取る場合に想定される待機です、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_LOGPROGRESS_SYNC |データベース レプリカのログの進行状況を更新するときに同時実行制御の待機します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_NOTIFICATION_DEQUEUE |Windows Server フェールオーバー クラスタリングの通知を処理するバックグラウンド タスクが、次の通知を待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_NOTIFICATION_WORKER_EXCLUSIVE_ACCESS |Always On 可用性レプリカ マネージャーは、Windows Server フェールオーバー クラスタ リングの通知を処理するバック グラウンド タスクのランタイム状態に対するシリアル化のアクセスを待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_NOTIFICATION_WORKER_STARTUP_SYNC |バックグラウンド タスクが、Windows Server フェールオーバー クラスタリングの通知を処理するバックグラウンド タスクの起動完了を待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_NOTIFICATION_WORKER_TERMINATION_SYNC |バックグラウンド タスクが、Windows Server フェールオーバー クラスタリングの通知を処理するバックグラウンド タスクの終了を待機しています。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_PARTNER_SYNC |パートナーの一覧で同時実行制御の待機します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_READ_ALL_NETWORKS |WSFC ネットワークの一覧に対する読み取りまたは書き込みアクセスの取得を待機しています。 内部使用のみです。 注:エンジン (sys.dm_hadr_cluster_networks) などの動的管理ビューで使用される WSFC ネットワークの一覧を保持するか、WSFC を参照するステートメントを常にで TRANSACT-SQL を検証するには、ネットワークの情報。 WSFC 関連のエンジンの起動時にこの一覧が更新されると、通知、および (たとえば、データが失われると WSFC クォーラムを取り戻します) の内部で常に再起動します。 通常、この一覧の更新中はタスクがブロックされます。 、 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_RECOVERY_WAIT_FOR_CONNECTION |復旧を実行する前に、セカンダリ データベースがプライマリ データベースに接続するのを待機しています。 これは、想定される待機で、プライマリへの接続が確立するために速度が遅い場合に長くなることができます、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_RECOVERY_WAIT_FOR_UNDO |データベース復旧が、セカンダリ データベースが復帰および初期化フェーズを完了し、プライマリ データベースと共通のログ ポイントに戻るのを待機しています。 これは、フェールオーバー後に想定される待機です。元に戻す、Windows システム モニター (perfmon.exe) と動的管理ビューにより、進行状況を追跡できます、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_REPLICAINFO_SYNC |現在のレプリカの状態を更新する同時実行制御を待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SEEDING_CANCELLATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SEEDING_FILE_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SEEDING_LIMIT_BACKUPS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SEEDING_SYNC_COMPLETION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SEEDING_TIMEOUT_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SEEDING_WAIT_FOR_COMPLETION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SYNC_COMMIT |同期されているセカンダリ データベースのトランザクション コミット処理が、ログを書き込むのを待機しています。 この待機は、Transaction Delay パフォーマンス カウンターの影響も受けます。 この待機の種類が同期の可用性グループし、送信、書き込み、およびセカンダリ データベースにログを確認する時間を示します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_SYNCHRONIZING_THROTTLE |トランザクション コミット処理が、同期中のセカンダリ データベースに対して、プライマリのログの末尾からの遅れを取り戻して同期済み状態に遷移することを許可するのを待機しています。 これは、セカンダリ データベースが遅れを取り戻している場合の想定される待機です、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_TDS_LISTENER_SYNC |内部の Alwayson システムまたは WSFC クラスターは、リスナーを開始または停止されたことを要求します。 この要求の処理は常に非同期で行われ、冗長な要求を削除するメカニズムがあります。 また、構成の変更が原因でこのプロセスが中断される場合があります。 このリスナー同期メカニズムに関連したすべての待機は、この待機の種類を使用します。 内部でのみ使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_TDS_LISTENER_SYNC_PROCESSING |開始や、可用性グループ リスナーを停止する必要がありますを常に TRANSACT-SQL ステートメントの最後に使用されます。 開始/停止操作が非同期的に完了するため、リスナーの状況を認識するまで、この待機の種類を使用してユーザー スレッドをブロックします、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_THROTTLE_LOG_RATE_GOVERNOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_THROTTLE_LOG_RATE_MISMATCHED_SLO | Geo レプリケーションのセカンダリが下に構成されているときに発生しますプライマリよりもサイズ (低い SLO) を計算します。 プライマリ データベースは、遅延のログの使用量のため、セカンダリで調整されます。 これは、セカンダリ データベースの変更率が、プライマリ データベースの遅れが不足しているコンピューティング容量を持つことが原因です。 <br /> **適用対象**:Azure SQL データベース| 
|HADR_THROTTLE_LOG_RATE_LOG_SIZE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_THROTTLE_LOG_RATE_SEEDING |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_THROTTLE_LOG_RATE_SEND_RECV_QUEUE_SIZE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_TIMER_TASK |タイマー タスク オブジェクトのロックを待機しています。またこれは、実行される作業の間の実際の待機に使用されます。 など、1 回実行した後、10 秒おきに実行されるタスクの Always On 可用性グループは、タスクのスケジュールを変更する約 10 秒を待機し、待機が含まれています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_TRANSPORT_DBRLIST |トランスポート層のデータベース レプリカの一覧に対するアクセスを待機しています。 アクセスを許可するスピンロックのために使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_TRANSPORT_FLOW_CONTROL |未処理の未確認 Alwayson メッセージ数が、アウト時に待機しているフロー制御のしきい値。 これは、(データベースへのデータベースごと) ではなく、可用性レプリカのレプリカごとにします、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_TRANSPORT_SESSION |Always On 可用性グループは変更または基になるトランスポート状態へのアクセス中に待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_WORK_POOL |Always On 可用性グループのバック グラウンド作業タスク オブジェクトの同時実行制御の待機します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_WORK_QUEUE |Always On 可用性グループには、新しい作業が割り当てられるを待機しているワーカー スレッドがバック グラウンドします。 これは、通常の状態である新しい作業を待機している準備完了ワーカーがある場合の想定される待機です、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HADR_XRF_STACK_ACCESS |アクセス (検索、追加、および削除) Always On 可用性データベースの拡張された復旧分岐スタック、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HCCO_CACHE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HK_RESTORE_FILEMAP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HKCS_PARALLEL_MIGRATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HKCS_PARALLEL_RECOVERY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HTBUILD |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HTDELETE |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HTMEMO |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HTREINIT |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HTREPARTITION |スレッドが、バッチ モード演算子内の別の処理ステージの入力の同期中に発生します。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|HTTP_ENUMERATION |起動時に発生し、HTTP を開始するため HTTP エンドポイントを列挙します。| 
|HTTP_START |接続が HTTP の初期化完了を待機しているときに発生します。| 
|HTTP_STORAGE_CONNECTION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|IMPPROV_IOWAIT |SQL Server の一括読み込みを完了する I/O の待機と発生します。| 
|INSTANCE_LOG_RATE_GOVERNOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|INTERNAL_TESTING |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|IO_AUDIT_MUTEX |トレース イベント バッファーの同期中に発生します。| 
|IO_COMPLETION |I/O 操作の完了を待機しているときに発生します。 この待機の種類は通常、データ ページ以外の I/O を表します。 データ ページ I/O の完了の待機は、PAGEIOLATCH として表示\_\*待機します。| 
|IO_QUEUE_LIMIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|IO_RETRY |I/O 操作 (ディスクの読み取り/書き込みなど) に失敗すると発生します。原因はリソース不足による再試行です。| 
|IOAFF_RANGE_QUEUE |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|KSOURCE_WAKEUP |サービス コントロール タスクによって、サービス コントロール マネージャーからの要求を待機しているときに使用されます。 待機は長時間になることが予想されますが、問題はありません。| 
|KTM_ENLISTMENT |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|KTM_RECOVERY_MANAGER |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|KTM_RECOVERY_RESOLUTION |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|LATCH_DT |DT (破棄) ラッチを待機しているときに発生します。 これには、バッファー ラッチまたはトランザクション マーク ラッチは含まれません。 ラッチの一覧\_\*待機は sys.dm_os_latch_stats で使用できます。 sys.dm_os_latch_stats では、LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX、および LATCH_DT の待機はグループ化されます。| 
|LATCH_EX |EX (排他) ラッチを待機しているときに発生します。 これには、バッファー ラッチまたはトランザクション マーク ラッチは含まれません。 ラッチの一覧\_\*待機は sys.dm_os_latch_stats で使用できます。 sys.dm_os_latch_stats では、LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX、および LATCH_DT の待機はグループ化されます。| 
|LATCH_KP |KP (保持) ラッチを待機しているときに発生します。 これには、バッファー ラッチまたはトランザクション マーク ラッチは含まれません。 ラッチの一覧\_\*待機は sys.dm_os_latch_stats で使用できます。 sys.dm_os_latch_stats では、LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX、および LATCH_DT の待機はグループ化されます。| 
|LATCH_NL |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|LATCH_SH |SH (共有) ラッチを待機しているときに発生します。 これには、バッファー ラッチまたはトランザクション マーク ラッチは含まれません。 ラッチの一覧\_\*待機は sys.dm_os_latch_stats で使用できます。 sys.dm_os_latch_stats では、LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX、および LATCH_DT の待機はグループ化されます。| 
|LATCH_UP |UP (更新) ラッチを待機しているときに発生します。 これには、バッファー ラッチまたはトランザクション マーク ラッチは含まれません。 ラッチの一覧\_\*待機は sys.dm_os_latch_stats で使用できます。 sys.dm_os_latch_stats では、LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX、および LATCH_DT の待機はグループ化されます。| 
|LAZYWRITER_SLEEP |レイジー ライター タスクが中断されている場合に発生します。 待機中のバックグラウンド タスクで費やされた時間を測定することができます。 ユーザーの機能停止を検索しているときには、この待機状態は考慮しないでください。| 
|LCK_M_BU |タスクが一括更新 (BU) ロックの取得を待機しているときに発生します。| 
|LCK_M_BU_ABORT_BLOCKERS |タスクがアボート ブロッカーによる一括更新 (BU) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_BU_LOW_PRIORITY |タスクが優先度の低い一括更新 (BU) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_IS |タスクがインテント共有 (IS) ロックの取得を待機しているときに発生します。| 
|LCK_M_IS_ABORT_BLOCKERS |タスクがアボート ブロッカーによるインテント共有 (IS) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_IS_LOW_PRIORITY |タスクが優先度の低いインテント共有 (IS) ロックの取得を待機しているときに発生します。 (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_IU |タスクがインテント更新 (IU) ロックの取得を待機しているときに発生します。| 
|LCK_M_IU_ABORT_BLOCKERS |タスクがアボート ブロッカーによるインテント更新 (IU) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_IU_LOW_PRIORITY |タスクが優先度の低いインテント更新 (IU) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_IX |タスクがインテント排他 (IX) ロックの取得を待機しているときに発生します。| 
|LCK_M_IX_ABORT_BLOCKERS |タスクがアボート ブロッカーによるインテント排他 (IX) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_IX_LOW_PRIORITY |タスクが優先度の低いインテント排他 (IX) ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_NL |タスクが、現在のキー値に対する NULL ロックの取得、および現在のキーから以前のキーまでを対象とした挿入範囲ロックの取得を待機しているときに発生します。 キーの NULL ロックは、すぐに解放されるロックです。| 
|LCK_M_RIn_NL_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる NULL ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる挿入範囲ロックの取得を待機しているときに発生します。 キーの NULL ロックは、すぐに解放されるロックです。 (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_NL_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い NULL ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い挿入範囲ロックの取得を待機しているときに発生します。 キーの NULL ロックは、すぐに解放されるロックです。 (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_S |タスクが、現在のキー値に対する共有ロックの取得、および現在のキーから以前のキーまでを対象とした挿入範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RIn_S_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる共有ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる挿入範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_S_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い共有ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い挿入範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_U |タスクが、現在のキー値に対する更新ロックの取得、および現在のキーから以前のキーまでを対象とした挿入範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RIn_U_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる更新ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる挿入範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_U_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い更新ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い挿入範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_X |タスクが、現在のキー値に対する排他ロックの取得、および現在のキーから以前のキーまでを対象とした挿入範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RIn_X_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる排他ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる挿入範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RIn_X_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い排他ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い挿入範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RS_S |タスクが、現在のキー値に対する共有ロックの取得、および現在のキーから以前のキーまでを対象とした共有範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RS_S_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる共有ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる共有範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RS_S_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い共有ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い共有範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RS_U |タスクが、現在のキー値に対する更新ロックの取得、および現在のキーから以前のキーまでを対象とした更新範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RS_U_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる更新ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる更新範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RS_U_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い更新ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い更新範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RX_S |タスクが、現在のキー値に対する共有ロックの取得、および現在のキーから以前のキーまでを対象とした排他範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RX_S_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる共有ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる排他範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RX_S_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い共有ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い排他範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RX_U |タスクが、現在のキー値に対する更新ロックの取得、および現在のキーから以前のキーまでを対象とした排他範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RX_U_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる更新ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる排他範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RX_U_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い更新ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い排他範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RX_X |タスクが、現在のキー値に対する排他ロックの取得、および現在のキーから以前のキーまでを対象とした排他範囲ロックの取得を待機しているときに発生します。| 
|LCK_M_RX_X_ABORT_BLOCKERS |タスクが、現在のキー値に対するアボート ブロッカーによる排他ロックの取得、および現在のキーから以前のキーまでを対象としたアボート ブロッカーによる排他範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_RX_X_LOW_PRIORITY |タスクが、現在のキー値に対する優先度の低い排他ロックの取得、および現在のキーから以前のキーまでを対象とした優先度の低い排他範囲ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_S |タスクが共有ロックの取得を待機しているときに発生します。| 
|LCK_M_S_ABORT_BLOCKERS |タスクがアボート ブロッカーによる共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_S_LOW_PRIORITY |タスクが優先度の低い共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SCH_M |タスクがスキーマ変更ロックの取得を待機しているときに発生します。| 
|LCK_M_SCH_M_ABORT_BLOCKERS |タスクがアボート ブロッカーによるスキーマ変更ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SCH_M_LOW_PRIORITY |タスクが優先度の低いスキーマ変更ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SCH_S |タスクがスキーマ共有ロックの取得を待機しているときに発生します。| 
|LCK_M_SCH_S_ABORT_BLOCKERS |タスクがアボート ブロッカーによるスキーマ共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SCH_S_LOW_PRIORITY |タスクが優先度の低いスキーマ共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SIU |タスクがインテント更新付き共有ロックの取得を待機しているときに発生します。| 
|LCK_M_SIU_ABORT_BLOCKERS |タスクがアボート ブロッカーによるインテント更新付き共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SIU_LOW_PRIORITY |タスクが優先度の低いインテント更新付き共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SIX |タスクがインテント排他付き共有ロックの取得を待機しているときに発生します。| 
|LCK_M_SIX_ABORT_BLOCKERS |タスクがアボート ブロッカーによるインテント排他付き共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_SIX_LOW_PRIORITY |タスクが優先度の低いインテント排他付き共有ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_U |タスクが更新ロックの取得を待機しているときに発生します。| 
|LCK_M_U_ABORT_BLOCKERS |タスクがアボート ブロッカーによる更新ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_U_LOW_PRIORITY |タスクが優先度の低い更新ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_UIX |タスクがインテント排他付き更新ロックの取得を待機しているときに発生します。| 
|LCK_M_UIX_ABORT_BLOCKERS |タスクがアボート ブロッカーによるインテント排他付き更新ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_UIX_LOW_PRIORITY |タスクが優先度の低いインテント排他付き更新ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_X |タスクが排他ロックの取得を待機しているときに発生します。| 
|LCK_M_X_ABORT_BLOCKERS |タスクがアボート ブロッカーによる排他ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LCK_M_X_LOW_PRIORITY |タスクが優先度の低い排他ロックの取得を待機しているときに発生します (関連する ALTER TABLE および ALTER INDEX の優先度の低い待機オプション。)、 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOG_POOL_SCAN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOG_RATE_GOVERNOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGBUFFER |タスクが、ログ レコードを格納するログ バッファーの領域を待機しているときに発生します。 常に高い値が示される場合は、ログ デバイスで解放される領域よりも、サーバーにより生成されるログ サイズが大きいことを表しています。| 
|LOGCAPTURE_LOGPOOLTRUNCPOINT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGGENERATION |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|LOGMGR |データベースを閉じる間、ログのシャットダウン前に未処理のログ I/O が終了するのをタスクが待機しているときに発生します。| 
|LOGMGR_FLUSH |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|LOGMGR_PMM_LOG |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGMGR_QUEUE |ログ ライター タスクが作業要求を待機しているときに発生します。| 
|LOGMGR_RESERVE_APPEND |新しいログ レコードを書き込むために、タスクが、ログの切り捨てによるログ領域の解放の確認を待機しているときに発生します。 この待機を短縮すると、影響を受けるデータベースのログ ファイル サイズが増えることに注意してください。| 
|LOGPOOL_CACHESIZE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGPOOL_CONSUMER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGPOOL_CONSUMERSET |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGPOOL_FREEPOOLS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGPOOL_MGRSET |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGPOOL_REPLACEMENTSET |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOGPOOLREFCOUNTEDOBJECT_REFDONE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|LOWFAIL_MEMMGR_QUEUE |メモリが使用可能になるのを待機しているときに発生します。| 
|MD_AGENT_YIELD |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|MD_LAZYCACHE_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|MEMORY_ALLOCATION_EXT |SQL Server の内部のメモリ プールまたはオペレーティング システムのいずれかからメモリを割り当てているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|MEMORY_GRANT_UPDATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|METADATA_LAZYCACHE_RWLOCK |内部使用のみです。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|MIGRATIONBUFFER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|MISCELLANEOUS |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|MISCELLANEOUS |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|MSQL_DQ |タスクが分散クエリ操作の終了を待機しているときに発生します。 これは、複数のアクティブな結果セット (MARS) アプリケーションにデッドロックの可能性があるかどうかを検出するために使用されます。 分散クエリ呼び出しが終了すると、待機は終了します。| 
|MSQL_XACT_MGR_MUTEX |タスクが、セッション レベル トランザクション操作を実行するために、セッション トランザクション マネージャーの所有権の取得を待機しているときに発生します。| 
|MSQL_XACT_MUTEX |トランザクション使用の同期中に発生します。 要求でトランザクションを使用するには、まずミューテックスを取得する必要があります。| 
|MSQL_XP |タスクが、拡張ストアド プロシージャの終了を待機しているときに発生します。 SQL Server では、この待機状態を使用して、潜在的な MARS アプリケーションにデッドロックを検出します。 拡張ストアド プロシージャ呼び出しが終了すると、待機は終了します。| 
|MSSEARCH |フルテキスト検索の呼び出し中に発生します。 フルテキスト操作が完了すると、待機は終了します。 この待機はフルテキスト操作の競合ではなく、操作時間を表します。| 
|NET_WAITFOR_PACKET |ネットワークの読み取り中に、接続がネットワーク パケットを待機しているときに発生します。| 
|NETWORKSXMLMGRLOAD |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|NODE_CACHE_MUTEX |内部使用のみです。| 
|OLEDB |SQL Server は、SQL Server Native Client OLE DB プロバイダーを呼び出すときに発生します。 この種類の待機は、同期では使用されません。 代わりに、OLE DB プロバイダー呼び出しの持続時間を示します。| 
|ONDEMAND_TASK_QUEUE |バックグラウンド タスクが、優先度の高いシステム タスクの要求を待機しているときに発生します。 待機時間が長い場合は処理優先度が高い要求がないことを示します。問題があるわけではありません。| 
|PAGEIOLATCH_DT |タスクが、I/O 要求内のバッファー ラッチで待機しているときに発生します。 ラッチ要求は破棄モードです。 待機時間が長い場合、ディスク サブシステムに問題がある可能性があります。| 
|PAGEIOLATCH_EX |タスクが、I/O 要求内のバッファー ラッチで待機しているときに発生します。 ラッチ要求は排他モードです。 待機時間が長い場合、ディスク サブシステムに問題がある可能性があります。| 
|PAGEIOLATCH_KP |タスクが、I/O 要求内のバッファー ラッチで待機しているときに発生します。 ラッチ要求は保持モードです。 待機時間が長い場合、ディスク サブシステムに問題がある可能性があります。| 
|PAGEIOLATCH_NL |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PAGEIOLATCH_SH |タスクが、I/O 要求内のバッファー ラッチで待機しているときに発生します。 ラッチ要求は共有モードです。 待機時間が長い場合、ディスク サブシステムに問題がある可能性があります。| 
|PAGEIOLATCH_UP |タスクが、I/O 要求内のバッファー ラッチで待機しているときに発生します。 ラッチ要求は更新モードです。 待機時間が長い場合、ディスク サブシステムに問題がある可能性があります。| 
|PAGELATCH_DT |タスクが、I/O 要求内にないバッファー ラッチで待機しているときに発生します。 ラッチ要求は破棄モードです。| 
|PAGELATCH_EX |タスクが、I/O 要求内にないバッファー ラッチで待機しているときに発生します。 ラッチ要求は排他モードです。| 
|PAGELATCH_KP |タスクが、I/O 要求内にないバッファー ラッチで待機しているときに発生します。 ラッチ要求は保持モードです。| 
|PAGELATCH_NL |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PAGELATCH_SH |タスクが、I/O 要求内にないバッファー ラッチで待機しているときに発生します。 ラッチ要求は共有モードです。| 
|PAGELATCH_UP |タスクが、I/O 要求内にないバッファー ラッチで待機しているときに発生します。 ラッチ要求は更新モードです。| 
|PARALLEL_BACKUP_QUEUE |RESTORE HEADERONLY、RESTORE FILELISTONLY、または RESTORE LABELONLY によって生成された出力をシリアル化しているときに発生します。| 
|PARALLEL_REDO_DRAIN_WORKER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PARALLEL_REDO_FLOW_CONTROL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PARALLEL_REDO_LOG_CACHE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PARALLEL_REDO_TRAN_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PARALLEL_REDO_TRAN_TURN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PARALLEL_REDO_WORKER_SYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PARALLEL_REDO_WORKER_WAIT_WORK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PERFORMANCE_COUNTERS_RWLOCK |内部使用のみです。| 
|PHYSICAL_SEEDING_DMV |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|POOL_LOG_RATE_GOVERNOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_ABR |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PREEMPTIVE_AUDIT_ACCESS_EVENTLOG |[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] オペレーティング システム (SQLOS) スケジューラが、監査イベントを Windows イベント ログに書き込むためにプリエンプティブ モードに切り替えたときに発生します。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|PREEMPTIVE_AUDIT_ACCESS_SECLOG |SQLOS スケジューラが、監査イベントを Windows セキュリティ ログに書き込むためにプリエンプティブ モードに切り替えたときに発生します。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|PREEMPTIVE_CLOSEBACKUPMEDIA |SQLOS スケジューラが、バックアップ メディアを閉じるためにプリエンプティブ モードに切り替えたときに発生します。| 
|PREEMPTIVE_CLOSEBACKUPTAPE |SQLOS スケジューラが、テープ バックアップ デバイスを閉じるためにプリエンプティブ モードに切り替えたときに発生します。| 
|PREEMPTIVE_CLOSEBACKUPVDIDEVICE |SQLOS スケジューラが、仮想バックアップ デバイスを閉じるためにプリエンプティブ モードに切り替えたときに発生します。| 
|PREEMPTIVE_CLUSAPI_CLUSTERRESOURCECONTROL |SQLOS スケジューラが、Windows フェールオーバー クラスター操作を実行するためにプリエンプティブ モードに切り替えたときに発生します。| 
|PREEMPTIVE_COM_COCREATEINSTANCE |SQLOS スケジューラが、COM オブジェクトを作成するためにプリエンプティブ モードに切り替えたときに発生します。| 
|PREEMPTIVE_COM_COGETCLASSOBJECT |内部使用のみです。| 
|PREEMPTIVE_COM_CREATEACCESSOR |内部使用のみです。| 
|PREEMPTIVE_COM_DELETEROWS |内部使用のみです。| 
|PREEMPTIVE_COM_GETCOMMANDTEXT |内部使用のみです。| 
|PREEMPTIVE_COM_GETDATA |内部使用のみです。| 
|PREEMPTIVE_COM_GETNEXTROWS |内部使用のみです。| 
|PREEMPTIVE_COM_GETRESULT |内部使用のみです。| 
|PREEMPTIVE_COM_GETROWSBYBOOKMARK |内部使用のみです。| 
|PREEMPTIVE_COM_LBFLUSH |内部使用のみです。| 
|PREEMPTIVE_COM_LBLOCKREGION |内部使用のみです。| 
|PREEMPTIVE_COM_LBREADAT |内部使用のみです。| 
|PREEMPTIVE_COM_LBSETSIZE |内部使用のみです。| 
|PREEMPTIVE_COM_LBSTAT |内部使用のみです。| 
|PREEMPTIVE_COM_LBUNLOCKREGION |内部使用のみです。| 
|PREEMPTIVE_COM_LBWRITEAT |内部使用のみです。| 
|PREEMPTIVE_COM_QUERYINTERFACE |内部使用のみです。| 
|PREEMPTIVE_COM_RELEASE |内部使用のみです。| 
|PREEMPTIVE_COM_RELEASEACCESSOR |内部使用のみです。| 
|PREEMPTIVE_COM_RELEASEROWS |内部使用のみです。| 
|PREEMPTIVE_COM_RELEASESESSION |内部使用のみです。| 
|PREEMPTIVE_COM_RESTARTPOSITION |内部使用のみです。| 
|PREEMPTIVE_COM_SEQSTRMREAD |内部使用のみです。| 
|PREEMPTIVE_COM_SEQSTRMREADANDWRITE |内部使用のみです。| 
|PREEMPTIVE_COM_SETDATAFAILURE |内部使用のみです。| 
|PREEMPTIVE_COM_SETPARAMETERINFO |内部使用のみです。| 
|PREEMPTIVE_COM_SETPARAMETERPROPERTIES |内部使用のみです。| 
|PREEMPTIVE_COM_STRMLOCKREGION |内部使用のみです。| 
|PREEMPTIVE_COM_STRMSEEKANDREAD |内部使用のみです。| 
|PREEMPTIVE_COM_STRMSEEKANDWRITE |内部使用のみです。| 
|PREEMPTIVE_COM_STRMSETSIZE |内部使用のみです。| 
|PREEMPTIVE_COM_STRMSTAT |内部使用のみです。| 
|PREEMPTIVE_COM_STRMUNLOCKREGION |内部使用のみです。| 
|PREEMPTIVE_CONSOLEWRITE |内部使用のみです。| 
|PREEMPTIVE_CREATEPARAM |内部使用のみです。| 
|PREEMPTIVE_DEBUG |内部使用のみです。| 
|PREEMPTIVE_DFSADDLINK |内部使用のみです。| 
|PREEMPTIVE_DFSLINKEXISTCHECK |内部使用のみです。| 
|PREEMPTIVE_DFSLINKHEALTHCHECK |内部使用のみです。| 
|PREEMPTIVE_DFSREMOVELINK |内部使用のみです。| 
|PREEMPTIVE_DFSREMOVEROOT |内部使用のみです。| 
|PREEMPTIVE_DFSROOTFOLDERCHECK |内部使用のみです。| 
|PREEMPTIVE_DFSROOTINIT |内部使用のみです。| 
|PREEMPTIVE_DFSROOTSHARECHECK |内部使用のみです。| 
|PREEMPTIVE_DTC_ABORT |内部使用のみです。| 
|PREEMPTIVE_DTC_ABORTREQUESTDONE |内部使用のみです。| 
|PREEMPTIVE_DTC_BEGINTRANSACTION |内部使用のみです。| 
|PREEMPTIVE_DTC_COMMITREQUESTDONE |内部使用のみです。| 
|PREEMPTIVE_DTC_ENLIST |内部使用のみです。| 
|PREEMPTIVE_DTC_PREPAREREQUESTDONE |内部使用のみです。| 
|PREEMPTIVE_FILESIZEGET |内部使用のみです。| 
|PREEMPTIVE_FSAOLEDB_ABORTTRANSACTION |内部使用のみです。| 
|PREEMPTIVE_FSAOLEDB_COMMITTRANSACTION |内部使用のみです。| 
|PREEMPTIVE_FSAOLEDB_STARTTRANSACTION |内部使用のみです。| 
|PREEMPTIVE_FSRECOVER_UNCONDITIONALUNDO |内部使用のみです。| 
|PREEMPTIVE_GETRMINFO |内部使用のみです。| 
|PREEMPTIVE_HADR_LEASE_MECHANISM |Always On 可用性グループ リース マネージャーが Microsoft サポート診断用のスケジュール設定します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_HTTP_EVENT_WAIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_HTTP_REQUEST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_LOCKMONITOR |内部使用のみです。| 
|PREEMPTIVE_MSS_RELEASE |内部使用のみです。| 
|PREEMPTIVE_ODBCOPS |内部使用のみです。| 
|PREEMPTIVE_OLE_UNINIT |内部使用のみです。| 
|PREEMPTIVE_OLEDB_ABORTORCOMMITTRAN |内部使用のみです。| 
|PREEMPTIVE_OLEDB_ABORTTRAN |内部使用のみです。| 
|PREEMPTIVE_OLEDB_GETDATASOURCE |内部使用のみです。| 
|PREEMPTIVE_OLEDB_GETLITERALINFO |内部使用のみです。| 
|PREEMPTIVE_OLEDB_GETPROPERTIES |内部使用のみです。| 
|PREEMPTIVE_OLEDB_GETPROPERTYINFO |内部使用のみです。| 
|PREEMPTIVE_OLEDB_GETSCHEMALOCK |内部使用のみです。| 
|PREEMPTIVE_OLEDB_JOINTRANSACTION |内部使用のみです。| 
|PREEMPTIVE_OLEDB_RELEASE |内部使用のみです。| 
|PREEMPTIVE_OLEDB_SETPROPERTIES |内部使用のみです。| 
|PREEMPTIVE_OLEDBOPS |内部使用のみです。| 
|PREEMPTIVE_OS_ACCEPTSECURITYCONTEXT |内部使用のみです。| 
|PREEMPTIVE_OS_ACQUIRECREDENTIALSHANDLE |内部使用のみです。| 
|PREEMPTIVE_OS_AUTHENTICATIONOPS |内部使用のみです。| 
|PREEMPTIVE_OS_AUTHORIZATIONOPS |内部使用のみです。| 
|PREEMPTIVE_OS_AUTHZGETINFORMATIONFROMCONTEXT |内部使用のみです。| 
|PREEMPTIVE_OS_AUTHZINITIALIZECONTEXTFROMSID |内部使用のみです。| 
|PREEMPTIVE_OS_AUTHZINITIALIZERESOURCEMANAGER |内部使用のみです。| 
|PREEMPTIVE_OS_BACKUPREAD |内部使用のみです。| 
|PREEMPTIVE_OS_CLOSEHANDLE |内部使用のみです。| 
|PREEMPTIVE_OS_CLUSTEROPS |内部使用のみです。| 
|PREEMPTIVE_OS_COMOPS |内部使用のみです。| 
|PREEMPTIVE_OS_COMPLETEAUTHTOKEN |内部使用のみです。| 
|PREEMPTIVE_OS_COPYFILE |内部使用のみです。| 
|PREEMPTIVE_OS_CREATEDIRECTORY |内部使用のみです。| 
|PREEMPTIVE_OS_CREATEFILE |内部使用のみです。| 
|PREEMPTIVE_OS_CRYPTACQUIRECONTEXT |内部使用のみです。| 
|PREEMPTIVE_OS_CRYPTIMPORTKEY |内部使用のみです。| 
|PREEMPTIVE_OS_CRYPTOPS |内部使用のみです。| 
|PREEMPTIVE_OS_DECRYPTMESSAGE |内部使用のみです。| 
|PREEMPTIVE_OS_DELETEFILE |内部使用のみです。| 
|PREEMPTIVE_OS_DELETESECURITYCONTEXT |内部使用のみです。| 
|PREEMPTIVE_OS_DEVICEIOCONTROL |内部使用のみです。| 
|PREEMPTIVE_OS_DEVICEOPS |内部使用のみです。| 
|PREEMPTIVE_OS_DIRSVC_NETWORKOPS |内部使用のみです。| 
|PREEMPTIVE_OS_DISCONNECTNAMEDPIPE |内部使用のみです。| 
|PREEMPTIVE_OS_DOMAINSERVICESOPS |内部使用のみです。| 
|PREEMPTIVE_OS_DSGETDCNAME |内部使用のみです。| 
|PREEMPTIVE_OS_DTCOPS |内部使用のみです。| 
|PREEMPTIVE_OS_ENCRYPTMESSAGE |内部使用のみです。| 
|PREEMPTIVE_OS_FILEOPS |内部使用のみです。| 
|PREEMPTIVE_OS_FINDFILE |内部使用のみです。| 
|PREEMPTIVE_OS_FLUSHFILEBUFFERS |内部使用のみです。| 
|PREEMPTIVE_OS_FORMATMESSAGE |内部使用のみです。| 
|PREEMPTIVE_OS_FREECREDENTIALSHANDLE |内部使用のみです。| 
|PREEMPTIVE_OS_FREELIBRARY |内部使用のみです。| 
|PREEMPTIVE_OS_GENERICOPS |内部使用のみです。| 
|PREEMPTIVE_OS_GETADDRINFO |内部使用のみです。| 
|PREEMPTIVE_OS_GETCOMPRESSEDFILESIZE |内部使用のみです。| 
|PREEMPTIVE_OS_GETDISKFREESPACE |内部使用のみです。| 
|PREEMPTIVE_OS_GETFILEATTRIBUTES |内部使用のみです。| 
|PREEMPTIVE_OS_GETFILESIZE |内部使用のみです。| 
|PREEMPTIVE_OS_GETFINALFILEPATHBYHANDLE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_OS_GETLONGPATHNAME |内部使用のみです。| 
|PREEMPTIVE_OS_GETPROCADDRESS |内部使用のみです。| 
|PREEMPTIVE_OS_GETVOLUMENAMEFORVOLUMEMOUNTPOINT |内部使用のみです。| 
|PREEMPTIVE_OS_GETVOLUMEPATHNAME |内部使用のみです。| 
|PREEMPTIVE_OS_INITIALIZESECURITYCONTEXT |内部使用のみです。| 
|PREEMPTIVE_OS_LIBRARYOPS |内部使用のみです。| 
|PREEMPTIVE_OS_LOADLIBRARY |内部使用のみです。| 
|PREEMPTIVE_OS_LOGONUSER |内部使用のみです。| 
|PREEMPTIVE_OS_LOOKUPACCOUNTSID |内部使用のみです。| 
|PREEMPTIVE_OS_MESSAGEQUEUEOPS |内部使用のみです。| 
|PREEMPTIVE_OS_MOVEFILE |内部使用のみです。| 
|PREEMPTIVE_OS_NETGROUPGETUSERS |内部使用のみです。| 
|PREEMPTIVE_OS_NETLOCALGROUPGETMEMBERS |内部使用のみです。| 
|PREEMPTIVE_OS_NETUSERGETGROUPS |内部使用のみです。| 
|PREEMPTIVE_OS_NETUSERGETLOCALGROUPS |内部使用のみです。| 
|PREEMPTIVE_OS_NETUSERMODALSGET |内部使用のみです。| 
|PREEMPTIVE_OS_NETVALIDATEPASSWORDPOLICY |内部使用のみです。| 
|PREEMPTIVE_OS_NETVALIDATEPASSWORDPOLICYFREE |内部使用のみです。| 
|PREEMPTIVE_OS_OPENDIRECTORY |内部使用のみです。| 
|PREEMPTIVE_OS_PDH_WMI_INIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_OS_PIPEOPS |内部使用のみです。| 
|PREEMPTIVE_OS_PROCESSOPS |内部使用のみです。| 
|PREEMPTIVE_OS_QUERYCONTEXTATTRIBUTES |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_OS_QUERYREGISTRY |内部使用のみです。| 
|PREEMPTIVE_OS_QUERYSECURITYCONTEXTTOKEN |内部使用のみです。| 
|PREEMPTIVE_OS_REMOVEDIRECTORY |内部使用のみです。| 
|PREEMPTIVE_OS_REPORTEVENT |内部使用のみです。| 
|PREEMPTIVE_OS_REVERTTOSELF |内部使用のみです。| 
|PREEMPTIVE_OS_RSFXDEVICEOPS |内部使用のみです。| 
|PREEMPTIVE_OS_SECURITYOPS |内部使用のみです。| 
|PREEMPTIVE_OS_SERVICEOPS |内部使用のみです。| 
|PREEMPTIVE_OS_SETENDOFFILE |内部使用のみです。| 
|PREEMPTIVE_OS_SETFILEPOINTER |内部使用のみです。| 
|PREEMPTIVE_OS_SETFILEVALIDDATA |内部使用のみです。| 
|PREEMPTIVE_OS_SETNAMEDSECURITYINFO |内部使用のみです。| 
|PREEMPTIVE_OS_SQLCLROPS |内部使用のみです。| 
|PREEMPTIVE_OS_SQMLAUNCH |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] |  
|PREEMPTIVE_OS_VERIFYSIGNATURE |内部使用のみです。| 
|PREEMPTIVE_OS_VERIFYTRUST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_OS_VSSOPS |内部使用のみです。| 
|PREEMPTIVE_OS_WAITFORSINGLEOBJECT |内部使用のみです。| 
|PREEMPTIVE_OS_WINSOCKOPS |内部使用のみです。| 
|PREEMPTIVE_OS_WRITEFILE |内部使用のみです。| 
|PREEMPTIVE_OS_WRITEFILEGATHER |内部使用のみです。| 
|PREEMPTIVE_OS_WSASETLASTERROR |内部使用のみです。| 
|PREEMPTIVE_REENLIST |内部使用のみです。| 
|PREEMPTIVE_RESIZELOG |内部使用のみです。| 
|PREEMPTIVE_ROLLFORWARDREDO |内部使用のみです。| 
|PREEMPTIVE_ROLLFORWARDUNDO |内部使用のみです。| 
|PREEMPTIVE_SB_STOPENDPOINT |内部使用のみです。| 
|PREEMPTIVE_SERVER_STARTUP |内部使用のみです。| 
|PREEMPTIVE_SETRMINFO |内部使用のみです。| 
|PREEMPTIVE_SHAREDMEM_GETDATA |内部使用のみです。| 
|PREEMPTIVE_SNIOPEN |内部使用のみです。| 
|PREEMPTIVE_SOSHOST |内部使用のみです。| 
|PREEMPTIVE_SOSTESTING |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PREEMPTIVE_SP_SERVER_DIAGNOSTICS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_STARTRM |内部使用のみです。| 
|PREEMPTIVE_STREAMFCB_CHECKPOINT |内部使用のみです。| 
|PREEMPTIVE_STREAMFCB_RECOVER |内部使用のみです。| 
|PREEMPTIVE_STRESSDRIVER |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PREEMPTIVE_TESTING |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PREEMPTIVE_TRANSIMPORT |内部使用のみです。| 
|PREEMPTIVE_UNMARSHALPROPAGATIONTOKEN |内部使用のみです。| 
|PREEMPTIVE_VSS_CREATESNAPSHOT |内部使用のみです。| 
|PREEMPTIVE_VSS_CREATEVOLUMESNAPSHOT |内部使用のみです。| 
|PREEMPTIVE_XE_CALLBACKEXECUTE |内部使用のみです。| 
|PREEMPTIVE_XE_CX_FILE_OPEN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_XE_CX_HTTP_CALL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PREEMPTIVE_XE_DISPATCHER |内部使用のみです。| 
|PREEMPTIVE_XE_ENGINEINIT |内部使用のみです。| 
|PREEMPTIVE_XE_GETTARGETSTATE |内部使用のみです。| 
|PREEMPTIVE_XE_SESSIONCOMMIT |内部使用のみです。| 
|PREEMPTIVE_XE_TARGETFINALIZE |内部使用のみです。| 
|PREEMPTIVE_XE_TARGETINIT |内部使用のみです。| 
|PREEMPTIVE_XE_TIMERRUN |内部使用のみです。| 
|PREEMPTIVE_XETESTING |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|PRINT_ROLLBACK_PROGRESS |ALTER DATABASE 終了句を使って遷移されたデータベースで、ユーザー プロセスが終了するのを待機する場合に使用されます。 詳細については、ALTER DATABASE (TRANSACT-SQL) を参照してください。| 
|PRU_ROLLBACK_DEFERRED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_ALL_COMPONENTS_INITIALIZED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_COOP_SCAN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_DIRECTLOGCONSUMER_GETNEXT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_EVENT_SESSION_INIT_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_FABRIC_REPLICA_CONTROLLER_DATA_LOSS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_ACTION_COMPLETED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_CHANGE_NOTIFIER_TERMINATION_SYNC |(ポーリング) 経由で受信するバック グラウンド タスクの終了のバック グラウンド タスクが待機しているときに発生する Windows Server フェールオーバー クラスタ リングの通知、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_CLUSTER_INTEGRATION |追加、置換、または削除操作が (ネットワーク、ネットワーク アドレス、または可用性グループ リスナーのリスト) などで常に内部リストで書き込みロックの獲得を待機しています。 内部使用のみ <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_FAILOVER_COMPLETED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_JOIN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_OFFLINE_COMPLETED |Windows Server フェールオーバー クラスタ リングのオブジェクトを破棄する前にオフラインにするターゲットの可用性グループを Always On 可用性グループ削除操作は待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_ONLINE_COMPLETED |Always On を作成またはオンラインにする対象の可用性グループの可用性グループのフェールオーバー操作が待機しています、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_POST_ONLINE_COMPLETED |Always On 可用性グループ削除操作は、前のコマンドの一部としてスケジュール設定された任意のバック グラウンド タスクの終了を待機しています。 たとえば、可用性データベースをプライマリ ロールに遷移させるバックグラウンド タスクが存在する場合があります。 DROP AVAILABILITY GROUP DDL は、競合状態を回避するために終了するには、このバック グラウンド タスクを待つ必要があります、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_SERVER_READY_CONNECTIONS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADR_WORKITEM_COMPLETED |非同期作業タスクの完了を待機するスレッドによる、内部的な待機です。 これは想定される待機でありは CSS を使用します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_HADRSIM |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_LOG_CONSOLIDATION_IO |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_LOG_CONSOLIDATION_POLL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_MD_LOGIN_STATS |ログイン統計のメタデータでの内部同期中に発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_MD_RELATION_CACHE |テーブルまたはインデックスのメタデータでの内部同期中に発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_MD_SERVER_CACHE |リンク サーバー上のメタデータでの内部同期中に発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_MD_UPGRADE_CONFIG |サーバー全体の構成のアップグレードでの内部同期中に発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_PREEMPTIVE_APP_USAGE_TIMER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_PREEMPTIVE_AUDIT_ACCESS_WINDOWSLOG |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_QRY_BPMEMORY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_REPLICA_ONLINE_INIT_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_RESOURCE_SEMAPHORE_FT_PARALLEL_QUERY_SYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_SBS_FILE_OPERATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_XTP_FSSTORAGE_MAINTENANCE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|PWAIT_XTP_HOST_STORAGE_WAIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_ASYNC_CHECK_CONSISTENCY_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_ASYNC_PERSIST_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_ASYNC_PERSIST_TASK_START |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_ASYNC_QUEUE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_BCKG_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_BLOOM_FILTER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_CLEANUP_STALE_QUERIES_TASK_MAIN_LOOP_SLEEP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_CTXS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_DB_DISK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_DYN_VECTOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_EXCLUSIVE_ACCESS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_HOST_INIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_LOADDB |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_PERSIST_TASK_MAIN_LOOP_SLEEP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_QDS_CAPTURE_INIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_SHUTDOWN_QUEUE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_STMT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_STMT_DISK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_TASK_SHUTDOWN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QDS_TASK_START |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QE_WARN_LIST_SYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QPJOB_KILL |非同期自動統計更新が実行を開始したときに、強制終了の呼び出しにより操作が取り消されたことを示します。 終了スレッドは一時中断され、強制終了コマンドの受信開始を待機します。 1 秒未満であれば問題はありません。| 
|QPJOB_WAITFOR_ABORT |非同期自動統計更新の実行中に、強制終了の呼び出しにより操作が取り消されたことを示します。 更新は現在完了していますが、終了スレッド メッセージ調整が完了するまでは一時中断されます。 これは通常の状態ですが、発生することはほとんどありません。発生しても非常に短い時間です。 1 秒未満であれば問題はありません。| 
|QRY_MEM_GRANT_INFO_MUTEX |クエリ実行メモリ管理が、静的な許可情報リストへのアクセスを制御しようとするときに発生します。 この待機状態では、現在許可されており待機中のメモリ要求に関する情報が一覧表示されます。 またこの状態は、単純なアクセス制御状態です。 この状態では、長時間に及ぶ待機は避けてください。 このミューテックスが解放されない場合、新しいメモリを使用するすべてのクエリは応答を停止します。| 
|QRY_PARALLEL_THREAD_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QRY_PROFILE_LIST_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QUERY_ERRHDL_SERVICE_DONE |単に情報を示すためだけに特定されます。 サポートされていません。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|QUERY_WAIT_ERRHDL_SERVICE |単に情報を示すためだけに特定されます。  サポートされていません。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。  |  
|QUERY_EXECUTION_INDEX_SORT_EVENT_OPEN |オフラインでのインデックス作成が並列実行される場合、並べ替えを行っている複数のワーカー スレッドが並べ替えファイルへのアクセスを同期するときに発生する場合があります。| 
|QUERY_NOTIFICATION_MGR_MUTEX |クエリ通知マネージャー内のガベージ コレクション キューの同期中に発生します。| 
|QUERY_NOTIFICATION_SUBSCRIPTION_MUTEX |クエリ通知内のトランザクションの状態の同期中に発生します。| 
|QUERY_NOTIFICATION_TABLE_MGR_MUTEX |クエリ通知マネージャー内での内部同期中に発生します。| 
|QUERY_NOTIFICATION_UNITTEST_MUTEX |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|QUERY_OPTIMIZER_PRINT_MUTEX |クエリ オプティマイザー診断の出力作成の同期中に発生します。 この待機の種類は、マイクロソフト製品サポートの方向] の [診断設定を有効になっている場合にのみ発生します。| 
|QUERY_TASK_ENQUEUE_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|QUERY_TRACEOUT |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|RBIO_WAIT_VLF |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|RBIO_RG_STORAGE |ページ サーバーの消費量は遅延ログにより、ハイパー スケールのデータベースのコンピューティング ノードが制限されているときに発生します。 <br /> **適用対象**:Azure SQL データベースのハイパー スケールします。|
|RBIO_RG_DESTAGE |ハイパー スケールのデータベースのコンピューティング ノードが長期的なログのストレージ遅延ログの使用量のため制限されているときに発生します。 <br /> **適用対象**:Azure SQL データベースのハイパー スケールします。|
|RBIO_RG_REPLICA |ためにデータベースのコンピューティング ノードが制限されているハイパー スケールで読み取り可能セカンダリ レプリカ ノード ログの使用量を遅延する場合に発生します。 <br /> **適用対象**:Azure SQL データベースのハイパー スケールします。|
|RBIO_RG_LOCALDESTAGE |ログ サービスによってハイパー スケールのデータベースのコンピューティング ノードが遅延ログの使用量のため制限されているときに発生します。 <br /> **適用対象**:Azure SQL データベースのハイパー スケールします。|
|RECOVER_CHANGEDB |ウォーム スタンバイ データベース内で、データベースの状態の同期中に発生します。| 
|RECOVERY_MGR_LOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REDO_THREAD_PENDING_WORK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REDO_THREAD_SYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REMOTE_BLOCK_IO |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REMOTE_DATA_ARCHIVE_MIGRATION_DMV |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REMOTE_DATA_ARCHIVE_SCHEMA_DMV |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REMOTE_DATA_ARCHIVE_SCHEMA_TASK_QUEUE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REPL_CACHE_ACCESS |レプリケーション アーティクル キャッシュでの同期中に発生します。 この待機中、レプリケーション ログ リーダーは停止し、パブリッシュされたテーブルに対するデータ定義言語 (DDL) ステートメントはブロックされます。| 
|REPL_HISTORYCACHE_ACCESS |内部使用のみです。| 
|REPL_SCHEMA_ACCESS |レプリケーション スキーマのバージョン情報の同期中に発生します。 この状態は、レプリケートされたオブジェクトで DDL ステートメントが実行されるとき、および、ログ リーダーが DDL の発生に基づいてバージョン管理されたスキーマを作成または使用するときに発生します。 1 つのトランザクション レプリケーションでパブリッシャーに多数のパブリッシュされたデータベースが存在し、パブリッシュされたデータベースは非常にアクティブな場合は、この待機の種類の競合を確認できます。| 
|REPL_TRANFSINFO_ACCESS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REPL_TRANHASHTABLE_ACCESS |内部使用のみです。| 
|REPL_TRANTEXTINFO_ACCESS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|REPLICA_WRITES |タスクが、データベース スナップショットまたは DBCC レプリカへのページ書き込みの完了を待機しているときに発生します。| 
|REQUEST_DISPENSER_PAUSE |タスクが、未処理の I/O がすべて完了しスナップショット バックアップ用にファイルの I/O が固定されるのを待機しているときに発生します。| 
|REQUEST_FOR_DEADLOCK_SEARCH |デッドロック モニターが、次のデッドロック検索の開始を待機しているときに発生します。 この待機は、デッドロックが検出されてから次に検出されるまでの間に発生することが予想されます。このリソースにおける合計待機時間が長くても問題はありません。| 
|RESERVED_MEMORY_ALLOCATION_EXT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|RESMGR_THROTTLED |新しい要求が着信し、GROUP_MAX_REQUESTS 設定に基づいて絞り込まれたときに発生します。| 
|RESOURCE_GOVERNOR_IDLE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|RESOURCE_QUEUE |さまざまな内部リソース キューの同期中に発生します。| 
|RESOURCE_SEMAPHORE |他の同時実行クエリがあるため、クエリ メモリの要求がすぐに許可されない場合に発生します。 待機および待機時間が高い値を示している場合は、同時実行クエリの数が多すぎるか、またはメモリ要求の数が多すぎる可能性があります。| 
|RESOURCE_SEMAPHORE_MUTEX |クエリが、スレッドを予約するための要求を待機しているときに発生します。 この待機は、クエリのコンパイルとメモリの要求許可を同期しているときにも発生します。| 
|RESOURCE_SEMAPHORE_QUERY_COMPILE |コンパイルされる同時実行クエリの数が、スロットルの制限値に達したときに発生します。 待機および待機時間が高い値を示している場合は、コンパイル、再コンパイル、またはキャッシュできないプランの数が多すぎる可能性があります。| 
|RESOURCE_SEMAPHORE_SMALL_QUERY |他の同時実行クエリがあるため、サイズの小さいクエリからのメモリ要求がすぐに許可されない場合に発生します。 待機時間は数秒以内である必要があります。要求したメモリが数秒以内に許可されないと、サーバーによって要求がメイン クエリのメモリ プールに転送されます。 待機が高い値を示している場合は、待機クエリによって主要なメモリ プールがブロックされているときに、サイズの小さい同時実行クエリの数が多すぎる可能性があります。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|RESTORE_FILEHANDLECACHE_ENTRYLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|RESTORE_FILEHANDLECACHE_LOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|RG_RECONFIG |内部使用のみです。| 
|ROWGROUP_OP_STATS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|ROWGROUP_VERSION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|RTDATA_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SATELLITE_CARGO |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SATELLITE_SERVICE_SETUP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SATELLITE_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SBS_DISPATCH |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SBS_RECEIVE_TRANSPORT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SBS_TRANSPORT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SCAN_CHAR_HASH_ARRAY_INITIALIZATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SEC_DROP_TEMP_KEY |一時セキュリティ キーを削除しようとして失敗した後、再試行するまでの間に発生します。| 
|SECURITY_CNG_PROVIDER_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SECURITY_CRYPTO_CONTEXT_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SECURITY_DBE_STATE_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SECURITY_KEYRING_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SECURITY_MUTEX |ミューテックスを待機しているときに発生します。このミューテックスは、拡張キー管理 (EKM) 暗号化サービス プロバイダーのグローバル リストへのアクセス、および EKM セッションのセッション スコープ リストへのアクセスを制御します。| 
|SECURITY_RULETABLE_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SEMPLAT_DSI_BUILD |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SEQUENCE_GENERATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SEQUENTIAL_GUID |新しいシーケンシャル GUID を取得中に発生します。| 
|SERVER_IDLE_CHECK |リソース モニターがアイドル状態と SQL Server インスタンスを宣言しようとしてまたは起動しようとは、SQL Server インスタンスのアイドル状態の同期中に発生します。| 
|SERVER_RECONFIGURE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SESSION_WAIT_STATS_CHILDREN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SHARED_DELTASTORE_CREATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SHUTDOWN |シャットダウン ステートメントが、アクティブな接続の終了を待機しているときに発生します。| 
|SLEEP_BPOOL_FLUSH |ディスク サブシステムが飽和状態にならないよう、チェックポイントで新しい I/O の実行をスロットル中に発生します。| 
|SLEEP_BUFFERPOOL_HELPLW |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLEEP_DBSTARTUP |すべてのデータベースが復旧するのを待機している間、データベースの起動中に発生します。| 
|SLEEP_DCOMSTARTUP |DCOM の初期化が完了するを待機中に SQL Server インスタンスの起動中に最大で 1 回に発生します。| 
|SLEEP_MASTERDBREADY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLEEP_MASTERMDREADY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLEEP_MASTERUPGRADED |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLEEP_MEMORYPOOL_ALLOCATEPAGES |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLEEP_MSDBSTARTUP |SQL トレースが msdb データベースの起動完了を待機しているときに発生します。| 
|SLEEP_RETRY_VIRTUALALLOC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLEEP_SYSTEMTASK |tempdb の起動完了を待機している間、バックグラウンド タスクの開始中に発生します。| 
|SLEEP_TASK |ジェネリック イベントの発生を待機している間、タスクがスリープ状態のときに発生します。| 
|SLEEP_TEMPDBSTARTUP |タスクが、tempdb の開始完了を待機しているときに発生します。| 
|SLEEP_WORKSPACE_ALLOCATEPAGE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SLO_UPDATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SMSYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SNI_CONN_DUP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SNI_CRITICAL_SECTION |SQL Server のネットワーク コンポーネント内の内部同期中に発生します。| 
|SNI_HTTP_WAITFOR_0_DISCON |未処理の HTTP 接続が終了するを待機中に、SQL Server のシャット ダウン中に発生します。| 
|SNI_LISTENER_ACCESS |NUMA (non-uniform memory access) ノードが状態の変化を更新するのを待機している間に発生します。 状態の変化へのアクセスはシリアル化されます。| 
|SNI_TASK_COMPLETION |NUMA ノード状態の変化中にすべてのタスクが終了するのを待機しているときに発生します。| 
|SNI_WRITE_ASYNC |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SOAP_READ |HTTP ネットワークの読み取り完了を待機しているときに発生します。| 
|SOAP_WRITE |HTTP ネットワークの書き込み完了を待機しているときに発生します。| 
|SOCKETDUPLICATEQUEUE_CLEANUP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SOS_CALLBACK_REMOVAL |コールバックを削除するために、コールバックの一覧で同期を実行しているときに発生します。 サーバーの初期化が完了した後、通常この待機カウンターが変更されることはありません。| 
|SOS_DISPATCHER_MUTEX |ディスパッチャー プールの内部初期化中に発生します。 これには、プールの調整中も含まれます。| 
|SOS_LOCALALLOCATORLIST |[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] メモリ マネージャー内での内部同期中に発生します。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|SOS_MEMORY_TOPLEVELBLOCKALLOCATOR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SOS_MEMORY_USAGE_ADJUSTMENT |プール間でメモリ使用量が調整されている場合に発生します。| 
|SOS_OBJECT_STORE_DESTROY_MUTEX |メモリ プールからオブジェクトを破棄するときに、メモリ プール内での内部同期中に発生します。| 
|SOS_PHYS_PAGE_CACHE |物理ページを割り当てる前または物理ページをオペレーティング システムに返す前に取得する必要のあるミューテックスを取得するためにスレッドが待機する時間を示します。 この種類における待機は、SQL Server のインスタンスで AWE メモリを使用する場合にのみ表示されます、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SOS_PROCESS_AFFINITY_MUTEX |関係設定を処理するためのアクセスの同期中に発生します。| 
|SOS_RESERVEDMEMBLOCKLIST |SQL Server のメモリ マネージャーで内部同期中に発生します。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|SOS_SCHEDULER_YIELD |タスクが、他のタスクの実行にスケジューラを自主的に解放したときに発生します。 この待機中、タスクはクォンタムの更新を待機しています。| 
|SOS_SMALL_PAGE_ALLOC |メモリの割り当てと開放中に発生します。このメモリはいくつかのメモリ オブジェクトによって管理されます。| 
|SOS_STACKSTORE_INIT_MUTEX |内部ストアの初期化の同期中に発生します。| 
|SOS_SYNC_TASK_ENQUEUE_EVENT |タスクが同期して開始したときに発生します。 SQL Server のほとんどのタスクをコントロールに戻ります、タスクの要求が作業キューに配置された後すぐに、非同期的に開始されます。| 
|SOS_VIRTUALMEMORY_LOW |メモリ割り当てが、リソース マネージャーによる仮想メモリの解放を待機しているときに発生します。| 
|SOSHOST_EVENT |CLR などのホスト型のコンポーネントは、SQL Server のイベント同期オブジェクトで待機する場合に発生します。| 
|SOSHOST_INTERNAL |CLR などのホストされるコンポーネントで使用される、メモリ マネージャーのコールバックの同期中に発生します。| 
|SOSHOST_MUTEX |CLR などのホスト型のコンポーネントが SQL Server のミュー テックス同期オブジェクトで待機する場合に発生します。| 
|SOSHOST_RWLOCK |CLR などのホスト型のコンポーネントは、SQL Server のリーダー/ライター同期オブジェクトで待機する場合に発生します。| 
|SOSHOST_SEMAPHORE |CLR などのホスト型のコンポーネントは、SQL Server セマフォ同期オブジェクトを待機する場合に発生します。| 
|SOSHOST_SLEEP |ジェネリック イベントの発生を待機している間、ホストされるタスクがスリープ状態のときに発生します。 ホストされるタスクは、CLR などのホストされるコンポーネントで使用されます。| 
|SOSHOST_TRACELOCK |ストリームをトレースするためのアクセスの同期中に発生します。| 
|SOSHOST_WAITFORDONE |CLR などのホストされるコンポーネントが、タスクの完了を待機しているときに発生します。| 
|SP_PREEMPTIVE_SERVER_DIAGNOSTICS_SLEEP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SP_SERVER_DIAGNOSTICS_BUFFER_ACCESS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SP_SERVER_DIAGNOSTICS_INIT_MUTEX |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SP_SERVER_DIAGNOSTICS_SLEEP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SQLCLR_APPDOMAIN |CLR が、アプリケーション ドメインの起動完了を待機しているときに発生します。| 
|SQLCLR_ASSEMBLY |アプリケーション ドメインに読み込まれたアセンブリ一覧へのアクセスを待機しているときに発生します。| 
|SQLCLR_DEADLOCK_DETECTION |CLR がデッドロック検出の完了を待機しているときに発生します。| 
|SQLCLR_QUANTUM_PUNISHMENT |クォンタムの実行時間を超えたことが原因で、CLR タスクがスロットルされたときに発生します。 このスロットルは、こうしたリソース消費の多いタスクによる他のタスクへの影響を軽減するために行われます。| 
|SQLSORT_NORMMUTEX |内部同期中、内部の並べ替え構造が初期化される間に発生します。| 
|SQLSORT_SORTMUTEX |内部同期中、内部の並べ替え構造が初期化される間に発生します。| 
|SQLTRACE_BUFFER_FLUSH |タスクが、バックグラウンド タスクによってトレース バッファーが 4 秒ごとにディスクにフラッシュされるのを待機しているときに発生します。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|SQLTRACE_FILE_BUFFER |ファイル トレース中にトレース バッファーの同期中に発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SQLTRACE_FILE_READ_IO_COMPLETION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SQLTRACE_FILE_WRITE_IO_COMPLETION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SQLTRACE_INCREMENTAL_FLUSH_SLEEP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SQLTRACE_LOCK |内部使用のみです。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|SQLTRACE_PENDING_BUFFER_WRITERS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|SQLTRACE_SHUTDOWN |トレースのシャットダウンが、未処理のトレース イベントが完了するのを待機しているときに発生します。| 
|SQLTRACE_WAIT_ENTRIES |SQL トレース イベント キューが、パケットの到着を待機しているときに発生します。| 
|SRVPROC_SHUTDOWN |シャットダウン プロセスが、正常にシャットダウンするために内部リソースの解放を待機しているときに発生します。| 
|STARTUP_DEPENDENCY_MANAGER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|TDS_BANDWIDTH_STATE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|TDS_INIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|TDS_PROXY_CONTAINER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|TEMPOBJ |一時オブジェクトの削除が同期されるときに発生します。 この待機が発生するのはまれで、タスクが temp テーブルに対して削除操作を行うための排他アクセスを要求した場合にのみ発生します。| 
|TEMPORAL_BACKGROUND_PROCEED_CLEANUP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|TERMINATE_LISTENER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|THREADPOOL |タスクがワーカーの実行を待機しているときに発生します。 ワーカー数の最大設定値が低すぎるか、バッチ実行時間が長すぎるため、他のバッチ用にワーカー数が削減されている可能性があります。| 
|TIMEPRIV_TIMEPERIOD |拡張イベント タイマーの内部初期化中に発生します。| 
|TRACE_EVTNOTIF |内部使用のみです。| 
|TRACEWRITE |SQL トレースの行セット トレース プロバイダーが、空きバッファーまたは処理するイベントを含むバッファーのいずれかを待機しているときに発生します。| 
|TRAN_MARKLATCH_DT |トランザクション マーク ラッチで破棄モードのラッチを待機しているときに発生します。 トランザクション マーク ラッチは、マークされたトランザクションでのコミットの同期に使用されます。| 
|TRAN_MARKLATCH_EX |マークされたトランザクションで排他モードのラッチを待機しているときに発生します。 トランザクション マーク ラッチは、マークされたトランザクションでのコミットの同期に使用されます。| 
|TRAN_MARKLATCH_KP |マークされたトランザクションで保持モードのラッチを待機しているときに発生します。 トランザクション マーク ラッチは、マークされたトランザクションでのコミットの同期に使用されます。| 
|TRAN_MARKLATCH_NL |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|TRAN_MARKLATCH_SH |マークされたトランザクションで共有モードのラッチを待機しているときに発生します。 トランザクション マーク ラッチは、マークされたトランザクションでのコミットの同期に使用されます。| 
|TRAN_MARKLATCH_UP |マークされたトランザクションで更新モードのラッチを待機しているときに発生します。 トランザクション マーク ラッチは、マークされたトランザクションでのコミットの同期に使用されます。| 
|TRANSACTION_MUTEX |複数のバッチによるトランザクションへのアクセスの同期中に発生します。| 
|UCS_ENDPOINT_CHANGE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|UCS_MANAGER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|UCS_MEMORY_NOTIFICATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|UCS_SESSION_REGISTRATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|UCS_TRANSPORT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|UCS_TRANSPORT_STREAM_CHANGE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|UTIL_PAGE_ALLOC |トランザクション ログのスキャンが、メモリに負荷がかかっている間に、使用できるメモリを待機しているときに発生します。| 
|VDI_CLIENT_COMPLETECOMMAND |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|VDI_CLIENT_GETCOMMAND |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|VDI_CLIENT_OPERATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|VDI_CLIENT_OTHER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|VERSIONING_COMMITTING |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|VIA_ACCEPT |起動中に仮想インターフェイス アダプター (VIA) プロバイダー接続が完了すると発生します。| 
|VIEW_DEFINITION_MUTEX |キャッシュされたビュー定義へのアクセスの同期中に発生します。| 
|WAIT_FOR_RESULTS |クエリ通知が行われるのを待機しているときに発生します。| 
|WAIT_ON_SYNC_STATISTICS_REFRESH |同期の統計の更新が完了するまでクエリのコンパイルと実行を再開できるを待機しているときに発生します。<br /> **適用対象**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 以降|
|WAIT_SCRIPTDEPLOYMENT_REQUEST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_SCRIPTDEPLOYMENT_WORKER |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XLOGREAD_SIGNAL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_ASYNC_TX_COMPLETION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_CKPT_AGENT_WAKEUP |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_CKPT_CLOSE |チェックポイントを完了するを待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_CKPT_ENABLED |チェックポイント処理が有効にするを待機している [無効]、チェックポイントを処理するときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_CKPT_STATE_LOCK |チェックポイントの状態の確認を同期するときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_COMPILE_WAIT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] ～ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。| 
|WAIT_XTP_GUEST |データベース メモリ アロケーターは、メモリ不足の通知の受信を停止する必要があるときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_HOST_WAIT |待機がデータベース エンジンによってトリガーされ、ホストによって実装されるときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_OFFLINE_CKPT_BEFORE_REDO |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_OFFLINE_CKPT_LOG_IO |オフライン チェックポイントがログ読み取りの IO が完了するを待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_OFFLINE_CKPT_NEW_LOG |オフライン チェックポイントがスキャンする新しいログ レコードを待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_PROCEDURE_ENTRY |Drop procedure が完了するには、そのプロシージャのすべての現在の実行を待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_RECOVERY |データベースの復旧はメモリ最適化オブジェクトが終了するの復旧を待つときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_SERIAL_RECOVERY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_SWITCH_TO_INACTIVE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_TASK_SHUTDOWN |完了する、インメモリ OLTP のスレッドを待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAIT_XTP_TRAN_DEPENDENCY |トランザクション依存関係を待機しているときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAITFOR |WAITFOR TRANSACT-SQL ステートメントの結果として発生します。 この待機時間は、ステートメントに渡すパラメーターによって決まります。 この待機はユーザーによって開始されるものです。| 
|WAITFOR_PER_QUEUE |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WAITFOR_TASKSHUTDOWN |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|WAITSTAT_MUTEX |sys.dm_os_wait_stats の設定に使用する統計コレクションへのアクセスの同期中に発生します。| 
|WCC |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|WINDOW_AGGREGATES_MULTIPASS |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WINFAB_API_CALL |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WINFAB_REPLICA_BUILD_OPERATION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WINFAB_REPORT_FAULT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|WORKTBL_DROP |作業テーブルの削除が失敗してから、再試行されるまで一時停止しているときに発生します。| 
|WRITE_COMPLETION |書き込み操作が進行中のときに発生します。| 
|WRITELOG |ログ フラッシュの完了を待機しているときに発生します。 ログ フラッシュの原因となる主な操作としては、チェックポイントとトランザクションのコミットがあります。| 
|XACT_OWN_TRANSACTION |トランザクションの所有権取得を待機しているときに発生します。| 
|XACT_RECLAIM_SESSION |セッションの現在の所有者がその所有権を解放するのを待機しているときに発生します。| 
|XACTLOCKINFO |トランザクションのロック一覧へのアクセスの同期中に発生します。 このロック一覧には、トランザクション自体だけでなく、ページ分割時にデッドロック検出やロック移行などの操作からもアクセスが行われます。| 
|XACTWORKSPACE_MUTEX |トランザクションからの参加解除や、トランザクションの参加メンバー間におけるデータベース ロック数の同期中に発生します。| 
|XDB_CONN_DUP_HASH |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XDES_HISTORY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XDES_OUT_OF_ORDER_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XDES_SNAPSHOT |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XDESTSVERMGR |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XE_BUFFERMGR_ALLPROCESSED_EVENT |拡張イベント セッション バッファーがターゲットにフラッシュされたときに発生します。 この待機はバックグラウンド スレッドで発生します。| 
|XE_BUFFERMGR_FREEBUF_EVENT |次のいずれかの条件が該当した場合に発生します。| 
|XE_CALLBACK_LIST |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XE_CX_FILE_READ |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XE_DISPATCHER_CONFIG_SESSION_LIST |非同期ターゲットを使用している拡張イベント セッションが開始されたか、停止された場合に発生します。 このタイプの待機は、次のいずれかを示します。| 
|XE_DISPATCHER_JOIN |拡張イベント セッションに使用されているバックグラウンド スレッドの終了時に発生します。| 
|XE_DISPATCHER_WAIT |拡張イベント セッションに使用されているバックグラウンド スレッドが、イベント バッファーの処理を待っているときに発生します。| 
|XE_FILE_TARGET_TVF |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XE_LIVE_TARGET_TVF |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XE_MODULEMGR_SYNC |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|XE_OLS_LOCK |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。| 
|XE_PACKAGE_LOCK_BACKOFF |単に情報を示すためだけに特定されます。 サポートされていません。 <br /> **適用対象**:[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]のみです。 |  
|XE_SERVICES_EVENTMANUAL |内部使用のみです。| 
|XE_SERVICES_MUTEX |内部使用のみです。| 
|XE_SERVICES_RWLOCK |内部使用のみです。| 
|XE_SESSION_CREATE_SYNC |内部使用のみです。| 
|XE_SESSION_FLUSH |内部使用のみです。| 
|XE_SESSION_SYNC |内部使用のみです。| 
|XE_STM_CREATE |内部使用のみです。| 
|XE_TIMER_EVENT |内部使用のみです。| 
|XE_TIMER_MUTEX |内部使用のみです。| 
|XE_TIMER_TASK_DONE |内部使用のみです。| 
|XIO_CREDENTIAL_MGR_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XIO_CREDENTIAL_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XIO_EDS_MGR_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XIO_EDS_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XIO_IOSTATS_BLOBLIST_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XIO_IOSTATS_FCBLIST_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XIO_LEASE_RENEW_MGR_RWLOCK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTP_HOST_DB_COLLECTION |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTP_HOST_LOG_ACTIVITY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTP_HOST_PARALLEL_RECOVERY |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTP_PREEMPTIVE_TASK |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTP_TRUNCATION_LSN |内部使用のみです。 <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTPPROC_CACHE_ACCESS |すべてのネイティブ コンパイル ストアド プロシージャのキャッシュ オブジェクトへのアクセスの場合に発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
|XTPPROC_PARTITIONED_STACK_CREATE |特定のプロシージャ (する必要があります単一スレッド) ストアド プロシージャのキャッシュ構造 NUMA ノードごとの割り当てをネイティブでコンパイルされたときに発生します、。 <br /> **適用対象**: [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|

  
 次の Xevent は、パーティションに関連する**スイッチ**とオンライン インデックス再構築します。 構文については、次を参照してください。 [ALTER TABLE &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md)と[ALTER INDEX &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)します。  
  
-   lock_request_priority_state  
  
-   process_killed_by_abort_blockers  
  
-   ddl_with_wait_at_low_priority  
  
 ロックの互換性対応表を参照してください。 [sys.dm_tran_locks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)します。  
  
## <a name="see-also"></a>関連項目  
    
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_session_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md)   
 [sys.dm_db_wait_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-wait-stats-azure-sql-database.md)  
  
  


