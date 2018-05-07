---
title: sys.dm_resource_governor_workload_groups (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cb9694a1768b5038c0a6fcc2439139f8a0d05059
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmresourcegovernorworkloadgroups-transact-sql"></a>sys.dm_resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  ワークロード グループ統計と、ワークロード グループの現在のメモリ内構成を返します。 このビューを sys.dm_resource_governor_resource_pools と結合すると、リソース プール名を取得できます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_resource_governor_workload_groups**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ワークロード グループの ID。 NULL 値は許可されません。|  
|name|**sysname**|ワークロード グループの名前。 NULL 値は許可されません。|  
|pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|external_pool_id|**int**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 外部リソース プールの ID です。 NULL 値は許可されません。|  
|statistics_start_time|**datetime**|ワークロード グループの統計コレクションがリセットされた時刻。 NULL 値は許可されません。|  
|total_request_count|**bigint**|ワークロード グループで完了した要求の累積数。 NULL 値は許可されません。|  
|total_queued_request_count|**bigint**|GROUP_MAX_REQUESTS 制限に達した後にキューに置かれた要求の累積数。 NULL 値は許可されません。|  
|active_request_count|**int**|現在の要求数。 NULL 値は許可されません。|  
|queued_request_count|**int**|現在キューに置かれている要求の数。 NULL 値は許可されません。|  
|total_cpu_limit_violation_count|**bigint**|CPU 制限を超える要求の累積数。 NULL 値は許可されません。|  
|total_cpu_usage_ms|**bigint**|このワークロード グループによる累積 CPU 使用率 (ミリ秒単位)。 NULL 値は許可されません。|  
|max_request_cpu_time_ms|**bigint**|1 つの要求に対する最大 CPU 使用率 (ミリ秒単位)。 NULL 値は許可されません。<br /><br /> **注:** request_max_cpu_time_sec とは異なり、測定値は、これは構成可能な設定です。 詳細については、「[CPU Threshold Exceeded イベント クラス](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)」を参照してください。|  
|blocked_task_count|**int**|ブロックされたタスクの現在の数。 NULL 値は許可されません。|  
|total_lock_wait_count|**bigint**|発生したロック待機の累積数。 NULL 値は許可されません。|  
|total_lock_wait_time_ms|**bigint**|ロック保持の累積合計経過時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|total_query_optimization_count|**bigint**|このワークロード グループ内のクエリ最適化の累積数。 NULL 値は許可されません。|  
|total_suboptimal_plan_generation_count|**bigint**|メモリ不足のためにこのワークロード グループ内で発生した、最適ではないプラン生成の累積数。 NULL 値は許可されません。|  
|total_reduced_memgrant_count|**bigint**|クエリの最大サイズ制限に達したメモリ許可の累積数。 NULL 値は許可されません。|  
|max_request_grant_memory_kb|**bigint**|統計のリセット以降、1 つの要求に対する最大メモリ許可サイズ (KB 単位)。 NULL 値は許可されません。|  
|active_parallel_thread_count|**bigint**|並列スレッド使用状況の現在の数。 NULL 値は許可されません。|  
|importance|**sysname**|このワークロード グループ内の要求の相対的重要度を示す現在の構成値。 次のいずれかの重要度は、メディアで既定値: Low、Medium、または高です。<br /><br /> NULL 値は許可されません。|  
|request_max_memory_grant_percent|**int**|1 つの要求に対する最大メモリ許可の現在の設定 (%)。 NULL 値は許可されません。|  
|request_max_cpu_time_sec|**int**|1 つの要求に対する最大 CPU 使用制限の現在の設定 (秒単位)。 NULL 値は許可されません。|  
|request_memory_grant_timeout_sec|**int**|1 つの要求に対するメモリ許可のタイムアウトの現在の設定 (秒単位)。 NULL 値は許可されません。|  
|group_max_requests|**int**|同時要求の最大数の現在の設定。 NULL 値は許可されません。|  
|max_dop|**int**|ワークロード グループの並列処理の最大限度。 既定値は 0 で、グローバル設定が使用されます。 NULL 値は許可されません。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 この動的管理ビューには、メモリ内の構成が表示されます。 格納されている構成メタデータを表示するには、sys.resource_governor_workload_groups カタログ ビューを使用します。  
  
 ALTER RESOURCE GOVERNOR RESET STATISTICS が正常に実行されると、次のカウンターがリセットされます statistics_start_time、total_request_count、total_queued_request_count、total_cpu_limit_violation_count、total_cpu_usage_ms、max_request_。cpu_time_ms、total_lock_wait_count、total_lock_wait_time_ms、total_query_optimization_count、total_suboptimal_plan_generation_count、total_reduced_memgrant_count、および max_request_grant_memory_kb です。 statistics_start_time は現在のシステム日付と時刻に設定され、その他のカウンターがゼロ (0) に設定します。  
  
## <a name="permissions"></a>権限  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [sys.resource_governor_workload_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



