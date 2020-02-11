---
title: dm_os_job_object (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 43063bb56607d1b5a21ae04b40ee4c7a17825521
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900135"
---
# <a name="sysdm_os_job_object-azure-sql-database"></a>sys.dm_os_job_object (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

SQL Server プロセスを管理するジョブオブジェクトの構成と、ジョブオブジェクトレベルでの特定のリソース消費量の統計を示す1行のデータを返します。 SQL Server がジョブオブジェクトで実行されていない場合は、空のセットを返します。 

ジョブオブジェクトは、オペレーティングシステムレベルで CPU、メモリ、および IO リソースガバナンスを実装する Windows コンストラクトです。 ジョブオブジェクトの詳細については、「 [Job objects](/windows/desktop/ProcThread/job-objects)」を参照してください。 
  
|[列]|データ型|[説明]|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|SQL Server のスレッドが各スケジューリング間隔中に使用できるプロセッササイクルの部分を指定します。 この値は、1万サイクルのスケジュール間隔で、使用可能なサイクルの割合として報告されます。 たとえば、値100は、スレッドが CPU コアを使用できることを意味します。|
|cpu_affinity_mask|**bigint**|SQL Server プロセスがプロセッサグループ内で使用できる論理プロセッサを示すビットマスク。 たとえば、cpu_affinity_mask 255 (バイナリでは 1111 1111) は、最初の8個の論理プロセッサを使用できることを意味します。|
|cpu_affinity_group|**int**|SQL Server によって使用されるプロセッサグループの番号。|
|memory_limit_mb|**bigint**|コミットされたメモリの最大量 (MB 単位)。ジョブオブジェクト内のすべてのプロセス (SQL Server を含む) で累積的を使用できます。| 
|process_memory_limit_mb |**bigint**|SQL Server など、ジョブオブジェクト内の1つのプロセスが使用できるコミット済みメモリの最大量 (MB 単位)。|
|workingset_limit_mb |**bigint**|SQL Server ワーキングセットが使用できるメモリの最大量 (MB 単位)。|
|non_sos_mem_gap_mb|**bigint**|スレッドスタック、Dll、およびその他の SOS 以外のメモリ割り当てに対して確保されるメモリの量 (MB 単位)。 SOS ターゲットメモリは`process_memory_limit_mb` 、と`non_sos_mem_gap_mb`の差です。| 
|low_mem_signal_threshold_mb|**bigint**|メモリのしきい値 (MB 単位)。 ジョブオブジェクトで使用可能なメモリの量がこのしきい値を下回ると、メモリ不足の通知信号が SQL Server プロセスに送信されます。 |
|total_user_time|**bigint**|ジョブオブジェクトが作成されてから、ジョブオブジェクト内のスレッドがユーザーモードで費やした 100 ns タイマー刻みの合計数。 |
|total_kernel_time |**bigint**|ジョブオブジェクトが作成されてから、ジョブオブジェクト内のスレッドがカーネルモードで消費した 100 ns タイマー刻みの合計数。 |
|write_operation_count |**bigint**|ジョブオブジェクトが作成されてから、SQL Server によって発行されたローカルディスク上の書き込み IO 操作の合計数。 |
|read_operation_count |**bigint**|ジョブオブジェクトが作成されてから、SQL Server によって発行されたローカルディスク上の読み取り IO 操作の合計数。 |
|peak_process_memory_used_mb|**bigint**|ジョブオブジェクトが作成されてから、SQL Server など、ジョブオブジェクト内の1つのプロセスが使用していたメモリのピーク容量 (MB 単位)。| 
|peak_job_memory_used_mb|**bigint**|ジョブオブジェクトが作成されてから、ジョブオブジェクト内のすべてのプロセスが累積的を使用したメモリのピーク容量 (MB 単位)。|
  
## <a name="permissions"></a>アクセス許可  
SQL Database Managed Instance では、 `VIEW SERVER STATE`権限が必要です。 SQL Database では、データベースにおける `VIEW DATABASE STATE` アクセス許可が必要です。  
 
## <a name="see-also"></a>参照  

マネージインスタンスの詳細については、「 [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)」を参照してください。
  
