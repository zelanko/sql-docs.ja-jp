---
title: dm_exec_dms_workers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_workers management view
- sys.dm_exec_dms_workers management view
ms.assetid: f468da29-78c3-4f10-8a3c-17905bbf46f2
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4951954bb9f6336c2c984a8d74c2224eab4dfbb0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821092"
---
# <a name="sysdm_exec_dms_workers-transact-sql"></a>dm_exec_dms_workers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  DMS ステップを完了するすべてのワーカーに関する情報を保持します。  
  
 このビューには、最後の1000要求とアクティブな要求のデータが表示されます。アクティブな要求には、常にこのビュー内のデータが含まれます。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|この DMS ワーカーが含まれているクエリ。 request_id、step_index、および dms_step_index は、このビューのキーを形成します。||  
|step_index|`int`|この DMS ワーカーが含まれているクエリステップ。|「 [Transact-sql&#41;&#40;dm_exec_distributed_request_steps](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)のステップインデックス」を参照してください。|  
|dms_step_index|`int`|このワーカーが実行されている DMS プランのステップ。|「 [Dm_exec_dms_workers (transact-sql)」を](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)参照してください。|  
|compute_node_id|`int`|ワーカーが実行されているノード。|「 [Sys. dm_exec_compute_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)」を参照してください。|  
|distribution_id|`int`|||  
|型|`nvarcha(32)`|||  
|status|`nvarchar(32)`|この手順の状態|' Pending '、' Running '、' Complete '、' Failed '、' UndoFailed '、' PendingCancel '、' 取り消し済み '、' 元に戻す '、' Aborted '|  
|bytes_per_sec|`bigint`|||  
|bytes_processed|`bigint`|||  
|rows_processed|`bigint`|||  
|start_time|`datetime`|ステップが実行を開始した時刻|小さいまたは現在の時刻に等しいが、このステップが属するクエリの end_compile_time 以上です。|  
|end_time|`datetime`|このステップの実行が完了した時刻。が取り消されたか、失敗しました。|小または現在の時刻に等しいか start_time 以上で、現在実行中またはキューに置かれているステップに対して NULL に設定されます。|  
|total_elapsed_time|`int`|クエリステップが実行されていた合計時間 (ミリ秒)|0 ~ end_time と start_time の差。 キューに登録されたステップの場合は0。|  
|cpu_time|`bigint`|||  
|query_time|`int`|||  
|buffers_available|`int`|||  
|dms_cpid|`int`|||  
|sql_spid|`int`|||  
|error_id|`nvarchar(36)`|||  
|source_info|`nvarchar(4000)`|||  
|destination_info|`nvarchar(4000)`|||  
|コマンドを使用します|`nvarchar(4000)`|||
|compute_pool_id|`int`|プールの一意の識別子。|

## <a name="see-also"></a>参照  
 [動的管理ビューを使用した PolyBase のトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;データベース関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
