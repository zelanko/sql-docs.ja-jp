---
title: sys.dm_exec_function_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1c7f02a3f8e13924886c4a6d2ad3b790382938e4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>sys.dm_exec_function_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  キャッシュされた関数のパフォーマンス統計が集計を返します。 ビューには、各キャッシュされている関数のプランの 1 つの行が返され、行の有効期間は、関数が残っている限りキャッシュします。 関数がキャッシュから削除されると、対応する行はこのビューから削除します。 その時点でパフォーマンス統計 SQL トレース イベントが発生したような**sys.dm_exec_query_stats**です。 メモリ内の関数と CLR のスカラー関数を含む、スカラー関数に関する情報を返します。 テーブル値関数についての情報は返しません。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  
  
> [!NOTE]
> 最初のクエリ**sys.dm_exec_function_stats**サーバーで現在実行中のワークロードがある場合、不正確な結果を生じる可能性があります。 クエリを再実行すると、より正確な結果を確認できます。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|関数が存在するデータベースの ID。|  
|**object_id**|**int**|関数のオブジェクト id 番号。|  
|**type**|**char(2)**|オブジェクトの型: FN = スカラー値関数|  
|**type_desc**|**nvarchar(60)**|オブジェクトの種類の説明: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|これは、クエリと関連付けるために使用できる**sys.dm_exec_query_stats**するは、この関数内から実行されました。|  
|**plan_handle**|**varbinary(64)**|インメモリ プランの識別子。 この識別子は一時的なもので、プランがキャッシュに残っている間だけ一定の値になります。 この値で使用することがあります、 **sys.dm_exec_cached_plans**動的管理ビュー。<br /><br /> 0x000 ときに、ネイティブ コンパイルの関数のクエリがメモリ最適化テーブルは常になります。|  
|**cached_time**|**datetime**|関数がキャッシュに追加された時刻です。|  
|**last_execution_time**|**datetime**|前回は、関数が実行されたとします。|  
|**execution_count**|**bigint**|以降に、関数が実行された回数を最後にコンパイルします。|  
|**total_worker_time**|**bigint**|合計 CPU 時間にコンパイルされた後にこの関数の実行で使用された (マイクロ秒)。<br /><br /> 関数のネイティブ コンパイル、 **total_worker_time**多くの実行にかかる 1 ミリ秒未満の場合に正確なことができない可能性があります。|  
|**last_worker_time**|**bigint**|最後に、関数が実行されたときに使用された CPU 時間、マイクロ秒単位で。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|この関数で 1 回の実行中に使用された (マイクロ秒) の最小 CPU 時間。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|この関数で 1 回の実行中に使用されたマイクロ秒単位の最大 CPU 時間。 <sup>1</sup>|  
|**total_physical_reads**|**bigint**|コンパイルされた後に、この関数の実行によって実行される、物理読み取りの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_physical_reads**|**bigint**|物理読み取りの数は、関数が実行された最終時刻を実行します。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_physical_reads**|**bigint**|この関数が 1 回の実行中に行われた物理読み取りの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_physical_reads**|**bigint**|この関数が 1 回の実行中に行われた物理読み取りの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_writes**|**bigint**|コンパイルされた後に、この関数の実行で実行する論理書き込みの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_writes**|**bigint**|前回プランが実行されたときにダーティになったバッファー プール ページの数。 ページが既にダーティの場合 (変更された場合)、書き込みはカウントされません。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_writes**|**bigint**|この関数が 1 回の実行中に行われた論理書き込みの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_writes**|**bigint**|この関数が 1 回の実行中に行われた論理書き込みの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_reads**|**bigint**|コンパイルされた後に、この関数の実行で実行する論理読み取りの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_reads**|**bigint**|論理読み取りの数は、関数が実行された最終時刻を実行します。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_reads**|**bigint**|この関数が 1 回の実行中に行われた論理読み取りの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_reads**|**bigint**|この関数が 1 回の実行中に行われた論理読み取りの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_elapsed_time**|**bigint**|経過時間の合計 (マイクロ秒)、この関数の実行が完了するのです。|  
|**last_elapsed_time**|**bigint**|経過時間 (マイクロ秒)、前回には、この関数の実行を完了します。|  
|**min_elapsed_time**|**bigint**|最小経過時間 (マイクロ秒) のいずれか、この関数の実行を完了します。|  
|**max_elapsed_time**|**bigint**|最大経過時間 (マイクロ秒) のいずれか、この関数の実行を完了します。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="examples"></a>使用例  
 次の例では、平均経過時間で識別される上位 10 個の関数に関する情報を返します。  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'function name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_function_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys.dm_exec_procedure_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
