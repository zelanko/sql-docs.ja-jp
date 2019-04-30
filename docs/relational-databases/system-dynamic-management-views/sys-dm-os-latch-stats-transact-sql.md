---
title: sys.dm_os_latch_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eb61a77aca509393143d4abae98af0a9efb5e888
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63048046"
---
# <a name="sysdmoslatchstats-transact-sql"></a>sys.dm_os_latch_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  クラス別に整理されたすべてのラッチ待機に関する情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_latch_stats**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|latch_class|**nvarchar(120)**|ラッチ クラスの名前。|  
|waiting_requests_count|**bigint**|このクラス内のラッチに対する待機の数。 このカウンターは、ラッチ待機の先頭にインクリメントされます。|  
|wait_time_ms|**bigint**|クラス内のラッチに対する合計待機時間 (ミリ秒単位)。<br /><br /> **注:** この列は、ラッチの待機中に、ラッチ待機の最後に、5 分ごとに更新されます。|  
|max_wait_time_ms|**bigint**|メモリ オブジェクトがラッチを待機した最大時間。 この値が著しく大きい場合、内部デッドロックを示している可能性があります。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
  
## <a name="remarks"></a>コメント  
 sys.dm_os_latch_stats を使用すると、別のラッチ クラスの待機数や待機時間を相対的に確認することにより、ラッチの競合の発生源を特定できます。 いくつかの状況では、解決またはラッチの競合を緩和することができます。 ただし、状況もあります。 が必要になることにお問い合わせください[!INCLUDE[msCoName](../../includes/msconame-md.md)]カスタマー サポート サービス。  
  
 次のように `DBCC SQLPERF` を使用すると、sys.dm_os_latch_stats の内容をリセットできます。  
  
```  
DBCC SQLPERF ('sys.dm_os_latch_stats', CLEAR);  
GO  
```  
  
 これにより、すべてのカウンターが 0 にリセットされます。  
  
> [!NOTE]  
>  これらの統計は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再起動されると保存されません。 すべてのデータが、前回の統計がリセットされた後、または累積的な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]開始されました。  
  
