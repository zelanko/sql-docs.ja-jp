---
title: sys.dm_exec_query_resource_semaphores (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dca59c6557e951922fa19ebd95526aab5149b9fd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecqueryresourcesemaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のクエリのリソース セマフォの状態に関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 **sys.dm_exec_query_resource_semaphores**一般的なクエリ実行メモリの状態を提供し、システムがメモリ不足のためにアクセスできるかどうかを判断することができます。 このビューから取得されるメモリ情報を補完するもの[sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)をサーバーのメモリ状態の完全な図を提供します。 **sys.dm_exec_query_resource_semaphores**小さなクエリのリソース セマフォの別の行と、標準リソース セマフォの 1 つの行を返します。 これには、小さなクエリ セマフォの 2 つの要件があります。  
  
-   要求されたメモリ許可が 5 MB 未満にする必要があります。  
  
-   クエリのコストが 3 より小さいコスト単位にする必要があります。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_exec_query_resource_semaphores**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|リソース セマフォの非一意の ID。 標準リソース セマフォの場合は 0、小さなクエリのリソース セマフォの場合は 1 です。|  
|**target_memory_kb**|**bigint**|許可使用対象メモリ (KB 単位)。|  
|**max_target_memory_kb**|**bigint**|最大許容対象メモリ (KB 単位)。 小さなクエリのリソース セマフォの場合は NULL になります。|  
|**total_memory_kb**|**bigint**|リソース セマフォで保持されるメモリ (KB 単位)。 システム メモリが不足またはメモリが頻繁に許可されている最小を強制された場合、この値がより大きくすることができます、 **target_memory_kb**または**max_target_memory_kb**値。 合計メモリは、使用可能メモリと許可されているメモリの合計です。|  
|**available_memory_kb**|**bigint**|新しい許可で使用可能なメモリ (KB 単位)。|  
|**granted_memory_kb**|**bigint**|許可されているメモリの合計 (KB 単位)。|  
|**used_memory_kb**|**bigint**|許可されているメモリの中で物理的に使用される部分 (KB 単位)。|  
|**grantee_count**|**int**|許可条件が満たされているアクティブ クエリの数。|  
|**waiter_count**|**int**|許可条件が満たされるのを待機しているクエリの数。|  
|**timeout_error_count**|**bigint**|サーバーが起動した後のタイムアウト エラーの合計数。 小さなクエリのリソース セマフォの場合は NULL になります。|  
|**forced_grant_count**|**bigint**|サーバーが起動した後の強制的な最小メモリ許可の合計数。 小さなクエリのリソース セマフォの場合は NULL になります。|  
|**pool_id**|**int**|このリソース セマフォが属しているリソース プールの ID。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="remarks"></a>解説  
 ORDER BY または集計を含む動的管理ビューを使用するクエリではメモリの使用量が増える場合があり、それによってトラブルシューティングが必要な問題が発生する可能性があります。  
  
 使用して**sys.dm_exec_query_resource_semaphores**トラブルシューティングのためにはの将来のバージョンを使用するアプリケーションでは含まれません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 データベース管理者は、リソース ガバナー機能を使用することで、サーバー リソースを最大 64 個までのリソース プールに分散できます。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、各プールが小規模の独立したサーバー インスタンスのように動作し、2 つのセマフォを必要とします。  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


