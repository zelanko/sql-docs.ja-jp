---
title: sys.dm_os_memory_cache_entries (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_memory_cache_entries
- sys.dm_os_memory_cache_entries
- dm_os_memory_cache_entries_TSQL
- sys.dm_os_memory_cache_entries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_entries dynamic management view
ms.assetid: dd32be6b-10d1-4059-b4fd-0bf817f40d54
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a69088658cf9e76ac52c882872ef0e1eed6500b9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmosmemorycacheentries-transact-sql"></a>sys.dm_os_memory_cache_entries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、キャッシュ内のすべてのエントリに関する情報を返します。 このビューを使って、キャッシュ エントリとそれらに関連するオブジェクトをトレースできます。 また、キャッシュ エントリに関する統計を取得することもできます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_memory_cache_entries**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|キャッシュのアドレス。 NULL 値は許可されません。|  
|**name**|**nvarchar (256)**|キャッシュの名前。 NULL 値は許可されません。|  
|**type**|**varchar(60)**|キャッシュの種類。 NULL 値は許可されません。|  
|**entry_address**|**varbinary(8)**|キャッシュ エントリの記述子のアドレス。 NULL 値は許可されません。|  
|**entry_data_address**|**varbinary(8)**|キャッシュ エントリ内のユーザー データのアドレス。<br /><br /> 0x00000000 = エントリ データ アドレスは使用できません。<br /><br /> NULL 値は許可されません。|  
|**in_use_count**|**int**|キャッシュ エントリの同時実行ユーザーの数。 NULL 値は許可されません。|  
|**is_dirty**|**bit**|このキャッシュ エントリが削除対象としてマークされているかどうかを示します。 1 = 削除の対象としてマークされています。 NULL 値は許可されません。|  
|**disk_ios_count**|**int**|このキャッシュ エントリの作成時に発生した I/O の数。 NULL 値は許可されません。|  
|**context_switches_count**|**int**|このキャッシュ エントリの作成時に発生したコンテキストの切り替えの回数。 NULL 値は許可されません。|  
|**original_cost**|**int**|キャッシュ エントリの元のコスト。 この値は、発生した I/O の数、CPU 命令コスト、およびこのキャッシュ エントリで使用されたメモリ量の概数です。 コストが大きいほど、アイテムがキャッシュから削除される可能性は低くなります。 NULL 値は許可されません。|  
|**current_cost**|**int**|キャッシュ エントリの現在のコスト。 この値はエントリの削除プロセス中に更新されます。 現在のコストは、エントリが再利用されると元の値にリセットされます。 NULL 値は許可されません。|  
|**memory_object_address**|**varbinary(8)**|関連するメモリ オブジェクトのアドレス。 NULL 値が許可されます。|  
|**pages_allocated_count**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> キャッシュ エントリを格納する 8 KB ページの数。 NULL 値は許可されません。|  
|**pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このキャッシュ エントリで使用されるメモリの量 (KB 単位)。  NULL 値は許可されません。|  
|**entry_data**|**nvarchar(2048)**|キャッシュ エントリのシリアル化された表示。 この情報は、キャッシュの保存に依存します。 NULL 値が許可されます。|  
|**pool_id**|**int**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> キャッシュ エントリに関連付けられているリソース プール ID。 NULL 値が許可されます。<br /><br /> katmai ではない|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="see-also"></a>参照  
 
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


