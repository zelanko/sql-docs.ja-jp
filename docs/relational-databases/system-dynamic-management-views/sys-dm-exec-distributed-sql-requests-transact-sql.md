---
title: dm_exec_distributed_sql_requests (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_distributed_requests management view
- dm_exec_distributed_requests management view
ms.assetid: d065dc01-35d4-472f-9554-53ac41e7d104
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0bfaaa65c08155263c15a1e4e4ddf17c20913e66
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827976"
---
# <a name="sysdm_exec_distributed_sql_requests-transact-sql"></a>dm_exec_distributed_sql_requests (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  クエリの SQL ステップの一部として、すべての SQL クエリディストリビューションに関する情報を保持します。  このビューには、最後の1000要求のデータが表示されます。アクティブな要求には、常にこのビュー内のデータが含まれます。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|execution_id と step_index このビューのキーを構成します。 要求に関連付けられている一意の数値 id。|詳細については、「 [sys. dm_exec_requests &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) 」を参照してください。|  
|step_index|**int**|この分布が含まれるクエリステップのインデックス。|『 [Transact-sql&#41;&#40;dm_exec_distributed_request_steps](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)の step_index を参照してください。|  
|compute_node_id|**int**|このステップで表される操作の種類。|『 [Transact-sql&#41;&#40;dm_exec_compute_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)の compute_node_id を参照してください。|  
|distribution_id|**int**|ステップが実行されている場所です。|配布スコープではないノードスコープで実行される要求の場合は、-1 に設定します。|  
|status|**nvarchar(32)**|この手順の状態|アクティブ、キャンセル、完了、失敗、キューに登録済み|  
|error_id|**nvarchar (36)**|このステップに関連付けられているエラーの一意の id (存在する場合)|エラーが発生しなかった場合は、「id of [sys. dm_exec_compute_node_errors &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md)」を参照してください。|  
|start_time|**datetime**|ステップが実行を開始した時刻|小さいまたは現在の時刻に等しいが、このステップが属するクエリの end_compile_time 以上です。|  
|end_time|**datetime**|このステップの実行が完了した時刻。が取り消されたか、失敗しました。|小または現在の時刻に等しいか start_time 以上で、現在実行中またはキューに置かれているステップに対して NULL に設定されます。|  
|total_elapsed_time|**int**|クエリステップが実行されていた合計時間 (ミリ秒)|0 ~ end_time と start_time の差。 キューに登録されたステップの場合は0。|  
|row_count|**bigint**|この要求によって変更または返された行の合計数|データが変更または返されなかったステップの場合は0。それ以外の場合は、影響を受けた行の数。 DMS ステップの場合は-1 に設定します。|  
|調べる|**int**|クエリの配布を実行している SQL Server インスタンスのセッション id||  
|コマンドを使用します|nvarchar(4000)|このステップのコマンドの完全なテキストを保持します。|ステップの任意の有効な要求文字列。 4000文字を超える場合は切り捨てられます。|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューを使用した PolyBase のトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;データベース関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
