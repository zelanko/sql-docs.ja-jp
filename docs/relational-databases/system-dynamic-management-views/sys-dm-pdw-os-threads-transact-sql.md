---
description: sys.dm_pdw_os_threads (Transact-sql)
title: sys.dm_pdw_os_threads (Transact-sql) |Microsoft Docs
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: ab7974ad344765d567d7b7fdb62d6e1b71d20892
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440760"
---
# <a name="sysdm_pdw_os_threads-transact-sql"></a>sys.dm_pdw_os_threads (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|影響を受けるノードの ID。<br /><br /> このビューのキーは pdw_node_id と thread_id によって形成されます。|[Transact-sql&#41;&#40;sys.dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|thread_id|**int**|このビューのキーは pdw_node_id と thread_id によって形成されます。||  
|process_id|**int**|||  
|name|**nvarchar (255)**|||  
|priority|**int**|||  
|start_time|**datetime**|||  
|state|**nvarchar(32)**|||  
|wait_reason|**nvarchar(32)**|||  
|total_processor_elapsed_time|**bigint**|スレッドによって使用されたカーネル時間の合計。||  
|total_user_elapsed_time|**bigint**|スレッドによって使用された合計ユーザー時間||  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics と並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
