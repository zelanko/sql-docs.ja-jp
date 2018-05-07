---
title: sys.dm_os_latch_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_latch_stats_TSQL
- dm_os_latch_stats_TSQL
- dm_os_latch_stats
- sys.dm_os_latch_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_latch_stats dynamic management view
ms.assetid: 2085d9fc-828c-453e-82ec-b54ed8347ae5
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94868f568b65e814f389ff45878113db8915d6da
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmoslatchstats-transact-sql"></a>sys.dm_os_latch_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべてのラッチ待機に関する情報を、クラスごとに返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_latch_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|latch_class|**nvarchar(120)**|ラッチ クラスの名前。|  
|waiting_requests_count|**bigint**|クラス内のラッチに対する待機数。 このカウンターは、ラッチ待機の開始時に増加します。|  
|wait_time_ms|**bigint**|クラス内のラッチに対する合計待機時間 (ミリ秒単位)。<br /><br /> **注:** この列はラッチの待機中に、ラッチ待機の最後に、5 分ごとに更新します。|  
|max_wait_time_ms|**bigint**|メモリ オブジェクトがラッチを待機した最大時間。 この値が著しく大きい場合、内部デッドロックを示している可能性があります。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="remarks"></a>解説  
 sys.dm_os_latch_stats を使用すると、別のラッチ クラスの待機数や待機時間を相対的に確認することにより、ラッチの競合の発生源を特定できます。 状況によっては、ラッチの競合を自分で解決または緩和できます。 ただし、ある可能性がありますが必要になるような場合にお問い合わせください[!INCLUDE[msCoName](../../includes/msconame-md.md)]カスタマー サポート サービス。  
  
 次のように `DBCC SQLPERF` を使用すると、sys.dm_os_latch_stats の内容をリセットできます。  
  
```  
DBCC SQLPERF ('sys.dm_os_latch_stats', CLEAR);  
GO  
```  
  
 これは、すべてのカウンターを 0 にリセットします。  
  
> [!NOTE]  
>  これらの統計は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再起動されると保存されません。 すべてのデータが、前回の統計がリセットされた後、または累積的な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]開始されました。  
  
