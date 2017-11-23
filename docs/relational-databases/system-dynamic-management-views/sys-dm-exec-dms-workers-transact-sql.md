---
title: "sys.dm_exec_dms_workers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS
dev_langs: TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_workers management view
- sys.dm_exec_dms_workers management view
ms.assetid: f468da29-78c3-4f10-8a3c-17905bbf46f2
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b5677eb04a9a5809c2caf25d37edd288e4b1efbc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecdmsworkers-transact-sql"></a>sys.dm_exec_dms_workers (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  DMS の手順を実行するすべての作業者に関する情報を保持します。  
  
 このビューは、過去 1000 件の要求とアクティブな要求のデータを示しています。アクティブな要求には、常に、このビュー内のデータがあります。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar (32)**|クエリを DMS ワーカーは、一部の of.request_id、step_index、および dms_step_index は、このビューのキーを形成します。||  
|step_index|**int**|DMS ワーカーの一部である手順のクエリを実行します。|内の手順インデックスを参照してください[sys.dm_exec_distributed_request_steps &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|**int**|このワーカーが実行されている DMS プランのステップします。|参照してください[sys.dm_exec_dms_workers (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|**int**|ワーカーが実行されているノードです。|参照してください[sys.dm_exec_compute_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|||  
|型|**nvarcha(32)**|||  
|ステータス|**nvarchar (32)**|この手順の状態|'Pending'、'Running'、'完了'、'失敗'、'UndoFailed'、'PendingCancel'、' が取り消されました '、'を元に戻す'、'中止'|  
|bytes_per_sec|**bigint**|||  
|bytes_processed|**bigint**|||  
|rows_processed|**bigint**|||  
|start_time|**datetime**|ステップの実行開始時刻|小さいまたは現在の時刻と等しい、大きいか等しい end_compile_time が、この手順が属している、クエリのです。|  
|end_time|**datetime**|このステップ実行を完了したが取り消された場合、または失敗したの時間です。|小さいまたは現在の時刻に等しいと大きいか等しい start_time、手順については、現在実行中に NULL を設定するか、キューに登録します。|  
|total_elapsed_time|**int**|クエリのステップが実行されて、ミリ秒単位で時間の合計|0 ～ start_time と end_time の間の違いです。 手順についてはキューに置かれた 0 を返します。|  
|cpu_time|**bigint**|||  
|query_time|**int**|||  
|buffers_available|**int**|||  
|dms_cpid|**int**|||  
|sql_spid|**int**|||  
|error_id|**nvarchar (36)**|||  
|source_info|**nvarchar (4000)**|||  
|destination_info|**nvarchar (4000)**|||  
|command|**nvarchar (4000)**|||  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
