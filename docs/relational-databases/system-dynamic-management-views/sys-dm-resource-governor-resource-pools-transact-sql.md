---
title: sys.dm_resource_governor_resource_pools (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6a1d56202136dbc06d6bf2eabb49d40bc5c756bd
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43082752"
---
# <a name="sysdmresourcegovernorresourcepools-transact-sql"></a>sys.dm_resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  リソース プールの現在の状態、現在の構成、および統計に関する情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_resource_governor_resource_pools**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|NAME|**sysname**|リソース プールの名前。 NULL 値は許可されません。|  
|statistics_start_time|**datetime**|このプールの統計がリセットされた時刻。 NULL 値は許可されません。|  
|total_cpu_usage_ms|**bigint**|リソース ガバナー統計がリセットされた後の累積 CPU 使用率 (ミリ秒単位)。 NULL 値は許可されません。|  
|cache_memory_kb|**bigint**|現在の合計キャッシュ メモリ使用量 (KB 単位)。 NULL 値は許可されません。|  
|compile_memory_kb|**bigint**|現在の合計メモリ流用量 (KB 単位)。 この量の大半はコンパイルと最適化に使用されますが、他のメモリ ユーザーに使用されている可能性もあります。 NULL 値は許可されません。|  
|used_memgrant_kb|**bigint**|メモリ許可から現在使用 (流用) されている合計メモリ。 NULL 値は許可されません。|  
|total_memgrant_count|**bigint**|このリソース プールにおけるメモリ許可の累積数。 NULL 値は許可されません。|  
|total_memgrant_timeout_count|**bigint**|このリソース プールにおけるメモリ許可のタイムアウトの累積数。 NULL 値は許可されません。|  
|active_memgrant_count|**int**|メモリ許可の現在の数。 NULL 値は許可されません。|  
|active_memgrant_kb|**bigint**|現在のメモリ許可の合計 (KB 単位)。 NULL 値は許可されません。|  
|memgrant_waiter_count|**int**|メモリ許可で現在保留中のクエリの数。 NULL 値は許可されません。|  
|max_memory_kb|**bigint**|リソース プールで保持できる最大メモリ量 (KB 単位)。 これは、現在の設定およびサーバーの状態に基づいて決まります。 NULL 値は許可されません。|  
|used_memory_kb|**bigint**|使用される、キロバイト、リソース プールのメモリの量。 NULL 値は許可されません。|  
|target_memory_kb|**bigint**|リソース プールで取得しようとしている目標メモリ量 (KB 単位)。 これは、現在の設定およびサーバーの状態に基づいて決まります。 NULL 値は許可されません。|  
|out_of_memory_count|**bigint**|リソース ガバナー統計がリセットされた後にプールで失敗したメモリ割り当ての数。 NULL 値は許可されません。|  
|min_cpu_percent|**int**|CPU の競合がある場合にリソース プールのすべての要求に保証される平均 CPU 帯域幅の現在の構成。 NULL 値は許可されません。|  
|max_cpu_percent|**int**|CPU の競合がある場合にリソース プールのすべての要求に許可される最大平均 CPU 帯域幅の現在の構成。 NULL 値は許可されません。|  
|min_memory_percent|**int**|メモリの競合がある場合にリソース プールのすべての要求に保証されるメモリ量の現在の構成。 これは、他のリソース プールとは共有されません。 NULL 値は許可されません。|  
|max_memory_percent|**int**|このリソース プールの要求で使用できる合計サーバー メモリの割合の現在の構成。 NULL 値は許可されません。|  
|cap_cpu_percent|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース プールのすべての要求に割り当てられる、CPU 帯域幅のハード キャップ。 CPU の最大帯域幅レベルを、指定したレベルに制限します。 値の許容範囲は 1 ～ 100 です。 NULL 値は許可されません。|  
|min_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのディスク ボリューム設定ごとの、1 秒あたりの最小 I/O (IOPS)。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|max_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのディスク ボリューム設定ごとの、1 秒あたりの最大 I/O (IOPS)。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  つまり、リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定値は 0.|  
|read_io_queued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナーがリセットされた後にエンキューされた読み取り IO の合計。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|read_io_issued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に発行された読み取り IO の合計。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|read_io_completed_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に完了した読み取り IO の合計。 NULL 値は許可されません。|  
|read_io_throttled_total|**int**|リソース ガバナー統計がリセットされた後に調整された読み取り IO の合計。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|read_bytes_total|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に読み取られたバイト数の合計。 NULL 値は許可されません。|  
|read_io_stall_total_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 読み取り IO の到着から完了までの合計時間 (ミリ秒単位)。 NULL 値は許可されません。 |  
|read_io_stall_queued_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 読み取り IO の到着から発行までの合計時間 (ミリ秒単位)。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。<br /><br /> かどうか、IO 設定、待機時間の原因となって、プールの減算を決定する**確認するのに**から**read_io_stall_total_ms**します。|  
|write_io_queued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後にエンキューされた書き込み IO の合計。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|write_io_issued_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に発行された書き込み IO の合計。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|write_io_completed_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に完了した書き込み IO の合計。 値が許容されません。|  
|write_io_throttled_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に調整された書き込み IO の合計。 値が許容されません。|  
|write_bytes_total|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース ガバナー統計がリセットされた後に書き込まれたバイト数の合計。 NULL 値は許可されません。|  
|write_io_stall_total_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 書き込み IO の到着から完了までの合計時間 (ミリ秒単位)。 NULL 値は許可されません。 |  
|write_io_stall_queued_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 書き込み IO の到着から発行までの合計時間 (ミリ秒単位)。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。<br /><br /> これは、IO リソース管理によって発生した遅延です。|  
|io_issue_violations_total|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> IO 発行違反の合計。 つまり、IO の発行レートが予約レートを下回った回数です。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|io_issue_delay_total_ms|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> IO の発行予定時間から実際に発行されるまでの合計時間 (ミリ秒単位)。 NULL 値が許可されます。 IO についてリソース プールが管理されていない場合  (リソース プールの MIN_IOPS_PER_VOLUME および MAX_IOPS_PER_VOLUME の設定が 0 の場合) は NULL です。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="remarks"></a>コメント  
 リソース ガバナー ワークロード グループとリソース ガバナー リソース プールには、多対一のマッピングがあります。 このため、多くのリソース プール統計が、ワークロード グループ統計から派生しています。  
  
 この動的管理ビューには、メモリ内の構成が表示されます。 格納されている構成メタデータを表示するには、sys.resource_governor_resource_pools カタログ ビューを使用します。  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



