---
title: sys.dm_os_workers (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_workers_TSQL
- sys.dm_os_workers_TSQL
- dm_os_workers
- sys.dm_os_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_workers dynamic management view
ms.assetid: 4d5d1e52-a574-4bdd-87ae-b932527235e8
caps.latest.revision: 47
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce7582dc2c432ee0cfaf0dc04d47d59db9d2aff3
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmosworkers-transact-sql"></a>sys.dm_os_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  システム内のワーカーごとに 1 行のデータを返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_workers**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|worker_address|**varbinary(8)**|ワーカーのメモリ アドレス。|  
|ステータス|**int**|内部使用のみです。|  
|is_preemptive|**bit**|1 = ワーカーは、プリエンプティブなスケジュール設定で実行中です。 外部コードを実行中のワーカーは、プリエンプティブなスケジュール設定で実行されます。|  
|is_fiber|**bit**|1 = ワーカーは、簡易プーリングで実行中です。 詳細については、このトピックの「 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)のバックアップと復元で使用する基本的なバックアップ メディア用語を紹介します。|  
|is_sick|**bit**|1 = ワーカーは、スピン ロックを取得しようとして停止しています。 このビットが設定されている場合、頻繁にアクセスされるオブジェクトで競合の問題が発生している可能性があります。|  
|is_in_cc_exception|**bit**|1 = ワーカーは現在処理されてない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]例外。|  
|is_fatal_exception|**bit**|ワーカーが重大な例外を受け取ったかどうかを示します。|  
|is_inside_catch|**bit**|1 = ワーカーは、現在例外を処理中です。|  
|is_in_polling_io_completion_routine|**bit**|1 = ワーカーは、現在保留中の I/O に対して I/O 完了ルーチンを実行中です。 詳細については、次を参照してください。 [sys.dm_io_pending_io_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-pending-io-requests-transact-sql.md)です。|  
|context_switch_count|**int**|ワーカーによって実行された、スケジューラのコンテキスト切り替えの数。|  
|pending_io_count|**int**|ワーカーによって実行された物理 I/O の数。|  
|pending_io_byte_count|**bigint**|ワーカーに対して保留となっているすべての物理 I/O の合計バイト数。|  
|pending_io_byte_average|**int**|ワーカーの物理 I/O の平均バイト数。|  
|wait_started_ms_ticks|**bigint**|特定の時点、 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)ワーカーが SUSPENDED 状態になったときに、します。 この値を ms_ticks から減算[sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)ワーカーが待機している (ミリ秒) の数を返します。|  
|wait_resumed_ms_ticks|**bigint**|特定の時点、 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)ワーカーの状態が RUNNABLE になったときに、します。 この値を ms_ticks から減算[sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)実行可能キューでされている、ミリ秒数を返します。|  
|task_bound_ms_ticks|**bigint**|特定の時点、 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)タスクがワーカーにバインドされている場合、します。|  
|worker_created_ms_ticks|**bigint**|特定の時点、 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)ワーカーが作成されたときに、します。|  
|exception_num|**int**|ワーカーで前回発生した例外のエラー番号。|  
|exception_severity|**int**|ワーカーで前回発生した例外の重大度。|  
|exception_address|**varbinary(8)**|例外をスローしたコード アドレス。|  
|affinity|**bigint**|ワーカーのスレッド関係。 内のスレッドの関係と一致[sys.dm_os_threads &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)です。|  
|state|**nvarchar(60)**|ワーカーの状態。 次の値のいずれかです。<br /><br /> INIT = ワーカーは、現在初期化中です。<br /><br /> RUNNING = ワーカーは、現在非プリエンプティブまたはプリエンプティブのいずれかで実行中です。<br /><br /> RUNNABLE = ワーカーは、スケジューラ上で実行できる状態です。<br /><br /> SUSPENDED = ワーカーは現在中断されています。イベントによるシグナル送信を待機中です。|  
|start_quantum|**bigint**|ワーカーの現在の実行が開始された時間 (ミリ秒単位)。|  
|end_quantum|**bigint**|ワーカーの現在の実行が終了した時間 (ミリ秒単位)。|  
|last_wait_type|**nvarchar(60)**|前回の待機の種類。 待機の種類の一覧は、次を参照してください。 [sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)です。|  
|return_code|**int**|前回の待機からの戻り値。 次の値のいずれかです。<br /><br /> 0 =SUCCESS<br /><br /> 3 = DEADLOCK<br /><br /> 4 = PREMATURE_WAKEUP<br /><br /> 258 = TIMEOUT|  
|quantum_used|**bigint**|内部使用のみです。|  
|max_quantum|**bigint**|内部使用のみです。|  
|boost_count|**int**|内部使用のみです。|  
|tasks_processed_count|**int**|ワーカーが処理したタスクの数。|  
|fiber_address|**varbinary(8)**|ワーカーが関連付けられているファイバーのメモリ アドレス。<br /><br /> NULL = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、簡易プーリング用に構成されていません。|  
|task_address|**varbinary(8)**|現在のタスクのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_tasks と組み合わせます&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)です。|  
|memory_object_address|**varbinary(8)**|ワーカーのメモリ オブジェクトのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_memory_objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)です。|  
|thread_address|**varbinary(8)**|ワーカーに関連付けられているスレッドのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_threads &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)です。|  
|signal_worker_address|**varbinary(8)**|オブジェクトに最後にシグナルを送信したワーカーのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)です。|  
|scheduler_address|**varbinary(8)**|スケジューラのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_schedulers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)です。|  
|processor_group|**smallint**|このスレッドに割り当てられているプロセッサ グループ ID が格納されます。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 ワーカーの状態が RUNNING で、非プリエンプティブに実行されている場合、そのワーカーのアドレスは、sys.dm_os_schedulers 内の active_worker_address と一致します。  
  
 イベントで待機中のワーカーがシグナルを受け取ると、そのワーカーは実行可能キューの先頭に置かれます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でこれが 1,000 回続けて発生すると、ワーカーはキューの末尾に置かれます。 ワーカーがキューの末尾に移動すると、パフォーマンスに影響が生じる場合があります。  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="examples"></a>使用例  
 次のクエリを使用すると、SUSPENDED または RUNNABLE 状態でのワーカーの実行時間を調べることができます。  
  
