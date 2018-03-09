---
title: "sys.dm_pdw_dms_workers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aac00b2fd1ba5a5922c2618ccfadad6fc2d2b8ac
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  DMS の手順を実行するすべての作業者に関する情報を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この DMS ワーカーの一部であることをクエリします。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Request_id 内を参照してください[sys.dm_pdw_exec_requests &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)。|  
|step_index|**int**|DMS ワーカーの一部である手順のクエリを実行します。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Step_index を参照してください[sys.dm_pdw_request_steps &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|dms_step_index|**int**|このワーカーが実行されている DMS プランのステップします。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。||  
|pdw_node_id|**int**|ワーカーが実行されているノードです。|Node_id を参照してください[sys.dm_pdw_nodes &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)。|  
|distribution_id|**Int**|作業者が存在する場合、実行している配布します。|Distribution_id を参照してください[sys.pdw_distributions &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md)。|  
|型|**nvarchar(32)**|このエントリが表す DMS のワーカー スレッドの種類です。|'DIRECT_CONVERTER'、'DIRECT_READER'、'FILE_READER'、'HASH_CONVERTER'、'HASH_READER'、'ROUNDROBIN_CONVERTER'、'EXPORT_READER'、'EXTERNAL_READER'、'EXTERNAL_WRITER'、'PARALLEL_COPY_READER'、'REJECT_WRITER'、'ライター'|  
|ステータス|**nvarchar(32)**|DMS ワーカーの状態です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|最後の 1 秒間の読み取りまたは書き込みのスループット。|以上の値を 0 にします。 クエリが取り消されましたかワーカーを実行する前に、失敗した場合は NULL です。|  
|bytes_processed|**bigint**|このワーカーによって処理された合計バイト数。|以上の値を 0 にします。 クエリが取り消されましたかワーカーを実行する前に、失敗した場合は NULL です。|  
|rows_processed|**bigint**|行の読み取りや書き込みのワーカーの数。|以上の値を 0 にします。 クエリが取り消されましたかワーカーを実行する前に、失敗した場合は NULL です。|  
|start_time|**datetime**|このワーカーの実行の開始時刻。|以上のクエリに、開始時刻には、このワーカーに属しています。 参照してください[sys.dm_pdw_request_steps &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|end_time|**datetime**|実行が終了した、失敗、または時刻が取り消されたです。|継続的なまたはキューに置かれた作業者の NULL を表します。 それ以外の場合、start_time より大きい。|  
|total_elapsed_time|**int**|時間の合計は、ミリ秒単位での実行に費やされました。|以上の値を 0 にします。<br /><br /> 時間の合計には、システムを起動または再起動からが経過しました。 Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|cpu_time|**bigint**|CPU 時間をミリ秒単位で、このワーカーによって消費されています。|以上の値を 0 にします。|  
|query_time|**int**|SQL までの期間は、ミリ秒単位でのスレッドに行を返すを開始します。|以上の値を 0 にします。|  
|buffers_available|**int**|使用されていないバッファーの数。| クエリが取り消されましたかワーカーを実行する前に、失敗した場合は NULL です。|  
|sql_spid|**int**|この DMS ワーカーの処理を実行する SQL Server インスタンス上のセッション id です。||  
|dms_cpid|**int**|実際に実行しているスレッドのプロセス ID。||  
|error_id|**nvarchar(36)**|存在する場合は、ワーカーの実行中に発生したエラーの一意の識別子。|Error_id を参照してください[sys.dm_pdw_request_steps &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|source_info|**nvarchar (4000)**|リーダー、ソース テーブルと列の仕様では。||  
|destination_info|**nvarchar (4000)**|ライターの場合、変換先テーブルの仕様です。||  
  
 このビューで保持される最大行数のについては、次を参照してください。[システム ビューの最大値](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)です。  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
