---
title: sys.dm_db_file_space_usage (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql-non-specified
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
- dm_db_file_space_usage
- sys.dm_db_file_space_usage_TSQL
- sys.dm_db_file_space_usage
- dm_db_file_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_file_space_usage dynamic management view
ms.assetid: 148a5276-a8d5-49d2-8146-3c63d24c2144
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 65be93c18aed0f9c03ea781ee7de3069c4e99698
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmdbfilespaceusage-transact-sql"></a>sys.dm_db_file_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース内の各ファイルに関する使用領域の情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_db_file_space_usage**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|データベース ID。|  
|file_id|**smallint**|ファイル ID。<br /><br /> file_id マップ内の file_id [sys.dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md)およびの fileid に[sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md)です。|  
|filegroup_id|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ファイル グループ ID。|  
|total_page_count|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ファイル内のページの総数。|  
|allocated_extent_page_count|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ファイルに含まれる割り当て済みエクステント内の総ページ数。|  
|unallocated_extent_page_count|**bigint**|ファイルに含まれる未割り当てエクステント内の総ページ数。<br /><br /> 割り当て済みのエクステント内の未使用ページは含まれません。|  
|version_store_reserved_page_count|**bigint**|バージョン ストアに割り当てられる単一エクステント内の総ページ数。 バージョン ストア ページは、混合エクステントからは割り当てられません。<br /><br /> IAM ページは、常に混合エクステントから割り当てられるので、この数に含まれません。 PFS ページは、単一エクステントから割り当てられる場合はこの数に含まれます。<br /><br /> 詳細については、次を参照してください。 [sys.dm_tran_version_store &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md)。|  
|user_object_reserved_page_count|**bigint**|データベース内のユーザー オブジェクトに対して単一エクステントから割り当てられるページの総数。 割り当て済みのエクステントの未使用ページは、この数に含まれません。<br /><br /> IAM ページは、常に混合エクステントから割り当てられるので、この数に含まれません。 PFS ページは、単一エクステントから割り当てられる場合はこの数に含まれます。<br /><br /> 内の total_pages 列を使用することができます、 [sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)カタログ ビューをユーザー オブジェクト内の各アロケーション ユニットの予約済みページ数を返します。 ただし、total_pages 列には IAM ページの数が含まれることに注意してください。|  
|internal_object_reserved_page_count|**bigint**|ファイル内の内部オブジェクトに対して割り当てられる単一エクステント内の総ページ数。 割り当て済みのエクステントの未使用ページは、この数に含まれません。<br /><br /> IAM ページは、常に混合エクステントから割り当てられるので、この数に含まれません。 PFS ページは、単一エクステントから割り当てられる場合はこの数に含まれます。<br /><br /> それぞれの内部オブジェクトのページ数を返すカタログ ビューや動的管理オブジェクトはありません。|  
|mixed_extent_page_count|**bigint**|ファイルに含まれる混合エクステント内の、割り当て済みページと未割り当てページの総数。 混合エクステントには、異なるオブジェクトに割り当てられたページが含まれます。 この数には、ファイル内のすべての IAM ページが含まれます。|
|modified_extent_page_count|**bigint**|**以降で**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]<br /><br />変更されたページの合計数には、前回のデータベースの完全バックアップ以降、ファイルのエクステントが割り当てられます。変更されたページ数は、差分バックアップと役に立つかどうかを決定する最後の完全バックアップ以降のデータベースの差分変更を追跡するために使用できます。|
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
|distribution_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 分布に関連付けられている一意の数値 id です。|  
  
## <a name="remarks"></a>解説  
 ページ数は常にエクステント レベルのものです。 したがって、ページ数の値は常に 8 の倍数になります。 グローバル アロケーション マップ (GAM) と共有グローバル アロケーション マップ (SGAM) の割り当てページを含むエクステントは、割り当て済みの単一エクステントです。 これらは前で説明したページ数には含まれません。  
  
 現在のバージョン ストアの内容は[sys.dm_tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md)です。 バージョン ストア ページはグローバル リソースなので、セッションおよびタスク レベルではなくファイル レベルで追跡されます。 セッションでバージョンを生成することもできますが、セッションが終了するときバージョンを削除することはできません。 バージョン ストア クリーンアップでは、特定バージョンへのアクセスを必要とする、実行時間が最も長いトランザクションを考慮する必要があります。 Elapsed_time_seconds 列を表示することによって、バージョン ストア クリーンアップに関連する実行の最も長いトランザクションを検出できます[sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md)です。  
  
 mixed_extent_page_count 列で変更が頻繁に行われる場合は、SGAM ページの使用頻度が高いことが考えられます。 この場合、PAGELATCH_UP 待機の数が多くなっていることがあります。またこの待機では、待機リソースが SGAM ページになっています。 詳細については、次を参照してください[sys.dm_os_waiting_tasks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md)、 [sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)、および[sys.dm_os_latch_。stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)です。  
  
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
  
-   カーソルまたはスプール操作と一時的なラージ オブジェクト (LOB) の記憶域用の作業テーブル  
  
-   ハッシュ結合などの操作用の作業ファイル  
  
-   並べ替え実行結果  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_db_file_space_usage.database_id、file_id|sys.dm_io_virtual_file_stats.database_id、file_id|一対一|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="examples"></a>使用例  
  
### <a name="determing-the-amount-of-free-space-in-tempdb"></a>tempdb の使用可能な空き領域の確認  
 次のクエリでは、空きページと合計の空き領域の合計数を返します (mb) 使用可能なすべてのファイルで**tempdb**です。  
  
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
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
