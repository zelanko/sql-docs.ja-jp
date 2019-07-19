---
title: sys.dm_exec_external_work (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 049bf084381adaa0bf7e817eb7ae3bdb24feb118
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097755"
---
# <a name="sysdmexecexternalwork-transact-sql"></a>sys.dm_exec_external_work (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  各コンピューティング ノード上のワーカーごとのワークロードに関する情報を返します。  
  
 外部データ ソース (例: Hadoop または外部の SQL Server) との通信にスピンアップして作業を識別するために sys.dm_exec_external_work をクエリします。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|関連付けられている PolyBase クエリの一意の識別子。|参照してください*request_ID*で[sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)します。|  
|step_index|**int**|このワーカーが実行して、要求。|参照してください*step_index*で[sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)します。|  
|dms_step_index|**int**|このワーカーを実行している DMS プランのステップします。|参照してください[sys.dm_exec_dms_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)します。|  
|compute_node_id|**int**|ノード、ワーカーがで実行されています。|参照してください[sys.dm_exec_compute_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)します。|  
|type|**nvarchar(60)**|外部の作業の種類。|ファイルの分割 '|  
|work_id|**int**|実際の分割の ID。|大きいまたは 0。|  
|input_name|**nvarchar (4000)**|読み取るへの入力の名前|Hadoop を使用する場合は、ファイル名。|  
|read_location|**bigint**|オフセットまたは場所を読み取る。|読み取るファイルのオフセット。|  
|bytes_processed|**bigint**|このワーカーによって処理された合計バイト数。|大きいまたは 0。|  
|長さ|**bigint**|Split または Hadoop が発生した場合、HDFS ブロックの長さ|ユーザー定義が可能です。 既定値は 64 M です。|  
|status|**nvarchar(32)**|ワーカーの状態|保留中、処理、完了、失敗した、中止されました|  
|start_time|**datetime**|作業の開始||  
|end_time|**datetime**|作業の終了||  
|total_elapsed_time|**int**|合計時間 (ミリ秒)||  
  
## <a name="see-also"></a>関連項目  
 [PolyBase 動的管理ビューでのトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
