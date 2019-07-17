---
title: sys.database_query_store_options (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de6033aaa70b415ff7d218c2a0d8c3138845c8fc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022644"
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  このデータベースのクエリ ストア オプションを返します。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|ユーザーによって明示的に設定、クエリ ストアの目的の操作モードを示します。<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(60)**|クエリ ストアの目的の操作モードの説明テキスト。<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|クエリ ストアの操作モードを示します。 だけでなく、ユーザーが必要な目的の状態の一覧は、実際の状態がエラー状態を指定できます。<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = エラー|  
|**actual_state_desc**|**nvarchar(60)**|クエリ ストアの実際の操作モードの説明テキストです。<br />OFF<br />READ_ONLY<br />READ_WRITE<br />ERROR<br /><br /> 実際の状態が、目的の状態と異なる場合は、状況があります。<br />-データベースが読み取り専用モードに設定されている場合、またはクエリ ストアのサイズが構成されているクォータを超えた場合は、クエリ ストアは、読み取り/書き込みが、ユーザーが指定されていた場合でも読み取り専用モードで動作可能性があります。<br />極端なシナリオでクエリ ストアは、内部エラーにより、エラー状態を入力できます。 クエリ ストアを実行して回復できるこのような場合、SQL 2017 以降で、`sp_query_store_consistency_check`影響を受けたデータベースでストアド プロシージャ。 実行されている場合`sp_query_store_consistency_check`動作しないと、SQL 2016 を実行して、データを消去する必要があります `ALTER DATABASE [YourDatabaseName] SET QUERY_STORE CLEAR ALL;`|  
|**readonly_reason**|**int**|ときに、 **desired_state_desc**は READ_WRITE ですおよび**actual_state_desc**が READ_ONLY、 **readonly_reason**返しますは少しをクエリ ストアがであるかを示すマップ。読み取り専用モードです。<br /><br /> **1** -データベースが読み取り専用モード<br /><br /> **2** -データベースがシングル ユーザー モード<br /><br /> **4** -データベースが緊急モード<br /><br /> **8** -データベースがセカンダリ レプリカ (Always On の対象と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]geo レプリケーション)。 のみ、この値を効果的に確認できます**読み取り可能な**セカンダリ レプリカ<br /><br /> **65536** -クエリ ストアは MAX_STORAGE_SIZE_MB オプションによって設定されたサイズ制限に達しました。<br /><br /> **131072** -クエリのストア内の別のステートメントの数が内部メモリの上限に達しました。 不要なクエリを削除するか、クエリ ストアを読み取り/書き込みモードに転送を有効にする上位のサービス階層へのアップグレードを検討してください。<br />**適用対象:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]」を参照してください。<br /><br /> **262144** -ディスク上に保存するを待機しているメモリ内の項目のサイズが内部メモリの上限に達しました。 クエリ ストアは、メモリ内の項目がディスクに保存されるまで一時的に読み取り専用モードになります。 <br />**適用対象:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]」を参照してください。<br /><br /> **524288** -データベースはディスク サイズの上限に達しました。 クエリ ストア データベースに属しているユーザー、クエリ ストアをさらに拡張できないことを意味するデータベースは、できない場合の領域がない場合、できなくなります。<br />**適用対象:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]」を参照してください。 <br /> <br /> クエリ ストアの操作を切り替えるモード戻る読み取り/書き込みを参照してください**検証クエリ ストアは継続にクエリのデータを収集**の[クエリ ストアに関するベスト プラクティスとして](../../relational-databases/performance/best-practice-with-the-query-store.md#Verify)します。|  
|**current_storage_size_mb**|**bigint**|メガバイト単位でディスク上のクエリのストアのサイズ。|  
|**flush_interval_seconds**|**bigint**|クエリを定期的にフラッシュする期間は、秒単位でディスクにデータを格納します。 既定値は**900** (15 分)。<br /><br /> 使用して、変更、`ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)`ステートメント。|  
|**interval_length_minutes**|**bigint**|分単位で統計の集計間隔です。 任意の値を指定することはできません。 次のいずれかを使用します:1、5、10、15、30、60、および 1440 分です。 既定値は**60**分。|  
|**max_storage_size_mb**|**bigint**|メガバイト (MB) 単位でクエリ ストアの最大ディスク サイズです。 既定値は**100** MB です。<br />[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium edition の既定値は 1 GB と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]Basic エディションの既定値は 10 MB です。<br /><br /> 使用して、変更、`ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)`ステートメント。|  
|**stale_query_threshold_days**|**bigint**|ポリシー設定を持たないクエリがクエリのストアに保存しておく日数。 既定値は**30**します。 リテンション期間ポリシーを無効にする 0 に設定します。<br />[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic エディションの場合、既定の日数は 7 日です。<br /><br /> 使用して、変更、`ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )`ステートメント。|  
|**max_plans_per_query**|**bigint**|ストアド プランの最大数を制限します。 既定値は**200**します。 最大値に達すると、クエリ ストアは、そのクエリの新しいプランをキャプチャを停止します。 0 に設定には、キャプチャしたプランの数に関して制限が削除されます。<br /><br /> 使用して、変更、`ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)`ステートメント。|  
|**query_capture_mode**|**smallint**|現在アクティブなクエリ キャプチャ モード:<br /><br /> **1** = すべて - すべてのクエリがキャプチャされます。 これは、既定の構成値 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。<br /><br /> 2 = 自動 - 実行の数とリソースの消費量に基づいて関連するクエリをキャプチャします。 これは、既定の構成値の[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]します。<br /><br /> 3 = なし - 新しいクエリのキャプチャを停止します。 クエリ ストアは、既にキャプチャされたクエリのコンパイルと実行時の統計情報を収集し続けます。 重要なクエリのキャプチャされない可能性がありますので、この構成を注意深く使用します。|  
|**query_capture_mode_desc**|**nvarchar(60)**|クエリ ストアの実際のキャプチャ モードの説明テキスト。<br /><br /> すべて (既定値を[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> **自動**(既定値を[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> なし|  
|**size_based_cleanup_mode**|**smallint**|データの総量が最大サイズに近づいたときに、クリーンアップを自動的にアクティブにするかどうかを制御します。<br /><br /> 0 = OFF - サイズに基づくクリーンアップを自動的にアクティブ化されません。<br /><br /> **1** = 自動 - サイズに基づくクリーンアップはディスク上のサイズに達すると自動的にアクティブ**90%** の*max_storage_size_mb*します。 これは既定の構成値です。<br /><br />サイズのクリーンアップでは、まず最も安価で最も古いクエリを削除します。 約停止した**80%** の*max_storage_size_mb*に到達します。|  
|**size_based_cleanup_mode_desc**|**nvarchar(60)**|クエリ ストアの実際のサイズに基づくクリーンアップ モードの説明テキスト。<br /><br /> OFF <br /> **自動**(既定値)|  
|**wait_stats_capture_mode**|**smallint**|クエリ ストア待機統計情報のキャプチャを実行するかどうかを制御します。 <br /><br /> 0 = OFF <br /> **1** = ON<br /> **適用対象**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|
|**wait_stats_capture_mode_desc**|**nvarchar(60)**|実際の待機統計情報のキャプチャ モードの説明テキスト。 <br /><br /> OFF <br /> **ON** (既定値)<br /> **適用対象**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
  
## <a name="permissions"></a>アクセス許可  
 `VIEW DATABASE STATE` アクセス許可が必要です。  
  
## <a name="see-also"></a>関連項目  
 [sys.query_context_settings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
