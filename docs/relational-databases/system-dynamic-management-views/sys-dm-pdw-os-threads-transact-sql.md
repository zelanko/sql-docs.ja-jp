---
title: "sys.dm_pdw_os_threads (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: ddc12f05-edeb-4848-b6d7-e851684cf044
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ca9c5f015c5818348de45d69df84416ca8a2b25
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwosthreads-transact-sql"></a>sys.dm_pdw_os_threads (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|影響を受けるノードの ID。<br /><br /> pdw_node_id と thread_id は、このビューのキーを形成します。|Node_id を参照してください[sys.dm_pdw_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|thread_id|**int**|pdw_node_id と thread_id は、このビューのキーを形成します。||  
|process_id|**int**|||  
|name|**nvarchar (255)**|||  
|priority|**int**|||  
|start_time|**datetime**|||  
|state|**nvarchar (32)**|||  
|wait_reason|**nvarchar (32)**|||  
|total_processor_elapsed_time|**bigint**|カーネルの総時間がスレッドで使用します。||  
|total_user_elapsed_time|**bigint**|スレッドによって使用される合計ユーザー時間||  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
