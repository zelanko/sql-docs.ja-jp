---
title: sys.dm_resource_governor_workload_groups_history_ex (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups_history_ex_TSQL
- sys.dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_resource_governor_workload_groups_history_ex dynamic management view
author: joesackmsft
ms.author: josack
manager: craigg
ms.openlocfilehash: 1a2123c3da5945fb42184631e43fe27d83972375
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66744024"
---
# <a name="sysdmresourcegovernorworkloadgroupshistoryex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

リソースの最後の 30 分 15 秒間隔でスナップショットを返しますでは、Azure SQL Database の統計をプールします。
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pool_id**| ssNoversion |リソース プールの ID。 NULL 値は許可されません。|
|**group_id**| ssNoversion |ワークロード グループの ID。 NULL 値は許可されません。|
|**name**| nvarchar (256) |ワークロード グループの名前。 NULL 値は許可されません。|
|**snapshot_time**| DATETIME |作成されたリソース グループの統計情報のスナップショットの日時。|
|**duration_ms**| ssNoversion |現在と以前のスナップショット間の期間。|
|**active_worker_count**| ssNoversion |現在のスナップショットで worker の合計数。|
|**active_request_count**| ssNoversion |現在の要求数。 NULL 値は許可されません。|
|**active_session_count**| ssNoversion |現在のスナップショットのアクティブなセッションの合計。|
|**total_request_count**| BIGINT |ワークロード グループで完了した要求の累積数。 NULL 値は許可されません。|
|**delta_request_count**| ssNoversion |最後のスナップショットからのワークロード グループで完了した要求の数。 NULL 値は許可されません。|
|**total_cpu_usage_ms**| BIGINT |累積 CPU 使用率、このワークロード グループで、(ミリ秒)。 NULL 値は許可されません。|
|**delta_cpu_usage_ms**| ssNoversion |最後のスナップショット以降のミリ秒単位の CPU 使用率。 NULL 値は許可されません。|
|**delta_cpu_usage_preemptive_ms**| ssNoversion |Preemptive win32 呼び出しは最後のスナップショット以降しない SQL CPU の RG によって制御します。|
|**delta_reads_reduced_memgrant_count**| ssNoversion |最大クエリ サイズの上限を最新のスナップショット以降に達しているメモリ許可の数。 NULL 値は許可されません。|
|**reads_throttled**| ssNoversion |調整の読み取りの合計数。|
|**delta_reads_queued**| ssNoversion |合計には、最後のスナップショット以降の IOs エンキューが読み取られました。 NULL 値が許可されます。 IO リソース グループが制御されていない場合は null です。|
|**delta_reads_issued**| ssNoversion |読み取り最後のスナップショット以降に発行された Io の合計。 NULL 値が許可されます。 IO リソース グループが制御されていない場合は null です。|
|**delta_reads_completed**| ssNoversion |読み取り Io の最後のスナップショット以降に完了の合計。 NULL 値は許可されません。|
|**delta_read_bytes**| BIGINT |最後のスナップショットから読み取られたバイト数の合計。 NULL 値は許可されません。|
|**delta_read_stall_ms**| ssNoversion |読み取り IO の到着から最後のスナップショットから完了までのミリ秒単位で合計時間。 NULL 値は許可されません。|
|**delta_read_stall_queued_ms**| ssNoversion |読み取りの IO の到着から最後のスナップショットから発行までのミリ秒単位で合計時間。 NULL 値が許可されます。 IO リソース グループが制御されていない場合は null です。 0 以外の delta_read_stall_queued_ms RG IO が影響されるを意味します。|
|**delta_writes_queued**| ssNoversion |最後のスナップショットから IOs のエンキューされたを書き込みの合計。 NULL 値が許可されます。 IO リソース グループが制御されていない場合は null です。|
|**delta_writes_issued**| ssNoversion |IOs の最新のスナップショット以降に発行された書き込みの合計。 NULL 値が許可されます。 IO リソース グループが制御されていない場合は null です。|
|**delta_writes_completed**| ssNoversion |合計書き込み IOs は、最後のスナップショット以降に完了します。 NULL 値は許可されません。|
|**delta_writes_bytes**| BIGINT |最後のスナップショット以降に書き込まれたバイト数の合計数。 NULL 値は許可されません。|
|**delta_write_stall_ms**| ssNoversion |書き込み IO の到着から最後のスナップショットから完了までのミリ秒単位の合計時間。 NULL 値は許可されません。|
|**delta_background_writes**| ssNoversion |最後のスナップショット以降のバック グラウンド タスクによって実行される書き込みの合計。|
|**delta_background_write_bytes**| BIGINT |書き込みの合計サイズ (バイト単位) の最後のスナップショット以降のバック グラウンド タスクによって実行されます。|
|**delta_log_bytes_used**| BIGINT |使用 (バイト単位) の最後のスナップショット以降のログです。|
|**delta_log_temp_db_bytes_used**| BIGINT |Tempdb のログ (バイト単位) の最後のスナップショット以降を使用します。|
|**delta_query_optimizations**| BIGINT |このワークロード グループで最新のスナップショット以降のクエリの最適化の数。 NULL 値は許可されません。|
|**delta_suboptimal_plan_generations**| BIGINT |最後のスナップショット以降にメモリ不足のためには、このワークロード グループで発生する最適なプラン生成結果の数。 NULL 値は許可されません。
|**max_memory_grant_kb**| BIGINT |最大メモリは、(KB 単位) グループに付与します。|
|**max_request_cpu_msec**| BIGINT |最大 CPU 使用率、1 つの要求 (ミリ秒)。 NULL 値は許可されません。|
|**max_concurrent_request**| ssNoversion |最大同時要求数の現在の設定。 NULL 値は許可されません。|
|**max_io**| ssNoversion |グループの最大の IO 制限。|
|**max_global_io**| ssNoversion |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。
|**max_queued_io**| ssNoversion |単に情報を示すためだけに特定されます。 サポートされていません。 将来の互換性は保証されません。|
|**max_log_rate_kb**| BIGINT |リソース グループ レベルでログの最大速度 (キロのバイト数/秒)。|
|**max_session**| ssNoversion |グループのセッションの制限。|
|**max_worker**| ssNoversion |グループのワーカーの上限。|
|||

## <a name="permissions"></a>アクセス許可

このビューには、VIEW SERVER STATE 権限が必要です。

## <a name="remarks"></a>コメント

ユーザーは、ワークロード プールのユーザーとして Azure SQL Database インスタンスのシステムの内部プール リソースの消費量をリアルタイムに近いを監視するには、この動的管理ビューにアクセスできます。

> [!IMPORTANT]
> この DMV によって表示されるデータのほとんどは、社内従量課金プラン向けで、変更される可能性があります。

## <a name="examples"></a>使用例

次の例では、ユーザー プールによってログ率の最大のデータと各スナップショットの消費量を返します。

```sql
SELECT snapshot_time,
       name,
       max_log_rate_kb,
       delta_log_bytes_used
FROM sys.dm_resource_governor_workload_groups_history_ex
WHERE name LIKE 'User%'
ORDER BY snapshot_time DESC;
```

## <a name="see-also"></a>関連項目

- [翻訳ログ レートのガバナンス](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [エラスティック プール DTU のリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [エラスティック プールの vCore のリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
