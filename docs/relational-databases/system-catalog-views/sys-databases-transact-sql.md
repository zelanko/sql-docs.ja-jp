---
title: sys.databases (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 152
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 49f8ab952cad03717474d17a4697063050777e26
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182528"
---
# <a name="sysdatabases-transact-sql"></a>sys.databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに、データベースごとに 1 行のデータを保持します。  
  
 データベースがない場合`ONLINE`、または`AUTO_CLOSE`に設定されている`ON`と、データベースが閉じられて、一部の列の値があります`NULL`です。 データベースがある場合`OFFLINE`、対応する行は、特権の低いユーザーに表示されません。 データベースがある場合は、対応する行を表示する`OFFLINE`、ユーザーがいる必要がありますには、少なくとも、`ALTER ANY DATABASE`サーバー レベルの権限、または`CREATE DATABASE`でアクセス許可、`master`データベース。  
  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|インスタンス内で一意のデータベースの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内、または、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]サーバー。|  
|**database_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内、または [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバー内で一意な、データベースの識別子。|  
|**source_database_id**|**int**|NULL 以外 = このデータベース スナップショットのソース データベースの ID です。<br /> NULL = データベース スナップショットではありません。|  
|**owner_sid**|**varbinary(85)**|サーバーに登録したデータベースの外部所有者の SID (セキュリティ識別子) です。 データベースを所有する方法については、次を参照してください。、**データベースの ALTER AUTHORIZATION**のセクション[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)です。|  
|**create_date**|**datetime**|データベースの作成または名前の変更を行った日付です。 **Tempdb**サーバーを再起動するたびに、この値が変更されました。|  
|**compatibility_level**|**tinyint**|バージョンに対応する整数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のどちらの動作が互換性のあります。<br /> **値**:**に適用されます**<br /> 70:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] |  
|**collation_name**|**sysname**|データベースの照合順序です。 データベースの既定の照合順序として機能します。<br /> NULL = データベースがオンラインではありません。または、AUTO_CLOSE が ON に設定されていて、データベースが閉じられています。|  
|**user_access**|**tinyint**|ユーザー アクセス設定です。<br /> 0 = MULTI_USER が指定されています。<br /> 1 = SINGLE_USER が指定されています。<br /> 2 = RESTRICTED_USER が指定されています。|  
|**user_access_desc**|**nvarchar(60)**|ユーザー アクセス設定の説明です。|  
|**is_read_only**|**bit**|1 = データベースは READ_ONLY です。<br /> 0 = データベースは READ_WRITE です。|  
|**is_auto_close_on**|**bit**|1 = AUTO_CLOSE は ON です。<br /> 0 = AUTO_CLOSE は OFF です。|  
|**is_auto_shrink_on**|**bit**|1 = AUTO_SHRINK は ON です。<br /> 0 = AUTO_SHRINK は OFF です。|  
|**状態**|**tinyint**|**値&#124;に適用されます**<br /> 0 = ONLINE <br /> 1 = RESTORING <br /> 2 = RECOVERING:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 3 = RECOVERY_PENDING:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 4 = SUSPECT <br /> 5 = EMERGENCY:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 6 = オフライン:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 7 = コピーします。 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **注:** Always On データベースに対してクエリを実行、`database_state`または`database_state_desc`列[sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)です。|  
|**state_desc**|**nvarchar(60)**|データベースの状態の説明です。 状態を参照してください。|  
|**is_in_standby**|**bit**|データベースは、復元ログに対し、読み取り専用です。|  
|**is_cleanly_shutdown**|**bit**|1 = データベースはクリーンにシャットダウンされ、起動時に復旧処理は必要ありません。<br /> 0 = データベースはクリーンにシャットダウンされなかったため、起動時に復旧処理が必要です。|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING は ON です。<br /> 0 = SUPPLEMENTAL_LOGGING は OFF です。|  
|**snapshot_isolation_state**|**tinyint**|ALLOW_SNAPSHOT_ISOLATION オプションで設定された、許可されているスナップショット分離トランザクションの状態です。<br /> 0 = スナップショット分離の状態は OFF です (既定)。 スナップショット分離は許可されていません。<br /> 1 = スナップショット分離の状態は ON です。 スナップショット分離は許可されています。<br /> 2 = スナップショット分離の状態は OFF に移行中です。 すべてのトランザクションで、その変更がバージョン管理されます。 スナップショット分離を使用して新しいトランザクションを開始することはできません。 ALTER DATABASE が実行されたときにアクティブだったすべてのトランザクションが完了するまで、データベースは OFF に移行中の状態となります。<br /> 3 = スナップショット分離の状態は ON に移行中です。 新しいトランザクションで、その変更がバージョン管理されます。 スナップショット分離の状態が 1 (ON) になるまで、トランザクションではスナップショット分離を使用できません。 ALTER DATABASE が実行されたときにアクティブだったすべての更新トランザクションが完了するまで、データベースは ON に移行中の状態となります。|  
|**snapshot_isolation_state_desc**|**nvarchar(60)**|ALLOW_SNAPSHOT_ISOLATION オプションで設定された、許可されているスナップショット分離トランザクションの状態の説明です。|  
|**is_read_committed_snapshot_on**|**bit**|1 = READ_COMMITTED_SNAPSHOT オプションは ON です。 READ COMMITTED 分離レベルでの読み取り操作は、スナップショット スキャンに基づいており、ロックを取得しません。<br /> 0 = READ_COMMITTED_SNAPSHOT オプションは OFF です (既定)。 READ COMMITTED 分離レベルでの読み取り操作は、共有ロックを使用します。|  
|**recovery_model**|**tinyint**|選択される復旧モデルです。<br /> 1 = FULL<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar(60)**|選択される復旧モデルの説明です。|  
|**page_verify_option**|**tinyint**|PAGE_VERIFY オプションの設定です。<br /> 0 = NONE<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = CHECKSUM|  
|**page_verify_option_desc**|**nvarchar(60)**|PAGE_VERIFY オプション設定の説明です。|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS は ON です。<br /> 0 = AUTO_CREATE_STATISTICS は OFF です。|  
|**is_auto_create_stats_incremental_on**|**bit**|Auto Stats の増分処理オプションの既定の設定を示します。<br /> 0 = Auto Stats は増分作成されません。<br /> 1 = 可能な場合、Auto Stats は増分作成されます。<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**is_auto_update_stats_on**|**bit**|1 = AUTO_UPDATE_STATISTICS は ON です。<br /> 0 = AUTO_UPDATE_STATISTICS は OFF です。|  
|**is_auto_update_stats_async_on**|**bit**|1 = AUTO_UPDATE_STATISTICS_ASYNC は ON です。<br /> 0 = AUTO_UPDATE_STATISTICS_ASYNC は OFF です。|  
|**is_ansi_null_default_on**|**bit**|1 = ANSI_NULL_DEFAULT は ON です。<br /> 0 = ANSI_NULL_DEFAULT は OFF です。|  
|**is_ansi_nulls_on**|**bit**|1 = ANSI_NULLS は ON です。<br /> 0 = ANSI_NULLS は OFF です。|  
|**is_ansi_padding_on**|**bit**|1 = ANSI_PADDING は ON です<br /> 0 = ANSI_PADDING は OFF です。|  
|**is_ansi_warnings_on**|**bit**|1 = ANSI_WARNINGS は ON です。<br /> 0 = ANSI_WARNINGS は OFF です。|  
|**is_arithabort_on**|**bit**|1 = ARITHABORT は ON です。<br /> 0 = ARITHABORT は OFF です。|  
|**is_concat_null_yields_null_on**|**bit**|1 = CONCAT_NULL_YIELDS_NULL は ON です。<br /> 0 = CONCAT_NULL_YIELDS_NULL は OFF です。|  
|**is_numeric_roundabort_on**|**bit**|1 = NUMERIC_ROUNDABORT は ON です。<br /> 0 = NUMERIC_ROUNDABORT は OFF です。|  
|**is_quoted_identifier_on**|**bit**|1 = QUOTED_IDENTIFIER は ON です。<br /> 0 = QUOTED_IDENTIFIER は OFF です。|  
|**is_recursive_triggers_on**|**bit**|1 = RECURSIVE_TRIGGERS は ON です。<br /> 0 = RECURSIVE_TRIGGERS は OFF です。|  
|**is_cursor_close_on_commit_on**|**bit**|1 = CURSOR_CLOSE_ON_COMMIT は ON です。<br /> 0 = CURSOR_CLOSE_ON_COMMIT は OFF です。|  
|**is_local_cursor_default**|**bit**|1 = CURSOR_DEFAULT はローカルです。<br /> 0 = CURSOR_DEFAULT はグローバルです。|  
|**is_fulltext_enabled**|**bit**|1 = データベースに対してフルテキストが有効です。<br /> 0 = データベースに対してフルテキストが無効です。|  
|**is_trustworthy_on**|**bit**|1 = データベースは信頼できるものとしてマークされています。<br /> 0 = データベースは信頼できるものとしてマークされていません。|  
|**is_db_chaining_on**|**bit**|1 = 複数データベースにまたがる組み合わせ所有権は ON<br /> 0 = 複数データベースの組み合わせ所有権は OFF です。|  
|**is_parameterization_forced**|**bit**|1 = パラメーター化は FORCED です。<br /> 0 = パラメーター化は SIMPLE|  
|**is_master_key_encrypted_by_server**|**bit**|1 = データベースは暗号化されたマスター キーを保有しています。<br /> 0 = データベースは暗号化されたマスター キーを保有していません。|  
|**is_query_store_on**|**bit**|1 = クエリ ストアは、このデータベースを有効にします。 確認[sys.database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)をクエリ ストアの状態を表示します。<br /> 0 = クエリ ストアが有効になっていません。<br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
|**is_published**|**bit**|1 = データベースは、トランザクション レプリケーション トポロジまたはスナップショット レプリケーション トポロジにおけるパブリケーション データベースです。<br /> 0 = パブリケーション データベースではありません|  
|**is_subscribed**|**bit**|この列は使用されません。 データベースのサブスクライバーの状態に関係なく、常に 0 を返します。|  
|**is_merge_published**|**bit**|1 = データベースは、マージ レプリケーション トポロジにおけるパブリケーション データベースです。<br /> 0 = マージ レプリケーション トポロジにおけるパブリケーション データベースではありません。|  
|**is_distributor**|**bit**|1 = データベースは、レプリケーション トポロジにおけるディストリビューション データベースです。<br /> 0 = レプリケーション トポロジにおけるディストリビューション データベースではありません|  
|**is_sync_with_backup**|**bit**|1 = データベースはバックアップとのレプリケーション同期用に設定されています。<br /> 0 = バックアップとのレプリケーション同期用に設定されていません。|  
|**service_broker_guid**|**uniqueidentifier**|このデータベースの Service Broker の識別子です。 として使用される、 **broker_instance**ルーティング テーブルでターゲットのです。|  
|**is_broker_enabled**|**bit**|1 = このデータベースのブローカーは現在メッセージを送受信中です。<br /> 0 = このデータベースでは、すべての送信メッセージは転送キューにとどまり、受信メッセージはキューに配置されません。<br /> 既定では、復元されたデータベースまたはアタッチされたデータベースでは、ブローカーは無効になります。 ただし、フェールオーバー後にブローカーが有効になるデータベース ミラーリングは例外です。|  
|**log_reuse_wait**|**tinyint**|トランザクション ログ領域の再利用は、最後のチェックポイントの時点で、次のいずれかで現在待機中です。 (詳細なこれらの値の説明を参照してください[トランザクション ログ](../../relational-databases/logs/the-transaction-log-sql-server.md)。)。<br /> 0 = なし<br />   1 = チェックポイント (データベースが復旧モデルを使用しており、メモリ最適化データ ファイル グループを保持している場合、log_reuse_wait 列がチェックポイントまたは xtp_checkpoint を示す可能性があります)。**適用されます**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  2 = ログ バックアップ**対象**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  3 = アクティブなバックアップまたは復元**対象**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  4 = アクティブなトランザクション**対象**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  5 = データベース ミラーリング**対象**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  6 = レプリケーション**対象**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  7 = データベース スナップショットの作成**対象**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  8 = ログ スキャン**に適用されます**<br />  9 =「Always On 可用性グループ セカンダリ レプリカが、対応するセカンダリ データベースにこのデータベースのトランザクション ログ レコードを適用することです。 **適用されます**[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 以前のバージョンの SQL Server では、9 = その他 (一時的)。<br />  10 = 内部使用のみ**対象**[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  11 = 内部使用のみ**対象**[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 12 = 内部使用のみ**対象**[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />13 = の最も古いページ**対象**[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 14 = その他**対象**[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  16 = XTP_CHECKPOINT (データベースが復旧モデルを使用しており、メモリ最適化データ ファイル グループを保持している場合、log_reuse_wait 列がチェックポイントまたは xtp_checkpoint を示す可能性があります)。**適用されます**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**log_reuse_wait_desc**|**nvarchar(60)**|前回のチェックポイントの時点で現在待機中の、トランザクション ログ領域の再利用の理由の説明です。|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION は ON です。<br /> 0 = DATE_CORRELATION_OPTIMIZATION は OFF です。|  
|**is_cdc_enabled**|**bit**|1 = データベースで変更データ キャプチャが有効になっています。 詳細については、次を参照してください。 [sys.sp_cdc_enable_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)です。|  
|**is_encrypted**|**bit**|データベースが暗号化されているかどうかを示します (ALTER DATABASE SET ENCRYPTION 句を使用して最後に設定された状態を表します)。 次の値のいずれかです。<br /> 1 = 暗号化<br /> 0 = 暗号化されていません。<br /> データベース暗号化の詳細については、「[Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。<br /> データベースの暗号化が解除されて処理を行って場合**is_encrypted**は 0 の値を示します。 使用して、暗号化処理の状態を確認できます、 [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)動的管理ビュー。|  
|**is_honor_broker_priority_on**|**bit**|データベースでメッセージ交換の優先度が適用されるかどうかを示します (ALTER DATABASE SET HONOR_BROKER_PRIORITY 句を使用して最後に設定された状態を表します)。 次の値のいずれかです。<br /> 1 = HONOR_BROKER_PRIORITY は ON です。<br /> 0 = HONOR_BROKER_PRIORITY は OFF です。|  
|**replica_id**|**uniqueidentifier**|データベースが参加している可用性グループ (存在する場合) のローカル [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 可用性レプリカの一意の識別子です。<br /> NULL = データベースは可用性グループの可用性レプリカの一部ではありません。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**uniqueidentifier**|Always On 可用性グループ、存在するデータベースが参加している場合内のデータベースの一意の識別子。 **group_database_id**をデータベースが参加している可用性グループにすべてのセカンダリ レプリカとプライマリ レプリカでは、このデータベースに対して同じです。<br /> NULL = データベースは、どの可用性グループの可用性レプリカの一部でもありません。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|このオブジェクトにマップするリソース プールの ID です。 このリソース プールによって、このデータベースのメモリ最適化テーブルで使用できる合計メモリが制御されます。<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**default_language_lcid**|**smallint**|包含データベースの既定の言語のローカル ID (LCID) を示します。<br /> **注**として機能、 [default language サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md)の**sp_configure**です。 この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128)**|包含データベースの既定の言語を示します。<br /> この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|包含データベースの既定のフルテキスト言語のローカル ID (LCID) を示します。<br /> **注**既定値として機能[既定のフルテキスト言語サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md)の**sp_configure**です。 この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128)**|包含データベースの既定のフルテキスト言語を示します。<br /> この値は**null**非包含データベースです。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|包含データベースで入れ子になったトリガーが許可されるかどうかを示します。<br /> 0 = 入れ子になったトリガーは許可されません。<br /> 1 = 入れ子になったトリガーは許可されます。<br /> **注**として機能、 [nested triggers サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)の**sp_configure**です。 この値は**null**非包含データベースです。 参照してください[sys.configurations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)についてさらにします。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|包含データベースでノイズ ワードを変換する必要があるかどうかを示します。<br /> 0 = ノイズ ワードは変換する必要がありません。<br /> 1 = ノイズ ワードは変換する必要があります。<br /> **注**として機能、 [transform noise words サーバー構成オプション](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)の**sp_configure**です。 この値は**null**非包含データベースです。 参照してください[sys.configurations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)についてさらにします。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**two_digit_year_cutoff**|**smallint**|2 桁の数字を 4 桁の西暦として解釈する場合の区切りの年を表す 1753 ～ 9999 の範囲の数値を示します。<br /> **注**として機能、[構成 two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)の**sp_configure**です。 この値は**null**非包含データベースです。 参照してください[sys.configurations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)についてさらにします。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**containment**|**null でない tinyint**|データベースの包含状態を示します。<br />  0 = データベースの包含がオフ **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = データベースは部分的な包含**対象**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**containment_desc**|**nvarchar (60) いない null**|データベースの包含状態を示します。<br /> NONE = 従来のデータベース (包含なし)<br /> PARTIAL = 部分的包含データベース<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|データベースの復旧にかかる推定時間 (秒単位) です。 Null 値を許容します。<br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|遅延持続性の設定:<br /> 0 = 無効になっています<br /> 1 = 許可<br /> 2 = 強制<br /> 詳しくは、「[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)」をご覧ください。<br /> **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|  
|**delayed_durability_desc**|**nvarchar(60)**|遅延持続性の設定:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**is_memory_optimized_elevate_to_snapshot_on**|**bit**|セッション設定 TRANSACTION ISOLATION LEVEL が低い分離レベル (READ COMMITTED または READ UNCOMMITTED) に設定されている場合は、SNAPSHOT 分離を使用してメモリ最適化テーブルにアクセスします。<br /> 1 = 最小分離レベルは SNAPSHOT です。<br /> 0 = 分離レベルは引き上げられません。|  
|**is_federation_member**|**bit**|データベースがフェデレーションのメンバーであるかどうかを示します。<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|データベースが拡大するかどうかを示します。<br /> 0 = データベースは Stretch 対応ではありません。<br /> 1 = データベースは、拡張を有効にしました。<br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 詳細については、次を参照してください。 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)です。|  
|**is_mixed_page_allocation_on**|**bit**|かどうか、データベースのテーブルおよびインデックスことができます最初のページから割り当て混合エクステントを示します。<br /> 0 = テーブル、データベース内のインデックスは常に単一エクステントから最初のページを割り当てるとします。<br /> 1 = テーブルと、データベース内のインデックスは、混合エクステントから最初のページを割り当てることができます。<br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 詳細については、の SET MIXED_PAGE_ALLOCATION オプションを参照してください。 [ALTER DATABASE SET Options &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)です。|  
|**is_temporal_retention_enabled**|**bit**|テンポラルの保持ポリシーのクリーンアップ タスクが有効になっているかどうかを示します。<br /> **適用されます**: Azure SQL データベース|
|**catalog_collation_type**|**int**|カタログ照合順序の設定:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **適用されます**: Azure SQL データベース|
|**catalog_collation_type_desc**|**nvarchar(60)**|カタログ照合順序の設定:<br />COLLATE<br />SQL_Latin_1_General_CP1_CI_AS<br /> **適用されます**: Azure SQL データベース|
  
## <a name="permissions"></a>権限  
 場合、呼び出し元の`sys.databases`データベースの所有者ではないと、データベースが`master`または`tempdb`、対応する行を表示するために必要な最小限のアクセス許可は`ALTER ANY DATABASE`または`VIEW ANY DATABASE`サーバー レベルの権限、または`CREATE DATABASE`でアクセス許可、`master`データベース。 呼び出し元が接続されているデータベースはで常に表示する`sys.databases`です。  
  
> [!IMPORTANT]  
>  既定では、パブリックのロールには、`VIEW ANY DATABASE`データベース情報を表示するすべてのログインを許可する権限です。 データベースを検出する機能からのログインをブロックする`REVOKE`、`VIEW ANY DATABASE`からのアクセス許可`public`、または`DENY`' 個別のログインに VIEW ANY DATABASE 権限。  
  
## <a name="includesssdsincludessssds-mdmd-remarks"></a>[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 解説  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、このビューで使用できる、`master`データベースとユーザー データベース。 `master`データベースでは、このビュー情報を返します上、`master`データベースおよびサーバー上のすべてのユーザー データベース。 ユーザー データベースでは、このビューには、現在のデータベースと master データベースのみの情報が返されます。  
  
 新しいデータベースが作成される [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーの `master` データベースの `sys.databases` ビューを使用します。 データベースのコピーの開始後にクエリを実行できます、`sys.databases`と`sys.dm_database_copies`から表示、`master`コピーの進行状況に関する詳細情報を取得する移行先サーバーのデータベースです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-query-the-sysdatabases-view"></a>A. sys.databases ビューに対するクエリ  
 次の例で使用できる列のいくつかが返されます、`sys.databases`ビュー。  
  
```  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>B. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] でのコピーの進行状況を確認します。  
 次の例のクエリ、`sys.databases`と`sys.dm_database_copies`データベースに関する情報を返すビューが操作をコピーします。  
  
**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
  
```  
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```  
### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>C. テンポラル保有ポリシーの状態を確認してください。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 次の例のクエリ、`sys.databases`テンポラル保有期間のクリーンアップ タスクが有効になっているかどうかに情報を返します。 復元操作後に一時的な保有期間が無効である既定では注意してください。 使用して`ALTER DATABASE`明示的に有効にします。
  
**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```  
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
  
  
