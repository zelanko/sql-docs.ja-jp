---
title: sys. databases (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 02/11/2020
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
ms.openlocfilehash: 5b9b5147621fb459e419a29e0a31f9ad9381eb77
ms.sourcegitcommit: 9bdecafd1aefd388137ff27dfef532a8cb0980be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2020
ms.locfileid: "77147399"
---
# <a name="sysdatabases-transact-sql"></a>sys.databases (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]


  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに、データベースごとに 1 行のデータを保持します。  
  
データベース`ONLINE`がでない場合、また`AUTO_CLOSE`はに設定`ON`されていて、データベースが閉じている場合は`NULL`、一部の列の値がになることがあります。 データベースが`OFFLINE`の場合、対応する行は低い特権のユーザーには表示されません。 データベースが`OFFLINE`である場合に対応する行を表示するには、少なくと`ALTER ANY DATABASE`もサーバーレベルの権限、また`CREATE DATABASE`は`master`データベース内の権限を持っている必要があります。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス内または[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]サーバー内で一意のデータベースの名前。|  
|**database_id**|**int**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内、または [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバー内で一意な、データベースの識別子。|  
|**source_database_id**|**int**|NULL 以外 = このデータベース スナップショットのソース データベースの ID です。<br /> NULL = データベース スナップショットではありません。|  
|**owner_sid**|**varbinary (85)**|サーバーに登録したデータベースの外部所有者の SID (セキュリティ識別子) です。 データベースを所有できるユーザーの詳細については、「alter [authorization](../../t-sql/statements/alter-authorization-transact-sql.md)」の「 **alter authorization for databases** 」セクションを参照してください。|  
|**create_date**|**DATETIME**|データベースの作成または名前の変更を行った日付です。 **Tempdb**の場合は、サーバーが再起動されるたびにこの値が変更されます。|  
|**compatibility_level**|**tinyint**|動作に互換性のある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンに対応する整数です。<br /> **値**&#124;**適用さ**れます<br /> 70 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]から[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]から[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]から[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降および[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110 &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降および[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120 &#124; [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]以降および[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130 &#124; [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降<br /> 140 &#124; [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]以降 <br /> 150 &#124;[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]  |  
|**collation_name**|**sysname**|データベースの照合順序です。 データベースの既定の照合順序として機能します。<br /> NULL = データベースがオンラインでないか、AUTO_CLOSE が ON に設定されていて、データベースが閉じています。|  
|**user_access**|**tinyint**|ユーザー アクセス設定です。<br /> 0 = MULTI_USER が指定されています。<br /> 1 = SINGLE_USER が指定されています。<br /> 2 = RESTRICTED_USER が指定されています。|  
|**user_access_desc**|**nvarchar (60)**|ユーザー アクセス設定の説明です。|  
|**is_read_only**|**bit**|1 = データベースは READ_ONLY です。<br /> 0 = データベースは READ_WRITE です。|  
|**is_auto_close_on**|**bit**|1 = AUTO_CLOSE は ON です。<br /> 0 = AUTO_CLOSE は OFF です。|  
|**is_auto_shrink_on**|**bit**|1 = AUTO_SHRINK は ON です。<br /> 0 = AUTO_SHRINK は OFF です。|  
|**状態**|**tinyint**|**値 &#124; 適用されます**<br /> 0 = ONLINE <br /> 1 = 復元中 <br /> 2 = &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降の回復<br /> 3 = RECOVERY_PENDING &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降<br /> 4 = 問題あり <br /> 5 = 緊急 &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降<br /> 6 = オフライン &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降<br /> 7 = コピー &#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)][!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY &#124; [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)][!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **注:** Always On データベースの場合`database_state`は、 `database_state_desc` [dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)の列または列に対してクエリを実行します。|  
|**state_desc**|**nvarchar (60)**|データベースの状態の説明。 「状態」を参照してください。|  
|**is_in_standby**|**bit**|データベースは、復元ログに対し、読み取り専用です。|  
|**is_cleanly_shutdown**|**bit**|1 = データベースはクリーンにシャットダウンされ、起動時に復旧処理は必要ありません。<br /> 0 = データベースはクリーンにシャットダウンされなかったため、起動時に復旧処理が必要です。|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING は ON です。<br /> 0 = SUPPLEMENTAL_LOGGING は OFF です。|  
|**snapshot_isolation_state**|**tinyint**|ALLOW_SNAPSHOT_ISOLATION オプションによって設定された、許可されているスナップショット分離トランザクションの状態。<br /> 0 = スナップショット分離の状態は OFF です (既定)。 スナップショット分離は許可されていません。<br /> 1 = スナップショット分離の状態は ON です。 スナップショット分離は許可されています。<br /> 2 = スナップショット分離状態はオフ状態に遷移中です。 すべてのトランザクションで、その変更がバージョン管理されます。 スナップショット分離を使用して新しいトランザクションを開始することはできません。 ALTER DATABASE が実行されたときにアクティブだったすべてのトランザクションが完了するまで、データベースは OFF に移行中の状態となります。<br /> 3 = スナップショット分離の状態はオン状態に遷移中です。 新しいトランザクションでは、変更がバージョン管理されます。 スナップショット分離の状態が 1 (ON) になるまで、トランザクションでスナップショット分離を使用することはできません。 ALTER DATABASE が実行されたときにアクティブだったすべての更新トランザクションが完了するまで、データベースは状態に遷移したままになります。|  
|**snapshot_isolation_state_desc**|**nvarchar (60)**|ALLOW_SNAPSHOT_ISOLATION オプションによって設定された、許可されているスナップショット分離トランザクションの状態の説明。|  
|**is_read_committed_snapshot_on**|**bit**|1 = READ_COMMITTED_SNAPSHOT オプションは ON です。 READ COMMITTED 分離レベルでの読み取り操作は、スナップショット スキャンに基づいており、ロックを取得しません。<br /> 0 = READ_COMMITTED_SNAPSHOT オプションは OFF です (既定)。 Read committed 分離レベルでの読み取り操作では、共有ロックが使用されます。|  
|**recovery_model**|**tinyint**|選択される復旧モデルです。<br /> 1 = FULL<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar (60)**|選択された復旧モデルの説明です。|  
|**page_verify_option**|**tinyint**|PAGE_VERIFY オプションの設定です。<br /> 0 = NONE<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = CHECKSUM|  
|**page_verify_option_desc**|**nvarchar (60)**|PAGE_VERIFY オプション設定の説明です。|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS は ON です。<br /> 0 = AUTO_CREATE_STATISTICS は OFF です。|  
|**is_auto_create_stats_incremental_on**|**bit**|自動統計の増分オプションの既定の設定を示します。<br /> 0 = 自動作成の統計は非増分です。<br /> 1 = 可能な場合は、自動作成の統計情報は増分されます。<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降。|  
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
|**is_cursor_close_on_commit_on**|**bit**|1 = CURSOR_CLOSE_ON_COMMIT は ON です。<br /> 0 = CURSOR_CLOSE_ON_COMMIT は OFF です。|  
|**is_local_cursor_default**|**bit**|1 = CURSOR_DEFAULT はローカルです。<br /> 0 = CURSOR_DEFAULT はグローバルです。|  
|**is_fulltext_enabled**|**bit**|1 = データベースに対してフルテキストが有効です。<br /> 0 = データベースに対してフルテキストが無効です。|  
|**is_trustworthy_on**|**bit**|1 = データベースは信頼できるものとしてマークされています。<br /> 0 = データベースは信頼できるものとしてマークされていません。<br /> 既定では、復元またはアタッチされたデータベースの信頼が有効になっていません。|  
|**is_db_chaining_on**|**bit**|1 = 複数データベースの組み合わせ所有権は ON です。<br /> 0 = 複数データベースの組み合わせ所有権は OFF です。|  
|**is_parameterization_forced**|**bit**|1 = パラメーター化は FORCED です。<br /> 0 = パラメーター化は SIMPLE です。|  
|**is_master_key_encrypted_by_server**|**bit**|1 = データベースは暗号化されたマスター キーを保有しています。<br /> 0 = データベースは暗号化されたマスター キーを保有していません。|  
|**is_query_store_on**|**bit**|1 = このデータベースに対してクエリストアが有効になっています。 クエリストアの状態を表示するには、 [database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)を確認してください。<br /> 0 = クエリストアが有効になっていません<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降)。|  
|**is_published**|**bit**|1 = データベースは、トランザクション レプリケーション トポロジまたはスナップショット レプリケーション トポロジにおけるパブリケーション データベースです。<br /> 0 = パブリケーション データベースではありません。|  
|**is_subscribed**|**bit**|この列は使用されません。 データベースのサブスクライバーの状態に関係なく、常に 0 を返します。|  
|**is_merge_published**|**bit**|1 = データベースは、マージ レプリケーション トポロジにおけるパブリケーション データベースです。<br /> 0 = マージ レプリケーション トポロジにおけるパブリケーション データベースではありません。|  
|**is_distributor**|**bit**|1 = データベースは、レプリケーション トポロジにおけるディストリビューション データベースです。<br /> 0 = レプリケーション トポロジにおけるディストリビューション データベースではありません。|  
|**is_sync_with_backup**|**bit**|1 = データベースはバックアップとのレプリケーション同期用に設定されています。<br /> 0 = バックアップとのレプリケーション同期用に設定されていません。|  
|**service_broker_guid**|**UNIQUEIDENTIFIER**|このデータベースの Service Broker の識別子です。 ルーティング テーブルでターゲットの **broker_instance** として使用されます。|  
|**is_broker_enabled**|**bit**|1 = このデータベースのブローカーは現在メッセージを送受信中です。<br /> 0 = このデータベースでは、すべての送信メッセージは転送キューにとどまり、受信メッセージはキューに配置されません。<br /> 既定では、復元されたデータベースまたはアタッチされたデータベースでは、ブローカーは無効になります。 ただし、フェールオーバー後にブローカーが有効になるデータベース ミラーリングは例外です。|  
|**log_reuse_wait**|**tinyint**|トランザクションログ領域の再利用は、現在、最後のチェックポイントの時点で、次のいずれかを待機しています。 これらの値の詳細については、[トランザクションログ](../../relational-databases/logs/the-transaction-log-sql-server.md)を参照してください。<br /> **値 &#124; 適用されます**<br /> 0 = なし<br />   1 = チェックポイント (データベースが復旧モデルを使用していて、メモリ最適化データファイルグループがある場合は、 `log_reuse_wait`列がチェックポイントまたは xtp_checkpoint を[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]示すことが予想されます) &#124; 以降<br />  2 = ログバックアップ &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降<br />  3 = アクティブなバックアップまたは[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]復元 &#124; 以降<br />  4 = アクティブなトランザクション[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] &#124; 以降<br />  5 = データベースミラーリング &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降<br />  6 = レプリケーション &#124; [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降<br />  7 = データベーススナップショットの作成[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] &#124; 以降<br />  8 = ログスキャン <br />  9 = Always On 可用性グループセカンダリレプリカは、このデータベースのトランザクションログレコードを対応するセカンダリデータベースに適用します。 &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降<br />  9 = その他 (一時的) &#124; まで[!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)]<br />  10 = 内部使用のみ &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降<br />  11 = 内部使用のみ &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降<br /> 12 = 内部使用のみ &#124; [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降<br />13 = 最も古いページ[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] &#124; 以降<br /> 14 = その他[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の &#124; 以降<br />  16 = XTP_CHECKPOINT (データベースが復旧モデルを使用していて、メモリ最適化データファイルグループがある場合、log_reuse_wait 列がチェックポイントまたは xtp_checkpoint を示すこと[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]が予想されます) &#124; 以降|  
|**log_reuse_wait_desc**|**nvarchar (60)**|前回のチェックポイントの時点で現在待機中の、トランザクション ログ領域の再利用の理由の説明です。|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION は ON です。<br /> 0 = DATE_CORRELATION_OPTIMIZATION は OFF です。|  
|**is_cdc_enabled**|**bit**|1 = データベースで変更データ キャプチャが有効になっています。 詳細については、「 [sys. sp_cdc_enable_db &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)」を参照してください。|  
|**is_encrypted**|**bit**|データベースが暗号化されているかどうかを示します (は`ALTER DATABASE SET ENCRYPTION` 、句を使用して最後に設定された状態を反映します)。 次のいずれかの値を指定できます。<br /> 1 = 暗号化<br /> 0 = 暗号化されていない<br /> データベース暗号化の詳細については、「[Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。<br /> データベースの暗号化が解除されている場合、 `is_encrypted`には値0が表示されます。 [Dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)動的管理ビューを使用すると、暗号化プロセスの状態を確認できます。|  
|**is_honor_broker_priority_on**|**bit**|データベースがメッセージ交換の優先度を優先するかどうかを示します`ALTER DATABASE SET HONOR_BROKER_PRIORITY` (句を使用して最後に設定された状態を反映します)。 次のいずれかの値を指定できます。<br /> 1 = HONOR_BROKER_PRIORITY は ON です。<br /> 0 = HONOR_BROKER_PRIORITY は OFF です。<br /> 既定では、復元またはアタッチされたデータベースの broker の優先度はオフになっています。|  
|**replica_id**|**UNIQUEIDENTIFIER**|データベースが参加している可用性グループ (存在する場合) のローカル [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 可用性レプリカの一意の識別子です。<br /> NULL = データベースは可用性グループの可用性レプリカの一部ではありません。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**UNIQUEIDENTIFIER**|データベースが参加している Always On 可用性グループ (存在する場合) 内のデータベースの一意識別子。 **group_database_id**は、プライマリレプリカのこのデータベースと、データベースが可用性グループに参加しているすべてのセカンダリレプリカで同じです。<br /> NULL = データベースは、どの可用性グループの可用性レプリカの一部でもありません。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|このデータベースにマップされているリソースプールの id。 このリソースプールは、このデータベース内のメモリ最適化テーブルで使用できるメモリの合計を制御します。<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降|  
|**default_language_lcid**|**smallint**|包含データベースの既定の言語のローカル ID (LCID) を示します。<br /> **注:** の`sp_configure` [Default Language サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md)として機能します。 非包含データベースの場合、この値は**null**です。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128**|包含データベースの既定の言語を示します。<br /> 非包含データベースの場合、この値は**null**です。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|包含データベースの既定のフルテキスト言語のロケール id (lcid) を示します。<br /> **注:** 既定の[フルテキスト言語サーバー構成オプション](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md)の既定の構成として`sp_configure`機能します。 非包含データベースの場合、この値は**null**です。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128**|包含データベースの既定のフルテキスト言語を示します。<br /> 非包含データベースの場合、この値は**null**です。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|包含データベースで入れ子になったトリガーが許可されるかどうかを示します。<br /> 0 = 入れ子になったトリガーは許可されません。<br /> 1 = 入れ子になったトリガーは許可されます。<br /> **注:** の関数は、の`sp_configure` [Nested Triggers サーバー構成オプションを構成](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)します。 非包含データベースの場合、この値は**null**です。 詳細については[、「transact-sql&#41;&#40;の構成](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)」を参照してください。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|包含データベースでノイズ ワードを変換する必要があるかどうかを示します。<br /> 0 = ノイズ ワードは変換する必要がありません。<br /> 1 = ノイズ ワードは変換する必要があります。<br /> **注:** の`sp_configure`[変換ノイズワードのサーバー構成オプション](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)として機能します。 非包含データベースの場合、この値は**null**です。 詳細については[、「transact-sql&#41;&#40;の構成](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)」を参照してください。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降|  
|**two_digit_year_cutoff**|**smallint**|2 桁の数字を 4 桁の西暦として解釈する場合の区切りの年を表す 1753 ～ 9999 の範囲の数値を示します。<br /> **注:** の2桁表記の年の`sp_configure`[切り捨てサーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)として機能します。 非包含データベースの場合、この値は**null**です。 詳細については[、「transact-sql&#41;&#40;の構成](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)」を参照してください。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**封じ込める**|**tinyint not null**|データベースの包含状態を示します。<br />  0 = データベースの包含がオフです。 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = データベースは部分的な含有に**適用さ**れます: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降|  
|**containment_desc**|**nvarchar (60) not null**|データベースの包含状態を示します。<br /> NONE = 従来のデータベース (包含なし)<br /> PARTIAL = 部分的包含データベース<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|データベースの推定復旧時間 (秒) です。 NULL 値は許可されます。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降) と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|遅延持続性の設定:<br /> 0 = 無効<br /> 1 = 許可<br /> 2 = 強制<br /> 詳しくは、「[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)」をご覧ください。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]以降) および[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
|**delayed_durability_desc**|**nvarchar (60)**|遅延持続性の設定:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]以降) および[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
|**is_memory_optimized_elevate_to_snapshot_on**|**bit**|セッション設定 TRANSACTION ISOLATION LEVEL が低い分離レベル (READ COMMITTED または READ UNCOMMITTED) に設定されている場合は、SNAPSHOT 分離を使用してメモリ最適化テーブルにアクセスします。<br /> 1 = 最小分離レベルは SNAPSHOT です。<br /> 0 = 分離レベルは昇格されません。|  
|**is_federation_member**|**bit**|データベースがフェデレーションのメンバーであるかどうかを示します。<br /> **適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|データベースが拡張されているかどうかを示します。<br /> 0 = データベースは Stretch 対応ではありません。<br /> 1 = データベースは Stretch に対応しています。<br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降<br /> 詳細については、「[Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。|  
|**is_mixed_page_allocation_on**|**bit**|データベース内のテーブルとインデックスが混合エクステントから初期ページを割り当てることができるかどうかを示します。<br /> 0 = データベース内のテーブルとインデックスは、常に最初のページを一様なエクステントから割り当てます。<br /> 1 = データベース内のテーブルとインデックスは、混合エクステントから初期ページを割り当てることができます。<br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降<br /> 詳細については、「 [transact-sql&#41;&#40;の ALTER DATABASE Set オプション](../../t-sql/statements/alter-database-transact-sql-set-options.md)の set MIXED_PAGE_ALLOCATION オプション」を参照してください。|  
|**is_temporal_retention_enabled**|**bit**|テンポラル保持ポリシーのクリーンアップタスクが有効かどうかを示します。<br /> **適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type**|**int**|カタログの照合順序の設定:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**catalog_collation_type_desc**|**nvarchar (60)**|カタログの照合順序の設定:<br />COLLATE<br />SQL_Latin_1_General_CP1_CI_AS<br /> **適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|
|**is_result_set_caching_on**|**bit**|1 = is_result_set_caching_on は on です。</br>0 = is_result_set_caching_on はオフです。</br>**適用対象**: Azure SQL Data Warehouse Gen2。 この機能はすべてのリージョンにロールアウトされていますが、ご使用のインスタンスにデプロイされているバージョンと、利用可能な機能に関する最新の[AZURE SQL DW リリースノート](/azure/sql-data-warehouse/release-notes-10-0-10106-0)を確認してください。|
|**is_memory_optimized_enabled**|**bit**|[ハイブリッドバッファープール](../../database-engine/configure-windows/hybrid-buffer-pool.md)などの特定のインメモリ機能がデータベースに対して有効かどうかを示します。 [インメモリ OLTP](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)の可用性または構成の状態は反映されません。 <br />**適用対象**: SQL Server 2019 (15 .x)|
  
## <a name="permissions"></a>アクセス許可

 の`sys.databases`呼び出し元がデータベースの所有者ではなく、データベース`master`がまたは`tempdb`ではない場合、対応する行を表示するため`ALTER ANY DATABASE`に必要`VIEW ANY DATABASE`な最低限の権限は、 `CREATE DATABASE`または`master`データベース内のサーバーレベルの権限、または権限です。 呼び出し元が接続されているデータベースは、常に`sys.databases`で表示できます。  
  
> [!IMPORTANT]  
> 既定では、public ロールには`VIEW ANY DATABASE`権限が付与されているので、すべてのログインでデータベース情報を参照できます。 データベース`REVOKE` `VIEW ANY DATABASE`を検出する権限、から`public`の権限、または`DENY` `VIEW ANY DATABASE`個々のログインに対する権限をブロックする権限。  
  
## <a name="azure-sql-database-remarks"></a>Azure SQL Database 解説

[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]このビューは、 `master`データベースとユーザーデータベースで使用できます。 `master`データベースでは、このビューには、サーバー上`master`のデータベースとすべてのユーザーデータベースに関する情報が返されます。 ユーザー データベースでは、このビューには、現在のデータベースと master データベースのみの情報が返されます。  
  
 新しいデータベースが作成される `sys.databases` サーバーの `master` データベースの [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] ビューを使用します。 データベースのコピーが開始されたら、コピー `sys.databases`先サーバー `sys.dm_database_copies`の`master`データベースからおよびビューに対してクエリを実行し、コピーの進行状況に関する詳細情報を取得できます。  
  
## <a name="examples"></a>例  
  
### <a name="a-query-the-sysdatabases-view"></a>A. sys.databases ビューに対するクエリ

次の例では、 `sys.databases`ビューで使用できる列のいくつかを返します。  
  
```sql  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>B. 
  [!INCLUDE[ssSDS](../../includes/sssds-md.md)] でのコピーの進行状況を確認します。

次の例では`sys.databases` 、 `sys.dm_database_copies`ビューとビューに対してクエリを実行し、データベースのコピー操作に関する情報を返します。  
  
**適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```

### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>C. の一時リテンション期間ポリシーの状態を確認します。[!INCLUDE[ssSDS](../../includes/sssds-md.md)]

次の例では`sys.databases` 、をクエリして、テンポラル保持クリーンアップタスクが有効になっているかどうかの情報を返します。 復元操作の後、テンポラルリテンション期間は既定で無効になっていることに注意してください。 を`ALTER DATABASE`使用して、明示的に有効にします。
  
**適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```sql  
-- Execute from the master database.  
SELECT a.name, a.is_temporal_history_retention_enabled 
FROM sys.databases AS a;
```  
  
## <a name="next-steps"></a>次のステップ

- [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)
- [database_mirroring_witnesses &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)
- [database_recovery_status &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-recovery-status-transact-sql.md)
- [データベースとファイルのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)
- [dm_database_copies &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)  
