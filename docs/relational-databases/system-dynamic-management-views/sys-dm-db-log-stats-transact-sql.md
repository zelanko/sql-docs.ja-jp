---
title: "sys.dm_db_log_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_log_stats_TSQL
- sys.dm_db_log_stats
- sys.dm_db_log_stats_TSQL
- dm_db_log_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_stats dynamic management function
ms.assetid: 
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba933bad47beead99ea5f645a910b1783caa280e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdblogstats-transact-sql"></a>sys.dm_db_log_stats (TRANSACT-SQL)   
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

データベースのトランザクション ログ ファイルには、概要レベルの属性と情報を返します。 この情報を使用して監視とトランザクション ログの正常性診断します。   
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
 sys.dm_db_log_stats ( database_id )
```  
  
## <a name="arguments"></a>引数  

*database_id* |NULL |**既定**

データベースの ID です。 `database_id`is `int`. 有効な入力値は、データベースの ID 番号`NULL`、または`DEFAULT`です。 既定値は `NULL` です。 `NULL`および`DEFAULT`は現在のデータベースのコンテキストで対応する値。  
組み込み関数は、`DB_ID`を指定できます。 使用する場合`DB_ID`データベース名を指定せず、現在のデータベースの互換性レベルを 90 以上でなければなりません。

  
## <a name="tables-returned"></a>返されたテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id    |**int**    |データベース ID |  
|recovery_model |**nvarchar (60)**   |   データベースの復旧モデルです。 有効な値は次のとおりです。 <br /> SIMPLE<br /> BULK_LOGGED <br /> FULL |  
|log_min_lsn    |**nvarchar(24)**   |   トランザクション ログの現在の開始 LSN。 |  
|log_end_lsn    |**nvarchar(24)**   |   トランザクション ログの最後のログ レコードの LSN です。 |  
|current_vlf_sequence_number    |**bigint** |   現在 VLF のシーケンス番号時に実行します。 |  
|current_vlf_size_mb    |**float**  |   現在の VLF が mb 単位でサイズ。 |   
|total_vlf_count    |**bigint** |   トランザクション ログ内の Vlf の総数です。 |  
|total_log_size_mb  |**float**  |   トランザクション ログ サイズの合計 (MB)。 |  
|active_vlf_count   |**bigint** |   トランザクション ログのアクティブな Vlf の合計数。 |  
|active_log_size_mb |**float**  |   アクティブなトランザクション ログ サイズの合計 mb 単位で。 |  
|log_truncation_holdup_reason   |**nvarchar (60)**   |   ログ切り捨てホールド アップ理由です。 値と同じ`log_reuse_wait_desc`の列`sys.databases`です。  (詳細なこれらの値の説明を参照してください。[トランザクション ログ](../../relational-databases/logs/the-transaction-log-sql-server.md))。 <br />有効な値は次のとおりです。 <br />NOTHING<br />CHECKPOINT<br />LOG_BACKUP<br />ACTIVE_BACKUP_OR_RESTORE<br />ACTIVE_TRANSACTION<br />DATABASE_MIRRORING<br />レプリケーション<br />DATABASE_SNAPSHOT_CREATION<br />LOG_SCAN<br />AVAILABILITY_REPLICA<br />OLDEST_PAGE<br />XTP_CHECKPOINT<br />その他の一時的なもの |  
|log_backup_time    |**datetime**   |   最後のトランザクション ログ バックアップされた時刻。 |   
|log_backup_lsn |**nvarchar(24)**   |   最後のトランザクション ログ バックアップの LSN。 |   
|log_since_last_log_backup_mb   |**float**  |   最後のトランザクション ログ バックアップ LSN 以降、サイズを mb 単位でログに記録します。 |  
|log_checkpoint_lsn |**nvarchar(24)**   |   最後のチェックポイントの LSN。 |  
|log_since_last_checkpoint_mb   |**float**  |   最後のチェックポイント LSN 以降、サイズを mb 単位でログに記録します。 |  
|log_recovery_lsn   |**nvarchar(24)**   |   回復データベースの LSN。 場合`log_recovery_lsn`チェックポイントの LSN をする前に発生`log_recovery_lsn`それ以外の場合は、最も古いアクティブなトランザクション LSN、`log_recovery_lsn`は、チェックポイントの LSN。 |  
|log_recovery_size_mb   |**float**  |   ログのサイズ (MB) ログの復旧 LSN 以降。 |  
|recovery_vlf_count |**bigint** |   フェールオーバーまたはサーバーの再起動が発生した場合、回復する Vlf の合計数。 |  


## <a name="permissions"></a>Permissions  
必要があります、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="examples"></a>使用例  

### <a name="a-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-high-number-of-vlfs"></a>A. 内のデータベースを決定する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vlf の数が多いとインスタンス   
次のクエリは、ログ ファイルで 100 を超える vlf を使用してデータベースを返します。 Vlf 数が多いデータベースの起動、復元、および復旧時間に影響を与えることができます。

``` t-sql  
SELECT name AS 'Database Name', total_vlf_count AS 'VLF count' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id) 
WHERE total_vlf_count  > 100;
```   

### <a name="b-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-transaction-log-backups-older-than-4-hours"></a>B. 内のデータベースを決定する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4 時間以上経過してトランザクション ログのバックアップを持つインスタンス   
次のクエリでは、インスタンス内のデータベースの前回のログ バックアップ時刻を決定します。

``` t-sql  
SELECT name AS 'Database Name', log_backup_time AS 'last log backup time' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id); 
```

## <a name="see-also"></a>参照  
[動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)  

  
