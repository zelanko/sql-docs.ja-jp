---
title: sys.dm_exec_procedure_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ed76d84540b3c1c851e87c7e7fab0eb3120f7982
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43081773"
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  キャッシュされたストアド プロシージャの集計パフォーマンス統計を返します。 ビューは、キャッシュされたストアド プロシージャのプランごとに 1 行を返します。その行の有効期間はストアド プロシージャがキャッシュに残っている間になります。 つまり、ストアド プロシージャがキャッシュから削除されると、対応する行もこのビューから削除されます。 その時点では、パフォーマンス統計 SQL トレース イベントが発生するのような**sys.dm_exec_query_stats**します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  
  
> [!NOTE]
> 最初のクエリの**sys.dm_exec_procedure_stats**サーバーで現在実行中のワークロードがある場合、不正確な結果を生成可能性があります。 クエリを再実行すると、より正確な結果を確認できます。  
  
> [!NOTE]
> これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_exec_procedure_stats**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ストアド プロシージャが存在するデータベースの ID。|  
|**object_id**|**int**|ストアド プロシージャのオブジェクト ID 番号。|  
|**type**|**char(2)**|次のいずれかのオブジェクトの種類。<br /><br /> P = SQL ストアド プロシージャ<br /><br /> PC = アセンブリ (CLR) ストアド プロシージャ<br /><br /> X = 拡張ストアド プロシージャ|  
|**type_desc**|**nvarchar(60)**|オブジェクトの種類の説明です。<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|これでのクエリと関連付けるために使用できる**sys.dm_exec_query_stats**するこのストアド プロシージャ内から実行されました。|  
|**plan_handle**|**varbinary(64)**|インメモリ プランの識別子。 この識別子は一時的なもので、プランがキャッシュに残っている間だけ一定の値になります。 この値で使用できる、 **sys.dm_exec_cached_plans**動的管理ビュー。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0x000 になります。|  
|**cached_time**|**datetime**|ストアド プロシージャがキャッシュに追加された時刻。|  
|**last_execution_time**|**datetime**|前回ストアド プロシージャが実行された時刻。|  
|**execution_count**|**bigint**|後に、ストアド プロシージャが実行された回数は、最後にコンパイルされました。|  
|**total_worker_time**|**bigint**|コンパイルされたので、このストアド プロシージャの実行によって消費されたマイクロ秒での CPU 時間の合計です。<br /><br /> ネイティブ コンパイル ストアド プロシージャに関して、多くの実行が 1 ミリ秒未満である場合は、 **total_worker_time** は精度が高くない可能性があります。|  
|**last_worker_time**|**bigint**|ストアド プロシージャを前回実行したときに使用された CPU 時間 (マイクロ秒単位)。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|最小の CPU 時間をマイクロ秒でこのストアド プロシージャであることこれまで使用している 1 つの実行中に。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|最大 CPU 時間をマイクロ秒でこのストアド プロシージャが使用している 1 つの実行中に。 <sup>1</sup>|  
|**total_physical_reads**|**bigint**|コンパイルされたので、このストアド プロシージャの実行によって実行される、物理読み取りの合計数です。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_physical_reads**|**bigint**|物理読み取りの数は、ストアド プロシージャが実行された最後の時間を実行します。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_physical_reads**|**bigint**|このストアド プロシージャであること、物理読み取りの最小数は 1 つの実行中に実行しました。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_physical_reads**|**bigint**|このストアド プロシージャであること、物理読み取りの最大数が 1 つの実行中に実行します。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_writes**|**bigint**|コンパイルされたので、このストアド プロシージャの実行によって実行される、論理書き込みの合計数です。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_writes**|**bigint**|バッファー プール ページの数は、計画が実行された最後の時間を変更します。 ページが既にダーティの場合 (変更された場合)、書き込みはカウントされません。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_writes**|**bigint**|このストアド プロシージャの論理書き込みの最小数は 1 つの実行中に実行しました。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_writes**|**bigint**|このストアド プロシージャの論理書き込みの最大数は 1 つの実行中に実行しました。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_reads**|**bigint**|コンパイルされたので、このストアド プロシージャの実行によって実行される、論理読み取りの合計数です。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_reads**|**bigint**|論理読み取りの数は、ストアド プロシージャが実行された最後の時間を実行します。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_reads**|**bigint**|このストアド プロシージャの論理読み取りの最小数は 1 つの実行中に実行しました。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_reads**|**bigint**|このストアド プロシージャの論理読み取りの最大数は 1 つの実行中に実行しました。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_elapsed_time**|**bigint**|合計の経過時間をマイクロ秒で、このストアド プロシージャの実行が完了したのです。|  
|**last_elapsed_time**|**bigint**|経過時間をマイクロ秒単位で、これの最後に完了した実行のためのストアド プロシージャです。|  
|**min_elapsed_time**|**bigint**|最小経過時間をマイクロ秒で、これを完了した実行用のストアド プロシージャです。|  
|**max_elapsed_time**|**bigint**|最大経過時間をマイクロ秒で、これを完了した実行用のストアド プロシージャです。|  
|**total_spills**|**bigint**|コンパイルされたので、このストアド プロシージャの実行をこぼしたのページの合計数です。<br /><br /> **適用される**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**last_spills**|**bigint**|ページの数は、ストアド プロシージャが実行された最後の時間をこぼした。<br /><br /> **適用される**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**min_spills**|**bigint**|このストアド プロシージャが 1 つの実行中にこれまでにこぼしたことページの最小数です。<br /><br /> **適用される**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**max_spills**|**bigint**|このストアド プロシージャが 1 つの実行中にこれまでにこぼしたことページの最大数です。<br /><br /> **適用される**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**pdw_node_id**|**int**|この配布であるノードの識別子。<br /><br />**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
 <sup>1</sup>ネイティブ コンパイル ストアド プロシージャの統計コレクションを有効にすると、ワーカー時間がミリ秒単位で収集します。 クエリが 1 ミリ秒未満で実行された場合は、値は 0 になります。  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
   
## <a name="remarks"></a>コメント  
 ビュー内の統計は、ストアド プロシージャの実行が完了したときに更新されます。  
  
## <a name="examples"></a>使用例  
 次の例では、平均経過時間で識別される上位 10 個のストアド プロシージャに関する情報を返します。  
  
```sql  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>参照  
[実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)    
[sys.dm_exec_trigger_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)    
[sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  
  