```sql
SELECT   
    t1.session_id,  
    CONVERT(varchar(10), t1.status) AS status,  
    CONVERT(varchar(15), t1.command) AS command,  
    CONVERT(varchar(10), t2.state) AS worker_state,  
    w_suspended =   
      CASE t2.wait_started_ms_ticks  
        WHEN 0 THEN 0  
        ELSE   
          t3.ms_ticks - t2.wait_started_ms_ticks  
      END,  
    w_runnable =   
      CASE t2.wait_resumed_ms_ticks  
        WHEN 0 THEN 0  
        ELSE   
          t3.ms_ticks - t2.wait_resumed_ms_ticks  
      END  
  FROM sys.dm_exec_requests AS t1  
  INNER JOIN sys.dm_os_workers AS t2  
    ON t2.task_address = t1.task_address  
  CROSS JOIN sys.dm_os_sys_info AS t3  
  WHERE t1.scheduler_id IS NOT NULL;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```
 session_id status     command         worker_state w_suspended w_runnable  
 ---------- ---------- --------------- ------------ ----------- --------------------  
 4          background LAZY WRITER     SUSPENDED    688         688  
 6          background LOCK MONITOR    SUSPENDED    4657        4657
 19         background BRKR TASK       SUSPENDED    603820344   603820344  
 14         background BRKR EVENT HNDL SUSPENDED    63583641    63583641  
 51         running    SELECT          RUNNING      0           0  
 2          background RESOURCE MONITO RUNNING      0           603825954  
 3          background LAZY WRITER     SUSPENDED    422         422  
 7          background SIGNAL HANDLER  SUSPENDED    603820485   603820485  
 13         background TASK MANAGER    SUSPENDED    603824704   603824704  
 18         background BRKR TASK       SUSPENDED    603820407   603820407  
 9          background TRACE QUEUE TAS SUSPENDED    454         454  
 52         suspended  SELECT          SUSPENDED    35094       35094  
 1          background RESOURCE MONITO RUNNING      0           603825954  
```

 出力では、ときに`w_runnable`と`w_suspended`が等しい、これは、ワーカーが SUSPENDED 状態にある時間を表します。 等しくない場合、`w_runnable` は、RUNNABLE 状態でワーカーが費やした時間を示します。 出力では、セッション`52`は`SUSPENDED`の`35,094`(ミリ秒)。  
  
## <a name="see-also"></a>参照  
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


