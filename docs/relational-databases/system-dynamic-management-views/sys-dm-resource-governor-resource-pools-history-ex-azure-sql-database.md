---
title: sys.dm_resource_governor_resource_pools_history_ex (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor
- sys.resource_governor_TSQL
- resource_governor
- resource_governor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: d585f1f1245457aa9051f25bca696cf4495d93ed
ms.sourcegitcommit: 32dce314bb66c03043a93ccf6e972af455349377
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743923"
---
# <a name="sysdmresourcegovernorresourcepoolshistoryex-transact-sql"></a>sys.dm_resource_governor_resource_pools_history_ex (TRANSACT-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

リソースの最後の 30 分 15 秒間隔でスナップショットを返しますでは、Azure SQL Database の統計をプールします。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pool_id**|ssNoversion|リソース プールの ID。 NULL 値は許可されません。
|**name**|sysname|リソース プールの名前。 NULL 値は許可されません。|
|**snapshot_time**|datetime2|作成されたリソース プール統計のスナップショットの Datetime|
|**duration_ms**|ssNoversion|現在と以前のスナップショット間の期間|
|**statistics_start_time**|datetime2|このプールの統計がリセットされた時刻。 NULL 値は許可されません。|
|**active_session_count**|ssNoversion|現在のスナップショットのアクティブなセッションの合計|
|**active_worker_count**|ssNoversion|現在のスナップショットで worker の合計数|
|**delta_cpu_usage_ms**|ssNoversion|最後のスナップショット以降のミリ秒単位の CPU 使用率。 NULL 値は許可されません。|
|**delta_cpu_usage_preemptive_ms**|ssNoversion|Preemptive win32 呼び出しをしない SQL CPU の RG によって最後のスナップショットから管理します。|
|**used_data_space_kb**|BIGINT|ユーザーのプールに関連付けられているユーザー データベースで使用される領域の合計|
|**allocated_disk_space_kb**|BIGINT|データの合計では、ユーザー データベースのサイズをファイルに関連付けられているユーザー プール|
|**target_memory_kb**|BIGINT|キロバイト単位でのメモリ量の対象リソース プールが残るとしています。 現在の設定とサーバーの状態に基づきます。 NULL 値は許可されません。|
|**used_memory_kb**|BIGINT|使用される、キロバイト、リソース プールのメモリの量。 NULL 値は許可されません。|
|**cache_memory_kb**|BIGINT|現在の合計キャッシュ メモリ使用量 (KB 単位)。 NULL 値は許可されません。|
|**compile_memory_kb**|BIGINT|現在の合計メモリ流用量 (KB 単位)。 この量の大半はコンパイルと最適化に使用されますが、他のメモリ ユーザーに使用されている可能性もあります。 NULL 値は許可されません。|
|**active_memgrant_count**|BIGINT|メモリ許可の現在の数。 NULL 値は許可されません。|
|**active_memgrant_kb**|BIGINT|現在のメモリ許可のキロバイト (KB) 単位での合計。 NULL 値は許可されません。|
|**used_memgrant_kb**|BIGINT|現在の合計は、メモリ許可から (流用) のメモリを使用します。 NULL 値は許可されません。|
|**delta_memgrant_timeout_count**|ssNoversion|メモリの数は、この期間でこのリソース プールのタイムアウトを付与します。 NULL 値は許可されません。|
|**delta_memgrant_waiter_count**|ssNoversion|メモリに現在保留中のクエリの数を許可します。 NULL 値は許可されません。|
|**delta_out_of_memory_count**|ssNoversion|最後のスナップショットから、プール内の失敗したメモリ割り当ての数。 NULL 値は許可されません。|
|**delta_read_io_queued**|ssNoversion|合計には、最後のスナップショット以降の IOs エンキューが読み取られました。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**delta_read_io_issued**|ssNoversion|読み取り最後のスナップショット以降に発行された Io の合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**delta_read_io_completed**|ssNoversion|読み取り Io の最後のスナップショット以降に完了の合計。 NULL 値は許可されません。|
|**delta_read_io_throttled**|ssNoversion|読み取り Io のスナップショット以降の調整の合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**delta_read_bytes**|BIGINT|最後のスナップショットから読み取られたバイト数の合計。 NULL 値は許可されません。|
|**delta_read_io_stall_ms**|ssNoversion|読み取り IO の到着から最後のスナップショットから完了までのミリ秒単位で合計時間。 NULL 値は許可されません。|
|**delta_read_io_stall_queued_ms**|ssNoversion|読み取りの IO の到着から最後のスナップショットから発行までのミリ秒単位で合計時間。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。 0 以外の delta_read_io_stall_queued_ms RG IO が影響されるを意味します。|
|**delta_write_io_queued**|ssNoversion|最後のスナップショットから IOs のエンキューされたを書き込みの合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**delta_write_io_issued**|ssNoversion|IOs の最新のスナップショット以降に発行された書き込みの合計。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**delta_write_io_completed**|ssNoversion|合計書き込み IOs は、最後のスナップショット以降に完了します。 値が許容されません。|
|**delta_write_io_throttled**|ssNoversion|合計書き込み IOs は、最後のスナップショットから調整されています。 値が許容されません。|
|**delta_write_bytes**|BIGINT|最後のスナップショット以降に書き込まれたバイト数の合計数。 NULL 値は許可されません。|
|**delta_write_io_stall_ms**|ssNoversion|書き込み IO の到着から最後のスナップショットから完了までのミリ秒単位の合計時間。 NULL 値は許可されません。|
|**delta_write_io_stall_queued_ms**|ssNoversion|書き込み IO の到着から最後のスナップショットから発行までのミリ秒単位で合計時間。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**delta_io_issue_delay_ms**|ssNoversion|スケジュールされた問題と IO の最後のスナップショットからの実際の問題の間 (ミリ秒単位) の合計時間。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**max_iops_per_volume**|ssNoversion|このプールのディスク ボリューム設定ごと (IOPS) を 1 秒あたりの最大 I/O。 NULL 値が許可されます。 リソース プールの IO が制御されていない場合は null です。|
|**max_memory_kb**|BIGINT|最大リソース プールを持つことができます (キロバイト単位) のメモリ量。 現在の設定とサーバーの状態に基づきます。 NULL 値は許可されません。
|**max_log_rate_kb**|BIGINT|リソース プール レベルでログの最大速度 (キロのバイト数/秒)。|
|**max_data_space_kb**|BIGINT|最大エラスティック プール記憶域の上限はキロバイト単位でのこのエラスティック プールを設定します。|
|**max_session**|ssNoversion|プールのセッションの制限|
|**max_worker**|ssNoversion|プールのワーカーの上限|
|**min_cpu_percent**|ssNoversion|現在、保証される平均 CPU 帯域幅 CPU の競合がある場合に、リソース プール内のすべての要求の構成です。 NULL 値は許可されません。|
|**max_cpu_percent**|ssNoversion|現在、最大平均 CPU 帯域幅 CPU の競合がある場合に、リソース プールのすべての要求に許可されている構成です。 NULL 値は許可されません。|
|**cap_cpu_percent**|ssNoversion|リソース プール内のすべての要求を受信する、CPU 帯域幅のハード キャップ。 指定されたレベルには、最大の CPU 帯域幅レベルを制限します。 値の許容範囲は 1 ~ 100 です。 NULL 値は許可されません。|
|**min_vcores**|decimal(5,2)|現在、保証される平均 CPU 帯域幅 CPU の競合がある場合に、リソース プール内のすべての要求の構成です。  仮想コアの単位|
|**max_vcores**|decimal(5,2)|現在、最大平均 CPU 帯域幅 CPU の競合がある場合に、リソース プールのすべての要求に許可されている構成です。  仮想コアの単位|
|**cap_vcores**|decimal(5,2)|リソース プール内のすべての要求を受信する、CPU 帯域幅のハード キャップ。  仮想コアの単位|
|**instance_cpu_count**|ssNoversion|インスタンス用に構成された CPU の数|
|**instance_cpu_percent|decimal(5,2)|インスタンス用に構成された CPU 使用率|
|**instance_vcores**|decimal(5,2)|インスタンス用に構成された仮想コアの数|
|**delta_log_bytes_used**|decimal(5,2)|最後のスナップショットからプール レベルでのバイト単位での生成の合計ログ|
|**avg_login_rate_percent**|decimal(5,2)|ログインの制限と比較の最後のスナップショット以降のログイン数|
|**delta_vcores_used**|decimal(5,2)|最後のスナップショットから仮想コアの数の使用率を計算します。|
|**cap_vcores_used_percent**|decimal(5,2)|プールの制限の割合で表した平均コンピューティング使用率。|
|**instance_vcores_used_percent**|decimal(5,2)|SQL インスタンスの制限の割合で表した平均コンピューティング使用率。|
|**avg_data_io_percent**|decimal(5,2)|プールの限度に対する割合で表した平均 I/O 使用率。|
|**avg_log_write_percent**|decimal(5,2)|平均書き込みリソース使用率、プールの制限の割合。|
|**avg_storage_percent**|decimal(5,2)|プールの記憶域の上限の割合で表した平均ストレージ使用率。|
|**avg_allocated_storage_percent**|decimal(5,2)|エラスティック プール内のすべてのデータベースで割り当てられているデータ領域の割合。 これは、エラスティック プールの最大サイズのデータに割り当てられているデータ領域の比率です。 詳しくは、次のトピックをご覧ください。SQL DB でのファイル領域の管理|
|**max_worker_percent**|decimal(5,2)|プールの限度に対する割合で表した最大同時実行ワーカー (要求)。|
|**max_session_percent**|decimal(5,2)|プールの限度に対する割合で表した最大同時セッション数。|
|||

## <a name="permissions"></a>アクセス許可

このビューには、VIEW SERVER STATE 権限が必要です。

## <a name="remarks"></a>コメント

ユーザーは、ワークロード プールのユーザーとして Azure SQL Database インスタンスのシステムの内部プール リソースの消費量をリアルタイムに近いを監視するには、この動的管理ビューにアクセスできます。

> [!IMPORTANT]
> この DMV によって表示されるデータのほとんどは、社内従量課金プラン向けで、変更される可能性があります。

## <a name="examples"></a>使用例

次の例では、ユーザー プールによって最大ログ比率のデータと各スナップショットの消費量を返します  

```sql
select snapshot_time, name, max_log_rate_kb, delta_log_bytes_used from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

次の例は、論理マスターに接続することがなく sys.elastic_pool_resource_stats としてのような情報を返します

```sql
select snapshot_time, name, cap_vcores_used_percent,
  avg_data_io_percent,  
  avg_log_write_percent,
  avg_storage_percent,
  avg_allocated_storage_percent,
  max_data_space_kb,
  max_worker_percent,
  max_session_percent
    from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

## <a name="see-also"></a>参照

- [翻訳ログ レートのガバナンス](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [エラスティック プール DTU のリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [エラスティック プールの vCore のリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
