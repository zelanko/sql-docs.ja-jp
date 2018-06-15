---
title: sys.query_store_runtime_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SYS.QUERY_STORE_RUNTIME_STATS_TSQL
- QUERY_STORE_RUNTIME_STATS_TSQL
- SYS.QUERY_STORE_RUNTIME_STATS
- QUERY_STORE_RUNTIME_STATS
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_runtime_stats catalog view
- sys.query_store_runtime_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 85bb7aa5bf91f8d357556adac9e58fb6ab83df24
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182358"
---
# <a name="sysquerystoreruntimestats-transact-sql"></a>sys.query_store_runtime_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  クエリのランタイム実行の統計情報についてを説明します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_id**|**bigint**|ランタイム実行統計情報を表す行の識別子、 **plan_id**、 **execution_type**と**runtime_stats_interval_id**です。 これは、ランタイム統計情報の過去の時間間隔に対してのみ一意です。 現在アクティブな間隔のある可能性があります複数の行によって参照されるプランの実行時統計を表す**plan_id**、によって表される実行の種類と**execution_type**です。 通常、1 つの行がフラッシュされたランタイム統計情報を表すその他の (s) がメモリ内状態を表すに対し、ディスクにします。 そのため、すべての間隔の実際の状態を取得する必要があります、集計されたメトリックによってグループ化**plan_id**、 **execution_type**と**runtime_stats_interval_id**です。 |  
|**plan_id**|**bigint**|外部キーです。 結合[sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)です。|  
|**runtime_stats_interval_id**|**bigint**|外部キーです。 結合[sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)です。|  
|**execution_type**|**tinyint**|クエリの実行の種類を決定します。<br /><br /> 0 ～ 通常の実行 (が正常に完了)<br /><br /> 3 – クライアントによって起動される実行を中止します。<br /><br /> 4-例外は、実行を中止します。|  
|**execution_type_desc**|**nvarchar(128)**|実行の種類のフィールドの説明テキスト。<br /><br /> 0 – 標準<br /><br /> 3 – 中止されました<br /><br /> 4-例外|  
|**first_execution_time**|**datetimeoffset**|集計間隔内に、クエリ プランの最初の実行時間。|  
|**last_execution_time**|**datetimeoffset**|クエリの最後の実行時間は、集計間隔に含まれる計画します。|  
|**count_executions**|**bigint**|集計間隔内でクエリ プランの実行数の合計数。|  
|**avg_duration**|**float**|(マイクロ秒単位で報告されます)、集計間隔内に、クエリ プランの実行時間を平均します。|  
|**last_duration**|**bigint**|クエリの最後の継続時間 (マイクロ秒単位で報告されます) 集計間隔に含まれる計画してください。|  
|**min_duration**|**bigint**|(マイクロ秒単位で報告されます)、集計間隔内でクエリ プランの最小期間。|  
|**max_duration**|**bigint**|(マイクロ秒単位で報告されます)、集計間隔内に、クエリ プランの最大継続時間。|  
|**stdev_duration**|**float**|(マイクロ秒単位で報告されます)、集計間隔内でクエリ プランの期間の標準偏差です。|  
|**avg_cpu_time**|**float**|CPU の平均時間 (マイクロ秒単位で報告されます)、集計間隔内に、クエリ プラン。|  
|**last_cpu_time**|**bigint**|クエリの最後の CPU 時間 (マイクロ秒単位で報告されます) 集計間隔に含まれる計画してください。|  
|**min_cpu_time**|**bigint**|最小 CPU 時間 (マイクロ秒単位で報告されます)、集計間隔内でクエリ プラン。|  
|**max_cpu_time**|**bigint**|(マイクロ秒単位で報告されます)、集計間隔内でクエリ プランの最大 CPU 時間。|  
|**stdev_cpu_time**|**float**|クエリの CPU 時間の標準偏差 (マイクロ秒単位で報告されます) 集計間隔に含まれる計画してください。|  
|**avg_logical_io_reads**|**float**|集計間隔内でクエリ プランの論理の IO の数の平均値を読み取ります。 (読み取られた 8 KB ページの数で表されます)。|  
|**last_logical_io_reads**|**bigint**|集計間隔内でクエリ プランの最後論理の IO の数を読み取ります。 (読み取られた 8 KB ページの数で表されます)。|  
|**min_logical_io_reads**|**bigint**|集計間隔内でクエリ プランの論理の IO の最小数を読み取ります。 (読み取られた 8 KB ページの数で表されます)。|  
|**max_logical_io_reads**|**bigint**|集計間隔内でクエリ プランの論理の IO の最大数を読み取ります。(読み取られた 8 KB ページの数で表されます)。 |  
|**stdev_logical_io_reads**|**float**|論理の IO の数は、集計間隔内に、クエリ プランの標準偏差を読み取ります。 (読み取られた 8 KB ページの数で表されます)。|  
|**avg_logical_io_writes**|**float**|集計間隔内に、クエリ プランの論理の IO の数の平均値を書き込みます。|  
|**last_logical_io_writes**|**bigint**|集計間隔内に、クエリ プランの最後論理の IO の数を書き込みます。|  
|**min_logical_io_writes**|**bigint**|集計間隔内に、クエリ プランの論理の IO の最小数を書き込みます。|  
|**max_logical_io_writes**|**bigint**|集計間隔内に、クエリ プランの論理の IO の最大数を書き込みます。|  
|**stdev_logical_io_writes**|**float**|論理の IO の数は、集計間隔内に、クエリ プランの標準偏差を書き込みます。|  
|**avg_physical_io_reads**|**float**|集計間隔 (読み取られた 8 KB ページの数で表されます) 内でクエリ プランの物理 IO の数の平均値を読み取ります。|  
|**last_physical_io_reads**|**bigint**|最後の物理 IO 読み取り数 (読み取られた 8 KB ページの数で表されます)、集計間隔内でクエリ プランの。|  
|**min_physical_io_reads**|**bigint**|集計間隔 (読み取られた 8 KB ページの数で表されます) 内でクエリ プランの物理 IO の最小数を読み取ります。|  
|**max_physical_io_reads**|**bigint**|集計間隔 (読み取られた 8 KB ページの数で表されます) 内でクエリ プランの物理 IO の最大数を読み取ります。|  
|**stdev_physical_io_reads**|**float**|物理 IO の数は、集計間隔 (読み取られた 8 KB ページの数で表されます) 内に、クエリ プランの標準偏差を読み取ります。|  
|**avg_clr_time**|**float**|CLR の平均時間 (マイクロ秒単位で報告されます)、集計間隔内に、クエリ プラン。|  
|**last_clr_time**|**bigint**|クエリの最後の CLR 時間 (マイクロ秒単位で報告されます) 集計間隔に含まれる計画してください。|  
|**min_clr_time**|**bigint**|(マイクロ秒単位で報告されます)、集計間隔内でクエリ プランの最小 CLR 時間。|  
|**max_clr_time**|**bigint**|(マイクロ秒単位で報告されます)、集計間隔内でクエリ プランの最大の CLR 時間です。|  
|**stdev_clr_time**|**float**|(マイクロ秒単位で報告されます)、集計間隔内でクエリ プランの CLR 時間標準偏差です。|  
|**avg_dop**|**float**|集計間隔内に、クエリ プランの平均 DOP (並列処理の次数)。|  
|**last_dop**|**bigint**|集計間隔内でクエリ プランの前回の DOP (並列処理の次数)。|  
|**min_dop**|**bigint**|集計間隔内に、クエリ プランの最小 DOP (並列処理の次数)。|  
|**max_dop**|**bigint**|集計間隔内に、クエリ プランの最大 DOP (並列処理の次数)。|  
|**stdev_dop**|**float**|集計間隔内でクエリ プランの DOP (並列処理の次数) の標準偏差です。|  
|**avg_query_max_used_memory**|**float**|平均メモリ許可 (8 KB ページ単位の数として報告されます) の集計間隔内でクエリ プラン。 常にネイティブを使用してクエリの場合は 0 では、メモリ最適化の手順がコンパイルされます。|  
|**last_query_max_used_memory**|**bigint**|最後のメモリ許可 (8 KB ページ単位の数として報告されます)、集計間隔内に、クエリ プラン。 常にネイティブを使用してクエリの場合は 0 では、メモリ最適化の手順がコンパイルされます。|  
|**min_query_max_used_memory**|**bigint**|最小メモリ許可 (8 KB ページ単位の数として報告されます) の集計間隔内でクエリ プラン。 常にネイティブを使用してクエリの場合は 0 では、メモリ最適化の手順がコンパイルされます。|  
|**max_query_max_used_memory**|**bigint**|最大メモリ許可 (8 KB ページ単位の数として報告されます) の集計間隔内でクエリ プラン。 常にネイティブを使用してクエリの場合は 0 では、メモリ最適化の手順がコンパイルされます。|  
|**stdev_query_max_used_memory です。**|**float**|メモリ許可の集計間隔内でクエリ プランの標準偏差を返します (8 KB ページ単位の数として報告されます)。 常にネイティブを使用してクエリの場合は 0 では、メモリ最適化の手順がコンパイルされます。|  
|**avg_rowcount**|**float**|集計間隔内でクエリ プランの返された行の平均数。|  
|**last_rowcount**|**bigint**|集計間隔内でクエリ プランの前回の実行で返される行の数。|  
|**min_rowcount**|**bigint**|集計間隔に含まれるクエリに対して返される行の最小数を計画します。|  
|**max_rowcount**|**bigint**|集計間隔に含まれるクエリに対して返される行の最大数を計画します。|  
|**stdev_rowcount**|**float**|集計間隔内でクエリ プランの標準偏差を返される行の数です。|
|**avg_log_bytes_used**|**float**|集計間隔内で、クエリ プランで使用されるデータベースのログのバイト数の平均数です。 適用**Azure SQL データベースにのみ**です。|    
|**last_log_bytes_used**|**bigint**|集計間隔内で、クエリ プランの前回の実行で使用されるデータベースのログのバイト数。 適用**Azure SQL データベースにのみ**です。|  
|**min_log_bytes_used**|**bigint**|集計間隔内で、クエリ プランで使用されるデータベースのログのバイト数の最小数。  適用**Azure SQL データベースにのみ**です。|  
|**max_log_bytes_used**|**bigint**|集計間隔内で、クエリ プランで使用されるデータベースのログのバイト数の最大数。  適用**Azure SQL データベースにのみ**です。| 
|**stdev_log_bytes_used**|**float**|集計間隔内でのクエリ プランで使用されるデータベースのログのバイト数の標準偏差。  適用**Azure SQL データベースにのみ**です。|
  
## <a name="permissions"></a>権限  
 必要があります、 **VIEW DATABASE STATE**権限です。  
  
## <a name="see-also"></a>参照  
 [sys.database_query_store_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [関連するビュー、関数、プロシージャ](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
