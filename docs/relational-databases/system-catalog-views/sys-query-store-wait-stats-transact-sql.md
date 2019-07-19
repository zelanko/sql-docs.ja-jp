---
title: sys.query_store_wait_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.query_store_wait_stats
- query_store_wait_stats
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_wait_stats catalog view
- sys.query_store_wait_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 68ceb35ee3ef2cb3db3233c7050380584163c317
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067924"
---
# <a name="sysquerystorewaitstats-transact-sql"></a>sys.query_store_wait_stats (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  クエリの待機情報についてを説明します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**wait_stats_id**|**bigint**|Plan_id、runtime_stats_interval_id、execution_type および wait_category の待機の統計情報を表す行の識別子です。 過去の実行時統計の間隔でののみ一意です。 現在アクティブな間隔で execution_type wait_category によって表される待機のカテゴリで表された実行の種類の plan_id、によって参照されるプランの待機の統計情報を表す複数の行があります。 通常、1 つの行を表しますがフラッシュ待機の統計をディスクに、その他 (s) がメモリ内状態を表します。 そのため、間隔の実際の状態を取得する必要があります集計メトリックは、plan_id、runtime_stats_interval_id、execution_type および wait_category でグループ化します。 |  
|**plan_id**|**bigint**|外部キーです。 結合[sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)します。|  
|**runtime_stats_interval_id**|**bigint**|外部キーです。 結合[sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)します。|  
|**wait_category**|**tinyint**|待機の種類は、次の表を使用して、分類されにわたって待機時間を集計し、これらの待機のカテゴリ。 待機カテゴリによって異なりますが、問題を解決するが、同じカテゴリの潜在顧客から同様のトラブルシューティング エクスペリエンスへの型を待機する場合は、さまざまなフォロー アップ分析を必要とし、不足している部分を完了するには、待機にさらに、影響を受けるクエリを提供する、このような調査の大半が正常にします。|
|**wait_category_desc**|**nvarchar(128)**|待機のカテゴリ フィールドの説明テキストは、次の表を参照してください。|
|**execution_type**|**tinyint**|クエリの実行の種類を決定します。<br /><br /> 0 - 通常の実行 (が正常に完了)<br /><br /> 3-クライアントによる実行を中止<br /><br /> 4-例外は、実行を中止します。|  
|**execution_type_desc**|**nvarchar(128)**|実行の種類フィールドの説明テキスト。<br /><br /> 0 - 標準<br /><br /> 3-中止<br /><br /> 4-例外|  
|**total_query_wait_time_ms**|**bigint**|合計`CPU wait`集計間隔内でクエリ プランの時間し、待機のカテゴリ (ミリ秒単位で報告されます)。|
|**avg_query_wait_time_ms**|**float**|平均の待機時間 (ミリ秒単位で報告されます)、集計間隔と待機カテゴリ内の実行ごとのクエリ プラン。|
|**last_query_wait_time_ms**|**bigint**|最後に、集計間隔内でクエリ プランの待機時間と待機のカテゴリ (ミリ秒単位で報告されます)。|
|**min_query_wait_time_ms**|**bigint**|最小`CPU wait`集計間隔内でクエリ プランの時間し、待機のカテゴリ (ミリ秒単位で報告されます)。|
|**max_query_wait_time_ms**|**bigint**|最大`CPU wait`集計間隔内でクエリ プランの時間し、待機のカテゴリ (ミリ秒単位で報告されます)。|
|**stdev_query_wait_time_ms**|**float**|`Query wait` クエリの実行時間の標準偏差では、集計間隔に含まれる計画し、待機のカテゴリ (ミリ秒単位で報告されます)。|

## <a name="wait-categories-mapping-table"></a>待機カテゴリのマッピング テーブル

「%」をワイルドカードとして使用します。
  
