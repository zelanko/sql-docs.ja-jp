---
title: sys.dm_pdw_dms_external_work (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
caps.latest.revision: 5
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 95e5165f7194e02374753443bd9a7ef120709b4c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 外部の操作のすべてのデータ移動サービス (DM) ステップに関する情報を保持するシステム ビュー。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この DMS ワーカーを使用しているクエリ。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Request_id 内と同じ[sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)です。|  
|step_index|**int**|次の手順をこの DMS ワーカーを呼び出しているクエリです。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Step_index と同じ[sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)です。|  
|dms_step_index|**int**|DMS プランの現在の手順です。<br /><br /> request_id、step_index、および dms_step_index は、このビューのキーを形成します。|Dms___step_index と同じ[sys.dm_pdw_dms_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md)です。|  
|pdw_node_id|**int**|DMS ワーカーを実行しているノードです。|Node_id 内と同じ[sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)です。|  
|型|**nvarchar(60)**|このノードが実行されている外部の操作の種類。<br /><br /> ファイルの分割は、複数の小さいまでに分割されている外部の Hadoop ファイルに操作です。|' ファイルの分割 '|  
|work_id|**int**|ファイルの分割の id。|以上の値を 0 にします。<br /><br /> コンピューティング ノードごとに一意です。|  
|input_name|**nvarchar(60)**|読み取られている入力の名前の文字列を指定します。|Hadoop ファイルでは、これには、Hadoop のファイル名です。|  
|read_location|**bigint**|読み取り位置をオフセットします。||  
|estimated_bytes_processed|**bigint**|このワーカーによって処理されるバイト数。|以上の値を 0 にします。|  
|length|**bigint**|分割、ファイル内のバイト数。<br /><br /> Hadoop は、これには、HDFS のブロックのサイズです。|ユーザー定義です。 既定値は、64 MB です。|  
|ステータス|**nvarchar(32)**|ワーカーの状態です。|保留中で、処理、完了、失敗した、中止されました|  
|start_time|**datetime**|このワーカーの実行の開始時刻。|以上のクエリに、開始時刻には、このワーカーに属しています。 参照してください[sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)です。|  
|end_time|**datetime**|実行が終了した、失敗、または時刻が取り消されたです。|継続的なまたはキューに置かれた作業者の NULL を表します。 それ以外の場合、start_time より大きい。|  
|total_elapsed_time|**int**|時間の合計は、ミリ秒単位での実行に費やされました。|以上の値を 0 にします。<br /><br /> Total_elapsed_time では、整数の最大値を超えると、total_elapsed_time 引き続き、最大値になります。 この状態が「、最大値を超過しました」警告を生成します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
  
 このビューで保持される最大行数のについては、次を参照してください。[システム ビューの最大値](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)です。  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
