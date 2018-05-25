---
title: sys.dm_exec_requests (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_requests_TSQL
- sys.dm_exec_requests
- dm_exec_requests_TSQL
- dm_exec_requests
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_requests dynamic management view
ms.assetid: 4161dc57-f3e7-4492-8972-8cfb77b29643
caps.latest.revision: 67
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1b8e51c1078ebe9b1fd2784a14e8c8e1575eae27
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexecrequests-transact-sql"></a>sys.dm_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で実行中の各要求に関する情報を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部のコード (拡張ストアド プロシージャや分散クエリなど) を実行するには、スレッドを非プリエンプティブ スケジューラの制御外で実行する必要があります。 このとき、ワーカーはプリエンプティブ モードに切り替えられます。 この動的管理ビューによって返される時間の値には、プリエンプティブ モードで費やされた時間は含まれません。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|要求が関係しているセッションの ID。 NULL 値は許可されません。|  
|request_id|**int**|要求の ID。 セッションのコンテキスト内で一意です。 NULL 値は許可されません。|  
|start_time|**datetime**|要求到着時のタイムスタンプ。 NULL 値は許可されません。|  
|ステータス|**nvarchar(30)**|要求の状態です。 これは、次のいずれかを指定できます。<br /><br /> 背景情報<br />実行中<br />実行可能<br />休止中<br />中断<br /><br /> NULL 値は許可されません。|  
|command|**nvarchar(32)**|現在処理中のコマンドの種類。 一般的なコマンドの種類には次のものがあります。<br /><br /> SELECT<br />INSERT<br />UPDATE<br />DELETE<br />BACKUP LOG<br />BACKUP DATABASE<br />DBCC<br />FOR<br /><br /> 要求のテキストを取得するには、対応する sql_handle と共に、要求に対して sys.dm_exec_sql_text を使用します。 内部のシステム処理では、実行するタスクの種類に基づいてコマンドが設定されます。 このタスクには次のものがあります。<br /><br /> LOCK MONITOR<br />CHECKPOINTLAZY<br />WRITER<br /><br /> NULL 値は許可されません。|  
|sql_handle|**varbinary(64)**|要求の SQL テキストのハッシュ マップ。 NULL 値が許可されます。|  
|statement_start_offset|**int**|現在実行中のバッチまたはストアド プロシージャに含まれる、現在実行中のステートメントが開始されるまでの文字数。 sql_handle、statement_end_offset、sys.dm_exec_sql_text 動的管理関数と共に使用して、要求に対して現在実行中のステートメントを取得できます。 NULL 値が許可されます。|  
|statement_end_offset|**int**|現在実行中のバッチまたはストアド プロシージャに含まれる、現在実行中のステートメントが終了するまでの文字数。 sql_handle、statement_end_offset、sys.dm_exec_sql_text 動的管理関数と共に使用して、要求に対して現在実行中のステートメントを取得できます。 NULL 値が許可されます。|  
|plan_handle|**varbinary(64)**|SQL 実行プランのハッシュ マップ。 NULL 値が許可されます。|  
|database_id|**smallint**|要求の実行対象データベースの ID。 NULL 値は許可されません。|  
|user_id|**int**|要求を送信したユーザーの ID。 NULL 値は許可されません。|  
|connection_id|**uniqueidentifier**|要求を受信した接続の ID。 NULL 値が許可されます。|  
|blocking_session_id|**smallint**|要求をブロックしているセッションの ID。 この列が NULL の場合は、要求がブロックされていないか、ブロックしているセッションのセッション情報が使用または識別できません。<br /><br /> -2 = ブロックしているリソースは、孤立した分散トランザクションが所有しています。<br /><br /> -3 = ブロックしているリソースは、遅延復旧トランザクションが所有しています。<br /><br /> -4 = 内部ラッチの状態遷移のため、ブロックしているラッチの所有者のセッション ID を現時点では特定できませんでした。|  
|wait_type|**nvarchar(60)**|要求が現在ブロックされている場合の待機の種類。 NULL 値が許可されます。<br /><br /> 待機の種類については、次を参照してください。 [sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)です。|  
|wait_time|**int**|要求が現在ブロックされている場合の現時点での待機時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|last_wait_type|**nvarchar(60)**|要求がブロックされていた場合の最後の待機の種類。 NULL 値は許可されません。|  
|wait_resource|**nvarchar (256)**|要求が現在ブロックされている場合の現在待機中のリソース。 NULL 値は許可されません。|  
|open_transaction_count|**int**|要求に対して開いているトランザクションの数。 NULL 値は許可されません。|  
|open_resultset_count|**int**|要求に対して開いている結果セットの数。 NULL 値は許可されません。|  
|transaction_id|**bigint**|要求が実行されるトランザクションの ID。 NULL 値は許可されません。|  
|context_info|**varbinary (128)**|セッションの CONTEXT_INFO 値。 NULL 値が許可されます。|  
|percent_complete|**real**|次のコマンドで完了した作業の割合。<br /><br /> ALTER INDEX REORGANIZE<br />ALTER DATABASE の AUTO_SHRINK オプション<br />BACKUP DATABASE<br />DBCC CHECKDB<br />DBCC CHECKFILEGROUP<br />DBCC CHECKTABLE<br />DBCC INDEXDEFRAG<br />DBCC SHRINKDATABASE<br />DBCC SHRINKFILE<br />RECOVERY<br />RESTORE DATABASE<br />ROLLBACK<br />TDE ENCRYPTION<br /><br /> NULL 値は許可されません。|  
|estimated_completion_time|**bigint**|内部のみ。 NULL 値は許可されません。|  
|cpu_time|**int**|要求で使用される CPU 時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|total_elapsed_time|**int**|要求を受信してから経過した総時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|scheduler_id|**int**|この要求のスケジュールを設定しているスケジューラの ID。 NULL 値は許可されません。|  
|task_address|**varbinary(8)**|要求に関連付けられたタスクに割り当てられるメモリ アドレス。 NULL 値が許可されます。|  
|reads|**bigint**|要求で実行された読み取りの数。 NULL 値は許可されません。|  
|writes|**bigint**|要求で実行された書き込みの数。 NULL 値は許可されません。|  
|logical_reads|**bigint**|要求で実行された論理読み取りの数。 NULL 値は許可されません。|  
|text_size|**int**|要求の TEXTSIZE 設定。 NULL 値は許可されません。|  
|language|**nvarchar(128)**|要求の言語設定。 NULL 値が許可されます。|  
|date_format|**nvarchar(3)**|要求の DATEFORMAT 設定。 NULL 値が許可されます。|  
|date_first|**smallint**|要求の DATEFIRST 設定。 NULL 値は許可されません。|  
|quoted_identifier|**bit**|1 = 要求に対して QUOTED_IDENTIFIER が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|arithabort|**bit**|1 = 要求に対して ARITHABORT 設定が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|ansi_null_dflt_on|**bit**|1 = 要求に対して ANSI_NULL_DFLT_ON 設定が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|ansi_defaults|**bit**|1 = 要求に対して ANSI_DEFAULTS 設定が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|ansi_warnings|**bit**|1 = 要求に対して ANSI_WARNINGS 設定が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|ansi_padding|**bit**|1 = 要求に対して ANSI_PADDING 設定が ON です。<br /><br /> それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|ansi_nulls|**bit**|1 = 要求に対して ANSI_NULLS 設定が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|concat_null_yields_null|**bit**|1 = 要求に対して CONCAT_NULL_YIELDS_NULL 設定が ON です。 それ以外の場合は 0 になります。<br /><br /> NULL 値は許可されません。|  
|transaction_isolation_level|**smallint**|この要求に対するトランザクションの作成に使用された分離レベル。 NULL 値は許可されません。<br /><br /> 0 = Unspecified<br /><br /> 1 = ReadUncomitted<br /><br /> 2 = ReadCommitted<br /><br /> 3 = Repeatable<br /><br /> 4 = Serializable<br /><br /> 5 = Snapshot|  
|lock_timeout|**int**|要求のロック タイムアウトまでの時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|deadlock_priority|**int**|要求の DEADLOCK_PRIORITY 設定。 NULL 値は許可されません。|  
|row_count|**bigint**|要求によってクライアントに返された行数。 NULL 値は許可されません。|  
|prev_error|**int**|要求の実行中に発生した最後のエラー。 NULL 値は許可されません。|  
|nest_level|**int**|要求で実行されているコードの現在の入れ子レベル。 NULL 値は許可されません。|  
|granted_query_memory|**int**|要求でのクエリの実行に割り当てられたページ数。 NULL 値は許可されません。|  
|executing_managed_code|**bit**|特定の要求で、ルーチン、データ型、トリガーなどの共通言語ランタイム オブジェクトが現在実行されているかどうかを示します。 共通言語ランタイム オブジェクトが共通言語ランタイム内から [!INCLUDE[tsql](../../includes/tsql-md.md)] を実行した場合でも、共通言語ランタイム オブジェクトがスタックにある間は、このパラメーターが必ず設定されます。 NULL 値は許可されません。|  
|group_id|**int**|このクエリが属しているワークロード グループの ID。 NULL 値は許可されません。|  
|query_hash|**binary(8)**|クエリで計算され、同様のロジックを持つクエリを識別するために使用される、バイナリのハッシュ値です。 クエリ ハッシュを使用して、リテラル値だけが異なるクエリの全体的なリソース使用率を決定できます。|  
|query_plan_hash|**binary(8)**|クエリ実行プランで計算され、同様のクエリ実行プランを識別するために使用される、バイナリのハッシュ値です。 クエリ プラン ハッシュを使用して、同様の実行プランを持つクエリの累積コストを確認できます。|  
|statement_sql_handle|**varbinary(64)**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 個別のクエリの SQL ハンドル。 |  
|statement_context_id|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> Sys.query_context_settings への省略可能な外部キーです。 |  
|dop |**int** |**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> クエリの並列処理の次数。 |  
|parallel_worker_count |**int** |**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> これが、並列クエリの場合の予約済みの並列ワーカーの数。  |  
|external_script_request_id |**uniqueidentifier** |**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 現在の要求に関連付けられている外部スクリプトの要求 ID。 |  
|is_resumable |**bit** |**適用対象**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 要求が再開可能なインデックス操作であるかどうかを示します。 |  
  
## <a name="permissions"></a>権限  
 場合、ユーザーは`VIEW SERVER STATE`サーバーに対する権限をユーザーに表示されるセッションの実行中のすべてのインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 それ以外の場合、ユーザーが現在のセッションのみを表示します。 `VIEW SERVER STATE` 付与することはできません[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]ように`sys.dm_exec_requests`は常に現在の接続に限定されます。 
  
## <a name="examples"></a>使用例  
  
### <a name="a-finding-the-query-text-for-a-running-batch"></a>A. 実行中のバッチのクエリ テキストを探す  
 次の例では、`sys.dm_exec_requests` をクエリして目的のクエリを検索し、その `sql_handle` を出力結果からコピーします。  
  
```  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 次に、ステートメントのテキストを取得するを使用して、先ほどコピーした`sql_handle`をシステム関数`sys.dm_exec_sql_text(sql_handle)`です。  
  
```  
SELECT * FROM sys.dm_exec_sql_text(< copied sql_handle >);  
GO  
```  
  
### <a name="b-finding-all-locks-that-a-running-batch-is-holding"></a>B. 実行中のバッチが保持しているすべてのロックを検索する  
 次の例のクエリ**sys.dm_exec_requests**興味深いバッチとコピーを検索するその`transaction_id`出力からします。  
  
```  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 次に、ロックの情報を検索するを使用して、先ほどコピーした`transaction_id`をシステム関数**sys.dm_tran_locks**です。  
  
```  
SELECT * FROM sys.dm_tran_locks   
WHERE request_owner_type = N'TRANSACTION'   
    AND request_owner_id = < copied transaction_id >;  
GO  
```  
  
### <a name="c-finding-all-currently-blocked-requests"></a>C. 現在ブロックされているすべての要求を検索する  
 次の例のクエリ**sys.dm_exec_requests**ブロックされた要求に関する情報を検索します。  
  
```  
SELECT session_id ,status ,blocking_session_id  
    ,wait_type ,wait_time ,wait_resource   
    ,transaction_id   
FROM sys.dm_exec_requests   
WHERE status = N'suspended';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)   
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)   
 [sys.dm_exec_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)  
