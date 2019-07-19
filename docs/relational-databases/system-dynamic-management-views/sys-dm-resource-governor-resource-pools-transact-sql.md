---
title: sys.dm_resource_governor_resource_pools (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pools_TSQL
- dm_resource_governor_resource_pools_TSQL
- sys.dm_resource_governor_resource_pools
- dm_resource_governor_resource_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_resource_pools dynamic management view
ms.assetid: 9bfc926e-d8bc-40f8-9229-ab1f8a1e69c5
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0bc10288e7dbe204633eef70f9affb07855ae3e7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053321"
---
# <a name="sysdmresourcegovernorresourcepools-transact-sql"></a>sys.dm_resource_governor_resource_pools (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  リソース プールの現在の状態、現在の構成、および統計に関する情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_resource_governor_resource_pools**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|NAME|**sysname**|リソース プールの名前。 NULL 値は許可されません。|  
|statistics_start_time|**datetime**|このプールの統計がリセットされた時刻。 NULL 値は許可されません。|  
|total_cpu_usage_ms|**bigint**|リソース ガバナー統計がリセットされた後のミリ秒単位で累積の CPU 使用率。 NULL 値は許可されません。|  
|cache_memory_kb|**bigint**|現在の合計キャッシュ メモリ使用量 (KB 単位)。 NULL 値は許可されません。|  
|compile_memory_kb|**bigint**|現在の合計メモリ流用量 (KB 単位)。 この量の大半はコンパイルと最適化に使用されますが、他のメモリ ユーザーに使用されている可能性もあります。 NULL 値は許可されません。|  
|used_memgrant_kb|**bigint**|現在の合計は、メモリ許可から (流用) のメモリを使用します。 NULL 値は許可されません。|  
|total_memgrant_count|**bigint**|メモリの累積数は、このリソース プールに付与します。 NULL 値は許可されません。|  
|total_memgrant_timeout_count|**bigint**|メモリの累積数は、このリソース プールのタイムアウトを付与します。 NULL 値は許可されません。|  
|active_memgrant_count|**int**|メモリ許可の現在の数。 NULL 値は許可されません。|  
|active_memgrant_kb|**bigint**|現在のメモリ許可のキロバイト (KB) 単位での合計。 NULL 値は許可されません。|  
|memgrant_waiter_count|**int**|メモリに現在保留中のクエリの数を許可します。 NULL 値は許可されません。|  
|max_memory_kb|**bigint**|最大リソース プールを持つことができます (キロバイト単位) のメモリ量。 現在の設定とサーバーの状態に基づきます。 NULL 値は許可されません。|  
|used_memory_kb|**bigint**|使用される、キロバイト、リソース プールのメモリの量。 NULL 値は許可されません。|  
|target_memory_kb|**bigint**|キロバイト単位でのメモリ量の対象リソース プールが残るとしています。 現在の設定とサーバーの状態に基づきます。 NULL 値は許可されません。|  
|out_of_memory_count|**bigint**|リソース ガバナー統計がリセットされた後にプールで失敗したメモリ割り当ての数。 NULL 値は許可されません。|  
|min_cpu_percent|**int**|現在、保証される平均 CPU 帯域幅 CPU の競合がある場合に、リソース プール内のすべての要求の構成です。 NULL 値は許可されません。|  
|max_cpu_percent|**int**|現在、最大平均 CPU 帯域幅 CPU の競合がある場合に、リソース プールのすべての要求に許可されている構成です。 NULL 値は許可されません。|  
|min_memory_percent|**int**|保証されたメモリの競合がある場合に、リソース プール内のすべての要求のメモリ量の現在の構成。 これは、他のリソース プールとは共有されません。 NULL 値は許可されません。|  
|max_memory_percent|**int**|このリソース プールの要求で使用できる合計サーバー メモリの割合の現在の構成。 NULL 値は許可されません。|  
|cap_cpu_percent|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース プール内のすべての要求を受信する、CPU 帯域幅のハード キャップ。 指定されたレベルには、最大の CPU 帯域幅レベルを制限します。 値の許容範囲は 1 ~ 100 です。 NULL 値は許可されません。|  
|min_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのディスク ボリューム設定ごと (IOPS) を 1 秒あたりの最小 I/O。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|max_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのディスク ボリューム設定ごと (IOPS) を 1 秒あたりの最大 I/O。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 つまり、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定値は 0.|  
|read_io_queued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナーがリセットされた後にエンキューされた読み取り IO の合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|read_io_issued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 読み取りリソース ガバナー統計がリセットされた後に発行される Io の合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|read_io_completed_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に完了した読み取り IO の合計。 NULL 値は許可されません。|  
|read_io_throttled_total|**int**|IOs のリソース ガバナー統計がリセットされた後に調整された読み取りの合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|read_bytes_total|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に読み取られたバイト数の合計。 NULL 値は許可されません。|  
|read_io_stall_total_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 読み取り IO の到着から完了までのミリ秒単位で合計時間。 NULL 値は許可されません。 |  
|確認するのに|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 読み取り IO の到着から発行までのミリ秒単位で合計時間。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。<br /><br /> かどうか、IO 設定、待機時間の原因となって、プールの減算を決定する**確認するのに**から**read_io_stall_total_ms**します。|  
|write_io_queued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後 IOs のエンキューされたを書き込みの合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|write_io_issued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に発行される Io を書き込みの合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|write_io_completed_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に完了した書き込み IO の合計。 値が許容されません。|  
|write_io_throttled_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> IOs のリソース ガバナー統計がリセットされた後に調整された書き込みの合計。 値が許容されません。|  
|write_bytes_total|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に書き込まれたバイト数の合計。 NULL 値は許可されません。|  
|write_io_stall_total_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 書き込み IO の到着から完了までのミリ秒単位の合計時間。 NULL 値は許可されません。 |  
|write_io_stall_queued_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 書き込み IO の到着から発行までの合計時間 (ミリ秒単位)。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。<br /><br /> これは、IO リソース管理によって遅延です。|  
|io_issue_violations_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> IO 発行違反の合計。 IO の割合を発行するときの回数が予約レートよりも低かった。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|io_issue_delay_total_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> スケジュールされた問題と IO の実際の問題の間 (ミリ秒単位) の合計時間。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 これは、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME 設定は 0 です。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="remarks"></a>コメント  
 リソース ガバナー ワークロード グループとリソース ガバナー リソース プールの多対一のマッピングであります。 このため、多くのリソース プール統計が、ワークロード グループ統計から派生しています。  
  
 この動的管理ビューは、メモリ内の構成を示しています。 格納されている構成メタデータを表示するには、sys.resource_governor_resource_pools カタログ ビューを使用します。  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



