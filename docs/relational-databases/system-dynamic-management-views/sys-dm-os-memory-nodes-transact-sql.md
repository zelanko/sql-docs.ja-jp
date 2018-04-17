---
title: sys.dm_os_memory_nodes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2017
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
- dm_os_memory_nodes_TSQL
- sys.dm_os_memory_nodes
- sys.dm_os_memory_nodes_TSQL
- dm_os_memory_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_nodes dynamic management view
ms.assetid: bf4032fe-7db1-40e9-a62e-d69cebff4b44
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 91f30ee2c8a11c936480658af3c8ee0a4ddbf973
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmosmemorynodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  内部的な割り当て[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ マネージャー。 プロセス メモリ カウンター間の違いを追跡**sys.dm_os_process_memory**内部カウンター内の外部コンポーネントからメモリの使用を示すことができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ領域です。  
  
 ノードは、物理 NUMA メモリ ノードごとに作成されます。 これらの CPU ノードで異なる場合があります**sys.dm_os_nodes**です。  
  
 Windows メモリ割り当てルーチンを介して直接実行された割り当ては追跡されません。 次の表を使用してのみ実行されるメモリ割り当てに関する情報を提供する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ マネージャー インターフェイスです。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_memory_nodes**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|メモリ ノードの ID を指定します。 関連する**memory_node_id**の**sys.dm_os_memory_clerks**です。 Null を許容しません。|  
|**virtual_address_space_reserved_kb**|**bigint**|コミットも物理ページへのマップもされていない仮想アドレスの予約サイズ (KB 単位) を指定します。 Null を許容しません。|  
|**virtual_address_space_committed_kb**|**bigint**|コミットまたは物理ページへのマップが済んでいる仮想アドレスのサイズ (KB 単位) を指定します。 Null を許容しません。|  
|**locked_page_allocations_kb**|**bigint**|物理メモリの量を指定します (kb 単位) によってロックされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 Null を許容しません。|  
|**single_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> このノード上で実行されているスレッドが単一ページ アロケーターを使って割り当てたコミット済みのメモリ量 (KB 単位)。 このメモリは、バッファー プールから割り当てられます。 この値は、割り当て要求が満たされた物理的な場所ではなく、割り当て要求元のノードを示します。|  
|**pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> メモリ マネージャー ページ アロケーターによってこの NUMA ノードから割り当てられる、コミット済みのメモリ量 (KB 単位) を指定します。 Null を許容しません。|  
|**multi_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> このノード上で実行されているスレッドが複数ページ アロケーターを使って割り当てたコミット済みのメモリ量 (KB 単位)。 このメモリは、バッファー プール外から割り当てられます。 この値は、割り当て要求が発生したノード、割り当て要求が満たされた物理的な場所ではなくを示します。|  
|**shared_memory_reserved_kb**|**bigint**|このノードから予約された共有メモリの量 (KB 単位) を指定します。 Null を許容しません。|  
|**shared_memory_committed_kb**|**bigint**|このノードでコミットされた共有メモリの量 (KB 単位) を指定します。 Null を許容しません。|  
|**cpu_affinity_mask**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 内部使用のみです。 Null を許容しません。|  
|**online_scheduler_mask**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 内部使用のみです。 Null を許容しません。|  
|**processor_group**|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 内部使用のみです。 Null を許容しません。|  
|**foreign_committed_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 他のメモリ ノードからコミットされたメモリの量 (KB 単位) を指定します。 Null を許容しません。|  
|**target_kb** |**bigint** |**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]。<br /><br /> メモリ ノードは、メモリの目標を指定します (KB 単位)。 |   
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


