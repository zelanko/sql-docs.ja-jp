---
title: dm_pdw_os_threads (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ddc12f05-edeb-4848-b6d7-e851684cf044
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a4b9028d30db3c36157ef3db628dcb7c1cbeda00
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899228"
---
# <a name="sysdm_pdw_os_threads-transact-sql"></a>dm_pdw_os_threads (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|影響を受けるノードの ID。<br /><br /> このビューのキーは pdw_node_id と thread_id によって形成されます。|『 [Transact-sql&#41;&#40;dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|thread_id|**int**|このビューのキーは pdw_node_id と thread_id によって形成されます。||  
|process_id|**int**|||  
|name|**nvarchar(255)**|||  
|priority|**int**|||  
|start_time|**datetime**|||  
|state|**nvarchar(32)**|||  
|wait_reason|**nvarchar(32)**|||  
|total_processor_elapsed_time|**bigint**|スレッドによって使用されたカーネル時間の合計。||  
|total_user_elapsed_time|**bigint**|スレッドによって使用された合計ユーザー時間||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
