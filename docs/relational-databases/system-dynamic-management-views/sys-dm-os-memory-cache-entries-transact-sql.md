---
title: sys.dm_os_memory_cache_entries (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: a96d536143c7e636045eb926e9240e047c78070b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265800"
---
# <a name="sysdmosmemorycacheentries-transact-sql"></a>sys.dm_os_memory_cache_entries (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、キャッシュ内のすべてのエントリに関する情報を返します。 トレースは、関連付けられたオブジェクトへのエントリをキャッシュするには、このビューを使用します。 キャッシュ エントリに関する統計情報を取得するのに、このビューを使用することもできます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_memory_cache_entries**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|キャッシュのアドレス。 NULL 値は許可されません。|  
|**name**|**nvarchar (256)**|キャッシュの名前。 NULL 値は許可されません。|  
|**type**|**varchar(60)**|キャッシュの型。 NULL 値は許可されません。|  
|**entry_address**|**varbinary(8)**|キャッシュ エントリの記述子のアドレス。 NULL 値は許可されません。|  
|**entry_data_address**|**varbinary(8)**|キャッシュ エントリ内のユーザー データのアドレス。<br /><br /> 0x00000000 = エントリ データ アドレスは使用できません。<br /><br /> NULL 値は許可されません。|  
|**in_use_count**|**int**|このキャッシュ エントリの同時実行ユーザーの数。 NULL 値は許可されません。|  
|**is_dirty**|**bit**|このキャッシュ エントリが削除対象としてマークされているかどうかを示します。 1 = 削除対象としてマークします。 NULL 値は許可されません。|  
|**disk_ios_count**|**int**|このエントリが作成されたときに発生した I/o の数。 NULL 値は許可されません。|  
|**context_switches_count**|**int**|このエントリが作成されたときに発生したコンテキスト切り替えの数。 NULL 値は許可されません。|  
|**original_cost**|**int**|エントリの元のコスト。 この値は、発生した I/o の数の概算値、CPU 命令コスト、およびエントリによって消費されるメモリの量です。 コストが大きいほど、アイテムがキャッシュから削除される可能性は低くなります。 NULL 値は許可されません。|  
|**current_cost**|**int**|キャッシュ エントリの現在のコスト。 この値はエントリの削除プロセス中に更新されます。 現在のコストは、エントリが再利用の元の値にリセットされます。 NULL 値は許可されません。|  
|**memory_object_address**|**varbinary(8)**|関連付けられているメモリ オブジェクトのアドレス。 NULL 値が許可されます。|  
|**pages_allocated_count**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> キャッシュ エントリを格納する 8 KB ページの数。 NULL 値は許可されません。|  
|**pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このキャッシュ エントリで使用されるキロバイト (KB) のメモリの量。  NULL 値は許可されません。|  
|**entry_data**|**nvarchar(2048)**|キャッシュ エントリのシリアル化された表現。 この情報は、キャッシュの保存に依存します。 NULL 値が許可されます。|  
|**pool_id**|**int**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> エントリに関連付けられているリソース プールの id。 NULL 値が許可されます。<br /><br /> katmai ではないです。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

## <a name="see-also"></a>関連項目  
 
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


