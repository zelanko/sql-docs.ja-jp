---
title: sys.dm_db_file_space_usage (Transact-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_file_space_usage
- sys.dm_db_file_space_usage_TSQL
- sys.dm_db_file_space_usage
- dm_db_file_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_file_space_usage dynamic management view
ms.assetid: 148a5276-a8d5-49d2-8146-3c63d24c2144
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 99d5ebc844c2cee8f92266cf5ea18b82666ea203
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264467"
---
# <a name="sysdm_db_file_space_usage-transact-sql"></a>sys.dm_db_file_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース内の各ファイルに関する使用領域の情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_db_file_space_usage**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|データベース ID。|  
|file_id|**smallint**|ファイル ID。<br /><br /> file_id マップ内の file_id [sys.dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md)と内の fileid [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md)します。|  
|filegroup_id|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ファイル グループ ID。|  
|total_page_count|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ファイル内のページの総数。|  
|allocated_extent_page_count|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ファイルに含まれる割り当て済みエクステント内の総ページ数。|  
|unallocated_extent_page_count|**bigint**|ファイルに含まれる未割り当てエクステント内の総ページ数。<br /><br /> 割り当て済みのエクステント内の未使用ページは含まれません。|  
|version_store_reserved_page_count|**bigint**|バージョン ストアに割り当てられる単一エクステント内の総ページ数。 バージョン ストア ページは、混合エクステントからは割り当てられません。<br /><br /> IAM ページは、常に混合エクステントから割り当てられるので、この数に含まれません。 PFS ページは、単一エクステントから割り当てられる場合はこの数に含まれます。<br /><br /> 詳細については、[sys.dm_tran_version_store &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md) を参照してください。|  
|user_object_reserved_page_count|**bigint**|データベース内のユーザー オブジェクトに対して単一エクステントから割り当てられるページの総数。 割り当て済みのエクステントの未使用ページは、この数に含まれません。<br /><br /> IAM ページは、常に混合エクステントから割り当てられるので、この数に含まれません。 PFS ページは、単一エクステントから割り当てられる場合はこの数に含まれます。<br /><br /> 内の total_pages 列を使用することができます、 [sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)カタログ ビューをユーザー オブジェクトの各アロケーション ユニットの予約済みページ数を返します。 ただし、total_pages 列には IAM ページの数が含まれることに注意してください。|  
|internal_object_reserved_page_count|**bigint**|ファイル内の内部オブジェクトに対して割り当てられる単一エクステント内の総ページ数。 割り当て済みのエクステントの未使用ページは、この数に含まれません。<br /><br /> IAM ページは、常に混合エクステントから割り当てられるので、この数に含まれません。 PFS ページは、単一エクステントから割り当てられる場合はこの数に含まれます。<br /><br /> それぞれの内部オブジェクトのページ数を返すカタログ ビューや動的管理オブジェクトはありません。|  
|mixed_extent_page_count|**bigint**|ファイルに含まれる混合エクステント内の、割り当て済みページと未割り当てページの総数。 混合エクステントには、異なるオブジェクトに割り当てられたページが含まれます。 この数には、ファイル内のすべての IAM ページが含まれます。|
|modified_extent_page_count|**bigint**|**適用対象**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br />変更されたページの合計数には、前回のデータベースの完全バックアップ以降、ファイルのエクステントが割り当てられます。 変更されたページ数は、差分バックアップが必要なかどうかを決定する最後の完全バックアップ以降、データベースの差分変更の量を追跡するために使用できます。|
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
|distribution_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 分布に関連付けられている一意の数値 id です。|  
  
## <a name="remarks"></a>コメント  
 ページ数は常にエクステント レベルのものです。 したがって、ページ数の値は常に 8 の倍数になります。 グローバル アロケーション マップ (GAM) と共有グローバル アロケーション マップ (SGAM) の割り当てページを含むエクステントは、割り当て済みの単一エクステントです。 これらは前で説明したページ数には含まれません。 ページとエクステントの詳細については、次を参照してください。[ページとエクステントのアーキテクチャ ガイド](../../relational-databases/pages-and-extents-architecture-guide.md)します。 
  
 現在のバージョン ストアの内容は[sys.dm_tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md)します。 バージョン ストア ページはグローバル リソースなので、セッションおよびタスク レベルではなくファイル レベルで追跡されます。 セッションでバージョンを生成することもできますが、セッションが終了するときバージョンを削除することはできません。 バージョン ストア クリーンアップでは、特定バージョンへのアクセスを必要とする、実行時間が最も長いトランザクションを考慮する必要があります。 Elapsed_time_seconds 列を表示することによって、バージョン ストア クリーンアップに関連する最も長い実行中のトランザクションを検出できる[sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md)します。  
  
 mixed_extent_page_count 列で変更が頻繁に行われる場合は、SGAM ページの使用頻度が高いことが考えられます。 この場合、PAGELATCH_UP 待機の数が多くなっていることがあります。またこの待機では、待機リソースが SGAM ページになっています。 詳細については、次を参照してください[sys.dm_os_waiting_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md)、 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)、および[sys.dm_os_latch_。stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)します。  
  
## <a name="user-objects"></a>ユーザー オブジェクト  
 次のオブジェクトは、ユーザー オブジェクト ページ カウンターに含まれます。  
  
-   ユーザー定義テーブルとインデックス  
  
-   システム テーブルとインデックス  
  
-   グローバル一時テーブルとインデックス  
  
-   ローカル一時テーブルとインデックス  
  
-   テーブル変数  
  
-   テーブル値関数で返されるテーブル  
  
## <a name="internal-objects"></a>内部オブジェクト  
 内部オブジェクトは tempdb にのみ存在します。 次のオブジェクトは、内部オブジェクト ページ カウンターに含まれます。  
  
-   カーソルまたはスプール操作と一時的なラージ オブジェクト (LOB) ストレージ用の作業テーブル  
  
-   ハッシュ結合などの操作用の作業ファイル  
  
-   並べ替え実行結果  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_db_file_space_usage.database_id、file_id|sys.dm_io_virtual_file_stats.database_id、file_id|一対一|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

## <a name="examples"></a>使用例  
  
### <a name="determing-the-amount-of-free-space-in-tempdb"></a>tempdb の使用可能な空き領域の確認  
 次のクエリは、メガバイト (MB 単位) 使用可能なすべてのファイルで空きページと空き領域の合計の合計数を返します**tempdb**します。  
  
```sql
USE tempdb;  
GO  
SELECT SUM(unallocated_extent_page_count) AS [free pages],   
(SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]  
FROM sys.dm_db_file_space_usage;  
```  

### <a name="determining-the-amount-of-space-used-by-user-objects"></a>ユーザー オブジェクトにより使用される領域の確認  
 次のクエリを実行すると、tempdb のユーザー オブジェクトにより使用されるページ数の合計と領域の合計 (MB 単位) が返されます。  
  
```sql  
USE tempdb;  
GO  
SELECT SUM(user_object_reserved_page_count) AS [user object pages used],  
(SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]  
FROM sys.dm_db_file_space_usage;
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
