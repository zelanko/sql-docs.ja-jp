---
title: "sys.dm_os_nodes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cf36f7156f9297231fc232e8fecafee5e77427c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosnodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  SQLOS という内部コンポーネントは、ハードウェア プロセッサの局所性を疑似的に表現したノード構造を作成します。 これらの構造をソフト NUMA を使って変更することで、カスタム ノード レイアウトを作成できます。  
  
 次の表では、これらのノードに関する情報を示します。  
  
> **注:**この DMV からの呼び出しに[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_nodes**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|ノードの ID。|  
|node_state_desc|**nvarchar (256)**|ノード状態の説明。 相互排他的な値から先に表示され、続けて、組み合わせ可能な値が表示されます。 例:<br /><br /> Online、Thread Resources Low、Lazy Preemptive<br /><br /> 次の 4 つの相互に排他的な node_state_desc 値があります。 これらは、その説明を以下に示します。<br /><br /> ノードがオンラインでオンラインにします。<br /><br /> ノードがオフライン オフラインです。<br /><br /> アイドル状態: ノードは、保留中の作業要求を持たずがアイドル状態になりました。<br /><br /> IDLE_READY: ノードは、保留中の作業要求を持たずをアイドル状態に移行する準備ができました。<br /><br /> その説明を以下に示す 5 つの組み合わせ可能な node_state_desc 値。<br /><br /> DAC: このノードは、専用管理者接続の予約されています。<br /><br /> THREAD_RESOURCES_LOW: 新しいスレッドを作成できませんこのノード上でメモリ不足の状態が原因です。<br /><br /> ホット追加されました。 は、ノードがへの応答に追加されたことを示します、ホット アド CPU イベント。|  
|memory_object_address|**varbinary (8)**|このノードに関連付けられているメモリ オブジェクトのアドレス。 sys.dm_os_memory_objects.memory_object_address と一対一の関係にあります。|  
|memory_clerk_address|**varbinary (8)**|このノードに関連付けられているメモリ クラークのアドレス。 sys.dm_os_memory_clerks.memory_clerk_address と一対一の関係にあります。|  
|io_completion_worker_address|**varbinary (8)**|このノードの IO 完了に割り当てられているワーカーのアドレス。 sys.dm_os_workers.worker_address と一対一の関係にあります。|  
|memory_node_id|**smallint**|このノードが属しているメモリ ノードの ID。 sys.dm_os_memory_nodes.memory_node_id と多対一の関係にあります。|  
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
|pdw_node_id|**int**|この分布はでは、ノードの識別子。<br /><br /> **適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
  
## <a name="see-also"></a>参照  
  
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [ソフト NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  


