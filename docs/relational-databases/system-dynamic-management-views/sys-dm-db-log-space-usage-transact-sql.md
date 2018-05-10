---
title: sys.dm_db_log_space_usage (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_db_log_space_usage
- sys.dm_db_log_space_usage_TSQL
- dm_db_log_space_usage
- dm_db_log_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_space_usage dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b2cd22474c1aa2d54a620f59d08c65e7296949d6
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmdblogspaceusage-transact-sql"></a>sys.dm_db_log_space_usage (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

領域のトランザクション ログの利用状況情報を返します。 
  
> [!NOTE]
> すべてのトランザクション ログ ファイルが結合されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|データベース ID。|  
|total_log_size_in_bytes |**bigint** |ログのサイズ  |
|used_log_space_in_bytes |**bigint** |ログの占有サイズ  |     
|used_log_space_in_percent |**real** |ログの合計サイズに対する比率で表したログの占有サイズ |
|log_space_in_bytes_since_last_backup |**bigint** |最後のログ バックアップ以降に使用される領域の量 <br />**適用されます:** [!INCLUDE[sssql14-md](../../includes/sssql14-md.md)]を通じて[!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|
    
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="examples"></a>使用例  
  
### <a name="a-determine-the-amount-of-free-log-space-in-tempdb"></a>A. 容量のログの空き領域 tempdb の決定します。   
次のクエリは、tempdb の利用可能なメガバイト (MB) のログの合計空き領域を返します。

```sql
USE tempdb;  
GO  

SELECT (total_log_size_in_bytes - used_log_space_in_bytes)*1.0/1024/1024 AS [free log space in MB]  
FROM sys.dm_db_log_space_usage;  
```
  
## <a name="see-also"></a>参照  
[動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)    
[sys.dm_db_task_space_usage &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
[sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
[sys.dm_db_log_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) 



