---
title: sys.query_store_query (TRANSACT-SQL) |Microsoft Docs
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
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2837f590d6dcfc0cf260012c18834768059ce9ae
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43062015"
---
# <a name="sysquerystorequery-transact-sql"></a>sys.query_store_query (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  クエリとその関連する全体的な集計のランタイム実行の統計に関する情報が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|主キー。|  
|**query_text_id**|**bigint**|外部キーです。 結合[sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|外部キーです。 結合[sys.query_context_settings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)します。|  
|**object_id**|**bigint**|クエリが含まれるデータベース オブジェクトの ID (ストアド プロシージャ、トリガー、CLR UDF とユーザー定義集計などです。)。 データベース オブジェクト (アドホック クエリ) の一部として、クエリが実行されない場合は 0。|  
|**batch_sql_handle**|**varbinary(64)**|ステートメントのバッチ、クエリの ID では、一部です。 クエリが一時テーブルまたはテーブル変数を参照する場合にのみ設定されます。|  
|**query_hash**|**binary(8)**|論理クエリ ツリーに基づいて、個々 のクエリの MD5 ハッシュ。 オプティマイザー ヒントが含まれています。|  
|**is_internal_query**|**bit**|クエリは、内部的に生成されました。|  
|**query_parameterization_type**|**tinyint**|パラメーター化の種類。<br /><br /> 0 ～ なし<br /><br /> 1 – ユーザー<br /><br /> 2 – 簡単です<br /><br /> 3 – 強制|  
|**query_parameterization_type_desc**|**nvarchar(60)**|パラメーター化の種類の説明テキストです。|  
|**initial_compile_start_time**|**datetimeoffset**|開始時刻をコンパイルします。|  
|**last_compile_start_time**|**datetimeoffset**|開始時刻をコンパイルします。|  
|**last_execution_time**|**datetimeoffset**|最後の実行時間とは、最後に、クエリ/プランの終了時刻です。|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|クエリが、前回使用された最後の SQL バッチのハンドルです。 入力として提供する[sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)バッチの完全なテキストを取得します。|  
|**last_compile_batch_offset_start**|**bigint**|情報と共に last_compile_batch_sql_handle sys.dm_exec_sql_text に提供することができます。|  
|**last_compile_batch_offset_end**|**bigint**|情報と共に last_compile_batch_sql_handle sys.dm_exec_sql_text に提供することができます。|  
|**count_compiles**|**bigint**|コンパイルの統計情報です。|  
|**avg_compile_duration**|**float**|(マイクロ秒) の統計をコンパイルします。|  
|**last_compile_duration**|**bigint**|(マイクロ秒) の統計をコンパイルします。|  
|**avg_bind_duration**|**float**|(マイクロ秒) には、統計情報をバインドします。|  
|**last_bind_duration**|**bigint**|統計情報をバインドします。|  
|**avg_bind_cpu_time**|**float**|統計情報をバインドします。|  
|**last_bind_cpu_time**|**bigint**|統計情報をバインドします。|  
|**avg_optimize_duration**|**float**|マイクロ秒単位での最適化に関する統計。|  
|**last_optimize_duration**|**bigint**|最適化に関する統計。|  
|**avg_optimize_cpu_time**|**float**|マイクロ秒単位での最適化に関する統計。|  
|**last_optimize_cpu_time**|**bigint**|最適化に関する統計。|  
|**avg_compile_memory_kb**|**float**|メモリ統計情報をコンパイルします。|  
|**last_compile_memory_kb**|**bigint**|メモリ統計情報をコンパイルします。|  
|**max_compile_memory_kb**|**bigint**|メモリ統計情報をコンパイルします。|  
|**is_clouddb_internal_query**|**bit**|常に 0 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンプレミスです。|  
  
## <a name="permissions"></a>アクセス許可  
 必要があります、 **VIEW DATABASE STATE**権限。  
  
## <a name="see-also"></a>参照  
 [sys.database_query_store_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [関連するビュー、関数、プロシージャ](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
