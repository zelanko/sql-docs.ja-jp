---
title: sys.dm_os_nodes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/13/2018
ms.prod: sql-non-specified
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
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: baf6754510cc1881819317e00cd40ea1be3c886e
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmosnodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

SQLOS という内部コンポーネントは、ハードウェア プロセッサの局所性を疑似的に表現したノード構造を作成します。 これらの構造体を使用して変更することができます[ソフト NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md)カスタム ノード レイアウトを作成します。  

> [!NOTE]
> 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]特定のハードウェア構成のソフト NUMA は自動的に使用します。 詳細については、次を参照してください。[自動ソフト NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa)です。
  
次の表では、これらのノードに関する情報を示します。  
  
> [!NOTE]
> この DMV からの呼び出しに[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_nodes**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|ノードの ID。|  
|node_state_desc|**nvarchar (256)**|ノード状態の説明。 相互排他的な値から先に表示され、続けて、組み合わせ可能な値が表示されます。 以下に例を示します。<br /> Online、Thread Resources Low、Lazy Preemptive<br /><br />次の 4 つの相互に排他的な node_state_desc 値があります。 これらは、その説明を以下に示します。<br /><ul><li>ノードがオンラインでオンラインにします。<li>ノードがオフライン オフラインです。<li>アイドル状態: ノードは、保留中の作業要求を持たずがアイドル状態になりました。<li>IDLE_READY: ノードは、保留中の作業要求を持たずをアイドル状態に移行する準備ができました。</li></ul><br />その説明を以下に示す 3 つの組み合わせ可能な node_state_desc 値。<br /><ul><li>DAC: このノードの予約されています、[専用管理者接続](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)です。<li>THREAD_RESOURCES_LOW: 新しいスレッドを作成できませんこのノード上でメモリ不足の状態が原因です。<li>ホット追加されました。 は、ノードがへの応答に追加されたことを示します、ホット アド CPU イベント。</li></ul>|  
|memory_object_address|**varbinary(8)**|このノードに関連付けられているメモリ オブジェクトのアドレス。 一対一の関係に[sys.dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).memory_object_address です。|  
|memory_clerk_address|**varbinary(8)**|このノードに関連付けられているメモリ クラークのアドレス。 一対一の関係に[sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).memory_clerk_address です。|  
|io_completion_worker_address|**varbinary(8)**|このノードの IO 完了に割り当てられているワーカーのアドレス。 一対一の関係に[sys.dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).worker_address です。|  
|memory_node_id|**smallint**|このノードが属しているメモリ ノードの ID。 多対一の関係に[sys.dm_os_memory_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md).memory_node_id です。|  
|cpu_affinity_mask|**bigint**|このノードに関連付けられている CPU を識別するビットマップ。|  
|online_scheduler_count|**smallint**|このノードによって管理されるオンライン スケジューラの数です。|  
|idle_scheduler_count|**smallint**|アクティブなワーカーの存在しないオンライン スケジューラの数。|  
|active_worker_count|**int**|このノードによって管理されるすべてのスケジューラ上のアクティブ ワーカーの数。|  
|avg_load_balance|**int**|このノード上のスケジューラあたりの平均タスク数。|  
|timer_task_affinity_mask|**bigint**|タイマー タスクの割り当てが可能なスケジューラを識別するビットマップ。|  
|permanent_task_affinity_mask|**bigint**|永続的なタスクの割り当てが可能なスケジューラを識別するビットマップ。|  
|resource_monitor_state|**bit**|各ノードには、1 つのリソース モニターが割り当てられます。 リソース モニターの状態には、実行中とアイドル状態とがあります。 1 は実行中を、0 はアイドル状態を表します。|  
|online_scheduler_mask|**bigint**|このノードのプロセス関係マスクを識別します。|  
|processor_group|**smallint**|このノードのプロセッサ グループを識別します。|  
|cpu_count |**int** |このノードで利用できる Cpu の数。 |
|pdw_node_id|**int**|この分布はでは、ノードの識別子。<br /><br /> **適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="see-also"></a>参照    
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [ソフト NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