|整数値|待機のカテゴリ|待機の種類は、カテゴリに含める|  
|-----------------|---------------|-----------------|  
|**0**|**Unknown**|Unknown |  
|**1**|**CPU**|SOS_SCHEDULER_YIELD|
|**2**|**ワーカー スレッド**|THREADPOOL|
|**3**|**ロック**|LCK_M_%|
|**4**|**ラッチ**|LATCH_ %|
|**5**|**バッファー ラッチ**|PAGELATCH_ %|
|**6**|**バッファー IO**|PAGEIOLATCH_%|
|**7**|**コンパイル***|RESOURCE_SEMAPHORE_QUERY_COMPILE|
|**8**|**SQL CLR**|CLR %、SQLCLR %|
|**9**|**ミラーリング**|DBMIRROR %|
|"**10**"|**トランザクション**|XACT %、DTC %、TRAN_MARKLATCH_ %、MSQL_XACT_ %、TRANSACTION_MUTEX|
|**11**|**アイドル状態します。**|SLEEP_ %、LAZYWRITER_SLEEP、SQLTRACE_BUFFER_FLUSH、SQLTRACE_INCREMENTAL_FLUSH_SLEEP、SQLTRACE_WAIT_ENTRIES、FT_IFTS_SCHEDULER_IDLE_WAIT、XE_DISPATCHER_WAIT、REQUEST_FOR_DEADLOCK_SEARCH、LOGMGR_QUEUE、ONDEMAND_TASK_QUEUE、CHECKPOINT_キュー、XE_TIMER_EVENT|
|**12**|**Preemptive**|PREEMPTIVE_ %|
|**13**|**Service Broker**|BROKER_ % **(ただし BROKER_RECEIVE_WAITFOR されません)**|
|**14**|**トランザクション ログ IO**|LOGMGR、LOGBUFFER、LOGMGR_RESERVE_APPEND、LOGMGR_FLUSH、LOGMGR_PMM_LOG、CHKPT、ログへの書き込み|
|**15**|**ネットワーク IO**|ASYNC_NETWORK_IO、NET_WAITFOR_PACKET、PROXY_NETWORK_IO、EXTERNAL_SCRIPT_NETWORK_IOF|
|**16**|**Parallelism**|CXPACKET、EXCHANGE|
|**17**|**[メモリ]**|RESOURCE_SEMAPHORE、CMEMTHREAD、CMEMPARTITIONED、EE_PMOLOCK、MEMORY_ALLOCATION_EXT、RESERVED_MEMORY_ALLOCATION_EXT、MEMORY_GRANT_UPDATE|
|**18**|**ユーザーの待機**|WAITFOR、WAIT_FOR_RESULTS、BROKER_RECEIVE_WAITFOR|
|**19**|**トレース**|TRACEWRITE、SQLTRACE_LOCK、SQLTRACE_FILE_BUFFER、SQLTRACE_FILE_WRITE_IO_COMPLETION、SQLTRACE_FILE_READ_IO_COMPLETION、SQLTRACE_PENDING_BUFFER_WRITERS、SQLTRACE_SHUTDOWN、QUERY_TRACEOUT、TRACE_EVTNOTIFF|
|**20**|**フル テキスト検索**|FT_RESTART_CRAWL、フルテキストの GATHERER、MSSEARCH、FT_METADATA_MUTEX、FT_IFTSHC_MUTEX、FT_IFTSISM_MUTEX、FT_IFTS_RWLOCK、FT_COMPROWSET_RWLOCK、FT_MASTER_MERGE、FT_PROPERTYLIST_CACHE、FT_MASTER_MERGE_COORDINATOR、PWAIT_RESOURCE_SEMAPHORE_FT_PARALLEL_QUERY_SYNC|
|**21**|**その他のディスク IO**|ASYNC_IO_COMPLETION、IO_COMPLETION、BACKUPIO、WRITE_COMPLETION、IO_QUEUE_LIMIT、IO_RETRY|
|**22**|**レプリケーション**|SE_REPL_ %、REPL_ %、HADR_ % **(がない HADR_THROTTLE_LOG_RATE_GOVERNOR)** PWAIT_HADR_ %、REPLICA_WRITES、FCB_REPLICA_WRITE、FCB_REPLICA_READ、PWAIT_HADRSIM|
|**23**|**レート ガバナーについてログ**|LOG_RATE_GOVERNOR、POOL_LOG_RATE_GOVERNOR、HADR_THROTTLE_LOG_RATE_GOVERNOR、INSTANCE_LOG_RATE_GOVERNOR|

**コンパイル**待機のカテゴリが現在サポートされていません。

## <a name="permissions"></a>アクセス許可

 `VIEW DATABASE STATE` アクセス許可が必要です。  
  
## <a name="see-also"></a>関連項目

- [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)
- [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)
- [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)
- [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)
- [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)
- [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)
- [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)
- [クエリ ストアのストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
