---
title: dm_db_log_space_usage (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bfa102163012456e9b2660d26cb54dec3d58cfbb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264577"
---
# <a name="sysdm_db_log_space_usage-transact-sql"></a>dm_db_log_space_usage (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

トランザクションログの領域使用状況に関する情報を返します。 
  
> [!NOTE]
> すべてのトランザクションログファイルが結合されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|データベース ID。|  
|total_log_size_in_bytes |**bigint** |ログのサイズ  |
|used_log_space_in_bytes |**bigint** |ログの占有サイズ  |     
|used_log_space_in_percent |**本当の** |ログサイズの合計に対するログの占有サイズ。 |
|log_space_in_bytes_since_last_backup |**bigint** |前回のログバックアップ以降に使用された領域のサイズ <br />**適用対象:** [!INCLUDE[sssql14-md](../../includes/sssql14-md.md)]から[!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)]、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]。|
    
  
## <a name="permissions"></a>アクセス許可  

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   
  
## <a name="examples"></a>例  
  
### <a name="a-determine-the-amount-of-free-log-space-in-tempdb"></a>A. Tempdb の空きログ領域の量を確認する   
次のクエリは、tempdb で使用可能な空きログ領域の合計をメガバイト (MB) 単位で返します。

```sql
USE tempdb;  
GO  

SELECT (total_log_size_in_bytes - used_log_space_in_bytes)*1.0/1024/1024 AS [free log space in MB]  
FROM sys.dm_db_log_space_usage;  
```
  
## <a name="see-also"></a>参照  
[動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Transact-sql&#41;&#40;データベース関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)    
[dm_db_task_space_usage &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
[dm_db_session_space_usage &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
[dm_db_log_info &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
[dm_db_log_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) 



