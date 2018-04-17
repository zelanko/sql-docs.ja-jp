---
title: sys.database_query_store_options (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1c048c66e20e210f84d26dbff492aede56839fe2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このデータベースのクエリのストアのオプションを返します。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|クエリのストア、ユーザーによって明示的に設定の目的の操作モードを示します。<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(64)**|クエリのストアの目的の操作モードの説明テキスト。<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|クエリのストアの操作モードを示します。 だけでなく、ユーザーが必要とされる目的の状態の一覧は、実際の状態がエラー状態を指定できます。<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = エラー|  
|**actual_state_desc**|**nvarchar(64)**|クエリのストアの実際の操作モードの説明テキストです。<br />OFF<br />READ_ONLY<br />READ_WRITE<br />ERROR<br /><br /> 実際の状態が、目的の状態と異なる場合は、状況があります。<br /><br /> クエリ ストアは、読み取り/書き込みが、ユーザーが指定されていた場合でも、読み取り専用モードで動作可能性があります。 たとえば、データベースが読み取り専用モードの場合、またはクエリ ストアのサイズがクォータを超えた場合を問題が発生する可能性です。<br /><br /> 非常にまれに、クエリ ストアが最終的にエラー状態に内部エラーがあるためです。 この場合、クエリ ストアによって回復可能な実行**sp_query_store_consistency_check**影響を受けたデータベース内のプロシージャを格納します。|  
|**readonly_reason**|**int**|ときに、 **desired_state_desc**は READ_WRITE ですおよび**actual_state_desc**は、READ_ONLY、 **readonly_reason**を返しますが、少し理由は、クエリのストアを示すためにマップ。読み取り専用モードです。<br /><br /> 1 – データベースが読み取り専用モードには<br /><br /> 2 – データベースがシングル ユーザー モードです。<br /><br /> 4: データベースが緊急モードです。<br /><br /> 8-データベースがセカンダリ レプリカ (Always On と Azure に適用されます[!INCLUDE[ssSDS](../../includes/sssds-md.md)]geo レプリケーション)。 のみ、この値を効果的に監視できます**読み取り可能な**セカンダリ レプリカ<br /><br /> 65536: クエリのストアは MAX_STORAGE_SIZE_MB オプションによって設定されたサイズ制限に達しました。<br /><br /> 131, 072-クエリのストア内の別のステートメントの数は、内部メモリの上限に達しました。 必要としないクエリを削除するか、クエリ ストアを読み取り/書き込みモードに転送を有効にする上位のサービス階層へのアップグレードを検討してください。<br />[!INCLUDE[ssSDS](../../includes/sssds-md.md)]だけに適用されます。<br /><br /> でも 262, 144 – ディスクに永続化を待機しているメモリ内の項目のサイズは、内部メモリの制限に達しました。 メモリ内の項目はディスクに保存されるまで一時的に、クエリのストアは読み取り専用モードになります。 <br />[!INCLUDE[ssSDS](../../includes/sssds-md.md)]だけに適用されます。<br /><br />524288 – データベースは、ディスク サイズの上限に達しました。 クエリ ストアはユーザー データベースの一部なくなることを意味する、データベース領域がある場合はクエリ ストアがさらに増やすことができませんされなくなります。<br />[!INCLUDE[ssSDS](../../includes/sssds-md.md)]だけに適用されます。 <br /> <br /> クエリ ストアの操作を切り替えるにはモードに戻る読み取り/書き込みを参照してください**を確認してくださいクエリ ストアは、クエリのデータを連続して収集**のセクション[クエリ ストアに関するベスト プラクティスとして](../../relational-databases/performance/best-practice-with-the-query-store.md)です。|  
|**current_storage_size_mb**|**bigint**|メガバイト単位でディスク上のクエリのストアのサイズ。|  
|**flush_interval_seconds**|**bigint**|データのクエリの格納が正規ディスクにフラッシュする期間を定義します。 既定値は 900 (15 分) です。<br /><br /> 変更を使用して、`ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)`ステートメントです。|  
|**interval_length_minutes**|**bigint**|統計の集計間隔です。 任意の値を指定することはできません。 次のいずれかを使用します。 1、5、10、15、30、60、および 1440 分です。 既定値は、60 分です。|  
|**max_storage_size_mb**|**bigint**|クエリのストアの最大のディスクのサイズです。 既定値は、100 MB です。<br />[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition の既定値は 1 Gb、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic エディションの既定値は 10 Mb です。<br /><br /> 変更を使用して、`ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)`ステートメントです。|  
|**stale_query_threshold_days**|**bigint**|ないポリシー設定を使用したクエリのクエリのストアに保存しておく日数です。 既定値は 30 です。 保有ポリシーを無効にする 0 に設定します。<br />[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic エディションの場合、既定の日数は 7 日です。<br /><br /> 変更を使用して、`ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )`ステートメントです。|  
|**max_plans_per_query**|**bigint**|ストアド プランの最大数を制限します。 既定値は、200 です。 最大値に達すると、クエリのストアは、そのクエリへの新しいプランをキャプチャを停止します。 0 に設定は、キャプチャしたプランの数に関する制限を削除します。<br /><br /> 変更を使用して、`ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)`ステートメントです。|  
|**query_capture_mode**|**smallint**|現在アクティブなクエリのキャプチャ モード:<br /><br /> 1 = すべて - すべてのクエリが自動的にキャプチャされます。 これは、既定の構成値 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。<br /><br /> 2 = 自動 - 実行の数とリソースの消費量に基づいて関連するクエリをキャプチャします。 これは、既定の構成値[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。<br /><br /> 3 = なし - 新しいクエリのキャプチャを停止します。 クエリ ストアは、既にキャプチャされたクエリのコンパイルと実行時の統計情報を収集し続けます。 重要なクエリをキャプチャするされない場合がありますので、慎重に行ってこの構成を使用します。|  
|**query_capture_mode_desc**|**nvarchar(60)**|クエリのストアの実際のキャプチャ モードの説明テキスト。<br /><br /> すべて (既定の[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> 自動 (既定の[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> なし|  
|**size_based_cleanup_mode**|**smallint**|かどうかのクリーンアップが自動的にアクティブになるデータの合計サイズを取得する最大サイズに近いかを制御します。<br /><br /> 1 = OFF – サイズに基づいてのクリーンアップを自動的にアクティブ化されません。<br /><br /> 2 = 自動 - サイズに基づいてのクリーンアップはサイズのディスクに達したときの 90% のときに自動的にアクティブ**max_storage_size_mb**です。 これは、既定の構成値です。<br /><br />サイズのクリーンアップでは、まず最も安価で最も古いクエリを削除します。 Max_storage_size_mb の約 80% で停止します。|  
|**size_based_cleanup_mode_desc**|**smallint**|クエリのストアの実際のサイズに基づくクリーンアップ モードの説明テキスト。<br /><br /> OFF <br /><br /> 自動 (既定)|  
|**wait_stats_capture_mode**|**smallint**|クエリ ストアが待機の統計情報のキャプチャを実行するかどうかを制御します。 <br /><br /> 0 = OFF <br /><br /> 1 = ON <br /> **適用対象**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|
|**wait_stats_mode_capture_desc**|**nvarchar(60)**|実際の待機統計情報のキャプチャ モードの説明テキスト。 <br /><br /> OFF <br /><br /> (既定)<br /> **適用対象**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]| 
  
## <a name="permissions"></a>権限  
 必要があります、 **VIEW DATABASE STATE**権限です。  
  
## <a name="see-also"></a>参照  
 [sys.query_context_settings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [関連するビュー、関数、プロシージャ](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
