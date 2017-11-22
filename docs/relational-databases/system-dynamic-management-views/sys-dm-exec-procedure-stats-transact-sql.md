---
title: "sys.dm_exec_procedure_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f935b0e9a4c150830a03ecb2ea1f67a4cd270d3f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  キャッシュされたストアド プロシージャの集計パフォーマンス統計を返します。 ビューは、キャッシュされたストアド プロシージャのプランごとに 1 行を返します。その行の有効期間はストアド プロシージャがキャッシュに残っている間になります。 つまり、ストアド プロシージャがキャッシュから削除されると、対応する行もこのビューから削除されます。 その時点でパフォーマンス統計 SQL トレース イベントが発生したような**sys.dm_exec_query_stats**です。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  
  
> **注:**の最初のクエリ**sys.dm_exec_procedure_stats**サーバーで現在実行中のワークロードがある場合、不正確な結果を生じる可能性があります。 クエリを再実行すると、より正確な結果を確認できます。  
  
> **Azure SQL Data Warehouse に注意してください。** これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_exec_procedure_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ストアド プロシージャが存在するデータベースの ID。|  
|**object_id**|**int**|ストアド プロシージャのオブジェクト ID 番号。|  
|**型**|**char(2)**|次のいずれかのオブジェクトの種類。<br /><br /> P = SQL ストアド プロシージャ<br /><br /> PC = アセンブリ (CLR) ストアド プロシージャ<br /><br /> X = 拡張ストアド プロシージャ|  
|**type_desc**|**nvarchar (60)**|オブジェクトの種類の説明です。<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary (64)**|これは、クエリと関連付けるために使用できる**sys.dm_exec_query_stats**するは、このストアド プロシージャ内から実行されました。|  
|**plan_handle**|**varbinary (64)**|インメモリ プランの識別子。 この識別子は一時的なもので、プランがキャッシュに残っている間だけ一定の値になります。 この値で使用することがあります、 **sys.dm_exec_cached_plans**動的管理ビュー。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0x000 になります。|  
|**cached_time**|**datetime**|ストアド プロシージャがキャッシュに追加された時刻。|  
|**last_execution_time**|**datetime**|前回ストアド プロシージャが実行された時刻。|  
|**execution_count**|**bigint**|前回のコンパイル時以降に、ストアド プロシージャが実行された回数。|  
|**total_worker_time**|**bigint**|コンパイル後にストアド プロシージャの実行で使用された CPU 時間の合計 (マイクロ秒単位)。<br /><br /> ネイティブ コンパイル ストアド プロシージャに関して、多くの実行が 1 ミリ秒未満である場合は、 **total_worker_time** は精度が高くない可能性があります。|  
|**last_worker_time**|**bigint**|ストアド プロシージャを前回実行したときに使用された CPU 時間 (マイクロ秒単位)。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|このストアド プロシージャの 1 回の実行で使用された最小 CPU 時間 (マイクロ秒単位)。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|このストアド プロシージャの 1 回の実行で使用された最大 CPU 時間 (マイクロ秒単位)。 <sup>1</sup>|  
|**トリガー**|**bigint**|コンパイル後にこのストアド プロシージャの実行で行われた物理読み取りの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_physical_reads**|**bigint**|ストアド プロシージャを前回実行したときに行われた物理読み取りの数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_physical_reads**|**bigint**|このストアド プロシージャの 1 回の実行で行われた物理読み取りの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_physical_reads**|**bigint**|このストアド プロシージャの 1 回の実行で行われた物理読み取りの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_writes**|**bigint**|コンパイル後にこのストアド プロシージャの実行で行われた論理書き込みの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_writes**|**bigint**|前回プランが実行されたときにダーティになったバッファー プール ページの数。 ページが既にダーティの場合 (変更された場合)、書き込みはカウントされません。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_writes**|**bigint**|このストアド プロシージャの 1 回の実行で行われた論理書き込みの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_writes**|**bigint**|このストアド プロシージャの 1 回の実行で行われた論理書き込みの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_reads**|**bigint**|コンパイル後にこのストアド プロシージャの実行で行われた論理読み取りの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_reads**|**bigint**|ストアド プロシージャを前回実行したときに行われた論理読み取りの数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_reads**|**bigint**|このストアド プロシージャの 1 回の実行で行われた論理読み取りの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_reads**|**bigint**|このストアド プロシージャの 1 回の実行で行われた論理読み取りの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_elapsed_time**|**bigint**|このストアド プロシージャの実行完了までの経過時間の合計 (マイクロ秒単位)。|  
|**last_elapsed_time**|**bigint**|このストアド プロシージャの前回の実行完了までの経過時間 (マイクロ秒単位)。|  
|**min_elapsed_time**|**bigint**|任意のストアド プロシージャの実行完了までの最小経過時間 (マイクロ秒単位)。|  
|**max_elapsed_time**|**bigint**|任意のストアド プロシージャの実行完了までの最大経過時間 (マイクロ秒単位)。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
 <sup>1</sup>ネイティブ コンパイル ストアド プロシージャに対する統計コレクションを有効にすると、ワーカー時間がミリ秒単位で収集します。 クエリが 1 ミリ秒未満で実行された場合は、値は 0 になります。  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。 
  
## <a name="remarks"></a>解説  
 ビュー内の統計は、ストアド プロシージャの実行が完了したときに更新されます。  
  
## <a name="examples"></a>使用例  
 次の例では、平均経過時間で識別される上位 10 個のストアド プロシージャに関する情報を返します。  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
  


