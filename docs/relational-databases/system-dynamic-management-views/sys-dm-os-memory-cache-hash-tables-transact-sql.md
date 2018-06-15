---
title: sys.dm_os_memory_cache_hash_tables (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_hash_tables_TSQL
- sys.dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_hash_tables dynamic management view
ms.assetid: 68b94f35-8f80-4d2b-bcde-7a21934219af
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 50e261fb0c53da8caf9f9b41d15d0f96dc7a41e4
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467778"
---
# <a name="sysdmosmemorycachehashtables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  インスタンスでアクティブなキャッシュごとに 1 行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_memory_cache_hash_tables**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|キャッシュ エントリのアドレス (主キー)。 NULL 値は許可されません。|  
|**name**|**nvarchar (256)**|キャッシュの名前。 NULL 値は許可されません。|  
|**type**|**nvarchar(60)**|キャッシュの種類。 NULL 値は許可されません。|  
|**table_level**|**int**|ハッシュ テーブル番号。 キャッシュは、異なるハッシュ関数に対応する複数のハッシュ テーブルを持つことができます。 NULL 値は許可されません。|  
|**buckets_count**|**int**|ハッシュ テーブルに含まれるバケット数。 NULL 値は許可されません。|  
|**buckets_in_use_count**|**int**|現在使用されているバケット数。 NULL 値は許可されません。|  
|**buckets_min_length**|**int**|バケットの最小キャッシュ エントリ数。 NULL 値は許可されません。|  
|**buckets_max_length**|**int**|バケットの最大キャッシュ エントリ数。 NULL 値は許可されません。|  
|**buckets_avg_length**|**int**|各バケットの平均キャッシュ エントリ数。 NULL 値は許可されません。|  
|**buckets_max_length_ever**|**int**|サーバー起動後のハッシュ テーブルのハッシュ バケット内にあるキャッシュ済みエントリの最大数。 NULL 値は許可されません。|  
|**hits_count**|**bigint**|キャッシュ ヒットの数。 NULL 値は許可されません。|  
|**misses_count**|**bigint**|キャッシュ ミスの数。 NULL 値は許可されません。|  
|**buckets_avg_scan_hit_length**|**int**|検索したアイテムが見つかるまでにバケットで検証したエントリの平均数。 NULL 値は許可されません。|  
|**buckets_avg_scan_miss_length**|**int**|検索が失敗するまでにバケットで検証したエントリの平均数。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|この分布はでは、ノードの識別子。<br /><br /> **適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>権限 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="see-also"></a>参照  
 
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


