---
title: sys.query_store_plan (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_PLAN_TSQL
- SYS.QUERY_STORE_PLAN
- SYS.QUERY_STORE_PLAN_TSQL
- QUERY_STORE_PLAN
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_plan catalog view
- sys.query_store_plan catalog view
ms.assetid: b4d05439-6360-45db-b1cd-794f4a64935e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d1aee3dcdfe287e4d6db64be6c74edb7eb1362a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068047"
---
# <a name="sysquerystoreplan-transact-sql"></a>sys.query_store_plan (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  クエリに関連付けられている各実行プランに関する情報が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|
|**plan_id**|**bigint**|主キー。|  
|**query_id**|**bigint**|外部キーです。 結合[sys.query_store_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)します。|  
|**plan_group_id**|**bigint**|プランのグループの ID。 カーソル クエリには、複数通常必要があります (設定および fetch) プランです。 設定して、一緒にコンパイルされるフェッチ プランは、同じグループ内。<br /><br /> 0 は、グループが計画されていないことを意味します。|  
|**engine_version**|**nvarchar(32)**|プランのコンパイルに使用されているエンジンのバージョン **'major.minor.build.revision'** 形式。|  
|**compatibility_level**|**smallint**|クエリで参照されているデータベースのデータベース互換性レベルです。|  
|**query_plan_hash**|**binary(8)**|個々 のプランの MD5 ハッシュ。|  
|**query_plan**|**nvarchar(max)**|クエリ プランのプラン表示 XML です。|  
|**is_online_index_plan**|**bit**|プランは、オンラインのインデックス構築中に使用されました。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**is_trivial_plan**|**bit**|プランは、単純なプラン (出力では、クエリ オプティマイザーのステージ 0) です。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**is_parallel_plan**|**bit**|プランは並列です。 <br/>**注:** Azure SQL Data Warehouse (1) 1 つは常に返します。|  
|**is_forced_plan**|**bit**|プランが強制的にユーザーがストアド プロシージャを実行するときにマークされた**sys.sp_query_store_force_plan**します。 強制実行メカニズム*は保証されません*によって参照されるクエリを正確にこのプランが使用されること**query_id**します。 プランの強制再コンパイルするクエリし、通常同じまたは類似したプランによって参照されるプランに正確に生成されます**plan_id**します。 プランの強制が成功しなかった場合**force_failure_count**増加と**last_force_failure_reason**失敗の理由が表示されます。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**s_natively_compiled**|**bit**|プランには、ネイティブ コンパイルのメモリ最適化の手順が含まれます。 (0 = FALSE、1 = TRUE)。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**force_failure_count**|**bigint**|このプランの強制に失敗した回数。 クエリが再コンパイルされるときにだけインクリメントすることができます (*各実行ではなく*)。 毎回 0 にリセットされます**is_plan_forced**がから変更された**FALSE**に**TRUE**します。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**last_force_failure_reason**|**int**|プラン強制の失敗理由理由です。<br /><br /> 0: エラー、強制的に失敗する原因となったエラーのそれ以外の場合のエラー数<br /><br /> 8637:ONLINE_INDEX_BUILD<br /><br /> 8683:INVALID_STARJOIN<br /><br /> 8684:TIME_OUT<br /><br /> 8689:NO_DB<br /><br /> 8690:HINT_CONFLICT<br /><br /> 8691:SETOPT_CONFLICT<br /><br /> 8694:DQ_NO_FORCING_SUPPORTED<br /><br /> 8698:NO_PLAN<br /><br /> 8712:NO_INDEX<br /><br /> 8713:VIEW_COMPILE_FAILED<br /><br /> \<その他の値 >:GENERAL_FAILURE <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**last_force_failure_reason_desc**|**nvarchar(128)**|Last_force_failure_reason_desc の説明テキストです。<br /><br /> ONLINE_INDEX_BUILD。 クエリがターゲット テーブルにインデックスがオンラインに構築されているときに、データを変更しよう<br /><br /> INVALID_STARJOIN: プランには無効な StarJoin 仕様が含まれています<br /><br /> TIME_OUT:強制されたプランで指定したプランの検索中に許可される操作数のオプティマイザーを超えています<br /><br /> NO_DB:計画で指定されたデータベースが存在しません<br /><br /> HINT_CONFLICT:プランがクエリ ヒントと競合するためにクエリをコンパイルできません。<br /><br /> DQ_NO_FORCING_SUPPORTED:プランは、分散クエリまたはフルテキスト操作の使用と競合するため、クエリを実行することはできません。<br /><br /> NO_PLAN:強制されたプランがクエリに対して有効であることを確認できませんでした。 ので、クエリ プロセッサはクエリ プランを作成できませんでした。<br /><br /> NO_INDEX:不要になったのプランで指定されたインデックスが存在します。<br /><br /> VIEW_COMPILE_FAILED。計画で参照されているインデックス付きビューでの問題のためのクエリ プランを設定できませんでした。<br /><br /> GENERAL_FAILURE: 一般的な強制エラー (上の理由ではカバーしない) <br/>**注:** Azure SQL Data Warehouse は常に返します*NONE*します。|  
|**count_compiles**|**bigint**|コンパイルの統計情報を計画します。|  
|**initial_compile_start_time**|**datetimeoffset**|コンパイルの統計情報を計画します。|  
|**last_compile_start_time**|**datetimeoffset**|コンパイルの統計情報を計画します。|  
|**last_execution_time**|**datetimeoffset**|最後の実行時間とは、最後に、クエリ/プランの終了時刻です。|  
|**avg_compile_duration**|**float**|コンパイルの統計情報を計画します。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**last_compile_duration**|**bigint**|コンパイルの統計情報を計画します。 <br/>**注:** Azure SQL Data Warehouse は、ゼロ (0) を常に返します。|  
|**plan_forcing_type**|**int**|型の強制プランです。<br /><br />0:なし<br /><br />1:MANUAL<br /><br />2:AUTO|  
|**plan_forcing_type_desc**|**nvarchar(60)**|Plan_forcing_type の説明テキスト。<br /><br />NONE:プランの適用なし<br /><br />手動：ユーザーが強制されたプラン<br /><br />自動：自動チューニングによる強制プランします。|  

## <a name="plan-forcing-limitations"></a>プラン強制の制限事項
クエリ ストアには、クエリ オプティマイザーに特定の実行プランを使用させるためのメカニズムがあります。 ただし、適用の適用を妨げる可能性のある制限がいくつかあります。 

第 1 に、プランに次の構造が含まれる場合です。
* INSERT BULK ステートメント
* 外部テーブルの参照
* 分散クエリまたはフルテキスト操作
* グローバル クエリの使用 
* 動的カーソルまたはキーセット カーソル 
* 無効なスター結合の指定 

> [!NOTE]
> Azure SQL Database と SQL Server 2019 (プレビュー) に対する高速順方向カーソルと静的カーソル プランの強制をサポートします。

第 2 に、プランが依存しているオブジェクトが使用できなくなった場合です。
* データベース (プランの基になっているデータベースが存在しなくなった場合)
* インデックス (存在しない場合、または無効になった場合)

最後に、プラン自体に問題がある場合です。
* クエリに対して有効ではない
* クエリ オプティマイザーが許可されている操作の数を超えた
* プランの XML の形式が正しくない

## <a name="permissions"></a>アクセス許可  
 必要があります、 **VIEW DATABASE STATE**権限。  
  
## <a name="see-also"></a>参照  
 [sys.database_query_store_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
