---
title: sys.dm_os_memory_objects (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_objects
- sys.dm_os_memory_objects
- sys.dm_os_memory_objects_TSQL
- dm_os_memory_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_objects dynamic management view
ms.assetid: 5688bcf8-5da9-4ff9-960b-742b671d7096
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ca3a6a8891e74bd795f15e9a374194650e70b197
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265750"
---
# <a name="sysdmosmemoryobjects-transact-sql"></a>sys.dm_os_memory_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって割り当てられているメモリ オブジェクトを返します。 使用することができます**sys.dm_os_memory_objects**メモリ使用量を分析し、可能なメモリを識別するためにリークが発生します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**memory_object_address**|**varbinary(8)**|メモリ オブジェクトのアドレス。 NULL 値は許可されません。|  
|**parent_address**|**varbinary(8)**|親メモリ オブジェクトのアドレス。 NULL 値が許可されます。|  
|**pages_allocated_count**|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> メモリ オブジェクトによって割り当てられているページ数。 NULL 値は許可されません。|  
|**pages_in_bytes**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> メモリ オブジェクトのインスタンスによって割り当てられるメモリの量 (バイト単位)。 NULL 値は許可されません。|  
|**creation_options**|**int**|内部使用のみです。 NULL 値が許可されます。|  
|**bytes_used**|**bigint**|内部使用のみです。 NULL 値が許可されます。|  
|**type**|**nvarchar(60)**|メモリ オブジェクトの種類。<br /><br /> メモリ オブジェクトが属するコンポーネント、またはメモリ オブジェクトの機能を示します。 NULL 値が許可されます。|  
|**name**|**varchar(128)**|内部使用のみです。 Null 値を許容します。|  
|**memory_node_id**|**smallint**|メモリ オブジェクトが使用しているメモリ ノードの ID。 NULL 値は許可されません。|  
|**creation_time**|**datetime**|内部使用のみです。 NULL 値が許可されます。|  
|**max_pages_allocated_count**|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> メモリ オブジェクトによって割り当てられている最大ページ数。 NULL 値は許可されません。|  
|**page_size_in_bytes**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> メモリ オブジェクトによって割り当てられているのページのサイズ (バイト単位)。 NULL 値は許可されません。|  
|**max_pages_in_bytes**|**bigint**|メモリ オブジェクトによって使用されるメモリの最大量。 NULL 値は許可されません。|  
|**page_allocator_address**|**varbinary(8)**|ページ アロケーターのメモリ アドレス。 NULL 値は許可されません。 詳細については、次を参照してください。 [sys.dm_os_memory_clerks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)します。|  
|**creation_stack_address**|**varbinary(8)**|内部使用のみです。 NULL 値が許可されます。|  
|**sequence_num**|**int**|内部使用のみです。 NULL 値が許可されます。|  
|**partition_type**|**int**|パーティションの種類。<br /><br /> 0 - - 分割を可能なメモリ オブジェクト<br /><br /> 1-分割可能なメモリ オブジェクトを現在パーティション分割されていません。<br /><br /> 2-分割可能なメモリ オブジェクトの NUMA ノードでパーティション分割します。 1 つの NUMA ノードがある環境でこれは、1 と等価です。<br /><br /> 3-分割可能なメモリ オブジェクト。 CPU によってパーティションに分割します。|  
|**contention_factor**|**real**|このメモリ オブジェクトの競合を競合れないことを意味する 0 を指定する値。 メモリ割り当ての指定した数にはその期間中に競合が反射が加えられるたびに、値が更新されます。 スレッド セーフ メモリ オブジェクトにのみ適用されます。|  
|**waiting_tasks_count**|**bigint**|メモリ オブジェクトで発生する待機の数です。 このカウンターは、このメモリ オブジェクトから割り当てられたメモリされるたびに増加します。 増分値は、このメモリ オブジェクトにアクセスするを待機中のタスクの数です。 スレッド セーフ メモリ オブジェクトにのみ適用されます。 これは、正しいかどうかを待機せずに最適な残存作業時間値です。|  
|**exclusive_access_count**|**bigint**|メモリ オブジェクトに排他アクセスがどのくらいの頻度を指定します。 スレッド セーフ メモリ オブジェクトにのみ適用されます。  これは、正しいかどうかを待機せずに最適な残存作業時間値です。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
 **partition_type**、 **contention_factor**、 **waiting_tasks_count**、および**exclusive_access_count**で実装されていない[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]します。  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

## <a name="remarks"></a>コメント  
 メモリ オブジェクトはヒープであり、 割り当ての粒度はメモリ クラークよりも細かくなります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントでは、メモリ クラークの代わりにメモリ オブジェクトが使用されます。 メモリ オブジェクトでは、ページの割り当てにメモリ クラークのページ アロケーター インターフェイスが使用されます。 仮想または共有メモリ インターフェイスは使用されません。 割り当てパターンに応じて、コンポーネントでは各種メモリ オブジェクトを作成し、任意のサイズの領域を割り当てることができます。  
  
 メモリ オブジェクトの通常のページ サイズは 8 KB です。 ただし、増分メモリ オブジェクトには、ページ サイズを 512 バイトから 8 KB の範囲があります。  
  
> [!NOTE]  
>  ページ サイズは最大割り当てではなく、 メモリ クラークによって実装されたページ アロケーターでサポートされている割り当ての粒度です。 メモリ オブジェクトから、8 KB を超える割り当てを要求することができます。  
  
## <a name="examples"></a>使用例  
 次の例では、それぞれのメモリ オブジェクトの種類によって割り当てられたメモリのサイズを返します。  
  
```  
SELECT SUM (pages_in_bytes) as 'Bytes Used', type   
FROM sys.dm_os_memory_objects  
GROUP BY type   
ORDER BY 'Bytes Used' DESC;  
GO  
```  
  
## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)  
  
  


