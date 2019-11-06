---
title: sys.dm_os_memory_nodes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7d1be540f73a5a5e625a1f33f1c3f24e409fd307
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265764"
---
# <a name="sysdmosmemorynodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  内部的な割り当て[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ マネージャー。 プロセス メモリ カウンター間の差を追跡**sys.dm_os_process_memory**内部カウンターは、外部コンポーネントからメモリ使用量を示すことができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ領域です。  
  
 ノードは、物理 NUMA メモリ ノードごとに作成されます。 これらは CPU のノードから異なる可能性があります**sys.dm_os_nodes**します。  
  
 Windows メモリ割り当てルーチンを介して直接実行された割り当ては追跡されません。 次の表を使用してのみ実行されるメモリ割り当てに関する情報を提供する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ マネージャー インターフェイス。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_memory_nodes**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|メモリ ノードの ID を指定します。 関連する**memory_node_id**の**sys.dm_os_memory_clerks**します。 Null を許容しません。|  
|**virtual_address_space_reserved_kb**|**bigint**|コミットも物理ページへのマップをキロバイト (KB) 単位での仮想アドレスの予約の数を示します。 Null を許容しません。|  
|**virtual_address_space_committed_kb**|**bigint**|サポート技術情報、コミットまたは物理ページへのマップが済んでいる仮想アドレスの量を指定します。 Null を許容しません。|  
|**locked_page_allocations_kb**|**bigint**|物理メモリの量を指定します (kb 単位) によってロックされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 Null を許容しません。|  
|**single_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> サポート技術情報、単一ページ アロケーターを使用して、このノードで実行中のスレッドが割り当てられる、コミット済みメモリの量。 このメモリは、バッファー プールから割り当てられます。 この値は、割り当て要求が発生したノード、割り当て要求が満たされた物理的な場所ではなくを示します。|  
|**pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> メモリ マネージャー ページ アロケーターによってこの NUMA ノードから割り当てられる、コミット済みのメモリ量 (KB 単位) を指定します。 Null を許容しません。|  
|**multi_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> このノード上で実行されているスレッドが複数ページ アロケーターを使って割り当てたコミット済みのメモリ量 (KB 単位)。 このメモリは、バッファー プール外から割り当てられます。 この値は、割り当て要求が発生したノード、割り当て要求が満たされた物理的な場所ではなくを示します。|  
|**shared_memory_reserved_kb**|**bigint**|このノードから予約されている、サポート技術情報の共有メモリの量を指定します。 Null を許容しません。|  
|**shared_memory_committed_kb**|**bigint**|このノードでコミットされた共有メモリの量 (KB 単位) を指定します。 Null を許容しません。|  
|**cpu_affinity_mask**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 内部使用のみです。 Null を許容しません。|  
|**online_scheduler_mask**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 内部使用のみです。 Null を許容しません。|  
|**processor_group**|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 内部使用のみです。 Null を許容しません。|  
|**foreign_committed_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> (Kb 単位) の他のメモリ ノードからコミットされたメモリの量を指定します。 Null を許容しません。|  
|**target_kb** |**bigint** |**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]。<br /><br /> メモリ ノードは、メモリの目標を指定します (KB 単位)。 |   
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

## <a name="see-also"></a>関連項目  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


