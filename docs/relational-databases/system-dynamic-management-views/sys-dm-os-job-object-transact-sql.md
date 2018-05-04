---
title: sys.dm_os_job_object (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/17/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a381366960236b1881b103d68df48cee6f52e1c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmosjobobject-azure-sql-database"></a>sys.dm_os_job_object (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

SQL Server プロセスだけでなく、ジョブ オブジェクト レベルで特定リソース消費量の統計情報を管理するジョブ オブジェクトの構成を記述する 1 つの行を返します。 SQL Server はジョブ オブジェクトで実行されていない場合は、空のセットを返します。 

ジョブ オブジェクトは、オペレーティング システム レベルでの CPU、メモリ、および IO リソース管理を実装する Windows のコンストラクトです。 ジョブ オブジェクトに関する詳細については、次を参照してください。[ジョブ オブジェクト](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx)です。 

> [!NOTE]
> Sys.dm_os_job_object DMV が現在 sys.dm_job_object として表示されます。 これは一時的な:`sys.dm_os_job_object`この DMV の永続的な名前になります。 
  
|列|データ型|Description|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|SQL Server スレッドは、各スケジュールの間隔中に使用できるプロセッサ サイクルの一部を指定します。 値は 10000 サイクル スケジュールの間隔内で利用可能なサイクルの割合として報告されます。 例を値 100 は、スレッドが CPU コアを使用できることは、そのすべての容量を示します。|
|cpu_affinity_mask|**bigint**|論理プロセッサを記述するビット マスク SQL Server プロセスは、プロセッサ グループ内で使用できます。 たとえば、cpu_affinity_mask 255 (バイナリ 1111) つまり最初の 8 個の論理プロセッサを使用できます。|
|cpu_affinity_group|**int**|SQL Server で使用されているプロセッサ グループの数。|
|memory_limit_mb|**bigint**|SQL Server を含む、ジョブ オブジェクトのすべてのプロセスが累積的に使用できる、mb 単位でのコミットされたメモリの最大量。| 
|process_memory_limit_mb |**bigint**|SQL Server など、ジョブ オブジェクトの 1 つのプロセスを mb 単位でのコミットされたメモリの最大量を使用できます。|
|workingset_limit_mb |**bigint**|MB で、SQL Server のワーキング セットが使用できるメモリの最大量。|
|non_sos_mem_gap_mb|**bigint**|Mb 単位でのメモリの量は、スレッドのスタック、Dll、およびその他の非 SOS メモリ割り当てを確保します。 SOS ターゲット メモリ間の違いは、`process_memory_limit_mb`と`non_sos_mem_gap_mb`です。| 
|low_mem_signal_threshold_mb|**bigint**|メモリのしきい値を mb 単位で。 ジョブ オブジェクトの使用可能なメモリの量がこのしきい値より下にある場合は、SQL Server プロセスにメモリ不足の通知信号が送信されます。 |
|total_user_time|**bigint**|ジョブ オブジェクトが作成されてからユーザー モードで、ジョブ オブジェクト内のスレッドを 100 ns 刻みの合計数を設けます。 |
|total_kernel_time |**bigint**|ジョブ オブジェクト内のスレッドを 100 ns 刻みの合計数は、ジョブ オブジェクトが作成されてから、カーネル モードで費やしてきました。 |
|write_operation_count |**bigint**|合計数は、ローカル ディスク上にジョブ オブジェクトが作成された後に SQL Server によって発行された IO 操作を記述します。 |
|read_operation_count |**bigint**|ローカル ディスク上にジョブ オブジェクトが作成された後に SQL Server によって発行された読み取りの IO 操作の合計数。 |
|peak_process_memory_used_mb|**bigint**|ピーク時の SQL Server など、ジョブ オブジェクトの 1 つのプロセスを mb 単位でのメモリ量は、ジョブ オブジェクトが作成されたために使用します。| 
|peak_job_memory_used_mb|**bigint**|ピーク時のジョブ オブジェクトのすべてのプロセスは、ジョブ オブジェクトから累積的に使用している mb 単位でのメモリ量が作成されました。|
  
## <a name="permissions"></a>権限  
SQL データベース管理インスタンスが必要です。`VIEW SERVER STATE`権限です。 SQL データベースで必要があります、`VIEW DATABASE STATE`データベースの権限です。  
 
## <a name="see-also"></a>参照  

マネージ インスタンスについては、次を参照してください。[マネージ インスタンスの SQL データベース](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)です。
  
