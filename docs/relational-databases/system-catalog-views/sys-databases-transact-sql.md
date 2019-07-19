---
title: sys.databases (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- databases
- databases_TSQL
- sys.databases
- sys.databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.databases catalog view
ms.assetid: 46c288c1-3410-4d68-a027-3bbf33239289
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6817e41f48df740a59e371da9b78e09dd6894af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079387"
---
# <a name="sysdatabases-transact-sql"></a>sys.databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに、データベースごとに 1 行のデータを保持します。  
  
データベースがない場合`ONLINE`、または`AUTO_CLOSE`に設定されている`ON`と、データベースが閉じ、一部の列の値があります`NULL`します。 データベースがある場合`OFFLINE`、対応する行は低い特権のユーザーに表示されません。 データベースの場合、対応する行を表示する`OFFLINE`、ユーザーがいる必要があります、少なくとも`ALTER ANY DATABASE`サーバー レベルの権限または`CREATE DATABASE`でアクセス許可、`master`データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|インスタンス内で一意のデータベースの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内、または、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]サーバー。|  
|**database_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内、または [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバー内で一意な、データベースの識別子。|  
|**source_database_id**|**int**|NULL 以外 = このデータベース スナップショットのソース データベースの ID です。<br /> NULL = データベース スナップショットではありません。|  
|**owner_sid**|**varbinary(85)**|サーバーに登録されているデータベースの外部所有者の SID (セキュリティ識別子) にします。 データベースを所有する方法の詳細については、次を参照してください。、**データベースに対する ALTER AUTHORIZATION**の[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)します。|  
|**create_date**|**datetime**|日付、データベースの作成または変更します。 **Tempdb**、この値が、サーバーを再起動するたびに変更します。|  
|**compatibility_level**|**tinyint**|バージョンに対応する整数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のどちらの動作が互換性のあります。<br /> **値** &#124; **に適用されます**<br /> 70 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110 &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120 &#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130 &#124; [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 140 &#124; [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <br /> 150&#124; [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]  |  
|**collation_name**|**sysname**|データベースの照合順序です。 データベースの既定の照合順序として機能します。<br /> NULL = データベースがオンラインでないまたは AUTO_CLOSE が ON に設定され、データベースが閉じられます。|  
|**user_access**|**tinyint**|ユーザー アクセス設定です。<br /> 0 = MULTI_USER が指定されています。<br /> 1 = SINGLE_USER が指定されています。<br /> 2 = RESTRICTED_USER が指定されて|  
|**user_access_desc**|**nvarchar(60)**|ユーザー アクセス設定の説明です。|  
|**is_read_only**|**bit**|1 = データベースは READ_ONLY です。<br /> 0 = データベースは READ_WRITE です。|  
|**is_auto_close_on**|**bit**|1 = AUTO_CLOSE は ON です。<br /> 0 = AUTO_CLOSE は OFF です。|  
|**is_auto_shrink_on**|**bit**|1 = AUTO_SHRINK は ON です。<br /> 0 = AUTO_SHRINK は OFF です。|  
|**state**|**tinyint**|**値&#124;に適用されます**<br /> 0 = ONLINE <br /> 1 = を復元します。 <br /> 2 = RECOVERING &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 3 = RECOVERY_PENDING &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 4 = 問題あり <br /> 5 = EMERGENCY &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 6 = オフライン&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 7 = COPYING &#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY&#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **注:** Always On データベース クエリ、`database_state`または`database_state_desc`列[sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)します。|  
|**state_desc**|**nvarchar(60)**|データベースの状態の説明です。 状態を参照してください。|  
|**is_in_standby**|**bit**|データベースは、復元ログに対し、読み取り専用です。|  
|**is_cleanly_shutdown**|**bit**|1 = データベースは正常にシャット ダウン起動時に必要な復旧なし<br /> 0 = データベースはクリーンにシャットダウンされなかったため、起動時に復旧処理が必要です。|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING は ON です。<br /> 0 = SUPPLEMENTAL_LOGGING は OFF です。|  
|**snapshot_isolation_state**|**tinyint**|ALLOW_SNAPSHOT_ISOLATION オプションで設定された、許可されているスナップショット分離トランザクションの状態:<br /> 0 = スナップショット分離の状態は OFF です (既定)。 スナップショット分離は許可されていません。<br /> 1 = スナップショット分離の状態は ON です。 スナップショット分離が許可されます。<br /> 2 = スナップショット分離の状態が OFF に移行中は状態。 すべてのトランザクションで、その変更がバージョン管理されます。 スナップショット分離を使用して、新しいトランザクションを開始することはできません。 ALTER DATABASE が実行されたときにアクティブだったすべてのトランザクションが完了するまで、データベースは OFF に移行中の状態となります。<br /> 3 = スナップショット分離の状態が ON の状態に移行します。 新しいトランザクションでは、バージョン管理された、変更があります。 スナップショット分離の状態 (ON) 1 になるまで、トランザクションはスナップショット分離を使用できません。 データベースは、ALTER DATABASE が実行されたときにアクティブだったすべての更新トランザクションが完了するまで状態への移行に残ります。|  
|**snapshot_isolation_state_desc**|**nvarchar(60)**|ALLOW_SNAPSHOT_ISOLATION オプションで設定された、許可されているスナップショット分離トランザクションの状態の説明。|  
|**is_read_committed_snapshot_on**|**bit**|1 = READ_COMMITTED_SNAPSHOT オプションは ON です。 READ COMMITTED 分離レベルでの読み取り操作は、スナップショット スキャンに基づいており、ロックを取得しません。<br /> 0 = READ_COMMITTED_SNAPSHOT オプションは OFF です (既定)。 Read committed 分離レベルでの読み取り操作では、共有ロックを使用します。|  
|**recovery_model**|**tinyint**|選択される復旧モデル:<br /> 1 = 完全<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar(60)**|選択される復旧モデルの説明です。|  
|**page_verify_option**|**tinyint**|PAGE_VERIFY オプションの設定:<br /> 0 = NONE<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = チェックサム|  
|**page_verify_option_desc**|**nvarchar(60)**|PAGE_VERIFY オプション設定の説明です。|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS は ON です。<br /> 0 = AUTO_CREATE_STATISTICS は OFF です。|  
|**is_auto_create_stats_incremental_on**|**bit**|Auto stats の増分オプションの既定の設定を示します。<br /> 0 = 自動作成統計は増分<br /> 1 = 自動作成統計は増分可能な場合<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**is_auto_update_stats_on**|**bit**|1 = AUTO_UPDATE_STATISTICS は ON です。<br /> 0 = AUTO_UPDATE_STATISTICS は OFF です。|  
|**is_auto_update_stats_async_on**|**bit**|1 = AUTO_UPDATE_STATISTICS_ASYNC は ON です。<br /> 0 = AUTO_UPDATE_STATISTICS_ASYNC は OFF です。|  
|**is_ansi_null_default_on**|**bit**|1 = ANSI_NULL_DEFAULT は ON です。<br /> 0 = ANSI_NULL_DEFAULT は OFF です。|  
|**is_ansi_nulls_on**|**bit**|1 = ANSI_NULLS は ON です。<br /> 0 = ANSI_NULLS は OFF です。|  
|**is_ansi_padding_on**|**bit**|1 = ANSI_PADDING は ON です。<br /> 0 = ANSI_PADDING は OFF です。|  
|**is_ansi_warnings_on**|**bit**|1 = ANSI_WARNINGS は ON です。<br /> 0 = ANSI_WARNINGS は OFF です。|  
|**is_arithabort_on**|**bit**|1 = ARITHABORT は ON です。<br /> 0 = ARITHABORT は OFF です。|  
|**is_concat_null_yields_null_on**|**bit**|1 = CONCAT_NULL_YIELDS_NULL は ON です。<br /> 0 = CONCAT_NULL_YIELDS_NULL は OFF です。|  
|**is_numeric_roundabort_on**|**bit**|1 = NUMERIC_ROUNDABORT は ON です。<br /> 0 = NUMERIC_ROUNDABORT は OFF です。|  
|**is_quoted_identifier_on**|**bit**|1 = QUOTED_IDENTIFIER は ON です。<br /> 0 = QUOTED_IDENTIFIER は OFF です。|  
|**is_recursive_triggers_on**|**bit**|1 = RECURSIVE_TRIGGERS は ON です。<br /> 0 = RECURSIVE_TRIGGERS は OFF です。|  
|**is_cursor_close_on_commit_on**|**bit**|1 = CURSOR_CLOSE_ON_COMMIT is ON<br /> 0 = CURSOR_CLOSE_ON_COMMIT は OFF です。|  
|**is_local_cursor_default**|**bit**|1 = CURSOR_DEFAULT はローカルです<br /> 0 = CURSOR_DEFAULT はグローバル|  
|**is_fulltext_enabled**|**bit**|1 = データベースに対してフルテキストが有効です。<br /> 0 = データベースのフルテキストが無効になっています|  
|**is_trustworthy_on**|**bit**|1 = データベースが信頼可能のマークにされている場合<br /> 0 = データベースがマークされていない信頼|  
|**is_db_chaining_on**|**bit**|1 = 複数データベースにまたがる組み合わせ所有権は ON です。<br /> 0 = 複数データベースの組み合わせ所有権は OFF です。|  
|**is_parameterization_forced**|**bit**|1 = パラメーター化は FORCED です。<br /> 0 = パラメーター化は SIMPLE|  
|**is_master_key_encrypted_by_server**|**bit**|1 = データベースが暗号化されたマスター_キー<br /> 0 = データベースは暗号化されたマスター キーを保有していません。|  
|**is_query_store_on**|**bit**|1 = クエリ ストアがこのデータベースを有効にします。 確認[sys.database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)クエリ ストアの状態を表示します。<br /> 0 = クエリ ストアが有効になっていません<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] まで)。|  
|**is_published**|**bit**|1 = データベースは、トランザクションまたはスナップショット レプリケーション トポロジでパブリケーション データベース<br /> 0 = パブリケーション データベースではありません|  
|**is_subscribed**|**bit**|この列は使用されません。 データベースのサブスクライバーの状態に関係なく、常に 0 を返します。|  
|**is_merge_published**|**bit**|1 = データベースは、マージ レプリケーション トポロジにおけるパブリケーション データベースです。<br /> 0 = マージ レプリケーション トポロジにおけるパブリケーション データベースではありません。|  
|**is_distributor**|**bit**|1 = データベースは、レプリケーション トポロジにおけるディストリビューション データベース<br /> 0 = レプリケーション トポロジにおけるディストリビューション データベースではありません|  
|**is_sync_with_backup**|**bit**|1 = データベースはバックアップとのレプリケーション同期用に設定されています。<br /> 0 = バックアップとのレプリケーション同期用に設定されていません。|  
|**service_broker_guid**|**uniqueidentifier**|このデータベースの Service Broker の識別子です。 として使用される、 **broker_instance**のルーティング テーブル内のターゲット。|  
|**is_broker_enabled**|**bit**|1 = このブローカー データベースが現在の送信とメッセージを受信します。<br /> 0 = このデータベースでは、すべての送信メッセージは転送キューにとどまり、受信メッセージはキューに配置されません。<br /> 既定では、復元またはアタッチされたデータベースは、ブローカーが無効になっているがあります。 ただし、フェールオーバー後にブローカーが有効になるデータベース ミラーリングは例外です。|  
|**log_reuse_wait**|**tinyint**|トランザクション ログ領域の再利用は、最後のチェックポイントの時点で、次のいずれかで現在待機中です。 詳細なこれらの値の説明についてを参照してください。[トランザクション ログ](../../relational-databases/logs/the-transaction-log-sql-server.md)します。<br /> **値&#124;に適用されます**<br /> 0 = なし<br />   1 = チェックポイント (データベースでは、復旧モデルを使用して、メモリ最適化データ ファイル グループがときに、表示する必要する必要があります、`log_reuse_wait`列がチェックポイントまたは xtp_checkpoint を示すためです)。&#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  2 = ログ バックアップ&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  3 = アクティブなバックアップまたは復元&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  4 = アクティブなトランザクション&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  5 = データベース ミラーリング&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  6 = レプリケーション&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  7 = データベース スナップショットの作成&#124;[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  8 = ログ スキャン <br />  9 = an Always On 可用性グループ セカンダリ レプリカが、対応するセカンダリ データベースにこのデータベースのトランザクション ログ レコードを適用します。 &#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  9 = その他 (一時的)&#124;的にします。 [!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)]<br />  10 = 内部使用のみ&#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  11 = 内部使用のみ&#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 12 = 内部使用のみ&#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />13 = 最も古いページ&#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 14 = その他&#124;[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  16 = XTP_CHECKPOINT (データベース復旧モデルを使用するとおり、メモリ最適化データ ファイル グループ、はず、log_reuse_wait 列がチェックポイントまたは xtp_checkpoint を参照してください)。&#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**log_reuse_wait_desc**|**nvarchar(60)**|前回のチェックポイントの時点で現在待機中の、トランザクション ログ領域の再利用の理由の説明です。|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION は ON です。<br /> 0 = DATE_CORRELATION_OPTIMIZATION は OFF です。|  
|**is_cdc_enabled**|**bit**|1 = データベースは変更データ キャプチャを有効にします。 詳細については、次を参照してください。 [sys.sp_cdc_enable_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)します。|  
|**is_encrypted**|**bit**|データベースが暗号化されているかどうかを示します (最後に設定を使用して状態を反映、`ALTER DATABASE SET ENCRYPTION`句)。 次のいずれかの値になります。<br /> 1 = 暗号化<br /> 0 = 暗号化されていません。<br /> データベース暗号化の詳細については、「[Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。<br /> 場合は、データベースが暗号化が解除されて`is_encrypted`0 の値が表示されます。 使用して暗号化プロセスの状態を確認することができます、 [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)動的管理ビュー。|  
|**is_honor_broker_priority_on**|**bit**|データベースはメッセージ交換の優先度を優先するかどうかを示します (最後に設定を使用して状態を反映、`ALTER DATABASE SET HONOR_BROKER_PRIORITY`句)。 次のいずれかの値になります。<br /> 1 = HONOR_BROKER_PRIORITY は ON です。<br /> 0 = HONOR_BROKER_PRIORITY は OFF です。|  
|**replica_id**|**uniqueidentifier**|データベースが参加している可用性グループ (存在する場合) のローカル [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 可用性レプリカの一意の識別子です。<br /> NULL = データベースが可用性グループの可用性レプリカの一部ではありません。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**uniqueidentifier**|Always On 可用性グループ、存在するデータベースが参加している場合内のデータベースの一意の識別子。 **group_database_id**をデータベースが参加している可用性グループにすべてのセカンダリ レプリカとプライマリ レプリカでは、このデータベースに同じです。<br /> NULL = データベースは、任意の可用性グループの可用性レプリカの一部ではありません。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|このデータベースにマップされているリソース プールの id。 このリソース プールでは、このデータベースにメモリ最適化テーブルで使用できる合計メモリを制御します。<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**default_language_lcid**|**smallint**|包含データベースの既定の言語のローカル id (lcid) を示します。<br /> **注:** として機能、 [default language サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md)の`sp_configure`します。 この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128)**|包含データベースの既定の言語を示します。<br /> この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|包含データベースの既定のフルテキスト言語のロケール id (lcid) を示します。<br /> **注:** 既定値として関数[サーバー構成オプションの既定のフルテキスト言語を構成する](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md)の`sp_configure`します。 この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128)**|包含データベースの既定のフルテキスト言語を示します。<br /> この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|トリガーが包含データベースで許可される入れ子になっているかどうかを示します。<br /> 0 = 入れ子になったトリガーは許可されません。<br /> 1 = 入れ子になったトリガーが許可されます。<br /> **注:** として機能、 [nested triggers サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)の`sp_configure`します。 この値は**null**非包含データベースです。 参照してください[sys.configurations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)についてさらにします。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|示すかどうかまたは包含データベースでノイズ ワードを変換する必要があります。<br /> 0 = ノイズ ワードは変換する必要がありません。<br /> 1 = ノイズ ワードは変換する必要があります。<br /> **注:** として機能、 [transform noise words サーバー構成オプション](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)の`sp_configure`します。 この値は**null**非包含データベースです。 参照してください[sys.configurations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)についてさらにします。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**two_digit_year_cutoff**|**smallint**|2 桁の年を 4 桁の西暦年として解釈終了年を表す 1753 ~ 9999 の数値の値を示します。<br /> **注:** として機能、[構成 two digit year cutoff サーバー構成オプション](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)の`sp_configure`します。 この値は**null**非包含データベースです。 参照してください[sys.configurations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)についてさらにします。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**containment**|**null でない tinyint**|データベースの包含状態を示します。<br />  0 = データベースの包含がオフです。 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = データベースは部分的な包含**に適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**containment_desc**|**null でない nvarchar (60)**|データベースの包含状態を示します。<br /> NONE = 従来のデータベース (包含なし)<br /> PARTIAL = 部分的包含データベース<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|秒単位でデータベースの復旧の推定時間。 Null 値を許容します。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|遅延持続性の設定:<br /> 0 = 無効になっています<br /> 1 = 許可<br /> 2 = 強制<br /> 詳しくは、「[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)」をご覧ください。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
|**delayed_durability_desc**|**nvarchar(60)**|遅延持続性の設定:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
|**is_memory_optimized_elevate_to_snapshot_on**|**bit**|セッション設定 TRANSACTION ISOLATION LEVEL が低い分離レベル (READ COMMITTED または READ UNCOMMITTED) に設定されている場合は、SNAPSHOT 分離を使用してメモリ最適化テーブルにアクセスします。<br /> 1 = 最小分離レベルは SNAPSHOT です。<br /> 0 = 分離レベルは引き上げられません。|  
|**is_federation_member**|**bit**|データベースがフェデレーションのメンバーであることを示します。<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|データベースが拡大するかどうかを示します。<br /> 0 = データベースは Stretch が有効ではありません。<br /> 1 = データベースは Stretch に対応します。<br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 詳細については、「[Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。|  
|**is_mixed_page_allocation_on**|**bit**|かどうか、データベースにテーブルとインデックスから割り当てられる最初のページ混合エクステントを示します。<br /> 0 = テーブル、データベース内のインデックスは常に単一エクステントから最初のページを割り当てるとします。<br /> 1 = テーブルと、データベース内のインデックスは、混合エクステントから最初のページを割り当てることができます。<br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 詳細については、の SET MIXED_PAGE_ALLOCATION オプションを参照してください。 [ALTER DATABASE SET Options &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)します。|  
|**is_temporal_retention_enabled**|**bit**|テンポラル リテンション期間ポリシーのクリーンアップ タスクが有効になっているかどうかを示します。<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type**|**int**|カタログ照合順序の設定:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type_desc**|**nvarchar(60)**|カタログ照合順序の設定:<br />COLLATE<br />SQL_Latin_1_General_CP1_CI_AS<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**is_result_set_caching_on**|**int**|1 = is_result_set_caching_on が上</br>0 = is_result_set_caching_on はオフです</br>**適用対象**:Azure SQL Data Warehouse Gen2 します。 この機能は、すべてのリージョンにロールアウトされているが、中に、インスタンスと、最新バージョンに配置されているバージョンを確認してください[Azure SQL DW のリリース ノート](/azure/sql-data-warehouse/release-notes-10-0-10106-0)機能の可用性を実現します。|
  
## <a name="permissions"></a>アクセス許可  
 場合、呼び出し元の`sys.databases`データベースの所有者ではないと、データベースが`master`または`tempdb`、対応する行を表示するために必要な最小限のアクセス許可は`ALTER ANY DATABASE`または`VIEW ANY DATABASE`サーバー レベルの権限、または`CREATE DATABASE`でアクセス許可、`master`データベース。 呼び出し元が接続されているデータベースはで常に表示する`sys.databases`します。  
  
> [!IMPORTANT]  
> 既定の public ロールは、`VIEW ANY DATABASE`データベース情報を参照するすべてのログインを許可する権限。 データベースを検出する機能からのログインをブロックする`REVOKE`、`VIEW ANY DATABASE`からのアクセス許可`public`、または`DENY`、`VIEW ANY DATABASE`個別のログインのアクセスを許可します。  
  
## <a name="azure-sql-database-remarks"></a>Azure SQL データベースの解説  
[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]このビューで使用できる、`master`データベースとユーザー データベース。 `master`のデータベースでは、このビューを返します、情報、`master`データベースとサーバー上のすべてのユーザー データベース。 ユーザー データベースでは、このビューには、現在のデータベースと master データベースのみの情報が返されます。  
  
 新しいデータベースが作成される [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバーの `master` データベースの `sys.databases` ビューを使用します。 データベースのコピーが開始されると、クエリを実行できます、`sys.databases`と`sys.dm_database_copies`ビューから、`master`コピーの進行状況に関する詳細情報を取得する移行先サーバーのデータベース。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-query-the-sysdatabases-view"></a>A. sys.databases ビューに対するクエリ  
 次の例で使用できる列のいくつかを返します、`sys.databases`ビュー。  
  
```sql  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>B. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] でのコピーの進行状況を確認します。  
 次の例のクエリ、`sys.databases`と`sys.dm_database_copies`データベースに関する情報を返すビューは、操作をコピーします。  
  
**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```  
### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>C. テンポラル リテンション期間ポリシーの状態を確認します。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 次の例のクエリ、`sys.databases`テンポラル保有期間のクリーンアップ タスクが有効になっているかどうかの情報を返します。 復元操作後にテンポラル リテンション期間は既定で無効があります。 使用`ALTER DATABASE`を明示的に有効にします。
  
**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.is_temporal_history_retention_enabled 
FROM sys.databases AS a;
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.database_recovery_status &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-recovery-status-transact-sql.md)   
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.dm_database_copies &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)  
  
  
