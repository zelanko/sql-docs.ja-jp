---
title: sys.dm_exec_query_parallel_workers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
caps.latest.revision: 1
author: pelopes
ms.author: pelopes
manager: ajayj
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f2bc4634a5e2fddb4a3c8eda009eb28019089596
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036310"
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>sys.dm_exec_query_parallel_workers (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  1 つのノードには、ワーカーの可用性情報を返します。  
  
|名前|データ型|説明|  
|----------|---------------|-----------------|  
|**node_id**|**int**|NUMA ノード id。|  
|**scheduler_count**|**int**|このノード上のスケジューラの数。|  
|**max_worker_count**|**int**|並列クエリのワーカーの最大数。|  
|**reserved_worker_count**|**int**|並列クエリは、によって予約されているワーカーの数とすべての要求で使用されるメインのワーカーの数。| 
|**free_worker_count**|**int**|タスクの使用可能なワーカーの数。<br /><br />**注:** すべての受信要求は、空いているワーカーの数から減算されます、1 つ以上のワーカーを使用します。  無料のワーカーの数は負荷の高いサーバーで負の数値であることことができます。| 
|**used_worker_count**|**int**|並列クエリで使用されるワーカーの数。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
 
## <a name="examples"></a>使用例  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. 現在の並列ワーカーの可用性を表示します。  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
