---
title: sys.dm_exec_query_resource_semaphores (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_query_resource_semaphores_TSQL
- dm_exec_query_resource_semaphores_TSQL
- sys.dm_exec_query_resource_semaphores
- dm_exec_query_resource_semaphores
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_resource_semaphores dynamic management view
ms.assetid: e43a2aa9-dd52-4c89-911e-1a7d05f7ffbb
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5022c31d73fd610fb7aa14978819b702f4562499
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617920"
---
# <a name="sysdmexecqueryresourcesemaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のクエリのリソース セマフォの状態に関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 **sys.dm_exec_query_resource_semaphores**一般的なクエリ実行メモリの状態を示し、システムが十分なメモリにアクセスできるかどうかを判断することができます。 このビューから取得されるメモリ情報を補完する[sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)をサーバー メモリの状態の全体像を提供します。 **sys.dm_exec_query_resource_semaphores**小さなクエリのリソース セマフォに関する 1 行と、標準リソース セマフォの 1 つの行を返します。 これには、小さなクエリ セマフォの 2 つの要件があります。  
  
-   要求されたメモリ許可が 5 MB 未満にする必要があります。  
  
-   クエリのコストが 3 より小さいコスト単位にする必要があります。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_exec_query_resource_semaphores**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|リソース セマフォの非一意の ID。 標準リソース セマフォの場合は 0、小さなクエリのリソース セマフォの場合は 1 です。|  
|**target_memory_kb**|**bigint**|許可使用対象メモリ (KB 単位)。|  
|**max_target_memory_kb**|**bigint**|最大許容対象メモリ (KB 単位)。 小さなクエリのリソース セマフォの場合は NULL になります。|  
|**total_memory_kb**|**bigint**|リソース セマフォで保持されるメモリ (KB 単位)。 システムがメモリ不足、またはメモリが頻繁に許可された強制的な最小の場合、この値がより大きくすることができます、 **target_memory_kb**または**max_target_memory_kb**値。 合計メモリは、使用可能メモリと許可されているメモリの合計です。|  
|**available_memory_kb**|**bigint**|新しい許可で使用可能なメモリ (KB 単位)。|  
|**granted_memory_kb**|**bigint**|許可されているメモリの合計 (KB 単位)。|  
|**used_memory_kb**|**bigint**|許可されているメモリの中で物理的に使用される部分 (KB 単位)。|  
|**grantee_count**|**int**|許可条件が満たされているアクティブ クエリの数。|  
|**waiter_count**|**int**|許可条件が満たされるのを待機しているクエリの数。|  
|**timeout_error_count**|**bigint**|サーバーが起動した後のタイムアウト エラーの合計数。 小さなクエリのリソース セマフォの場合は NULL になります。|  
|**forced_grant_count**|**bigint**|サーバーが起動した後の強制的な最小メモリ許可の合計数。 小さなクエリのリソース セマフォの場合は NULL になります。|  
|**pool_id**|**int**|このリソース セマフォが属しているリソース プールの ID。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
  
## <a name="remarks"></a>コメント  
 ORDER BY または集計を含む動的管理ビューを使用するクエリではメモリの使用量が増える場合があり、それによってトラブルシューティングが必要な問題が発生する可能性があります。  
  
 使用して、 **sys.dm_exec_query_resource_semaphores**トラブルシューティングのための将来のバージョンを使用するアプリケーションでは含まれませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 データベース管理者は、リソース ガバナー機能を使用することで、サーバー リソースを最大 64 個までのリソース プールに分散できます。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、各プールが小規模の独立したサーバー インスタンスのように動作し、2 つのセマフォを必要とします。  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