## <a name="latches"></a>ラッチ  
 ラッチとは、さまざまな [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントで使用される軽量の同期オブジェクトです。 ラッチは、主にデータベース ページを同期するために使用されます。 各ラッチは、1 つのアロケーション ユニットに関連付けられています。  
  
 ラッチが別のスレッドによって、競合するモードで保持されており、ラッチ要求がすぐに許可されない場合は、ラッチ待機が発生します。 ロックと異なり、ラッチは操作後すぐに解放されます。書き込み操作の場合でも同様です。  
  
 ラッチは、コンポーネントと使用方法に基づいて複数のクラスに分類されます。 特定クラスのラッチは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内に、任意の時点でいくつでも存在できます。  
  
> [!NOTE]  
>  sys.dm_os_latch_stats は、すぐに許可されたラッチ要求、または待機せずに失敗したラッチ要求を追跡しません。  
  
 次の表では、さまざまなラッチ クラスについて簡単に説明します。  
  
|ラッチ クラス|Description|  
|-----------------|-----------------|  
|ALLOC_CREATE_RINGBUF|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部で使用され、割り当てリング バッファーの作成の同期を初期化します。|  
|ALLOC_CREATE_FREESPACE_CACHE|ヒープ用の内部空き領域キャッシュの同期を初期化するために使用します。|  
|ALLOC_CACHE_MANAGER|内部の一貫性テストを同期するために使用します。|  
|ALLOC_FREESPACE_CACHE|ヒープとバイナリ ラージ オブジェクト (BLOB) で使用できる領域を含む、ページのキャッシュへのアクセスを同期するために使用します。 このクラスのラッチの競合は、複数の接続が行をヒープまたは BLOB に同時に挿入しようとしたときに発生します。 このような競合を少なくするには、オブジェクトをパーティション分割します。 各パーティションには、独自のラッチが含まれます。 パーティション分割により、挿入が複数のラッチに分配されます。|  
|ALLOC_EXTENT_CACHE|割り当てられていないページを含む、エクステントのキャッシュへのアクセスを同期するために使用します。 このクラスのラッチの競合は、複数の接続が、同じアロケーション ユニット内のデータ ページを同時に割り当てようとしたときに発生します。 このような競合を少なくするには、このアロケーション ユニットが属しているオブジェクトをパーティション分割します。|  
|ACCESS_METHODS_DATASET_PARENT|並列操作中、子データセットの親データセットへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT_FACTORY|内部ハッシュ テーブルへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT|HoBt のメモリ内表記へのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT_COUNT|HoBt ページおよび行カウンターへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT_VIRTUAL_ROOT|内部 B-Tree のルート ページの抽象化に対するアクセスを同期するために使用します。|  
|ACCESS_METHODS_CACHE_ONLY_HOBT_ALLOC|作業テーブルへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_BULK_ALLOC|一括アロケーター内のアクセスを同期するために使用します。|  
|ACCESS_METHODS_SCAN_RANGE_GENERATOR|並列スキャン中、範囲ジェネレーターへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_KEY_RANGE_GENERATOR|キー範囲の並列スキャン中、先行読み取り操作へのアクセスを同期するために使用します。|  
|APPEND_ONLY_STORAGE_INSERT_POINT|高速の追加専用ストレージ ユニット内で、挿入を同期するために使用します。|  
|APPEND_ONLY_STORAGE_FIRST_ALLOC|追加専用ストレージ ユニットの最初の割り当てを同期するために使用します。|  
|APPEND_ONLY_STORAGE_UNIT_MANAGER|高速の追加専用ストレージ ユニット マネージャー内で、内部データ構造のアクセスを同期するために使用します。|  
|APPEND_ONLY_STORAGE_MANAGER|高速の追加専用ストレージ ユニット マネージャー内で、圧縮操作を同期するために使用します。|  
|BACKUP_RESULT_SET|並列バックアップ結果セットを同期するために使用します。|  
|BACKUP_TAPE_POOL|バックアップ テープ プールを同期するために使用します。|  
|BACKUP_LOG_REDO|バックアップ ログの再実行操作を同期するために使用します。|  
|BACKUP_INSTANCE_ID|パフォーマンス モニター カウンターをバックアップするインスタンス ID の生成を同期するために使用します。|  
|BACKUP_MANAGER|内部バックアップ マネージャーを同期するために使用します。|  
|BACKUP_MANAGER_DIFFERENTIAL|DBCC を使用した差分バックアップ操作を同期するために使用します。|  
|BACKUP_OPERATION|バックアップ操作で、データベース、ログ、ファイルのバックアップなどの内部データ構造を同期するために使用します。|  
|BACKUP_FILE_HANDLE|復元操作中にファイルを開く操作を同期するために使用します。|  
|BUFFER|データベース ページへの短時間アクセスを同期するために使用します。 いずれのデータベース ページを読み取りまたは修正する場合も、事前にバッファー ラッチが必要です。 バッファー ラッチの競合によって、ホット ページや低速な I/O など、いくつかの問題が発生する場合があります。<br /><br /> このラッチ クラスは、ページ ラッチを使用するすべての状況に対応しています。 sys.dm_os_wait_stats では、I/O 操作および読み取りが発生し、書き込み、ページ上操作ページ ラッチ待機の違いにより、します。|  
|BUFFER_POOL_GROW|バッファー プールの拡張操作中、内部バッファー マネージャーの同期に使用します。|  
|DATABASE_CHECKPOINT|データベース内のチェックポイントをシリアル化するために使用します。|  
|CLR_PROCEDURE_HASHTABLE|内部使用のみです。|  
|CLR_UDX_STORE|内部使用のみです。|  
|CLR_DATAT_ACCESS|内部使用のみです。|  
|CLR_XVAR_PROXY_LIST|内部使用のみです。|  
|DBCC_CHECK_AGGREGATE|内部使用のみです。|  
|DBCC_CHECK_RESULTSET|内部使用のみです。|  
|DBCC_CHECK_TABLE|内部使用のみです。|  
|DBCC_CHECK_TABLE_INIT|内部使用のみです。|  
|DBCC_CHECK_TRACE_LIST|内部使用のみです。|  
|DBCC_FILE_CHECK_OBJECT|内部使用のみです。|  
|DBCC_PERF|内部パフォーマンス モニター カウンターを同期するために使用します。|  
|DBCC_PFS_STATUS|内部使用のみです。|  
|DBCC_OBJECT_METADATA|内部使用のみです。|  
|DBCC_HASH_DLL|内部使用のみです。|  
|EVENTING_CACHE|内部使用のみです。|  
|FCB|ファイル制御ブロックへのアクセスを同期するために使用します。|  
|FCB_REPLICA|内部使用のみです。|  
|FGCB_ALLOC|ファイル グループ内のラウンド ロビン割り当て情報へのアクセスを同期するために使用します。|  
|FGCB_ADD_REMOVE|ADD および DROP ファイル操作を行うファイル グループへのアクセスを同期するために使用します。|  
|FILEGROUP_MANAGER|内部使用のみです。|  
|FILE_MANAGER|内部使用のみです。|  
|FILESTREAM_FCB|内部使用のみです。|  
|FILESTREAM_FILE_MANAGER|内部使用のみです。|  
|FILESTREAM_GHOST_FILES|内部使用のみです。|  
|FILESTREAM_DFS_ROOT|内部使用のみです。|  
|LOG_MANAGER|内部使用のみです。|  
|FULLTEXT_DOCUMENT_ID|内部使用のみです。|  
|FULLTEXT_DOCUMENT_ID_TRANSACTION|内部使用のみです。|  
|FULLTEXT_DOCUMENT_ID_NOTIFY|内部使用のみです。|  
|FULLTEXT_LOGS|内部使用のみです。|  
|FULLTEXT_CRAWL_LOG|内部使用のみです。|  
|FULLTEXT_ADMIN|内部使用のみです。|  
|FULLTEXT_AMDIN_COMMAND_CACHE|内部使用のみです。|  
|FULLTEXT_LANGUAGE_TABLE|内部使用のみです。|  
|FULLTEXT_CRAWL_DM_LIST|内部使用のみです。|  
|FULLTEXT_CRAWL_CATALOG|内部使用のみです。|  
|FULLTEXT_FILE_MANAGER|内部使用のみです。|  
|DATABASE_MIRRORING_REDO|内部使用のみです。|  
|DATABASE_MIRRORING_SERVER|内部使用のみです。|  
|DATABASE_MIRRORING_CONNECTION|内部使用のみです。|  
|DATABASE_MIRRORING_STREAM|内部使用のみです。|  
|QUERY_OPTIMIZER_VD_MANAGER|内部使用のみです。|  
|QUERY_OPTIMIZER_ID_MANAGER|内部使用のみです。|  
|QUERY_OPTIMIZER_VIEW_REP|内部使用のみです。|  
|RECOVERY_BAD_PAGE_TABLE|内部使用のみです。|  
|RECOVERY_MANAGER|内部使用のみです。|  
|SECURITY_OPERATION_RULE_TABLE|内部使用のみです。|  
|SECURITY_OBJPERM_CACHE|内部使用のみです。|  
|SECURITY_CRYPTO|内部使用のみです。|  
|SECURITY_KEY_RING|内部使用のみです。|  
|SECURITY_KEY_LIST|内部使用のみです。|  
|SERVICE_BROKER_CONNECTION_RECEIVE|内部使用のみです。|  
|SERVICE_BROKER_TRANSMISSION|内部使用のみです。|  
|SERVICE_BROKER_TRANSMISSION_UPDATE|内部使用のみです。|  
|SERVICE_BROKER_TRANSMISSION_STATE|内部使用のみです。|  
|SERVICE_BROKER_TRANSMISSION_ERRORS|内部使用のみです。|  
|SSBXmitWork|内部使用のみです。|  
|SERVICE_BROKER_MESSAGE_TRANSMISSION|内部使用のみです。|  
|SERVICE_BROKER_MAP_MANAGER|内部使用のみです。|  
|SERVICE_BROKER_HOST_NAME|内部使用のみです。|  
|SERVICE_BROKER_READ_CACHE|内部使用のみです。|  
|SERVICE_BROKER_WAITFOR_MANAGER| 待機キューのインスタンス レベルのマップを同期するために使用されます。 データベースの ID、データベースのバージョン、およびキューの ID の組ごとに 1 つのキューが存在します。 接続数が、このクラスのラッチ競合が発生する可能性が:、WAITFOR(RECEIVE) で待ち状態です。呼び出し元 WAITFOR(RECEIVE) です。WAITFOR のタイムアウトを超過メッセージの受信コミットまたは WAITFOR(RECEIVE); を含むトランザクションをロールバックしていますWAITFOR(RECEIVE) 待機状態のスレッドの数を減らすことによっての競合を減らすことができます。 |  
|SERVICE_BROKER_WAITFOR_TRANSACTION_DATA|内部使用のみです。|  
|SERVICE_BROKER_TRANSMISSION_TRANSACTION_DATA|内部使用のみです。|  
|SERVICE_BROKER_TRANSPORT|内部使用のみです。|  
|SERVICE_BROKER_MIRROR_ROUTE|内部使用のみです。|  
|TRACE_ID|内部使用のみです。|  
|TRACE_AUDIT_ID|内部使用のみです。|  
|TRACE|内部使用のみです。|  
|TRACE_CONTROLLER|内部使用のみです。|  
|TRACE_EVENT_QUEUE|内部使用のみです。|  
|TRANSACTION_DISTRIBUTED_MARK|内部使用のみです。|  
|TRANSACTION_OUTCOME|内部使用のみです。|  
|NESTING_TRANSACTION_READONLY|内部使用のみです。|  
|NESTING_TRANSACTION_FULL|内部使用のみです。|  
|MSQL_TRANSACTION_MANAGER|内部使用のみです。|  
|DATABASE_AUTONAME_MANAGER|内部使用のみです。|  
|UTILITY_DYNAMIC_VECTOR|内部使用のみです。|  
|UTILITY_SPARSE_BITMAP|内部使用のみです。|  
|UTILITY_DATABASE_DROP|内部使用のみです。|  
|UTILITY_DYNAMIC_MANAGER_VIEW|内部使用のみです。|  
|UTILITY_DEBUG_FILESTREAM|内部使用のみです。|  
|UTILITY_LOCK_INFORMATION|内部使用のみです。|  
|VERSIONING_TRANSACTION|内部使用のみです。|  
|VERSIONING_TRANSACTION_LIST|内部使用のみです。|  
|VERSIONING_TRANSACTION_CHAIN|内部使用のみです。|  
|VERSIONING_STATE|内部使用のみです。|  
|VERSIONING_STATE_CHANGE|内部使用のみです。|  
|KTM_VIRTUAL_CLOCK|内部使用のみです。|  
  
## <a name="see-also"></a>参照  
 
 [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