## <a name="latches"></a>ラッチ  
 ラッチとは、さまざまな [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントで使用される軽量の同期オブジェクトです。 ラッチは、データベース ページを同期する主に使用します。 各ラッチは、1 つのアロケーション ユニットに関連付けられています。  
  
 ラッチが別のスレッドによって、競合するモードで保持されており、ラッチ要求がすぐに許可されない場合は、ラッチ待機が発生します。 ロックとは異なり、ラッチは、書き込み操作であっても、操作の直後にリリースされます。  
  
 ラッチは、コンポーネントと使用状況に基づいたクラスにグループ化されます。 特定クラスのラッチは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内に、任意の時点でいくつでも存在できます。  
  
> [!NOTE]  
>  sys.dm_os_latch_stats は、すぐに許可されたラッチ要求、または待機せずに失敗したラッチ要求を追跡しません。  
  
 次の表には、さまざまなラッチ クラスの簡単な説明が含まれています。  
  
|ラッチ クラス|説明|  
|-----------------|-----------------|  
|ALLOC_CREATE_RINGBUF|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部で使用され、割り当てリング バッファーの作成の同期を初期化します。|  
|ALLOC_CREATE_FREESPACE_CACHE|ヒープの空き領域の内部キャッシュの同期を初期化するために使用します。|  
|ALLOC_CACHE_MANAGER|内部の一貫性テストを同期するために使用します。|  
|ALLOC_FREESPACE_CACHE|ヒープの空き領域と、ページのキャッシュへのアクセスを同期するために使用し、バイナリ ラージ オブジェクト (Blob)。 複数の接続が同時に、ヒープまたは BLOB に行を挿入しようとした場合、このクラスのラッチの競合が発生します。 このような競合を少なくするには、オブジェクトをパーティション分割します。 各パーティションは、独自のラッチを持っています。 パーティション分割すると、複数のラッチの挿入は配布します。|  
|ALLOC_EXTENT_CACHE|割り当てられていないページを含むエクステントのキャッシュへのアクセスを同期するために使用します。 このクラスのラッチの競合は、複数の接続を同時に、同じアロケーション ユニット内のデータ ページを割り当てるときに発生することができます。 このような競合は、このアロケーション ユニットが一部であるオブジェクトをパーティション分割で短縮できます。|  
|ACCESS_METHODS_DATASET_PARENT|並列操作中に親データセットへのアクセスをデータセットを同期するために使用します。|  
|ACCESS_METHODS_HOBT_FACTORY|内部ハッシュ テーブルへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT|HoBt のメモリ内表現へのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT_COUNT|HoBt ページおよび行カウンターへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_HOBT_VIRTUAL_ROOT|内部の B ツリーのルート ページの抽象化へのアクセスを同期するために使用します。|  
|ACCESS_METHODS_CACHE_ONLY_HOBT_ALLOC|作業テーブルへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_BULK_ALLOC|一括アロケーター内のアクセスを同期するために使用します。|  
|ACCESS_METHODS_SCAN_RANGE_GENERATOR|並列スキャン中、範囲ジェネレーターへのアクセスを同期するために使用します。|  
|ACCESS_METHODS_KEY_RANGE_GENERATOR|キー範囲の並列スキャン中、先行読み取り操作へのアクセスを同期するために使用します。|  
|APPEND_ONLY_STORAGE_INSERT_POINT|高速の追加専用ストレージ ユニットの挿入を同期するために使用します。|  
|APPEND_ONLY_STORAGE_FIRST_ALLOC|追加専用ストレージ ユニットの最初の割り当てを同期するために使用します。|  
|APPEND_ONLY_STORAGE_UNIT_MANAGER|高速追加専用ストレージ ユニット マネージャー内の内部データ構造へのアクセスの同期に使用されます。|  
|APPEND_ONLY_STORAGE_MANAGER|高速追加専用ストレージ ユニット マネージャーで圧縮操作を同期するために使用します。|  
|BACKUP_RESULT_SET|並列バックアップ結果セットを同期するために使用します。|  
|BACKUP_TAPE_POOL|バックアップ テープ プールを同期するために使用します。|  
|BACKUP_LOG_REDO|バックアップ ログのやり直し操作を同期するために使用します。|  
|BACKUP_INSTANCE_ID|バックアップのパフォーマンス モニター カウンターのインスタンス Id の生成を同期するために使用します。|  
|BACKUP_MANAGER|内部バックアップ マネージャーを同期するために使用します。|  
|BACKUP_MANAGER_DIFFERENTIAL|DBCC と差分バックアップ操作を同期するために使用します。|  
|BACKUP_OPERATION|バックアップ操作で、データベース、ログ、またはファイルのバックアップなどの内部データ構造の同期に使用されます。|  
|BACKUP_FILE_HANDLE|復元操作中にファイルを開く操作を同期するために使用します。|  
|バッファー|データベース ページへの短期的なアクセスを同期するために使用します。 読み取りや任意のデータベース ページを変更する前に、バッファー ラッチが必要です。 バッファー ラッチの競合では、ホット ページなど、いくつかの問題を示すでき、I/o が低下することができます。<br /><br /> このラッチ クラスは、ページ ラッチを使用するすべての状況に対応しています。 sys.dm_os_wait_stats は、ページ ラッチ待機は、I/O 操作および読み取りによって発生し、ページに対する書き込み操作間の差です。|  
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
|FGCB_ADD_REMOVE|追加のファイル グループへのアクセスを同期、削除、拡張、および圧縮ファイルの操作を使用します。|  
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
|SERVICE_BROKER_WAITFOR_MANAGER| 待機キューのインスタンス レベルのマップを同期するために使用します。 データベースの ID、データベースのバージョン、およびキューの ID の組ごとに 1 つのキューが存在します。 このクラスのラッチの競合は、多くの接続が場合に発生します。WAITFOR(RECEIVE) で待ち状態です。呼び出し元 WAITFOR(RECEIVE);WAITFOR タイムアウト。メッセージの受信コミットまたは WAITFOR(RECEIVE); を含むトランザクションをロールバックします。WAITFOR(RECEIVE) 待機状態のスレッドの数を減らすことでの競合を減らすことができます。 |  
|SERVICE_BROKER_WAITFOR_TRANSACTION_DATA|内部使用のみです。|  
|SERVICE_BROKER_TRANSMISSION_TRANSACTION_DATA|内部使用のみです。|  
|SERVICE_BROKER_TRANSPORT|内部使用のみです。|  
|SERVICE_BROKER_MIRROR_ROUTE|内部使用のみです。|  
|TRACE_ID|内部使用のみです。|  
|TRACE_AUDIT_ID|内部使用のみです。|  
|trace|内部使用のみです。|  
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
  
  


