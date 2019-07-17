---
title: sys.dm_resource_governor_workload_groups (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups
- sys.dm_resource_governor_workload_groups_TSQL
- dm_resource_governor_workload_groups
- dm_resource_governor_workload_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_workload_groups dynamic management view
ms.assetid: f63c4914-1272-43ef-b135-fe1aabd953e0
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: df55c4e17640710b5ada50a0aa12edb046822821
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053237"
---
# <a name="sysdmresourcegovernorworkloadgroups-transact-sql"></a>sys.dm_resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ワークロード グループ統計とワークロード グループの現在のメモリ内の構成を返します。 このビューを sys.dm_resource_governor_resource_pools と結合すると、リソース プール名を取得できます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_resource_governor_workload_groups**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ワークロード グループの ID。 NULL 値は許可されません。|  
|NAME|**sysname**|ワークロード グループの名前。 NULL 値は許可されません。|  
|pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|external_pool_id|**int**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 外部リソース プールの ID。 NULL 値は許可されません。|  
|statistics_start_time|**datetime**|ワークロード グループの統計コレクションがリセットされた時刻。 NULL 値は許可されません。|  
|total_request_count|**bigint**|ワークロード グループで完了した要求の累積数。 NULL 値は許可されません。|  
|total_queued_request_count|**bigint**|要求の累積数は、GROUP_MAX_REQUESTS 制限に達した後にキューに登録します。 NULL 値は許可されません。|  
|active_request_count|**int**|現在の要求数。 NULL 値は許可されません。|  
|queued_request_count|**int**|現在のキューに置かれた要求の数。 NULL 値は許可されません。|  
|total_cpu_limit_violation_count|**bigint**|CPU 制限を超過した要求の累積数。 NULL 値は許可されません。|  
|total_cpu_usage_ms|**bigint**|累積 CPU 使用率、このワークロード グループで、(ミリ秒)。 NULL 値は許可されません。|  
|max_request_cpu_time_ms|**bigint**|最大 CPU 使用率、1 つの要求 (ミリ秒)。 NULL 値は許可されません。<br /><br /> **注:** これは、構成可能な設定は、request_max_cpu_time_sec とは異なり、測定値です。 詳細については、「[CPU Threshold Exceeded イベント クラス](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)」を参照してください。|  
|blocked_task_count|**int**|現在ブロックされているタスクの数。 NULL 値は許可されません。|  
|total_lock_wait_count|**bigint**|発生したロック待機の累積数。 NULL 値は許可されません。|  
|total_lock_wait_time_ms|**bigint**|累積合計経過時間 (ミリ秒単位) のロックが保持されます。 NULL 値は許可されません。|  
|total_query_optimization_count|**bigint**|このワークロード グループ内のクエリ最適化の累積数。 NULL 値は許可されません。|  
|total_suboptimal_plan_generation_count|**bigint**|メモリ不足のためには、このワークロード グループで発生した最適なプラン生成結果の累積数。 NULL 値は許可されません。|  
|total_reduced_memgrant_count|**bigint**|クエリの最大サイズ制限に達したメモリ許可の累積数。 NULL 値は許可されません。|  
|max_request_grant_memory_kb|**bigint**|統計のリセット以降、1 つの要求に対する最大メモリ許可サイズ (KB 単位)。 NULL 値は許可されません。|  
|active_parallel_thread_count|**bigint**|並列スレッド使用状況の現在の数。 NULL 値は許可されません。|  
|importance|**sysname**|このワークロード グループ内の要求の相対的な重要度の現在の構成値。 重要度では、Medium が既定値を使用して、次の 1 つです。Low、Medium、または High。<br /><br /> NULL 値は許可されません。|  
|request_max_memory_grant_percent|**int**|1 つの要求の割合として、最大メモリ許可の現在の設定。 NULL 値は許可されません。|  
|request_max_cpu_time_sec|**int**|1 つの要求に対する最大 CPU 使用制限の現在の設定 (秒単位)。 NULL 値は許可されません。|  
|request_memory_grant_timeout_sec|**int**|メモリの現在の設定は、秒、1 つの要求で、タイムアウトを付与します。 NULL 値は許可されません。|  
|group_max_requests|**int**|最大同時要求数の現在の設定。 NULL 値は許可されません。|  
|max_dop|**int**|ワークロード グループの並列処理の最大限度。 既定値は 0 で、グローバル設定が使用されます。 NULL 値は許可されません。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="remarks"></a>コメント  
 この動的管理ビューは、メモリ内の構成を示しています。 格納されている構成メタデータを表示するには、sys.resource_governor_workload_groups カタログ ビューを使用します。  
  
 ALTER RESOURCE GOVERNOR RESET STATISTICS が正常に実行されると、次のカウンターがリセットされます statistics_start_time、total_request_count、total_queued_request_count、total_cpu_limit_violation_count、total_cpu_usage_ms、max_request_。cpu_time_ms、total_lock_wait_count、total_lock_wait_time_ms、total_query_optimization_count、total_suboptimal_plan_generation_count、total_reduced_memgrant_count、および max_request_grant_memory_kb の各します。 statistics_start_time は現在のシステム日付と時刻に設定されて、その他のカウンターがゼロ (0) に設定されます。  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [sys.resource_governor_workload_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



