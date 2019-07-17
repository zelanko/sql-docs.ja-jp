---
title: sys.dm_exec_function_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e67a50287e0878a3dcc0779bb4a78dbcbbdd0260
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68259255"
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>sys.dm_exec_function_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  集計キャッシュされた関数のパフォーマンス統計情報を返します。 ビューがキャッシュされている関数のプランごとに、1 つの行を返すし、行の有効期間は、関数が残っている限りキャッシュします。 関数がキャッシュから削除されると、対応する行がこのビューから削除します。 その時点では、パフォーマンス統計 SQL トレース イベントが発生するのような**sys.dm_exec_query_stats**します。 メモリ内の関数と CLR のスカラー関数を含む、スカラー関数に関する情報を返します。 テーブル値関数についての情報は返されません。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]では、動的管理ビューでデータベースの包含に影響を与える情報を公開することや、ユーザーがアクセスできる他のデータベースに関する情報を公開することはできません。 この情報を公開することを避けるため、接続されているテナントに属していないデータが含まれるすべての行はフィルターで除外します。  
  
> [!NOTE]
> 最初のクエリの**sys.dm_exec_function_stats**サーバーで現在実行中のワークロードがある場合、不正確な結果を生成可能性があります。 クエリを再実行すると、より正確な結果を確認できます。  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|関数が存在するデータベース ID。|  
|**object_id**|**int**|関数のオブジェクト id 番号。|  
|**type**|**char(2)**|次のいずれかのオブジェクトの種類。 FN = スカラー値関数|  
|**type_desc**|**nvarchar(60)**|オブジェクトの種類の説明です。SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|これでのクエリと関連付けるために使用できる**sys.dm_exec_query_stats**するは、この関数内から実行されました。|  
|**plan_handle**|**varbinary(64)**|メモリ内のプランの識別子。 この識別子は、一時的なプランをキャッシュに保持している間だけ一定のまま。 この値で使用できる、 **sys.dm_exec_cached_plans**動的管理ビュー。<br /><br /> 0x000 ときに、ネイティブ コンパイル関数クエリがメモリ最適化テーブルは常になります。|  
|**cached_time**|**datetime**|関数がキャッシュに追加された時刻。|  
|**last_execution_time**|**datetime**|関数が実行された最終時刻。|  
|**execution_count**|**bigint**|これ以降、関数が実行された回数を最後にコンパイルします。|  
|**total_worker_time**|**bigint**|コンパイルされた後に、この関数の実行で使用された (マイクロ秒) 内の CPU 時間の合計します。<br /><br /> ネイティブ コンパイル関数では、 **total_worker_time**多くの実行にかかる 1 ミリ秒未満の場合は、正確にできない可能性があります。|  
|**last_worker_time**|**bigint**|関数が実行された最後の時刻に使用された CPU 時間、マイクロ秒単位で。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|この関数で 1 回の実行中に使用された (マイクロ秒) の最小 CPU 時間。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|この関数で 1 回の実行中に使用された (マイクロ秒) の最大 CPU 時間。 <sup>1</sup>|  
|**total_physical_reads**|**bigint**|コンパイルされた後に、この関数の実行によって実行される物理読み取りの合計数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**last_physical_reads**|**bigint**|物理読み取りの数は、関数が実行された最終時刻を実行します。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**min_physical_reads**|**bigint**|この関数で 1 回の実行中に行われた物理読み取りの最小数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**max_physical_reads**|**bigint**|この関数で 1 回の実行中に行われた物理読み取りの最大数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**total_logical_writes**|**bigint**|コンパイルされた後に、この関数の実行によって実行される論理書き込みの合計数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**last_logical_writes**|**bigint**|前回プランが実行されたときにダーティになったバッファー プール ページの数。 ページが既にダーティの場合 (変更された場合)、書き込みはカウントされません。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**min_logical_writes**|**bigint**|この関数で 1 回の実行中に行われた論理書き込みの最小数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**max_logical_writes**|**bigint**|この関数で 1 回の実行中に行われた論理書き込みの最大数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**total_logical_reads**|**bigint**|コンパイルされた後に、この関数の実行によって実行される論理読み取りの合計数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**last_logical_reads**|**bigint**|論理読み取りの数は、関数が実行された最終時刻を実行します。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**min_logical_reads**|**bigint**|この関数で 1 回の実行中に行われた論理読み取りの最小数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**max_logical_reads**|**bigint**|この関数で 1 回の実行中に行われた論理読み取りの最大数。<br /><br /> 0 は、メモリ最適化テーブルのクエリは必ずします。|  
|**total_elapsed_time**|**bigint**|この関数の実行完了のマイクロ秒単位の合計経過時間。|  
|**last_elapsed_time**|**bigint**|この関数の最後に完了した実行のマイクロ秒単位の経過時間。|  
|**min_elapsed_time**|**bigint**|最小経過時間、いずれかのマイクロ秒単位には、この関数の実行を完了します。|  
|**max_elapsed_time**|**bigint**|最大経過時間をいずれかのマイクロ秒単位には、この関数の実行を完了します。|  
|**total_page_server_reads**|**bigint**|コンパイルされた後に、この関数の実行によって実行されるページ サーバーの読み取りの合計数。<br /><br /> **適用対象します。** Azure SQL データベースのハイパー スケールします。|  
|**last_page_server_reads**|**bigint**|関数が実行された最終時刻を実行するサーバーのページ読み取りの数。<br /><br /> **適用対象します。** Azure SQL データベースのハイパー スケールします。|  
|**min_page_server_reads**|**bigint**|ページ サーバーの最小数は、この関数が 1 回の実行中に行われたことを読み取ります。<br /><br /> **適用対象します。** Azure SQL データベースのハイパー スケールします。|  
|**max_page_server_reads**|**bigint**|ページ サーバーの最大数は、この関数が 1 回の実行中に行われたことを読み取ります。<br /><br /> **適用対象します。** Azure SQL データベースのハイパー スケールします。|
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   
  
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
  
## <a name="see-also"></a>関連項目  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys.dm_exec_procedure_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
