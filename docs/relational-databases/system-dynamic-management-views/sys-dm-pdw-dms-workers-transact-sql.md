---
title: sys.dm_pdw_dms_workers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c46c6b83d820d7c970d16e2e84a3a81a0e07b340
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36925913"
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  DMS の手順を実行するすべての作業者に関する情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この DMS ワーカーの一部であることをクエリします。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Request_id 内を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|step_index|**int**|DMS ワーカーの一部である手順のクエリを実行します。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Step_index を参照してください。 [sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)します。|  
|dms_step_index|**int**|このワーカーが実行されている DMS プランのステップします。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。||  
|pdw_node_id|**int**|ワーカーが実行されているノードです。|Node_id を参照してください。 [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)します。|  
|distribution_id|**Int**|作業者が存在する場合、実行している配布します。|Distribution_id を参照してください。 [sys.pdw_distributions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md)します。|  
|type|**nvarchar(32)**|このエントリが表す DMS のワーカー スレッドの種類です。|'DIRECT_CONVERTER'、'DIRECT_READER'、'FILE_READER'、'HASH_CONVERTER'、'HASH_READER'、'ROUNDROBIN_CONVERTER'、'EXPORT_READER'、'EXTERNAL_READER'、'EXTERNAL_WRITER'、'PARALLEL_COPY_READER'、'REJECT_WRITER'、'ライター'|  
|status|**nvarchar(32)**|DMS ワーカーの状態です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|最後の 1 秒間の読み取りまたは書き込みのスループット。|以上の値を 0 にします。 クエリが取り消されたまたは、ワーカーが実行前に、失敗した場合は NULL します。|  
|bytes_processed|**bigint**|このワーカーによって処理された合計バイト数。|以上の値を 0 にします。 クエリが取り消されたまたは、ワーカーが実行前に、失敗した場合は NULL します。|  
|rows_processed|**bigint**|行の読み取りや書き込みのワーカーの数。|以上の値を 0 にします。 クエリが取り消されたまたは、ワーカーが実行前に、失敗した場合は NULL します。|  
|start_time|**datetime**|このワーカーの実行の開始時刻。|以上のクエリに、開始時刻には、このワーカーに属しています。 参照してください[sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)します。|  
|end_time|**datetime**|実行が終了した、失敗、または時刻が取り消されたです。|継続的なまたはキューに置かれた作業者の NULL を表します。 それ以外の場合、start_time より大きい。|  
|total_elapsed_time|**int**|時間の合計は、ミリ秒単位での実行に費やされました。|以上の値を 0 にします。<br /><br /> 時間の合計には、システムを起動または再起動からが経過しました。 Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|cpu_time|**bigint**|CPU 時間をミリ秒単位で、このワーカーによって消費されています。|以上の値を 0 にします。|  
|query_time|**int**|SQL までの期間は、ミリ秒単位でのスレッドに行を返すを開始します。|以上の値を 0 にします。|  
|buffers_available|**int**|使用されていないバッファーの数。| クエリが取り消されたまたは、ワーカーが実行前に、失敗した場合は NULL します。|  
|sql_spid|**int**|この DMS ワーカーの処理を実行する SQL Server インスタンス上のセッション id です。||  
|dms_cpid|**int**|実際に実行しているスレッドのプロセス ID。||  
|error_id|**nvarchar(36)**|存在する場合は、ワーカーの実行中に発生したエラーの一意の識別子。|Error_id を参照してください。 [sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)します。|  
|source_info|**nvarchar (4000)**|リーダー、ソース テーブルと列の仕様では。||  
|destination_info|**nvarchar (4000)**|ライターの場合、変換先テーブルの仕様です。||  
  
 このビューで保持される最大行数は、詳細については、次を参照してください。[システム ビューの最大値](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)します。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
