---
title: "sys.dm_exec_trigger_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_trigger_stats
- dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_trigger_stats dynamic management function
ms.assetid: 863498b4-849c-434d-b748-837411458738
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67c6d5765ee5259134f6d9985a88bf94768490cf
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexectriggerstats-transact-sql"></a>sys.dm_exec_trigger_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  キャッシュされたトリガーの集計パフォーマンス統計を返します。 このビューには、トリガーごとに 1 行が含まれており、その行の有効期間はトリガーがキャッシュに残っている間です。 つまり、トリガーがキャッシュから削除されると、対応する行もこのビューから削除されます。 その時点でパフォーマンス統計 SQL トレース イベントが発生したような**sys.dm_exec_query_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|トリガーが存在するデータベースの ID。|  
|**object_id**|**int**|トリガーのオブジェクト ID 番号。|  
|**型**|**char(2)**|次のいずれかのオブジェクトの種類。<br /><br /> TA = アセンブリ (CLR) トリガー<br /><br /> TR = SQL トリガー|  
|**Type_desc**|**nvarchar (60)**|オブジェクトの種類の説明です。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**sql_handle**|**varbinary (64)**|これは、クエリと関連付けるために使用できる**sys.dm_exec_query_stats**するは、このトリガー内から実行されました。|  
|**plan_handle**|**varbinary (64)**|インメモリ プランの識別子。 この識別子は一時的なもので、プランがキャッシュに残っている間だけ一定の値になります。 この値で使用することがあります、 **sys.dm_exec_cached_plans**動的管理ビュー。|  
|**cached_time**|**datetime**|トリガーがキャッシュに追加された時刻。|  
|**last_execution_time**|**datetime**|前回トリガーが実行された時刻。|  
|**execution_count**|**bigint**|前回のコンパイル時以降に、トリガーが実行された回数。|  
|**total_worker_time**|**bigint**|コンパイル後にこのトリガーの実行で使用された CPU 時間の合計 (マイクロ秒単位)。|  
|**last_worker_time**|**bigint**|トリガーを前回実行したときに使用された CPU 時間 (マイクロ秒単位)。|  
|**min_worker_time**|**bigint**|このトリガーの 1 回の実行で使用された最大 CPU 時間 (マイクロ秒単位)。|  
|**max_worker_time**|**bigint**|このトリガーの 1 回の実行で使用された最大 CPU 時間 (マイクロ秒単位)。|  
|**トリガー**|**bigint**|コンパイル後にこのトリガーの実行で行われた物理読み取りの合計数。|  
|**last_physical_reads**|**bigint**|トリガーを前回実行したときに行われた物理読み取りの数。|  
|**min_physical_reads**|**bigint**|このトリガーの 1 回の実行で行われた物理読み取りの最小数。|  
|**max_physical_reads**|**bigint**|このトリガーの 1 回の実行で行われた物理読み取りの最大数。|  
|**total_logical_writes**|**bigint**|コンパイル後にこのトリガーの実行で行われた論理書き込みの合計数。|  
|**last_logical_writes**|**bigint**|**トリガー**論理書き込みの数が、トリガーが実行された最終時刻を実行します。|  
|**min_logical_writes**|**bigint**|このトリガーの 1 回の実行で行われた論理書き込みの最小数。|  
|**max_logical_writes**|**bigint**|このトリガーの 1 回の実行で行われた論理書き込みの最大数。|  
|**total_logical_reads**|**bigint**|コンパイル後にこのトリガーの実行で行われた論理読み取りの合計数。|  
|**last_logical_reads**|**bigint**|トリガーを前回実行したときに行われた論理読み取りの数。|  
|**min_logical_reads**|**bigint**|このトリガーの 1 回の実行で行われた論理読み取りの最小数。|  
|**max_logical_reads**|**bigint**|このトリガーの 1 回の実行で行われた論理読み取りの最大数。|  
|**total_elapsed_time**|**bigint**|このトリガーの実行完了までの経過時間の合計 (マイクロ秒単位)。|  
|**last_elapsed_time**|**bigint**|このトリガーの前回の実行完了までの経過時間 (マイクロ秒単位)。|  
|**min_elapsed_time**|**bigint**|このトリガーの任意の実行完了までの最小経過時間 (マイクロ秒単位)。|  
|**max_elapsed_time**|**bigint**|このトリガーの任意の実行完了までの最大経過時間 (マイクロ秒単位)。|  
  
## <a name="remarks"></a>解説  
 Windows Azure SQL データベースでは、動的管理ビューでデータベースの包含に影響を与える情報を公開することや、ユーザーがアクセスできる他のデータベースに関する情報を公開することはできません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  

ビュー内の統計は、クエリが完了したときに更新されます。  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。
  
  
## <a name="examples"></a>使用例  
 次の例では、平均経過時間で識別される上位 5 つのトリガーに関する情報を返します。  
  
```sql  
PRINT '--top 5 CPU consuming triggers '  
  
SELECT TOP 5 d.object_id, d.database_id, DB_NAME(database_id) AS 'database_name',   
    OBJECT_NAME(object_id, database_id) AS 'trigger_name', d.cached_time,  
    d.last_execution_time, d.total_elapsed_time,   
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],   
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_trigger_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
  [sys.dm_exec_procedure_stats および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)   
 [sys.dm_exec_cached_plans &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
  
