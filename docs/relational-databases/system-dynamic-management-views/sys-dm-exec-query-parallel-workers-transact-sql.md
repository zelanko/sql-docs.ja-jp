---
title: "sys.dm_exec_query_parallel_workers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: pelopes
ms.author: pelopes
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 99165e38dc4f1ad0b25a754f2c0f38b4ae413e84
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>sys.dm_exec_query_parallel_workers (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  1 つのノードには、ワーカーの可用性情報を返します。  
  
|名前|データ型|Description|  
|----------|---------------|-----------------|  
|**node_id**|**int**|NUMA ノードの id。|  
|**scheduler_count**|**int**|このノード上のスケジューラの数です。|  
|**max_worker_count**|**int**|並列クエリのワーカーの最大数。|  
|**reserved_worker_count**|**int**|並列クエリは、によって予約されているワーカーの数とすべての要求で使用されるメインのワーカーの数。| 
|**free_worker_count**|**int**|タスクの使用可能なワーカーの数。<br /><br />**注:**すべての受信要求を消費に少なくとも 1 つのワーカーは、空いているワーカー カウントから減算されます。  空いているワーカーの数が負荷の高いサーバーに負の数を指定できます。| 
|**used_worker_count**|**int**|並列クエリで使用しているワーカーの数。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
  [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. 現在の並列ワーカーの可用性を表示します。  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_workers &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
