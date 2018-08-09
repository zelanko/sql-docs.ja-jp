---
title: ALTER DATABASE の SET オプション (Transact-SQL) | Microsoft Docs
description: SQL Server および Azure SQL Database で、自動調整、暗号化、クエリ ストアなどのデータベースのオプションを設定する方法について説明します
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- online database state [SQL Server]
- database options [SQL Server]
- emergency database state [SQL Server]
- databases [SQL Server], options
- read-only databases
- recovery models [SQL Server], switching
- ALTER DATABASE statement, SET options
- offline database state [SQL Server]
- snapshot isolation framework option
- checksums [SQL Server]
- automatic tuning
- SQL plan regression correction
- auto_create_statistics
- auto_update_statistics
ms.assetid: f76fbd84-df59-4404-806b-8ecb4497c9cc
caps.latest.revision: 159
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 16505ba07dcd1035ad260b68785eea763c050d1b
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560502"
---
# <a name="alter-database-set-options-transact-sql"></a>ALTER DATABASE の SET オプション (Transact-SQL) 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Azure SQL Database のデータベース オプションを設定します。 ALTER DATABASE の他のオプションについては、「[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)」をご覧ください。

お使いの特定バージョンの SQL の構文、引数、注釈、権限、例を表示するには、以下のいずれかのタブをクリックします。

構文表記規則の詳細については、「[Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)」を参照してください。 

# <a name="sql-servertabsqlserver"></a>[SQL Server](#tab/sqlserver)
  
データベース ミラーリング、[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]、および互換性レベルは `SET` オプションですが、長くなるため別の記事で説明します。 詳しくは、「[ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)」、「[ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)」、および「[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」をご覧ください。  
  
> [!NOTE]  
> 多くのデータベース設定オプションは、[SET ステートメント](../../t-sql/statements/set-statements-transact-sql.md)を使用して現在のセッション用に構成できます。これらは多くの場合、接続するアプリケーションによって構成されます。 セッション レベルの SET オプションは、**ALTER DATABASE SET** の値をオーバーライドします。 次のデータベース オプションは、セッション用に設定できる値であり、他の SET オプションの値は明示的に指定されていません。  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE { database_name  | CURRENT }  
SET   
{  
    <option_spec> [ ,...n ] [ WITH <termination> ]   
}  
  
<option_spec> ::=   
{  
    <auto_option>   
  | <automatic_tuning_option>   
  | <change_tracking_option>   
  | <containment_option>   
  | <cursor_option>   
  | <database_mirroring_option>  
  | <date_correlation_optimization_option>  
  | <db_encryption_option>  
  | <db_state_option>  
  | <db_update_option>   
  | <db_user_access_option>   
  | <delayed_durability_option>  
  | <external_access_option>  
  | FILESTREAM ( <FILESTREAM_option> )  
  | <HADR_options>  
  | <mixed_page_allocation_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <recovery_option>  
  | <remote_data_archive_option>  
  | <service_broker_option>  
  | <snapshot_option>  
  | <sql_option>   
  | <target_recovery_time_option>   
  | <termination>  
}  
;
  
<auto_option> ::=   
{  
    AUTO_CLOSE { ON | OFF }   
  | AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }   
  | AUTO_SHRINK { ON | OFF }   
  | AUTO_UPDATE_STATISTICS { ON | OFF }   
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}  
  
<automatic_tuning_option> ::=  
{  
  AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = { ON | OFF } )
}  

<change_tracking_option> ::=  
{  
  CHANGE_TRACKING   
   {   
       = OFF  
     | = ON [ ( <change_tracking_option_list > [,...n] ) ]   
     | ( <change_tracking_option_list> [,...n] )  
   }  
}  
  
   <change_tracking_option_list> ::=  
   {  
       AUTO_CLEANUP = { ON | OFF }   
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }  
   }  
  
<containment_option> ::=   
   CONTAINMENT = { NONE | PARTIAL }  
  
<cursor_option> ::=   
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }   
  | CURSOR_DEFAULT { LOCAL | GLOBAL }   
}  
  
<database_mirroring_option>  
  ALTER DATABASE Database Mirroring  
  
<date_correlation_optimization_option> ::=  
    DATE_CORRELATION_OPTIMIZATION { ON | OFF }  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
  
<db_state_option> ::=  
    { ONLINE | OFFLINE | EMERGENCY }  
  
<db_update_option> ::=  
    { READ_ONLY | READ_WRITE }  
  
<db_user_access_option> ::=  
    { SINGLE_USER | RESTRICTED_USER | MULTI_USER }  
  
<delayed_durability_option> ::=  
    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<external_access_option> ::=  
{  
    DB_CHAINING { ON | OFF }  
  | TRUSTWORTHY { ON | OFF }  
  | DEFAULT_FULLTEXT_LANGUAGE = { <lcid> | <language name> | <language alias> }  
  | DEFAULT_LANGUAGE = { <lcid> | <language name> | <language alias> }  
  | NESTED_TRIGGERS = { OFF | ON }  
  | TRANSFORM_NOISE_WORDS = { OFF | ON }  
  | TWO_DIGIT_YEAR_CUTOFF = { 1753, ..., 2049, ..., 9999 }  
}  
<FILESTREAM_option> ::=  
{  
    NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL   
  | DIRECTORY_NAME = <directory_name>  
}  
<HADR_options> ::=  
    ALTER DATABASE SET HADR  
  
<mixed_page_allocation_option> ::=  
    MIXED_PAGE_ALLOCATION { OFF | ON }  
  
<parameterization_option> ::=  
    PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
    QUERY_STORE   
    {  
          = OFF   
        | = ON [ ( <query_store_option_list> [,...n] ) ]  
        | ( < query_store_option_list> [,...n] )  
        | CLEAR [ ALL ]  
    }  
}   
  
<query_store_option_list> ::=  
{  
      OPERATION_MODE = { READ_WRITE | READ_ONLY }   
    | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )  
    | DATA_FLUSH_INTERVAL_SECONDS = number   
    | MAX_STORAGE_SIZE_MB = number   
    | INTERVAL_LENGTH_MINUTES = number   
    | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
    | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
    | MAX_PLANS_PER_QUERY = number
    | WAIT_STATS_CAPTURE_MODE = [ ON | OFF ]
}  
  
<recovery_option> ::=   
{  
    RECOVERY { FULL | BULK_LOGGED | SIMPLE }   
  | TORN_PAGE_DETECTION { ON | OFF }  
  | PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }  
}  
  
<remote_data_archive_option> ::=  
{  
    REMOTE_DATA_ARCHIVE =  
    {  
        ON ( SERVER = <server_name> ,   
                  {   CREDENTIAL = <db_scoped_credential_name>  
                     | FEDERATED_SERVICE_ACCOUNT =  ON | OFF   
                  }  
               )  
      | OFF  
    }  
}  
  
<service_broker_option> ::=  
{  
    ENABLE_BROKER  
  | DISABLE_BROKER  
  | NEW_BROKER  
  | ERROR_BROKER_CONVERSATIONS  
  | HONOR_BROKER_PRIORITY { ON | OFF}  
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = {ON | OFF }  
}  
<sql_option> ::=   
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }   
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<target_recovery_time_option> ::=  
    TARGET_RECOVERY_TIME = target_recovery_time { SECONDS | MINUTES }  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  
```  
  
## <a name="arguments"></a>引数  
*database_name*  
変更するデータベースの名前を指定します。  
  
CURRENT  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
`CURRENT` を指定すると、現在のデータベースでアクションが実行されます。 `CURRENT` は、すべてのコンテキスト内のすべてのオプションでサポートされるわけではありません。 `CURRENT` でエラーが発生した場合は、データベース名を指定してください。  
  
**\<auto_option> ::=**
  
自動オプションを制御します。  
<a name="auto_close"></a> AUTO_CLOSE { ON | OFF }  
ON  
最後のユーザーが終了した後、データベースは正常にシャットダウンされ、そのリソースは解放されます。  
  
ユーザーが再びそのデータベースを使用しようとすると、そのデータベースが自動的に再度開かれます。 たとえば、`USE database_name` ステートメントを発行する場合などです。 AUTO_CLOSE が ON に設定されている状態でデータベースが正常にシャットダウンした場合は、次回[!INCLUDE[ssDE](../../includes/ssde-md.md)]が再起動したとき、ユーザーがデータベースを使用するまでは、データベースは開きません。  
  
OFF  
最後のユーザーが終了した後も、データベースは開いたままになります。  
  
AUTO_CLOSE オプションを使用すると、データベース ファイルを通常のファイルとして管理できるため、デスクトップ データベースには便利なオプションです。 普通のファイルと同じように、移動、コピーによるバックアップ作成、他のユーザーへの電子メール送信が可能です。 AUTO_CLOSE は非同期プロセスであるため、データベースを開いたり閉じたりする操作を繰り返しても、パフォーマンスは低下しません。  
  
> [!NOTE]  
>  AUTO_CLOSE オプションは、包含データベースまたは [!INCLUDE[ssSDS](../../includes/sssds-md.md)] では使用できません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_close_on 列か、DATABASEPROPERTYEX 関数の IsAutoClose プロパティを調べてください。  
  
> [!NOTE]  
>  AUTO_CLOSE が ON の場合、データベースからデータを取得できないため、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの一部の列、および DATABASEPROPERTYEX 関数は、NULL を返します。 これを解決するには、USE ステートメントを実行してデータベースを開きます。  
  
> [!NOTE]  
>  データベースをミラー化するには、AUTO_CLOSE を OFF に設定する必要があります。  
  
データベースを AUTOCLOSE = ON に設定すると、データベースの自動シャットダウンを開始する操作によって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのプラン キャッシュが消去されます。 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 以降では、プラン キャッシュ内のキャッシュストアが消去されるたびに、"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、一部のデータベース メンテナンス操作または再構成操作により、'%s' キャッシュストア (プラン キャッシュの一部) のキャッシュストア フラッシュを %d 個検出しました。" という情報メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに記録されます。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
 
<a name="auto_create_statistics"></a> AUTO_CREATE_STATISTICS { ON | OFF }  
ON  
クエリ プランを改善してクエリのパフォーマンスを向上させるために、クエリ オプティマイザーが必要に応じてクエリ述語内の列に対して 1 列ずつ統計を作成します。 これらの統計は、クエリ オプティマイザーがクエリをコンパイルするときに作成されます。 1 列ずつの統計は、まだ既存の統計オブジェクトの最初の列になっていない列についてのみ作成されます。  
  
既定値は ON です。 ほとんどのデータベースで既定の設定を使用することをお勧めします。  
  
OFF  
クエリ オプティマイザーがクエリをコンパイルするときにクエリ述語内の列の 1 列ずつの統計が作成されません。 このオプションを OFF に設定すると、最適ではないクエリ プランが作成されて、クエリのパフォーマンスが低下することがあります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_create_stats_on 列、または DATABASEPROPERTYEX 関数の IsAutoCreateStatistics プロパティを調べてください。  
  
詳細については、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
INCREMENTAL = ON | OFF  
AUTO_CREATE_STATISTICS が ON の場合に INCREMENTAL を ON に設定すると、増分統計がサポートされているときは常に、自動的に作成される統計が増分統計となります。 既定値は OFF です。 詳しくは、「[CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)」をご覧ください。  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]。  
  
<a name="auto_shrink"></a> AUTO_SHRINK { ON | OFF }  
ON  
データベース ファイルを定期的な圧縮処理の対象とします。  
  
データ ファイルとログ ファイルの両方を、自動的に圧縮できます。 AUTO_SHRINK では、データベースが単純復旧モデルに設定されている場合や、ログがバックアップされている場合にのみ、トランザクション ログのサイズが圧縮されます。 OFF に設定すると、未使用領域の定期チェックの際に、データベース ファイルは自動的に圧縮されません。  
  
AUTO_SHRINK オプションを使用すると、ファイル領域の 25% を超える領域が未使用の場合にファイルが圧縮されます。 未使用領域がファイル領域の 25% になるサイズ、またはそのファイルが作成された時点でのサイズの、どちらか大きい方のサイズまで圧縮されます。  
  
読み取り専用データベースは圧縮できません。  
  
OFF  
データベース ファイルは、未使用領域の定期的なチェックの際に、自動的に圧縮されません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_shrink_on 列、または DATABASEPROPERTYEX 関数の IsAutoShrink プロパティを調べてください。  
  
> [!NOTE]  
> AUTO_SHRINK オプションは、包含データベースでは使用できません。  
  
<a name="auto_update_statistics"></a> AUTO_UPDATE_STATISTICS { ON | OFF }  
ON  
クエリで使用される統計が古くなっている可能性がある場合にクエリ オプティマイザーによって更新されるように指定します。 挿入、更新、削除、またはマージの各操作によってテーブルまたはインデックス付きビューのデータの分布が変わると、統計は古くなったと判断されます。 クエリ オプティマイザーでは、統計が前回更新されてから発生したデータ変更の数をカウントし、その変更の数をしきい値と比較することで、統計が古くなっている可能性がないかを判断します。 このしきい値は、テーブルまたはインデックス付きビューの行数に基づいて決められます。  
  
クエリ オプティマイザーによる古い統計の確認は、クエリをコンパイルする前と、キャッシュされたクエリ プランを実行する前に行われます。 クエリをコンパイルする前は、クエリ オプティマイザーで、クエリ述語内の列、テーブル、およびインデックス付きビューを使用して古くなっている可能性がある統計が判断されます。 キャッシュされたクエリ プランを実行する前は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で、クエリ プランが最新の統計を参照しているかどうかが確認されます。  
  
AUTO_UPDATE_STATISTICS オプションは、インデックスに対して作成された統計、クエリ述語内の列に対して 1 列ずつ作成された統計、および CREATE STATISTICS ステートメントを使用して作成された統計に適用されます。 また、フィルター選択された統計情報にも適用されます。  
  
既定値は ON です。 ほとんどのデータベースで既定の設定を使用することをお勧めします。  
  
統計を同期的に更新するか非同期的に更新するかを指定するには、AUTO_UPDATE_STATISTICS_ASYNC オプションを使用します。  
  
OFF  
クエリで使用される統計が古くなっている可能性がある場合にクエリ オプティマイザーによって更新されないように指定します。 このオプションを OFF に設定すると、最適ではないクエリ プランが作成されて、クエリのパフォーマンスが低下することがあります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_update_stats_on 列、または DATABASEPROPERTYEX 関数の IsAutoUpdateStatistics プロパティを調べてください。  
  
詳細については、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
<a name="auto_update_statistics_async"></a> AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
ON  
AUTO_UPDATE_STATISTICS オプションの統計の更新を非同期更新にするように指定します。 クエリ オプティマイザーは、統計の更新が完了するのを待たずにクエリをコンパイルします。  
  
AUTO_UPDATE_STATISTICS が ON に設定されていなければ、このオプションを ON に設定しても、効果はありません。  
  
既定では、AUTO_UPDATE_STATISTICS_ASYNC オプションは OFF に設定されており、クエリ オプティマイザーによる統計の更新は同期更新になります。  
  
OFF  
AUTO_UPDATE_STATISTICS オプションの統計の更新を同期更新にするように指定します。 クエリ オプティマイザーは、統計の更新が完了するのを待ってからクエリをコンパイルします。  
  
AUTO_UPDATE_STATISTICS が ON に設定されていなければ、このオプションを OFF に設定しても、効果はありません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_update_stats_async_on 列を調べてください。  
  
統計の同期更新と非同期更新をそれぞれどのような場合に使用するのかについては、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
<a name="auto_tuning"></a> **\<automatic_tuning_option> ::=**  
**適用対象**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]  

`FORCE_LAST_GOOD_PLAN` [自動調整](../../relational-databases/automatic-tuning/automatic-tuning.md)オプションを有効または無効にします。  
  
FORCE_LAST_GOOD_PLAN = { ON | OFF }  
ON  
新しい SQL プランがパフォーマンスの低下を引き起こしている [!INCLUDE[tsql_md](../../includes/tsql_md.md)] クエリに対して、[!INCLUDE[ssde_md](../../includes/ssde_md.md)] では最後の既知の正常なプランが自動的に強制されます。 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] は、強制プランを使用する [!INCLUDE[tsql_md](../../includes/tsql_md.md)] クエリのクエリ パフォーマンスを継続的に監視します。 パフォーマンスが向上した場合、[!INCLUDE[ssde_md](../../includes/ssde_md.md)] では最後の既知の正常なプランの使用が続けられます。 パフォーマンスの向上が検出されない場合、[!INCLUDE[ssde_md](../../includes/ssde_md.md)] は新しい SQL プランを生成します。 クエリ ストアが有効でない場合、または*読み取り/書き込み*モードでない場合は、ステートメントは失敗します。   
OFF  
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] は、[sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) ビューの SQL プランの変更によって引き起こされる、潜在的なクエリ パフォーマンスの低下をレポートします。 ただし、これらの推奨事項は自動的には適用されません。 ユーザーは、ビューに表示される [!INCLUDE[tsql_md](../../includes/tsql_md.md)] スクリプトを適用することによって、アクティブな推奨事項を監視し、特定された問題を解決することができます。 これが既定値です。

**\<change_tracking_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssSDSFull](../../includes/sssds-md.md)]。  
  
変更の追跡のオプションを制御します。 変更の追跡の有効化、オプションの設定、オプションの変更、および変更の追跡の無効化が可能です。 例については、後の「例」のセクションをご覧ください。  
  
ON  
データベースの変更の追跡を有効にします。 変更の追跡を有効にすると、AUTO CLEANUP オプションと CHANGE RETENTION オプションも設定できます。  
  
AUTO_CLEANUP = { ON | OFF }  
ON  
指定した保有期間を過ぎると、変更追跡情報が自動的に削除されます。  
  
OFF  
変更追跡データがデータベースから削除されません。  
  
CHANGE_RETENTION =*retention_period* { DAYS | HOURS | MINUTES }  
データベースに変更追跡情報を保持する最低限の期間を指定します。 データは、AUTO_CLEANUP の値が ON のときにのみ削除されます。  
  
*retention_period* は、保有期間の数値部分を指定する整数です。  
  
既定の保有期間は 2 日です。 最小保有期間は 1 分です。 保有期間の既定の型は DAYS です。  
  
OFF  
データベースの変更の追跡を無効にします。 データベースの変更の追跡を無効にする前に、すべてのテーブルで変更の追跡を無効にする必要があります。  
  
**\<containment_option> ::=**  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
データベースの包含オプションを制御します。  
  
CONTAINMENT = { NONE | PARTIAL}  
なし  
データベースは非包含データベースです。  
  
PARTIAL  
データベースは包含データベースです。 レプリケーション、変更データ キャプチャ、または変更の追跡が有効になっているデータベースの包含状態を PARTIAL に設定すると失敗します。 エラー チェックは、エラーを 1 つ検出すると停止します。 包含データベースの詳細については、「 [Contained Databases](../../relational-databases/databases/contained-databases.md)」をご覧ください。  
  
**\<cursor_option> ::=**  
  
カーソル オプションを制御します。  
  
CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
ON  
トランザクションのコミットまたはロールバック時に開いていたすべてのカーソルが閉じます。  
  
OFF  
トランザクションがコミットされても、カーソルは開いたままになります。トランザクションをロールバックすると、INSENSITIVE または STATIC として定義されているカーソルを除き、すべてのカーソルが閉じます。  
  
SET ステートメントを使用した接続レベルの設定は、CURSOR_CLOSE_ON_COMMIT の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの CURSOR_CLOSE_ON_COMMIT を OFF に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_cursor_close_on_commit_on 列、または DATABASEPROPERTYEX 関数の IsCloseCursorsOnCommitEnabled プロパティを調べてください。  
 
CURSOR_DEFAULT { LOCAL | GLOBAL }  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 
  
カーソルのスコープを LOCAL と GLOBAL のどちらにするかを制御します。  
  
LOCAL  
LOCAL を指定すると、カーソルが作成時に GLOBAL として定義されていない場合、カーソルのスコープは、そのカーソルが作成されたバッチ、ストアド プロシージャ、またはトリガーに限定されます。 カーソル名はこのスコープ内だけで有効です。 カーソルは、バッチ、ストアド プロシージャ、またはトリガー内のローカル カーソル変数からか、ストアド プロシージャの OUTPUT パラメーターから参照できます。 OUTPUT パラメーター内でカーソルが戻されない限り、バッチ、ストアド プロシージャ、またはトリガーが終了すると、カーソルは暗黙的に割り当てを解除されます。 カーソルが OUTPUT パラメーターで戻された場合は、カーソルを参照している最後の変数が割り当て解除されるか、スコープ外になったときに、カーソルの割り当てが解除されます。  
  
GLOBAL  
GLOBAL を指定すると、カーソルが作成時に LOCAL として定義されていない場合、カーソルのスコープはその接続に対してグローバルになります。 カーソル名は、その接続によって実行されるストアド プロシージャやバッチの中で参照できます。  
  
接続が切断されたときだけカーソルが暗黙的に割り当てを解除されます。 詳しくは、「[DECLARE CURSOR](../../t-sql/language-elements/declare-cursor-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_local_cursor_default 列、または DATABASEPROPERTYEX 関数の IsLocalCursorsDefault プロパティを調べてください。  
  
**\<database_mirroring>**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
引数の説明については、「[ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)」をご覧ください。  
  
**\<date_correlation_optimization_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
date_correlation_optimization オプションを制御します。  
  
DATE_CORRELATION_OPTIMIZATION { ON | OFF }  
ON  
データベース内にある、FOREIGN KEY 制約でリンクされ、**datetime** 列を含んでいる 2 つのテーブル間の相関関係に関する統計が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって保持されます。  
  
OFF  
相関統計は保持されません。  
  
DATE_CORRELATION_OPTIMIZATION を ON に設定するには、データベースに対するアクティブな接続が、ALTER DATABASE ステートメントを実行する接続の他には存在しないようにします。 設定後、複数の接続がサポートされます。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_date_correlation_on 列を調べてください。  
  
**\<db_encryption_option> ::=**  
  
データベース暗号化の状態を制御します。  
  
ENCRYPTION {ON | OFF}  
データベースを暗号化する (ON) か、暗号化しない (OFF) かを設定します。 データベース暗号化について詳しくは、「[透過的なデータ暗号化](../../relational-databases/security/encryption/transparent-data-encryption.md)」および「[Azure SQL Database での Transparent Data Encryption](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)」をご覧ください。  
  
データベース レベルで暗号化を有効にすると、すべてのファイル グループが暗号化されます。 すべての新しいファイル グループに、その暗号化プロパティが継承されます。 データベースに **READ ONLY** に設定されているファイル グループがあると、データベースの暗号化操作は失敗します。  
  
データベースの暗号化の状態を確認するには、[sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) 動的管理ビューを使用します。  
  
**\<db_state_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 
  
データベースの状態を制御します。  
  
OFFLINE  
データベースが閉じ、正常にシャットダウンされ、オフラインとしてマークされます。 データベースがオフラインのときはデータベースを変更できません。  
  
ONLINE  
データベースが開き、使用可能になります。  
  
EMERGENCY  
データベースは READ_ONLY に設定され、ログ記録が無効になり、アクセスが sysadmin 固定サーバー ロールのメンバーに制限されます。 EMERGENCY は、主にトラブルシューティングの目的で使用されます。 たとえば、破損したログ ファイルが原因で問題ありとマークされたデータベースを EMERGENCY 状態に設定できます。 これにより、システム管理者はデータベースに読み取り専用でアクセスできるようになります。 sysadmin 固定サーバー ロールのメンバーのみが、データベースを EMERGENCY 状態に設定できます。  
  
> [!NOTE]  
> **権限:** データベースを OFFLINE または EMERGENCY 状態に変更するには、サブジェクト データベースに対する ALTER DATABASE 権限が必要です。 データベースを OFFLINE から ONLINE にするには、サーバー レベルの ALTER ANY DATABASE 権限が必要です。  
  
このオプションの状態を確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの state および state_desc 列、または [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) 関数の Status プロパティを調べます。 詳細については、「 [データベースの状態](../../relational-databases/databases/database-states.md)」を参照してください。  
  
RESTORING とマークされたデータベースを OFFLINE、ONLINE、または EMERGENCY に設定することはできません。 データベースが RESTORING 状態になるのは、アクティブな復元操作中や、バックアップ ファイルの破損によりデータベースまたはログ ファイルの復元操作が失敗した場合などです。  
  
**\<db_update_option> ::=**  
  
データベースで更新を許可するかどうかを制御します。  
  
READ_ONLY  
ユーザーは、データベースのデータを読み取ることができますが、変更はできません。  
  
> [!NOTE]  
>  クエリのパフォーマンスを向上させるには、データベースを READ_ONLY に設定する前に統計を更新します。 データベースを READ_ONLY に設定した後に追加の統計が必要な場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] によって統計が tempdb に作成されます。 読み取り専用データベースの統計について詳しくは、「[統計](../../relational-databases/statistics/statistics.md)」をご覧ください。  
  
READ_WRITE  
データベースに対して読み取りおよび書き込み操作を行うことができます。  
  
この状態を変更するには、データベースに対する排他的アクセスが必要になります。 詳細については、SINGLE_USER 句をご覧ください。  
  
> [!NOTE]  
> [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のフェデレーション データベースでは、SET {READ_ONLY | READ_WRITE} は無効です。  
  
**\<db_user_access_option> ::=**  
  
データベースへのユーザー アクセスを制御します。  
  
SINGLE_USER  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 
  
一度に 1 人のユーザーだけがデータベースにアクセスできます。 SINGLE_USER が指定されており、他のユーザーがデータベースに接続している場合には、指定したデータベースからすべてのユーザーが接続解除するまで、ALTER DATABASE ステートメントはブロックされます。 この動作をオーバーライドする場合は、WITH \<termination&gt; 句を確認します。  
  
このオプションを設定したユーザーがログオフしても、データベースは SINGLE_USER モードのままです。 そのユーザーがログオフした時点で、他のユーザーが 1 人だけデータベースに接続できます。  
  
データベースを SINGLE_USER に設定する前に、AUTO_UPDATE_STATISTICS_ASYNC オプションが OFF に設定されていることを確認します。 ON に設定されていると、統計の更新に使用されるバックグラウンド スレッドによってデータベースへの接続が使用されるため、シングル ユーザー モードではデータベースにアクセスできなくなります。 このオプションの状態を表示するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの is_auto_update_stats_async_on 列に対してクエリを実行します。 このオプションが ON に設定されている場合、次の作業を行います。  
  
1. AUTO_UPDATE_STATISTICS_ASYNC を OFF に設定します。  
  
2. [sys.dm_exec_background_job_queue](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md) 動的管理ビューにクエリを実行することにより、アクティブな非同期の統計ジョブがあるかどうかを確認します。  
  
アクティブなジョブがある場合、それらのジョブが完了するまで待つか、[KILL STATS JOB](../../t-sql/language-elements/kill-stats-job-transact-sql.md) を使用して手動でジョブを終了します。  
  
RESTRICTED_USER  
RESTRICTED_USER モードでは、db_owner 固定データベース ロールと、dbcreator 固定サーバー ロールおよび sysadmin 固定サーバー ロールのメンバーのみが、データベースに接続できます。ただし、接続ユーザー数に制限はありません。 データベースに対するすべての接続は、ALTER DATABASE ステートメントの終了句で指定した時間枠内に接続解除されます。 データベースが RESTRICTED_USER 状態に移行すると、資格のないユーザーによる接続の試みは拒否されます。  
  
MULTI_USER  
データベースに接続するための適切な権限を持つすべてのユーザーが許可されます。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの user_access 列、または DATABASEPROPERTYEX 関数の UserAccess プロパティを調べてください。  
  
**\<delayed_durability_option> ::=**  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
トランザクションを完全持続性または遅延持続性のどちらとしてコミットするかどうかを制御します。  
  
DISABLED  
SET DISABLED 以後のトランザクションはすべて完全持続性です。 ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションは無視されます。  
  
ALLOWED  
SET ALLOWED 以後のトランザクションはすべて、ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションに応じて、完全持続性または遅延持続性です。  
  
FORCED  
SET FORCED 以後のトランザクションはすべて遅延持続性です。 ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションは無視されます。  
  
**\<external_access_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 
  
別のデータベースのオブジェクトなど、外部リソースからデータベースにアクセスできるかどうかを制御します。  
  
DB_CHAINING {ON |OFF}  
ON  
データベースは、複数データベースの組み合わせ所有権の連係でソース データベースまたはターゲット データベースになることができます。  
  
OFF  
データベースは、複数データベースの組み合わせ所有権に参加できません。  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでは、cross db ownership chaining サーバー オプションが 0 (OFF) の場合に、この設定が認識されます。 cross db ownership chaining が 1 (ON) の場合は、このオプションの値にかかわらず、すべてのユーザー データベースが複数データベースの組み合わせ所有権に参加できます。 このオプションは、[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して設定します。  
  
このオプションを設定する、データベースに対する CONTROL SERVER 権限が必要です。  
  
master、model、および tempdb の各システム データベースでは、DB_CHAINING オプションを設定することはできません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_db_chaining_on 列を調べてください。  
  
信頼できる {ON |OFF}  
ON  
権限借用コンテキストを使用するデータベース モジュール (ユーザー定義関数やストアド プロシージャなど) は、データベース外部のリソースにアクセスできます。  
  
OFF  
権限借用コンテキスト内にあるデータベース モジュールは、データベース外部のリソースにアクセスできません。  
  
データベースがアタッチされている場合は常に、TRUSTWORTHY は OFF に設定されます。  
  
既定では、msdb データベースを除くすべてのシステム データベースで TRUSTWORTHY は OFF に設定されています。 model および tempdb データベースでは、この値は変更できません。 master データベースでは、TRUSTWORTHY オプションを ON に設定しないことを強くお勧めします。  
  
このオプションを設定する、データベースに対する CONTROL SERVER 権限が必要です。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_trustworthy_on 列を調べてください。  
  
DEFAULT_FULLTEXT_LANGUAGE  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
フルテキスト インデックス列に、既定の言語の値を指定します。  
  
> [!IMPORTANT]  
>  このオプションは、CONTAINMENT が PARTIAL に設定されている場合にのみ使用できます。 CONTAINMENT が NONE に設定されている場合、エラーが発生します。  
  
DEFAULT_LANGUAGE  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
新しく作成するすべてのログインの既定の言語を指定します。 ローカル ID (LCID)、言語の名前、または言語のエイリアスを提供することで言語を指定することができます。 使用可能な言語名およびエイリアスの一覧については、「[sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)」をご覧ください。 このオプションは、CONTAINMENT が PARTIAL に設定されている場合にのみ使用できます。 CONTAINMENT が NONE に設定されている場合、エラーが発生します。  
  
NESTED_TRIGGERS  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
AFTER トリガーを連鎖できるかどうかを指定します。つまり、1 つの操作が別のトリガーを開始し、開始されたトリガーからさらに別のトリガーを開始するなどの動作ができるかどうかを制御します。 このオプションは、CONTAINMENT が PARTIAL に設定されている場合にのみ使用できます。 CONTAINMENT が NONE に設定されている場合、エラーが発生します。  
  
TRANSFORM_NOISE_WORDS  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
ノイズ ワード (ストップワード) が原因でフルテキスト クエリのブール演算が失敗する場合に、エラー メッセージを非表示にします。 このオプションは、CONTAINMENT が PARTIAL に設定されている場合にのみ使用できます。 CONTAINMENT が NONE に設定されている場合、エラーが発生します。  
  
TWO_DIGIT_YEAR_CUTOFF  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
2 桁の数字を 4 桁の西暦として解釈する場合に、世紀の解釈の区切りとする年を 1753 ～ 9999 範囲の整数で指定します。 このオプションは、CONTAINMENT が PARTIAL に設定されている場合にのみ使用できます。 CONTAINMENT が NONE に設定されている場合、エラーが発生します。  
 
**\<FILESTREAM_option> ::=**  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
FileTable の設定を制御します。  
  
NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
OFF  
FileTable データに対する非トランザクション アクセスは無効です。  
  
READ_ONLY  
このデータベース内の FileTable の FILESTREAM データは、非トランザクション プロセスによって読み取ることができます。  
  
FULL  
FileTable の FILESTREAM データに対する完全な非トランザクション アクセスは有効です。  
  
DIRECTORY_NAME = *\<directory_name>*  
Windows と互換性のあるディレクトリ名です。 この名前は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内のすべてのデータベース レベルのディレクトリ名の中で一意である必要があります。 一意性の比較では、照合順序の設定とは関係なく、大文字と小文字は区別されません。 このオプションは、このデータベース内に FileTable を作成する前に設定する必要があります。  
  
**\<HADR_options> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 
  
「[ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)」をご覧ください。  
  
**\<mixed_page_allocation_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。 
  
MIXED_PAGE_ALLOCATION { OFF | ON } は、データベースが、テーブルまたはインデックスの最初の 8 ページに対して混合エクステントを使用して、最初のページを作成できるかどうかを制御します。  
 
OFF  
データベースは、常に単一エクステントを使用して最初のページを作成します。 これが既定値です。  
  
ON  
データベースは、混合エクステントを使用して最初のページを作成できます。  
  
この設定は、すべてのシステム データベースに対して ON です。 **tempdb** は OFF に対応する唯一のシステム データベースです。  
  
**\<PARAMETERIZATION_option> ::=**  
  
パラメーター化オプションを制御します。  
  
PARAMETERIZATION { SIMPLE | FORCED }  
SIMPLE  
クエリは、データベースの既定の動作に基づいてパラメーター化されます。  
  
FORCED  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、データベース内にあるすべてのクエリをパラメーター化します。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_parameterization_forced 列を調べてください。  
  
**\<query_store_options> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
ON |オフ |[すべて] をオフに  
コントロールは、このデータベースにクエリ ストアが有効になっている場合とそのコントロールが、クエリのストアの内容を削除します。  
  
ON  
クエリのストアを有効にします。  
  
OFF  
クエリのストアを無効にします。  これが既定値です。   
  
CLEAR  
クエリ ストアの内容を削除します。  
  
OPERATION_MODE  
クエリのストアの操作モードをについて説明します。 有効な値は、READ_ONLY、READ_WRITE はします。 READ_WRITE モードでは、クエリのストアは、収集し、クエリ プランとランタイム実行の統計情報が引き続き発生すます。 READ_ONLY モードでは、クエリのストアから情報を読み取ることができますが、新しい情報は追加されません。 クエリのストアを変更は、最大値が割り当てられているクエリのストアの領域が不足している場合は操作モードを READ_ONLY にします。  
  
CLEANUP_POLICY  
クエリのストアのデータ保有ポリシーをについて説明します。 STALE_QUERY_THRESHOLD_DAYS をクエリの情報は、クエリのストアに保存日数の数を決定します。 STALE_QUERY_THRESHOLD_DAYS は **bigint** 型です。  
  
DATA_FLUSH_INTERVAL_SECONDS  
クエリに書き込まれるデータ ストアが永続化する頻度を決定をディスクにします。 パフォーマンスを最適化するには、クエリのストアで収集したデータ非同期的にディスクに書き込まれます。 この非同期転送が発生する頻度を構成するには、DATA_FLUSH_INTERVAL_SECONDS 引数を使用します。 DATA_FLUSH_INTERVAL_SECONDS は **bigint** 型です。  
  
MAX_STORAGE_SIZE_MB  
クエリのストアに割り当てられた領域を判断します。 MAX_STORAGE_SIZE_MB は **bigint** 型です。  
  
INTERVAL_LENGTH_MINUTES  
クエリのストアにランタイムの実行の統計データを集計する時間間隔を決定します。 領域の使用状況を最適化するには、実行時の統計データ ストアでランタイム実行の統計は、一定の時間のウィンドウで集計されます。 この固定された時間帯を構成するには、INTERVAL_LENGTH_MINUTES 引数を使用します。 INTERVAL_LENGTH_MINUTES は **bigint** 型です。  
  
SIZE_BASED_CLEANUP_MODE  
かどうかのクリーンアップが自動的にアクティブになるデータの合計サイズを取得する最大サイズに近いかを制御します。  
  
OFF  
サイズ ベースのクリーンアップは自動的にアクティブ化されません。 
  
AUTO  
ディスクのサイズが **max_storage_size_mb** の 90% に達すると、サイズ ベースのクリーンアップが自動的にアクティブ化されます。 サイズのクリーンアップでは、まず最も安価で最も古いクエリを削除します。 **max_storage_size_mb** の約 80% で停止します。  これは、既定の構成値です。  
  
SIZE_BASED_CLEANUP_MODE は **nvarchar** 型です。  
  
QUERY_CAPTURE_MODE  
現在アクティブなクエリのキャプチャ モードを指定します。  
  
ALL すべてのクエリがキャプチャされます。 これは、既定の構成値です。  これは、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の既定の構成値です。
  
AUTO 実行の数とリソースの消費量に基づいて関連するクエリをキャプチャします。
  
NONE 新しいクエリのキャプチャを停止します。 クエリ ストアは、既にキャプチャされたクエリのコンパイルと実行時の統計情報を収集し続けます。 重要なクエリをキャプチャするされない場合がありますので、注意してこの構成を使用します。  
  
QUERY_CAPTURE_MODE は **nvarchar** 型です。  
  
max_plans_per_query  
各クエリに対して保持の計画の最大数を表す整数。 既定値は 200 です。  
  
**\<recovery_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
データベース復旧オプションおよびディスク I/O エラー チェックを制御します。  
  
FULL  
メディア障害が発生した後に、トランザクション ログのバックアップを使用して、完全復旧を行います。 データ ファイルが破損した場合、メディアの復旧によって、コミットされたすべてのトランザクションを復元できます。 詳しくは、「[復旧モデル](../../relational-databases/backup-restore/recovery-models-sql-server.md)」をご覧ください。  
  
BULK_LOGGED  
メディア障害が発生した後に、特定の大規模操作または一括操作において、パフォーマンスが最もよく、ログ領域の使用量が最も小さくなるようにして、復旧を行います。 最小ログ記録が可能な操作について詳しくは、「[トランザクション ログ](../../relational-databases/logs/the-transaction-log-sql-server.md)」をご覧ください。 BULK_LOGGED 復旧モデルでは、これらの操作に関するログ記録は最小になります。 詳しくは、「[復旧モデル](../../relational-databases/backup-restore/recovery-models-sql-server.md)」をご覧ください。  
  
SIMPLE  
最小のログ領域を使用する、単純なバックアップ方法が実行されます。 ログ領域は、サーバー障害の復旧での使用が終わると自動的に再利用できるようになります。 詳しくは、「[復旧モデル](../../relational-databases/backup-restore/recovery-models-sql-server.md)」をご覧ください。  
  
> [!IMPORTANT]  
> 単純復旧モデルは、他の 2 つのモデルよりも管理が簡単ですが、データ ファイルが破損した場合にデータが失われる危険性が高くなります。 前回のデータベースのバックアップ作成や差分バックアップ作成の後に行った変更はすべて失われるため、手作業で入力し直す必要があります。  
  
既定の復旧モデルは、**model** データベースの復旧モデルによって決定されます。 適切な復旧モデルの選択について詳しくは、「[復旧モデル](../../relational-databases/backup-restore/recovery-models-sql-server.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの **recovery_model** および **recovery_model_desc** 列、または DATABASEPROPERTYEX 関数の Recovery プロパティを調べてください。  
  
TORN_PAGE_DETECTION { ON | OFF }  
ON  
[!INCLUDE[ssDE](../../includes/ssde-md.md)] によって、不完全なページを検出できます。  
  
OFF  
[!INCLUDE[ssDE](../../includes/ssde-md.md)] は不完全なページを検出できません。  
  
> [!IMPORTANT]  
> 構文構造 TORN_PAGE_DETECTION ON | OFF は、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では削除される予定です。 新しい開発作業ではこの構文構造の使用を避け、現在この構文構造を使用しているアプリケーションは修正するようにしてください。 代わりに、PAGE_VERIFY オプションを使用してください。  
  
<a name="page_verify"></a> PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }  
ディスク I/O パスのエラーが原因で破損したデータベース ページを検出します。 ディスク I/O パスのエラーは、データベース破損問題の原因となる可能性があり、一般にはページがディスクに書き込まれている最中に発生した電源障害やディスクのハードウェア障害によって引き起こされます。  
  
CHECKSUM  
ページ全体の内容についてチェックサムを計算し、ページがディスクに書き込まれるときに、その値をページ ヘッダーに格納します。 ページがディスクから読み取られるときに、チェックサムが再計算され、ページ ヘッダーに格納されているチェックサムの値と比較されます。 両方の値が一致しない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと Windows イベント ログの両方に、エラー メッセージ 824 (チェックサム エラーを示す) がレポートされます。 チェックサム エラーは、I/O パスに問題があることを示します。 根本的な原因を確認するには、ハードウェア、ファームウェア ドライバー、BIOS、フィルター ドライバー (ウイルス対策ソフトウェアなど)、およびその他の I/O パス コンポーネントを点検する必要があります。  
  
TORN_PAGE_DETECTION  
8 KB のデータベース ページに含まれる 512 バイトのセクターごとに特定の 2 ビット パターンを保存し、ページがディスクに書き込まれるときに、データベース ページ ヘッダーに格納します。 そのページがディスクから読み取られるときに、ページ ヘッダーに保存されている各セクターの破損ビットと、実際のページ セクター情報とが比較されます。 値が一致しない場合は、ページの一部だけがディスクに書き込まれたことを示しています。 この場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと Windows イベント ログの両方に、エラー メッセージ 824 (破損ページ エラーを示す) がレポートされます。 ページの不完全書き込みにより破損したページは、通常はデータベース復旧時に検出されます。 ただし、その他の I/O パス障害によっても、破損ページが発生する可能性があります。  
  
なし  
データベース ページの書き込み時に CHECKSUM 値または TORN_PAGE_DETECTION 値は生成されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ページ ヘッダーに CHECKSUM 値や TORN_PAGE_DETECTION 値が存在する場合でも、読み取り中にチェックサムや破損ページを確認しません。  
  
PAGE_VERIFY オプションを使用する場合は、次に示す重要な点を考慮してください。  
  
- 既定値は CHECKSUM です。  
- ユーザー データベースまたはシステム データベースを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンにアップグレードしても、PAGE_VERIFY 値 (NONE または TORN_PAGE_DETECTION) が保持されます。 CHECKSUM の使用をお勧めします。  
  
    > [!NOTE]  
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでは、PAGE_VERIFY データベース オプションは tempdb データベースについては NONE に設定されており、変更できません。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新規インストールに対する tempdb データベースの既定値は CHECKSUM です。 インストール済みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードした場合、既定値は NONE のままです。 このオプションは変更できます。 tempdb データベースでは CHECKSUM を使用することをお勧めします。  
  
- TORN_PAGE_DETECTION は、使用するリソースが比較的少なくて済みますが、CHECKSUM による保護の最小限のサブセットしか利用できません。  
- PAGE_VERIFY は、データベースをオフラインにしたり、データベースをロックしたりなど、そのデータベース上での同時実行性を妨げるような措置を取らずに設定できます。  
- CHECKSUM は、TORN_PAGE_DETECTION と共存できません。 両方のオプションを同時に有効化することはできません。  
  
破損ページまたはチェックサム エラーが検出された場合には、データを復元することで復旧できます。障害がインデックス ページだけに限られていれば、インデックスを再構築することで復旧できる可能性があります。 チェックサム エラーが発生した場合、影響を受けるデータベース ページの種類を判別するには、DBCC CHECKDB を実行します。 復元オプションについて詳しくは、「[RESTORE の引数](../../t-sql/statements/restore-statements-arguments-transact-sql.md)」をご覧ください。 データを復元すれば、データ破損の問題は解決しますが、エラーが継続的に発生することを防ぐには、ディスク ハードウェア障害などの根本的な原因を、直ちに診断して修正しておく必要があります。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、チェックサム、破損ページ、またはその他の I/O エラーで読み取りに失敗した場合、その読み取りを 4 回再試行します。 いずれかの再試行で読み取りに成功した場合には、エラー ログにメッセージが書き込まれ、その読み取りを起動したコマンドは続行されます。 再試行が失敗した場合には、そのコマンドはエラー メッセージ 824 で失敗します。  
  
エラー メッセージ 823、824、および 825 について詳しくは、「[SQL Server でのメッセージ 823 エラーのトラブルシューティングの方法](http://support.microsoft.com/help/2015755)」、「[SQL Server でのメッセージ 824 のトラブルシューティングの方法](http://support.microsoft.com/help/2015756)」、および「[How to troubleshoot Msg 825 &#40;read retry&#41; in SQL Server](http://support.microsoft.com/help/2015757)」(SQL Server でのメッセージ 825 &#40;読み取り再試行&#41; のトラブルシューティングの方法) を参照してください。
  
このオプションの現在の設定を確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの *page_verify_option* 列、または [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) 関数の *IsTornPageDetectionEnabled* プロパティを調べてください。  
  
**\<remote_data_archive_option> ::=**  
 
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
有効にまたはデータベースの伸縮データベースを無効にします。 詳細については、「 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。  
  
REMOTE_DATA_ARCHIVE = { ON ( SERVER = \<server_name> , { CREDENTIAL = \<db_scoped_credential_name> | FEDERATED_SERVICE_ACCOUNT =  ON | OFF } )| OFF ON  
データベースのデータベースの伸縮有効にします。 追加の前提条件を含む詳細については、「[データベースに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
**権限**: データベースまたはテーブル データベースの伸縮を有効にするには、db_owner アクセス許可が必要です。 データベースの伸縮データベースを有効にすると、管理データベースのアクセス許可も必要です。  
  
SERVER = \<server_name>  
Azure サーバーのアドレスを指定します。 名前の `.database.windows.net` の部分を含めます。 たとえば、 `MyStretchDatabaseServer.database.windows.net`のようにします。  
  
CREDENTIAL = \<db_scoped_credential_name>  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが Azure サーバーに接続するために使用する、データベース スコープ資格情報を指定します。 このコマンドを実行する前に、資格情報が存在することを確認します。 詳しくは、「[CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)」をご覧ください。  
  
FEDERATED_SERVICE_ACCOUNT =  ON | OFF  
以下の条件をすべて満たす場合、オンプレミスの SQL Server のフェデレーション サービス アカウントを使用して、リモート Azure サーバーと通信できます。  
  
- SQL Server のインスタンスを実行しているサービス アカウントがドメイン アカウントである。  
- Active Directory が Azure Active Directory とフェデレーションされているドメインに、ドメイン アカウントが属している。  
- Azure Active Directory 認証をサポートするように、リモート Azure サーバーが構成されている。  
- SQL Server のインスタンスを実行しているサービス アカウントが、リモート Azure サーバー上で dbmanager または sysadmin アカウントとして構成されている。  
  
ON を指定する場合は、CREDENTIAL 引数を指定することはできません。 OFF を指定する場合は、CREDENTIAL 引数を指定する必要があります。  
  
OFF  
データベースの伸縮データベースを無効にします。 詳細については、「 [Stretch Database を無効にして、リモート データを戻す](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md)」を参照してください。  
  
データベースが不要になった Stretch データベースに対して有効になっているすべてのテーブルを格納した後は、のみ、データベースの伸縮データベース無効にすることができます。 Stretch データベースを無効にした後のデータの移行が停止し、クエリの結果が含まれないようにリモート テーブルからの結果。  
  
Stretch を無効にしても、リモート データベースは削除されません。 リモート データベースを削除する場合は、Azure portal を使用して削除する必要があります。  
  
**\<service_broker_option> ::=**  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
次の [!INCLUDE[ssSB](../../includes/sssb-md.md)] オプション (メッセージ配信の有効化または無効化、新しい [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子の設定、メッセージ交換の優先度の ON または OFF への設定) を制御します。  
  
ENABLE_BROKER  
指定したデータベースに対して [!INCLUDE[ssSB](../../includes/sssb-md.md)] を有効にします。 メッセージ配信が開始され、sys.databases カタログ ビューでは is_broker_enabled フラグが true に設定されます。 データベースは、既存の [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子を保持します。 Service Broker は、データベースがデータベース ミラーリング構成でプリンシパルである間は有効にすることができません。  
  
> [!NOTE]  
>  ENABLE_BROKER には排他的データベース ロックが必要です。 他のセッションによってデータベースのリソースがロックされている場合、ENABLE_BROKER は、そのセッションがロックを解除するまで待機します。 ユーザー データベースで [!INCLUDE[ssSB](../../includes/sssb-md.md)] を有効にするには、データベースをシングル ユーザー モードに設定するなどして、他のセッションがそのデータベースを使用しないようにしてから ALTER DATABASE SET ENABLE_BROKER ステートメントを実行する必要があります。 msdb データベースで [!INCLUDE[ssSB](../../includes/sssb-md.md)] を有効にするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で必要なロックを取得できるように、まず [!INCLUDE[ssSB](../../includes/sssb-md.md)] エージェントを停止します。  
  
DISABLE_BROKER  
指定したデータベースに対して [!INCLUDE[ssSB](../../includes/sssb-md.md)] を無効にします。 メッセージ配信が停止され、is_broker_enabled フラグが sys.databases カタログ ビューで false に設定されます。 データベースは、既存の [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子を保持します。  
  
NEW_BROKER  
データベースは新しいブローカー識別子を受信するように指定します。 データベースは新しい Service Broker と見なされるため、データベースにおける既存のすべてのメッセージ交換は、終了ダイアログ メッセージを生成せずに、直ちに削除されます。 古い [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子を参照するルートは、新しい識別子を使用して作成し直す必要があります。  
  
ERROR_BROKER_CONVERSATIONS  
[!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージ配信を有効にします。 これは、データベースの既存の [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子を保持します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] により、データベース内のメッセージ交換がすべて終了し、エラーが返されます。 これによりアプリケーションは、既存のメッセージ交換に対して、通常のクリーンアップを実行できます。  
  
HONOR_BROKER_PRIORITY {ON | OFF}  
ON  
メッセージ交換に割り当てられた優先度が、送信操作で考慮されます。 優先度が高いメッセージ交換のメッセージは、低い優先度が割り当てられたメッセージ交換のメッセージよりも先に送信されます。  
  
OFF  
すべてのメッセージ交換が既定の優先度レベルを持つと見なして、送信操作が実行されます。  
  
新しいダイアログや、送信待ちメッセージがないダイアログでは、HONOR_BROKER_PRIORITY オプションに対する変更が直ちに有効になります。 ALTER DATABASE の実行時に送信待ちメッセージがあるダイアログでは、それらのメッセージの一部が送信されるまで、新しい設定が反映されません。 すべてのダイアログで新しい設定が使用されるようになるまでの時間は、場合により大幅に異なります。  
  
このプロパティの現在の設定は、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの is_broker_priority_honored 列に表示されます。  
 
**\<snapshot_option> ::=**  
  
トランザクション分離レベルを決定します。  
  
ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
ON  
データベース レベルでのスナップショット オプションを有効にします。 有効にした場合、スナップショット分離を使用するトランザクションがなくても、DML ステートメントによって、行バージョンの生成が開始されます。 このオプションを有効にすると、トランザクションで SNAPSHOT トランザクション分離レベルを指定できます。 SNAPSHOT 分離レベルでトランザクションが実行されると、すべてのステートメントはトランザクション開始時のデータのスナップショットを参照します。 SNAPSHOT 分離レベルで実行されているトランザクションが複数のデータベースのデータにアクセスする場合は、すべてのデータベースで ALLOW_SNAPSHOT_ISOLATION が ON に設定されている必要があります。ALLOW_SNAPSHOT_ISOLATION が OFF になっているデータベース内のテーブルにアクセスする場合は、トランザクション内の各ステートメントで、FROM 句内のすべての参照に対してロック ヒントを使用する必要があります。  
  
OFF  
データベース レベルでのスナップショット オプションを無効にします。 トランザクションに、SNAPSHOT トランザクション分離レベルを指定できません。  
  
ALLOW_SNAPSHOT_ISOLATION を新しい状態に (ON から OFF へ、または OFF から ON へ) 設定した場合、ALTER DATABASE は、データベース内にあるすべての既存のトランザクションがコミットされるまで、呼び出し元に制御を返しません。 データベースが既に ALTER DATABASE ステートメントで指定した状態にある場合には、制御は呼び出し元に直ちに返されます。 ALTER DATABASE ステートメントがすぐに制御を返さない場合には、[sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) を使用して、長時間実行されているトランザクションがあるかどうかを確認できます。 ALTER DATABASE ステートメントが取り消された場合、データベースは、ALTER DATABASE が開始された時点での状態に留まります。 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューに、データベース内のスナップショット分離トランザクションの状態が表示されます。 **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON の場合、ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF は 6 秒間待ってから、操作を再試行します。  
  
データベースが OFFLINE の場合には、ALLOW_SNAPSHOT_ISOLATION の状態を変更できません。  
  
READ_ONLY のデータベースで ALLOW_SNAPSHOT_ISOLATION を設定すると、このデータベースが後に READ_WRITE に設定された場合でも、この設定が保持されます。  
  
master、model、msdb、および tempdb データベースでは、ALLOW_SNAPSHOT_ISOLATION 設定を変更できます。 tempdb でこの設定を変更すると、この設定は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが停止および再起動されるたびに保持されます。 model でこの設定を変更すると、この設定は、tempdb を除く新たに作成されたすべてのデータベースの既定値となります。  
  
master および msdb データベースでは、このオプションは既定で ON になります。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの snapshot_isolation_state 列を調べてください。  
  
READ_COMMITTED_SNAPSHOT { ON | OFF }  
ON  
データベース レベルでの Read Committed スナップショット オプションを有効にします。 有効にした場合、スナップショット分離を使用するトランザクションがなくても、DML ステートメントによって、行バージョンの生成が開始されます。 このオプションを有効にすると、READ COMMITTED 分離レベルを指定しているトランザクションは、ロックではなく、行のバージョン管理を使用します。 トランザクションが READ_COMMITTED 分離レベルで実行されている場合、すべてのステートメントは、ステートメントの開始時に存在していたデータのスナップショットを参照します。  
  
OFF  
データベース レベルでの Read Committed スナップショット オプションを無効にします。 READ COMMITTED 分離レベルを指定しているトランザクションは、ロックを使用します。  
  
READ_COMMITTED_SNAPSHOT を ON または OFF に設定するには、ALTER DATABASE コマンドを実行している接続以外にデータベースへのアクティブな接続が存在しないようにする必要があります。 データベースがシングル ユーザー モードになっている必要はありません。 データベースが OFFLINE の場合には、このオプションの状態は変更できません。  
  
READ_ONLY のデータベースで READ_COMMITTED_SNAPSHOT を設定すると、このデータベースが後で READ_WRITE に設定された場合でも、この設定が保持されます。  
  
master、tempdb、または msdb システム データベースでは、READ_COMMITTED_SNAPSHOT を ON に設定することはできません。 model でこの設定を変更すると、この設定は、tempdb を除く新たに作成されたすべてのデータベースの既定値となります。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_read_committed_snapshot_on 列を調べてください。  
  
> [!WARNING]  
>  **DURABILITY = SCHEMA_ONLY** でテーブルが作成される場合、**READ_COMMITTED_SNAPSHOT** がその後 **ALTER DATABASE** を使用して変更されると、テーブル内のデータは失われます。  
  
MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
ON  
トランザクション分離レベルが SNAPSHOT より低い分離レベル (たとえば、READ COMMITTED または READ UNCOMMITTEDREAD) に設定されている場合は、メモリ最適化テーブル上で解釈されたすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作が SNAPSHOT 分離レベルで実行されます。 この動作は、トランザクション分離レベルがセッション レベルで明示的に設定されているか、既定値が暗黙的に使用されるかに関係なく実行されます。  
  
OFF  
メモリ最適化テーブル上で解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作のトランザクション分離レベルは引き上げられません。  
  
データベースが OFFLINE の場合には、MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT の状態を変更できません。  
  
既定では、このオプションは OFF になっています。  
  
このオプションの現在の設定を確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの **is_memory_optimized_elevate_to_snapshot_on** 列を調べてください。  
  
**\<sql_option> ::=**  
  
ANSI 準拠のオプションをデータベース レベルで制御します。  
  
ANSI_NULL_DEFAULT { ON | OFF }  
CREATE TABLE ステートメントまたは ALTER TABLE ステートメントで NULL を許可するかどうかが明示的に定義されていない場合に、列または [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)の既定値を NULL と NOT NULL のどちらにするかを指定します。 制約によって定義された列は、この設定に関係なく制約のルールに従います。  
  
ON  
既定値は NULL になります。  
  
OFF  
既定値は NOT NULL になります。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_NULL_DEFAULT に関するデータベースレベルの既定の設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_NULL_DEFAULT を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)」をご覧ください。  
  
ANSI 互換性を確保するために、データベース オプション ANSI_NULL_DEFAULT を ON に設定すると、データベースの既定値が NULL に変更されます。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_null_default_on 列、または DATABASEPROPERTYEX 関数の IsAnsiNullDefault プロパティを調べてください。  
  
ANSI_NULLS { ON | OFF }  
ON  
NULL 値との比較結果は、すべて UNKNOWN になります。  
  
OFF  
UNICODE 以外の値と NULL 値の比較結果は、両方の値が NULL 値である場合には TRUE になります。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ANSI_NULLS が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_NULLS の既定のデータベース設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_NULLS を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)」をご覧ください。  
  
SET ANSI_NULLS は、計算列やインデックス付きビューのインデックスを作成または変更する場合にも、ON に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_nulls_on 列、または DATABASEPROPERTYEX 関数の IsAnsiNullsEnabled プロパティを調べてください。  
  
ANSI_PADDING { ON | OFF }  
ON  
文字列は、**varchar** または **nvarchar** データ型に変換または挿入される前に、埋め込まれて同じ長さになります。  
  
**varchar** 型または **nvarchar** 型の列に挿入された文字値の末尾の空白も、**varbinary** 型の列に挿入されたバイナリ値の末尾の 0 も、切り捨てられません。 列の長さに合わせるためにパディングされることはありません。  
  
OFF  
**varchar** 型または **nvarchar** 型に対する末尾の空白、および **varbinary** 型に対する末尾の 0 は、切り捨てられます。  
  
OFF を指定した場合、この設定は新しい列の定義にのみ影響します。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ANSI_PADDING が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 ANSI_PADDING は常に ON に設定することをお勧めします。 計算列やインデックス付きビューのインデックスを作成または操作するときには、ANSI_PADDING を ON に設定する必要があります。  
  
**char(*n*)** および **binary(*n*)** 列が NULL を許容する場合は、ANSI_PADDING を ON に設定すると、列の長さに合うようにパディングが行われますが、ANSI_PADDING を OFF に設定すると、末尾の空白および 0 は切り捨てられます。 **char(*n*)** および **binary(*n*)** 列が NULL を許容しない場合は、常に列の長さに合うようにパディングが行われます。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_PADDING に関するデータベースレベルの既定の設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、そのセッションの ANSI_PADDING を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_padding_on 列、または DATABASEPROPERTYEX 関数の IsAnsiPaddingEnabled プロパティを調べてください。  
  
ANSI_WARNINGS { ON | OFF }  
ON  
集計関数で、0 除算などの条件が発生したり、NULL 値が出現した場合に、エラーまたは警告が発行されます。  
  
OFF  
0 除算などの条件が発生しても、警告は発行されず、NULL 値が返されます。  
  
SET ANSI_WARNINGS は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_WARNINGS の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_WARNINGS を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_warnings_on 列、または DATABASEPROPERTYEX 関数の IsAnsiWarningsEnabled プロパティを調べてください。  
  
ARITHABORT { ON | OFF }  
ON  
クエリ実行中にオーバーフローまたは 0 除算エラーが発生したとき、クエリは終了します。  
  
OFF  
これらのエラーが発生すると、警告メッセージが表示されますが、クエリ、バッチ、トランザクションは、エラーが発生しなかったかのように処理を続行します。  
  
SET ARITHABORT は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_arithabort_on 列、または DATABASEPROPERTYEX 関数の IsArithmeticAbortEnabled プロパティを調べてください。  
  
COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }   
詳しくは、「[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」をご覧ください。  
  
CONCAT_NULL_YIELDS_NULL { ON | OFF }  
ON  
オペランドのいずれかが NULL の場合、連結操作の結果は NULL になります。 たとえば、文字列 "This is" と NULL を連結すると、結果は "This is" ではなく NULL になります。  
  
OFF  
NULL 値は、空の文字列として扱われます。  
  
CONCAT_NULL_YIELDS_NULL は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CONCAT_NULL_YIELDS_NULL が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
SET ステートメントを使用した接続レベルの設定は、CONCAT_NULL_YIELDS_NULL の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの CONCAT_NULL_YIELDS_NULL を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_concat_null_yields_null_on 列か、または DATABASEPROPERTYEX 関数の IsNullConcat プロパティを調べてください。  
  
QUOTED_IDENTIFIER { ON | OFF }  
ON  
二重引用符は区切られた識別子を囲むために使用できます。  
  
二重引用符で囲まれた文字列はすべて、オブジェクト識別子として解釈されます。 引用符で囲まれた識別子は、[!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子の規則に従う必要はありません。 引用符で囲まれた識別子はキーワードにすることができ、通常は [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子として使用できない文字を含めることもできます。 単一引用符 (') がリテラル文字列の一部になっている場合は、それを二重引用符 (") で表記できます。  
  
OFF  
識別子は、引用符で囲むことはできず、[!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子に関するすべての規則に従う必要があります。 リテラルは単一引用符と二重引用符のどちらで区切ることもできます。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では識別子を角かっこ ([ ]) で囲むこともできます。 角かっこで囲まれた識別子は、QUOTED_IDENTIFIER オプションの設定に関係なくいつでも使用できます。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
テーブルを作成するときに QUOTED IDENTIFIER オプションが OFF に設定されている場合でも、作成されるテーブルのメタデータでは、このオプションは常に ON として格納されます。  
  
SET ステートメントを使用した接続レベルの設定は、QUOTED_IDENTIFIER の既定のデータベース設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、QUOTED_IDENTIFIER を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_quoted_identifier_on 列、または DATABASEPROPERTYEX 関数の IsQuotedIdentifiersEnabled プロパティを調べてください。  
  
NUMERIC_ROUNDABORT { ON | OFF }  
ON  
式の精度が低下した場合にエラーが生成されます。  
  
OFF  
有効桁数が失われてもエラー メッセージが生成されず、結果を格納する列または変数の有効桁数に丸められます。  
  
NUMERIC_ROUNDABORT は、計算列やインデックス付きビューのインデックスを作成または変更する場合は、OFF に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_numeric_roundabort_on 列、または DATABASEPROPERTYEX 関数の IsNumericRoundAbortEnabled プロパティを調べてください。  
  
RECURSIVE_TRIGGERS { ON | OFF }  
ON  
AFTER トリガーの再帰呼び出しを可能にします。  
  
OFF  
AFTER トリガーの直接再帰呼び出しだけが実行できなくなります。 AFTER トリガーの間接再帰呼び出しも無効にするには、**sp_configure** を使用して、nested triggers サーバー オプションを **0** に設定します。  
  
> [!NOTE]  
>  RECURSIVE_TRIGGERS が OFF の場合は、直接再帰呼び出しのみが回避されます。 間接再帰呼び出しを無効にするには、nested triggers サーバー オプションを 0 に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_recursive_triggers_on 列、または DATABASEPROPERTYEX 関数の IsRecursiveTriggersEnabled プロパティを調べてください。  
  
**\<target_recovery_time_option> ::=**  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
間接的なチェックポイントの生成頻度をデータベースごとに指定します。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降、新しいデータベースに対する既定値は 1 分であり、これはデータベースが間接チェックポイントを使用することを示します。 旧バージョンの既定値は 0 です。これは、データベースが自動チェックポイントを使用することを示し、その頻度はサーバー インスタンスの復旧間隔の設定によって異なります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、ほとんどのシステムに対して 1 分をお勧めします。  
  
TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
*target_recovery_time*  
クラッシュが発生した場合、指定したデータベースが復旧に要する時間の上限を指定します。  
  
SECONDS  
*target_recovery_time* が秒単位で表されていることを示します。  
  
MINUTES  
*target_recovery_time* が分単位で表されていることを示します。  
  
間接的なチェックポイントについて詳しくは、「[データベース チェックポイント](../../relational-databases/logs/database-checkpoints-sql-server.md)」をご覧ください。  
  
**WITH \<termination> ::=**  
  
データベースの状態が変更されるときに、未完了のトランザクションをいつロールバックするかを指定します。 データベースがロックされている場合に終了句を省略すると、ALTER DATABASE ステートメントが無限に待機します。 指定できる終了句は 1 つだけで、SET 句の後に指定します。  
  
> [!NOTE]  
>  すべてのデータベース オプションで WITH \<termination> 句が使用できるわけではありません。 詳細については、このトピックの「解説」セクションの「[オプションの設定](#SettingOptions)」にある表をご覧ください。  
  
ROLLBACK AFTER "*整数*" [SECONDS] | ROLLBACK IMMEDIATE  
指定した秒数の後、または直ちにロールバックするかどうかを指定します。  
  
NO_WAIT  
要求されたデータベースの状態またはオプションの変更をすぐに完了できない場合、トランザクションが独自にコミットまたはロールバックするのを待機せずに、要求が失敗します。  
  
##  <a name="SettingOptions"></a> オプションの設定  
データベース オプションの現在の設定を取得するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューまたは [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) を使用します。  
  
データベース オプションを設定すると、変更は直ちに有効になります。  
  
新しく作成するデータベースのデータベース オプションの既定値を変更するには、model データベース内の適切なデータベース オプションを変更してください。  
  
データベース オプションの中には、WITH \<termination> 句を使用しないものや、他のオプションと組み合わせて指定できないものもあります。 次の表では、そのようなオプションについて説明します。  
  
|オプションのカテゴリ|他のオプションとの組み合わせの可否|WITH \<termination> 句の使用の可否|  
|----------------------|-----------------------------------------|---------------------------------------------|  
|\<db_state_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<db_user_access_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<db_update_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<delayed_durability_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<external_access_option>|[ユーザー アカウント制御]|いいえ|  
|\<cursor_option>|[ユーザー アカウント制御]|いいえ|  
|\<auto_option>|[ユーザー アカウント制御]|いいえ|  
|\<sql_option>|[ユーザー アカウント制御]|いいえ|  
|\<recovery_option>|[ユーザー アカウント制御]|いいえ|  
|\<target_recovery_time_option>|いいえ|[ユーザー アカウント制御]|  
|\<database_mirroring_option>|いいえ|いいえ|  
|ALLOW_SNAPSHOT_ISOLATION|いいえ|いいえ|  
|READ_COMMITTED_SNAPSHOT|いいえ|[ユーザー アカウント制御]|  
|MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<service_broker_option>|[ユーザー アカウント制御]|いいえ|  
|DATE_CORRELATION_OPTIMIZATION|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<parameterization_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<change_tracking_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<db_encryption_option>|[ユーザー アカウント制御]|いいえ|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのプラン キャッシュは、次のいずれかのオプションを設定することにより消去されます。  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY||  
  
プロシージャ キャッシュは、次のシナリオでもフラッシュされます。  
  
- AUTO_CLOSE データベース オプションが ON に設定されている。 データベースを参照 (または使用) するユーザー接続が 1 つも存在しない場合、バックグラウンド タスクがデータベースを自動的に閉じてシャットダウンすることを試みます。  
- 既定のオプションが設定されているデータベースに対して複数のクエリを実行した。 データベースはその後削除されます。  
- ソース データベースのデータベース スナップショットが削除された。  
- データベースのトランザクション ログを正常に再構築した。  
- データベースのバックアップを復元した。  
-   データベースをデタッチした。  
  
プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 プラン キャッシュ内のキャッシュストアが消去されるたびに、"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、一部のデータベース メンテナンス操作または再構成操作により、'%s' キャッシュストア (プラン キャッシュの一部) のキャッシュストア フラッシュを %d 個検出しました" という情報メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに含まれます。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-options-on-a-database"></a>A. データベースのオプションを設定する  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースに対して、復旧モデルおよびデータ ページ検証のオプションを設定します。  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL PAGE_VERIFY CHECKSUM;  
GO  
  
```  
  
### <a name="b-setting-the-database-to-readonly"></a>B. データベースを READ_ONLY に設定する  
データベースまたはファイル グループの状態を READ_ONLY または READ_WRITE に変更するには、データベースに対する排他的アクセスが必要です。 次の例では、排他的アクセスを取得するために、データベースを `SINGLE_USER` モードに設定します。 次に、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの状態を `READ_ONLY` に設定し、データベースへのアクセス権をすべてのユーザーに戻します。  
  
> [!NOTE]  
>  この例では、最初の `WITH ROLLBACK IMMEDIATE` ステートメントで、終了オプション `ALTER DATABASE` を使用しています。 すべての未完了のトランザクションはロールバックされ、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースへの他のすべての接続は直ちに接続解除されます。  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET SINGLE_USER  
WITH ROLLBACK IMMEDIATE;  
GO  
ALTER DATABASE AdventureWorks2012  
SET READ_ONLY  
GO  
ALTER DATABASE AdventureWorks2012  
SET MULTI_USER;  
GO  
  
```  
  
### <a name="c-enabling-snapshot-isolation-on-a-database"></a>C. データベースの SNAPSHOT 分離を有効にする  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに対する SNAPSHOT 分離フレームワーク オプションを有効にします。  
  
```sql  
USE AdventureWorks2012;  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET ALLOW_SNAPSHOT_ISOLATION ON;  
GO  
-- Check the state of the snapshot_isolation_framework  
-- in the database.  
SELECT name, snapshot_isolation_state,   
    snapshot_isolation_state_desc AS description  
FROM sys.databases  
WHERE name = N'AdventureWorks2012';  
GO  
  
```  
  
結果セットは、SNAPSHOT 分離フレームワークが有効であることを示しています。  
  
|NAME |snapshot_isolation_state |description|  
|-------------------- |------------------------  |----------|  
|AdventureWorks2012   |1                        | ON |  
  
### <a name="d-enabling-modifying-and-disabling-change-tracking"></a>D. 変更の追跡を有効化、変更、および無効化する  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更の追跡を有効にし、保有期間を `2` 日に設定します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);  
```  
  
次の例では、保有期間を `3` 日に変更する方法を示します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);  
```  
  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更の追跡を無効にする方法を示します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF;  
```  
  
### <a name="e-enabling-the-query-store"></a>E. クエリのストアを有効にします。  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
次の例では、クエリのストアを有効にして、ストアのクエリ パラメーターを構成します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET QUERY_STORE = ON   
    (  
      OPERATION_MODE = READ_WRITE   
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 )  
    , DATA_FLUSH_INTERVAL_SECONDS = 900   
    , MAX_STORAGE_SIZE_MB = 1024   
    , INTERVAL_LENGTH_MINUTES = 60   
    );  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
[ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
[ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
[統計](../../relational-databases/statistics/statistics.md)   
[CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
[変更の追跡の有効化と無効化](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)   
[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
[SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
[sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
[クエリ ストアを使用する際の推奨事項](../../relational-databases/performance/best-practice-with-the-query-store.md) 
  
# <a name="sql-db-logical-servertabsqldbls"></a>[SQL DB 論理サーバー](#tab/sqldbls)

互換性レベルは `SET` のオプションですが、「[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」で説明されています。  
  
> [!NOTE]  
> 多くのデータベース設定オプションは、[SET ステートメント](../../t-sql/statements/set-statements-transact-sql.md)を使用して現在のセッション用に構成できます。これらは多くの場合、接続するアプリケーションによって構成されます。 セッション レベルの SET オプションは、**ALTER DATABASE SET** の値をオーバーライドします。 次のデータベース オプションは、セッション用に設定できる値であり、他の SET オプションの値は明示的に指定されていません。  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE { database_name | Current }  
SET   
{  
    <option_spec> [ ,...n ] [ WITH <termination> ]   
}  
;  

<option_spec> ::=
{  
    <auto_option>
  | <automatic_tuning_option>
  | <change_tracking_option>
  | <cursor_option>
  | <db_encryption_option>
  | <db_update_option>
  | <db_user_access_option>
  | <delayed_durability_option>
  | <parameterization_option>
  | <query_store_options>
  | <snapshot_option>
  | <sql_option>
  | <target_recovery_time_option>
  | <termination>
  | <temporal_history_retention>
}  
;  
<auto_option> ::= 
{  
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] } 
  | AUTO_SHRINK { ON | OFF } 
  | AUTO_UPDATE_STATISTICS { ON | OFF } 
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}

<automatic_tuning_option> ::=  
{  AUTOMATIC_TUNING = { AUTO | INHERIT | CUSTOM } 
  | AUTOMATIC_TUNING ( CREATE_INDEX = { DEFAULT | ON | OFF } )
  | AUTOMATIC_TUNING ( DROP_INDEX = { DEFAULT | ON | OFF } )
  | AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = { DEFAULT | ON | OFF } )
}  

ALTER DATABASE current SET AUTOMATIC_TUNING = AUTO | INHERIT | CUSTOM
ALTER DATABASE current SET AUTOMATIC_TUNING (FORCE_LAST_GOOD_PLAN = ON, CREATE_INDEX = DEFAULT, DROP_INDEX = OFF)

<change_tracking_option> ::=  
{  
  CHANGE_TRACKING 
   { 
       = OFF  
     | = ON [ ( <change_tracking_option_list > [,...n] ) ] 
     | ( <change_tracking_option_list> [,...n] )  
   }  
}  

   <change_tracking_option_list> ::=  
   {  
       AUTO_CLEANUP = { ON | OFF } 
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }  
   }  

<cursor_option> ::= 
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF } 
}  
  
<db_encryption_option> ::=  
  ENCRYPTION { ON | OFF }  
  
<db_update_option> ::=  
  { READ_ONLY | READ_WRITE }  
  
<db_user_access_option> ::=  
  { RESTRICTED_USER | MULTI_USER }  
  
<delayed_durability_option> ::=  DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<parameterization_option> ::=  
  PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
  QUERY_STORE 
  {  
    = OFF 
    | = ON [ ( <query_store_option_list> [,... n] ) ]  
    | ( < query_store_option_list> [,... n] )  
    | CLEAR [ ALL ]  
  }  
} 
  
<query_store_option_list> ::=  
{  
  OPERATION_MODE = { READ_WRITE | READ_ONLY } 
  | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )  
  | DATA_FLUSH_INTERVAL_SECONDS = number 
  | MAX_STORAGE_SIZE_MB = number 
  | INTERVAL_LENGTH_MINUTES = number 
  | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
  | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
  | MAX_PLANS_PER_QUERY = number  
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }  
}  
<sql_option> ::= 
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  

<temporal_history_retention>  ::=  TEMPORAL_HISTORY_RETENTION { ON | OFF }
```  

## <a name="arguments"></a>引数  
*database_name*  
変更するデータベースの名前を指定します。  
  
CURRENT  
`CURRENT` を指定すると、現在のデータベースでアクションが実行されます。 `CURRENT` は、すべてのコンテキスト内のすべてのオプションでサポートされるわけではありません。 `CURRENT` でエラーが発生した場合は、データベース名を指定してください。 
  
**\<auto_option> ::=**
  
自動オプションを制御します。  
<a name="auto_create_statistics"></a> AUTO_CREATE_STATISTICS { ON | OFF }  
ON  
クエリ プランを改善してクエリのパフォーマンスを向上させるために、クエリ オプティマイザーが必要に応じてクエリ述語内の列に対して 1 列ずつ統計を作成します。 これらの統計は、クエリ オプティマイザーがクエリをコンパイルするときに作成されます。 1 列ずつの統計は、まだ既存の統計オブジェクトの最初の列になっていない列についてのみ作成されます。  
  
既定値は ON です。 ほとんどのデータベースで既定の設定を使用することをお勧めします。  
  
OFF  
クエリ オプティマイザーがクエリをコンパイルするときにクエリ述語内の列の 1 列ずつの統計が作成されません。 このオプションを OFF に設定すると、最適ではないクエリ プランが作成されて、クエリのパフォーマンスが低下することがあります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_create_stats_on 列、または DATABASEPROPERTYEX 関数の IsAutoCreateStatistics プロパティを調べてください。  
  
詳細については、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
INCREMENTAL = ON | OFF  
AUTO_CREATE_STATISTICS が ON の場合に INCREMENTAL を ON に設定すると、増分統計がサポートされているときは常に、自動的に作成される統計が増分統計となります。 既定値は OFF です。 詳しくは、「[CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)」をご覧ください。  
  
<a name="auto_shrink"></a> AUTO_SHRINK { ON | OFF }  
ON  
データベース ファイルを定期的な圧縮処理の対象とします。  
  
データ ファイルとログ ファイルの両方を、自動的に圧縮できます。 AUTO_SHRINK では、データベースが単純復旧モデルに設定されている場合や、ログがバックアップされている場合にのみ、トランザクション ログのサイズが圧縮されます。 OFF に設定すると、未使用領域の定期チェックの際に、データベース ファイルは自動的に圧縮されません。  
  
AUTO_SHRINK オプションを使用すると、ファイル領域の 25% を超える領域が未使用の場合にファイルが圧縮されます。 未使用領域がファイル領域の 25% になるサイズ、またはそのファイルが作成された時点でのサイズの、どちらか大きい方のサイズまで圧縮されます。  
  
読み取り専用データベースは圧縮できません。  
  
OFF  
データベース ファイルは、未使用領域の定期的なチェックの際に、自動的に圧縮されません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_shrink_on 列、または DATABASEPROPERTYEX 関数の IsAutoShrink プロパティを調べてください。  
  
> [!NOTE]  
> AUTO_SHRINK オプションは、包含データベースでは使用できません。  
  
<a name="auto_update_statistics"></a> AUTO_UPDATE_STATISTICS { ON | OFF }  
ON  
クエリで使用される統計が古くなっている可能性がある場合にクエリ オプティマイザーによって更新されるように指定します。 挿入、更新、削除、またはマージの各操作によってテーブルまたはインデックス付きビューのデータの分布が変わると、統計は古くなったと判断されます。 クエリ オプティマイザーでは、統計が前回更新されてから発生したデータ変更の数をカウントし、その変更の数をしきい値と比較することで、統計が古くなっている可能性がないかを判断します。 このしきい値は、テーブルまたはインデックス付きビューの行数に基づいて決められます。  
  
クエリ オプティマイザーによる古い統計の確認は、クエリをコンパイルする前と、キャッシュされたクエリ プランを実行する前に行われます。 クエリをコンパイルする前は、クエリ オプティマイザーで、クエリ述語内の列、テーブル、およびインデックス付きビューを使用して古くなっている可能性がある統計が判断されます。 キャッシュされたクエリ プランを実行する前は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で、クエリ プランが最新の統計を参照しているかどうかが確認されます。  
  
AUTO_UPDATE_STATISTICS オプションは、インデックスに対して作成された統計、クエリ述語内の列に対して 1 列ずつ作成された統計、および CREATE STATISTICS ステートメントを使用して作成された統計に適用されます。 また、フィルター選択された統計情報にも適用されます。  
  
既定値は ON です。 ほとんどのデータベースで既定の設定を使用することをお勧めします。  
  
統計を同期的に更新するか非同期的に更新するかを指定するには、AUTO_UPDATE_STATISTICS_ASYNC オプションを使用します。  
  
OFF  
クエリで使用される統計が古くなっている可能性がある場合にクエリ オプティマイザーによって更新されないように指定します。 このオプションを OFF に設定すると、最適ではないクエリ プランが作成されて、クエリのパフォーマンスが低下することがあります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_update_stats_on 列、または DATABASEPROPERTYEX 関数の IsAutoUpdateStatistics プロパティを調べてください。  
  
詳細については、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
<a name="auto_update_statistics_async"></a> AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
ON  
AUTO_UPDATE_STATISTICS オプションの統計の更新を非同期更新にするように指定します。 クエリ オプティマイザーは、統計の更新が完了するのを待たずにクエリをコンパイルします。  
  
AUTO_UPDATE_STATISTICS が ON に設定されていなければ、このオプションを ON に設定しても、効果はありません。  
  
既定では、AUTO_UPDATE_STATISTICS_ASYNC オプションは OFF に設定されており、クエリ オプティマイザーによる統計の更新は同期更新になります。  
  
OFF  
AUTO_UPDATE_STATISTICS オプションの統計の更新を同期更新にするように指定します。 クエリ オプティマイザーは、統計の更新が完了するのを待ってからクエリをコンパイルします。  
  
AUTO_UPDATE_STATISTICS が ON に設定されていなければ、このオプションを OFF に設定しても、効果はありません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_update_stats_async_on 列を調べてください。  
  
統計の同期更新と非同期更新をそれぞれどのような場合に使用するのかについては、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  

**\<automatic_tuning_option> ::=**  
**適用対象**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]  

データベースの[自動調整](../../relational-databases/automatic-tuning/automatic-tuning.md)が有効または無効になります。

AUTOMATIC_TUNING = { AUTO | INHERIT | CUSTOM } AUTO 自動調整の値を AUTO に設定すると、自動調整に Azure 構成の既定値が適用されます。
INHERIT 値 INHERIT を使用すると、親サーバーから既定の構成が継承されます。 親サーバー上の自動調整の構成をカスタマイズする必要があり、これらのカスタム設定を継承 (INHERIT) する、このようなサーバー上にデータベースがすべて存在する場合に特に便利です。 継承が機能するために、3 つの個別の調整オプションである FORCE_LAST_GOOD_PLAN、CREATE_INDEX、DROP_INDEX をデータベース上で DEFAULT に設定する必要があることに注意してください。
CUSTOM 値 CUSTOM を使用すると、データベース上で利用可能なそれぞれの自動調整オプションを手動でカスタムに構成する必要があります。

[自動調整](../../relational-databases/automatic-tuning/automatic-tuning.md)の自動インデックス管理 `CREATE_INDEX` オプションを有効または無効になります。

CREATE_INDEX = { DEFAULT | ON | OFF } 既定 サーバーから既定の設定が継承されます。 この場合、個別の自動調整を有効または無効にするオプションは、サーバー レベルで定義されます。
ON 有効にすると、不足しているインデックスがデータベース上で自動的に生成されます。 インデックスの作成に従って、ワークロードのパフォーマンスの向上が確認されます。 このような作成されたインデックスでこれ以上ワークロード パフォーマンスに利点が提供されなくなると、自動的に元に戻されます。 自動的に作成されたインデックスは、システムで生成されたインデックスとしてフラグが設定されます。
OFF データベース上で不足しているインデックスが自動的に生成されません。

[自動調整](../../relational-databases/automatic-tuning/automatic-tuning.md)の自動インデックス管理 `DROP_INDEX` オプションを有効または無効になります。

DROP_INDEX = { DEFAULT | ON | OFF } 既定 サーバーから既定の設定が継承されます。 この場合、個別の自動調整を有効または無効にするオプションは、サーバー レベルで定義されます。
ON パフォーマンス ワークロードに対する重複または不要になったインデックスが自動的にドロップされます。 OFF データベース上で不足しているインデックスが自動的にドロップされません。

[自動調整](../../relational-databases/automatic-tuning/automatic-tuning.md)の自動プラン修正 `FORCE_LAST_GOOD_PLAN` オプションを有効または無効になります。

FORCE_LAST_GOOD_PLAN = { DEFAULT | ON | OFF }  
既定 サーバーから既定の設定が継承されます。 この場合、個別の自動調整を有効または無効にするオプションは、サーバー レベルで定義されます。
ON  
新しい SQL プランがパフォーマンスの低下を引き起こしている [!INCLUDE[tsql_md](../../includes/tsql_md.md)] クエリに対して、[!INCLUDE[ssde_md](../../includes/ssde_md.md)] では最後の既知の正常なプランが自動的に強制されます。 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] は、強制プランを使用する [!INCLUDE[tsql_md](../../includes/tsql_md.md)] クエリのクエリ パフォーマンスを継続的に監視します。 パフォーマンスが向上した場合、[!INCLUDE[ssde_md](../../includes/ssde_md.md)] では最後の既知の正常なプランの使用が続けられます。 パフォーマンスの向上が検出されない場合、[!INCLUDE[ssde_md](../../includes/ssde_md.md)] は新しい SQL プランを生成します。 クエリ ストアが有効でない場合、または*読み取り/書き込み*モードでない場合は、ステートメントは失敗します。   
OFF  
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] は、[sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) ビューの SQL プランの変更によって引き起こされる、潜在的なクエリ パフォーマンスの低下をレポートします。 ただし、これらの推奨事項は自動的には適用されません。 ユーザーは、ビューに表示される [!INCLUDE[tsql_md](../../includes/tsql_md.md)] スクリプトを適用することによって、アクティブな推奨事項を監視し、特定された問題を解決することができます。 これが既定値です。

**\<change_tracking_option> ::=**  
  
変更の追跡のオプションを制御します。 変更の追跡の有効化、オプションの設定、オプションの変更、および変更の追跡の無効化が可能です。 例については、後の「例」のセクションをご覧ください。  
  
ON  
データベースの変更の追跡を有効にします。 変更の追跡を有効にすると、AUTO CLEANUP オプションと CHANGE RETENTION オプションも設定できます。  
  
AUTO_CLEANUP = { ON | OFF }  
ON  
指定した保有期間を過ぎると、変更追跡情報が自動的に削除されます。  
  
OFF  
変更追跡データがデータベースから削除されません。  
  
CHANGE_RETENTION =*retention_period* { DAYS | HOURS | MINUTES }  
データベースに変更追跡情報を保持する最低限の期間を指定します。 データは、AUTO_CLEANUP の値が ON のときにのみ削除されます。  
  
*retention_period* は、保有期間の数値部分を指定する整数です。  
  
既定の保有期間は 2 日です。 最小保有期間は 1 分です。 保有期間の既定の型は DAYS です。  
  
OFF  
データベースの変更の追跡を無効にします。 データベースの変更の追跡を無効にする前に、すべてのテーブルで変更の追跡を無効にする必要があります。  
  
**\<cursor_option> ::=**  
  
カーソル オプションを制御します。  
  
CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
ON  
トランザクションのコミットまたはロールバック時に開いていたすべてのカーソルが閉じます。  
  
OFF  
トランザクションがコミットされても、カーソルは開いたままになります。トランザクションをロールバックすると、INSENSITIVE または STATIC として定義されているカーソルを除き、すべてのカーソルが閉じます。  
  
SET ステートメントを使用した接続レベルの設定は、CURSOR_CLOSE_ON_COMMIT の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの CURSOR_CLOSE_ON_COMMIT を OFF に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_cursor_close_on_commit_on 列、または DATABASEPROPERTYEX 関数の IsCloseCursorsOnCommitEnabled プロパティを調べてください。 接続が切断されたときだけカーソルが暗黙的に割り当てを解除されます。 詳しくは、「[DECLARE CURSOR](../../t-sql/language-elements/declare-cursor-transact-sql.md)」をご覧ください。  
  
**\<db_encryption_option> ::=**  
  
データベース暗号化の状態を制御します。  
  
ENCRYPTION {ON | OFF}  
データベースを暗号化する (ON) か、暗号化しない (OFF) かを設定します。 データベース暗号化について詳しくは、「[透過的なデータ暗号化](../../relational-databases/security/encryption/transparent-data-encryption.md)」および「[Azure SQL Database での Transparent Data Encryption](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)」をご覧ください。  
  
データベース レベルで暗号化を有効にすると、すべてのファイル グループが暗号化されます。 すべての新しいファイル グループに、その暗号化プロパティが継承されます。 データベースに **READ ONLY** に設定されているファイル グループがあると、データベースの暗号化操作は失敗します。  
  
データベースの暗号化の状態を確認するには、[sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) 動的管理ビューを使用します。  
  
**\<db_update_option> ::=**  
  
データベースで更新を許可するかどうかを制御します。  
  
READ_ONLY  
ユーザーは、データベースのデータを読み取ることができますが、変更はできません。  
  
> [!NOTE]  
>  クエリのパフォーマンスを向上させるには、データベースを READ_ONLY に設定する前に統計を更新します。 データベースを READ_ONLY に設定した後に追加の統計が必要な場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] によって統計が tempdb に作成されます。 読み取り専用データベースの統計について詳しくは、「[統計](../../relational-databases/statistics/statistics.md)」をご覧ください。  
  
READ_WRITE  
データベースに対して読み取りおよび書き込み操作を行うことができます。  
  
この状態を変更するには、データベースに対する排他的アクセスが必要になります。 詳細については、SINGLE_USER 句をご覧ください。  
  
> [!NOTE]  
> [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のフェデレーション データベースでは、SET {READ_ONLY | READ_WRITE} は無効です。  
  
**\<db_user_access_option> ::=**  
  
データベースへのユーザー アクセスを制御します。  
  
RESTRICTED_USER  
RESTRICTED_USER モードでは、db_owner 固定データベース ロールと、dbcreator 固定サーバー ロールおよび sysadmin 固定サーバー ロールのメンバーのみが、データベースに接続できます。ただし、接続ユーザー数に制限はありません。 データベースに対するすべての接続は、ALTER DATABASE ステートメントの終了句で指定した時間枠内に接続解除されます。 データベースが RESTRICTED_USER 状態に移行すると、資格のないユーザーによる接続の試みは拒否されます。  **RESTRICTED_USER** は、SQL Database Managed Instance では変更できません。
  
MULTI_USER  
データベースに接続するための適切な権限を持つすべてのユーザーが許可されます。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの user_access 列、または DATABASEPROPERTYEX 関数の UserAccess プロパティを調べてください。  
  
**\<delayed_durability_option> ::=**  
  
トランザクションを完全持続性または遅延持続性のどちらとしてコミットするかどうかを制御します。  
  
DISABLED  
SET DISABLED 以後のトランザクションはすべて完全持続性です。 ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションは無視されます。  
  
ALLOWED  
SET ALLOWED 以後のトランザクションはすべて、ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションに応じて、完全持続性または遅延持続性です。  
  
FORCED  
SET FORCED 以後のトランザクションはすべて遅延持続性です。 ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションは無視されます。  
  
**\<PARAMETERIZATION_option> ::=**  
  
パラメーター化オプションを制御します。  
  
PARAMETERIZATION { SIMPLE | FORCED }  
SIMPLE  
クエリは、データベースの既定の動作に基づいてパラメーター化されます。  
  
FORCED  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、データベース内にあるすべてのクエリをパラメーター化します。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_parameterization_forced 列を調べてください。  
  
**\<query_store_options> ::=**  
  
ON |オフ |[すべて] をオフに  
コントロールは、このデータベースにクエリ ストアが有効になっている場合とそのコントロールが、クエリのストアの内容を削除します。  
  
ON  
クエリのストアを有効にします。  
  
OFF  
クエリのストアを無効にします。  これが既定値です。   
  
CLEAR  
クエリ ストアの内容を削除します。  
  
OPERATION_MODE  
クエリのストアの操作モードをについて説明します。 有効な値は、READ_ONLY、READ_WRITE はします。 READ_WRITE モードでは、クエリのストアは、収集し、クエリ プランとランタイム実行の統計情報が引き続き発生すます。 READ_ONLY モードでは、クエリのストアから情報を読み取ることができますが、新しい情報は追加されません。 クエリのストアを変更は、最大値が割り当てられているクエリのストアの領域が不足している場合は操作モードを READ_ONLY にします。  
  
CLEANUP_POLICY  
クエリのストアのデータ保有ポリシーをについて説明します。 STALE_QUERY_THRESHOLD_DAYS をクエリの情報は、クエリのストアに保存日数の数を決定します。 STALE_QUERY_THRESHOLD_DAYS は **bigint** 型です。  
  
DATA_FLUSH_INTERVAL_SECONDS  
クエリに書き込まれるデータ ストアが永続化する頻度を決定をディスクにします。 パフォーマンスを最適化するには、クエリのストアで収集したデータ非同期的にディスクに書き込まれます。 この非同期転送が発生する頻度を構成するには、DATA_FLUSH_INTERVAL_SECONDS 引数を使用します。 DATA_FLUSH_INTERVAL_SECONDS は **bigint** 型です。  
  
MAX_STORAGE_SIZE_MB  
クエリのストアに割り当てられた領域を判断します。 MAX_STORAGE_SIZE_MB は **bigint** 型です。  
  
INTERVAL_LENGTH_MINUTES  
クエリのストアにランタイムの実行の統計データを集計する時間間隔を決定します。 領域の使用状況を最適化するには、実行時の統計データ ストアでランタイム実行の統計は、一定の時間のウィンドウで集計されます。 この固定された時間帯を構成するには、INTERVAL_LENGTH_MINUTES 引数を使用します。 INTERVAL_LENGTH_MINUTES は **bigint** 型です。  
  
SIZE_BASED_CLEANUP_MODE  
かどうかのクリーンアップが自動的にアクティブになるデータの合計サイズを取得する最大サイズに近いかを制御します。  
  
OFF  
サイズ ベースのクリーンアップは自動的にアクティブ化されません。 
  
AUTO  
ディスクのサイズが **max_storage_size_mb** の 90% に達すると、サイズ ベースのクリーンアップが自動的にアクティブ化されます。 サイズのクリーンアップでは、まず最も安価で最も古いクエリを削除します。 **max_storage_size_mb** の約 80% で停止します。  これは、既定の構成値です。  
  
SIZE_BASED_CLEANUP_MODE は **nvarchar** 型です。  
  
QUERY_CAPTURE_MODE  
現在アクティブなクエリのキャプチャ モードを指定します。  
  
ALL すべてのクエリがキャプチャされます。 これは、既定の構成値です。
  
AUTO 実行の数とリソースの消費量に基づいて関連するクエリをキャプチャします。  これは、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] の既定の構成値です。
  
NONE 新しいクエリのキャプチャを停止します。 クエリ ストアは、既にキャプチャされたクエリのコンパイルと実行時の統計情報を収集し続けます。 重要なクエリをキャプチャするされない場合がありますので、注意してこの構成を使用します。  
  
QUERY_CAPTURE_MODE は **nvarchar** 型です。  
  
max_plans_per_query  
各クエリに対して保持の計画の最大数を表す整数。 既定値は 200 です。  
  
**\<snapshot_option> ::=**  
  
トランザクション分離レベルを決定します。  
  
ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
ON  
データベース レベルでのスナップショット オプションを有効にします。 有効にした場合、スナップショット分離を使用するトランザクションがなくても、DML ステートメントによって、行バージョンの生成が開始されます。 このオプションを有効にすると、トランザクションで SNAPSHOT トランザクション分離レベルを指定できます。 SNAPSHOT 分離レベルでトランザクションが実行されると、すべてのステートメントはトランザクション開始時のデータのスナップショットを参照します。 SNAPSHOT 分離レベルで実行されているトランザクションが複数のデータベースのデータにアクセスする場合は、すべてのデータベースで ALLOW_SNAPSHOT_ISOLATION が ON に設定されている必要があります。ALLOW_SNAPSHOT_ISOLATION が OFF になっているデータベース内のテーブルにアクセスする場合は、トランザクション内の各ステートメントで、FROM 句内のすべての参照に対してロック ヒントを使用する必要があります。  
  
OFF  
データベース レベルでのスナップショット オプションを無効にします。 トランザクションに、SNAPSHOT トランザクション分離レベルを指定できません。  
  
ALLOW_SNAPSHOT_ISOLATION を新しい状態に (ON から OFF へ、または OFF から ON へ) 設定した場合、ALTER DATABASE は、データベース内にあるすべての既存のトランザクションがコミットされるまで、呼び出し元に制御を返しません。 データベースが既に ALTER DATABASE ステートメントで指定した状態にある場合には、制御は呼び出し元に直ちに返されます。 ALTER DATABASE ステートメントがすぐに制御を返さない場合には、[sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) を使用して、長時間実行されているトランザクションがあるかどうかを確認できます。 ALTER DATABASE ステートメントが取り消された場合、データベースは、ALTER DATABASE が開始された時点での状態に留まります。 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューに、データベース内のスナップショット分離トランザクションの状態が表示されます。 **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON の場合、ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF は 6 秒間待ってから、操作を再試行します。  
  
データベースが OFFLINE の場合には、ALLOW_SNAPSHOT_ISOLATION の状態を変更できません。  
  
READ_ONLY のデータベースで ALLOW_SNAPSHOT_ISOLATION を設定すると、このデータベースが後に READ_WRITE に設定された場合でも、この設定が保持されます。  
  
master、model、msdb、および tempdb データベースでは、ALLOW_SNAPSHOT_ISOLATION 設定を変更できます。 tempdb でこの設定を変更すると、この設定は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが停止および再起動されるたびに保持されます。 model でこの設定を変更すると、この設定は、tempdb を除く新たに作成されたすべてのデータベースの既定値となります。  
  
master および msdb データベースでは、このオプションは既定で ON になります。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの snapshot_isolation_state 列を調べてください。  
  
READ_COMMITTED_SNAPSHOT { ON | OFF }  
ON  
データベース レベルでの Read Committed スナップショット オプションを有効にします。 有効にした場合、スナップショット分離を使用するトランザクションがなくても、DML ステートメントによって、行バージョンの生成が開始されます。 このオプションを有効にすると、READ COMMITTED 分離レベルを指定しているトランザクションは、ロックではなく、行のバージョン管理を使用します。 トランザクションが READ_COMMITTED 分離レベルで実行されている場合、すべてのステートメントは、ステートメントの開始時に存在していたデータのスナップショットを参照します。  
  
OFF  
データベース レベルでの Read Committed スナップショット オプションを無効にします。 READ COMMITTED 分離レベルを指定しているトランザクションは、ロックを使用します。  
  
READ_COMMITTED_SNAPSHOT を ON または OFF に設定するには、ALTER DATABASE コマンドを実行している接続以外にデータベースへのアクティブな接続が存在しないようにする必要があります。 データベースがシングル ユーザー モードになっている必要はありません。 データベースが OFFLINE の場合には、このオプションの状態は変更できません。  
  
READ_ONLY のデータベースで READ_COMMITTED_SNAPSHOT を設定すると、このデータベースが後で READ_WRITE に設定された場合でも、この設定が保持されます。  
  
master、tempdb、または msdb システム データベースでは、READ_COMMITTED_SNAPSHOT を ON に設定することはできません。 model でこの設定を変更すると、この設定は、tempdb を除く新たに作成されたすべてのデータベースの既定値となります。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_read_committed_snapshot_on 列を調べてください。  
  
> [!WARNING]  
>  **DURABILITY = SCHEMA_ONLY** でテーブルが作成される場合、**READ_COMMITTED_SNAPSHOT** がその後 **ALTER DATABASE** を使用して変更されると、テーブル内のデータは失われます。  
  
MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }  
  
ON  
トランザクション分離レベルが SNAPSHOT より低い分離レベル (たとえば、READ COMMITTED または READ UNCOMMITTEDREAD) に設定されている場合は、メモリ最適化テーブル上で解釈されたすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作が SNAPSHOT 分離レベルで実行されます。 この動作は、トランザクション分離レベルがセッション レベルで明示的に設定されているか、既定値が暗黙的に使用されるかに関係なく実行されます。  
  
OFF  
メモリ最適化テーブル上で解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作のトランザクション分離レベルは引き上げられません。  
  
データベースが OFFLINE の場合には、MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT の状態を変更できません。  
  
既定では、このオプションは OFF になっています。  
  
このオプションの現在の設定を確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの **is_memory_optimized_elevate_to_snapshot_on** 列を調べてください。  
  
**\<sql_option> ::=**  
  
ANSI 準拠のオプションをデータベース レベルで制御します。  
  
ANSI_NULL_DEFAULT { ON | OFF }  
CREATE TABLE ステートメントまたは ALTER TABLE ステートメントで NULL を許可するかどうかが明示的に定義されていない場合に、列または [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)の既定値を NULL と NOT NULL のどちらにするかを指定します。 制約によって定義された列は、この設定に関係なく制約のルールに従います。  
  
ON  
既定値は NULL になります。  
  
OFF  
既定値は NOT NULL になります。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_NULL_DEFAULT に関するデータベースレベルの既定の設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_NULL_DEFAULT を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)」をご覧ください。  
  
ANSI 互換性を確保するために、データベース オプション ANSI_NULL_DEFAULT を ON に設定すると、データベースの既定値が NULL に変更されます。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_null_default_on 列、または DATABASEPROPERTYEX 関数の IsAnsiNullDefault プロパティを調べてください。  
  
ANSI_NULLS { ON | OFF }  
ON  
NULL 値との比較結果は、すべて UNKNOWN になります。  
  
OFF  
UNICODE 以外の値と NULL 値の比較結果は、両方の値が NULL 値である場合には TRUE になります。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ANSI_NULLS が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_NULLS の既定のデータベース設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_NULLS を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)」をご覧ください。  
  
SET ANSI_NULLS は、計算列やインデックス付きビューのインデックスを作成または変更する場合にも、ON に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_nulls_on 列、または DATABASEPROPERTYEX 関数の IsAnsiNullsEnabled プロパティを調べてください。  
  
ANSI_PADDING { ON | OFF }  
ON  
文字列は、**varchar** または **nvarchar** データ型に変換または挿入される前に、埋め込まれて同じ長さになります。  
  
**varchar** 型または **nvarchar** 型の列に挿入された文字値の末尾の空白も、**varbinary** 型の列に挿入されたバイナリ値の末尾の 0 も、切り捨てられません。 列の長さに合わせるためにパディングされることはありません。  
  
OFF  
**varchar** 型または **nvarchar** 型に対する末尾の空白、および **varbinary** 型に対する末尾の 0 は、切り捨てられます。  
  
OFF を指定した場合、この設定は新しい列の定義にのみ影響します。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ANSI_PADDING が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 ANSI_PADDING は常に ON に設定することをお勧めします。 計算列やインデックス付きビューのインデックスを作成または操作するときには、ANSI_PADDING を ON に設定する必要があります。  
  
**char(*n*)** および **binary(*n*)** 列が NULL を許容する場合は、ANSI_PADDING を ON に設定すると、列の長さに合うようにパディングが行われますが、ANSI_PADDING を OFF に設定すると、末尾の空白および 0 は切り捨てられます。 **char(*n*)** および **binary(*n*)** 列が NULL を許容しない場合は、常に列の長さに合うようにパディングが行われます。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_PADDING に関するデータベースレベルの既定の設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、そのセッションの ANSI_PADDING を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_padding_on 列、または DATABASEPROPERTYEX 関数の IsAnsiPaddingEnabled プロパティを調べてください。  
  
ANSI_WARNINGS { ON | OFF }  
ON  
集計関数で、0 除算などの条件が発生したり、NULL 値が出現した場合に、エラーまたは警告が発行されます。  
  
OFF  
0 除算などの条件が発生しても、警告は発行されず、NULL 値が返されます。  
  
SET ANSI_WARNINGS は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_WARNINGS の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_WARNINGS を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_warnings_on 列、または DATABASEPROPERTYEX 関数の IsAnsiWarningsEnabled プロパティを調べてください。  
  
ARITHABORT { ON | OFF }  
ON  
クエリ実行中にオーバーフローまたは 0 除算エラーが発生したとき、クエリは終了します。  
  
OFF  
これらのエラーが発生すると、警告メッセージが表示されますが、クエリ、バッチ、トランザクションは、エラーが発生しなかったかのように処理を続行します。  
  
SET ARITHABORT は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_arithabort_on 列、または DATABASEPROPERTYEX 関数の IsArithmeticAbortEnabled プロパティを調べてください。  
  
COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
詳しくは、「[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」をご覧ください。  
  
CONCAT_NULL_YIELDS_NULL { ON | OFF }  
ON  
オペランドのいずれかが NULL の場合、連結操作の結果は NULL になります。 たとえば、文字列 "This is" と NULL を連結すると、結果は "This is" ではなく NULL になります。  
  
OFF  
NULL 値は、空の文字列として扱われます。  
  
CONCAT_NULL_YIELDS_NULL は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CONCAT_NULL_YIELDS_NULL が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
SET ステートメントを使用した接続レベルの設定は、CONCAT_NULL_YIELDS_NULL の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの CONCAT_NULL_YIELDS_NULL を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_concat_null_yields_null_on 列か、または DATABASEPROPERTYEX 関数の IsNullConcat プロパティを調べてください。  
  
QUOTED_IDENTIFIER { ON | OFF }  
ON  
二重引用符は区切られた識別子を囲むために使用できます。  
  
二重引用符で囲まれた文字列はすべて、オブジェクト識別子として解釈されます。 引用符で囲まれた識別子は、[!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子の規則に従う必要はありません。 引用符で囲まれた識別子はキーワードにすることができ、通常は [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子として使用できない文字を含めることもできます。 単一引用符 (') がリテラル文字列の一部になっている場合は、それを二重引用符 (") で表記できます。  
  
OFF  
識別子は、引用符で囲むことはできず、[!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子に関するすべての規則に従う必要があります。 リテラルは単一引用符と二重引用符のどちらで区切ることもできます。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では識別子を角かっこ ([ ]) で囲むこともできます。 角かっこで囲まれた識別子は、QUOTED_IDENTIFIER オプションの設定に関係なくいつでも使用できます。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
テーブルを作成するときに QUOTED IDENTIFIER オプションが OFF に設定されている場合でも、作成されるテーブルのメタデータでは、このオプションは常に ON として格納されます。  
  
SET ステートメントを使用した接続レベルの設定は、QUOTED_IDENTIFIER の既定のデータベース設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、QUOTED_IDENTIFIER を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_quoted_identifier_on 列、または DATABASEPROPERTYEX 関数の IsQuotedIdentifiersEnabled プロパティを調べてください。  
  
NUMERIC_ROUNDABORT { ON | OFF }  
ON  
式の精度が低下した場合にエラーが生成されます。  
  
OFF  
有効桁数が失われてもエラー メッセージが生成されず、結果を格納する列または変数の有効桁数に丸められます。  
  
NUMERIC_ROUNDABORT は、計算列やインデックス付きビューのインデックスを作成または変更する場合は、OFF に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_numeric_roundabort_on 列、または DATABASEPROPERTYEX 関数の IsNumericRoundAbortEnabled プロパティを調べてください。  
  
RECURSIVE_TRIGGERS { ON | OFF }  
ON  
AFTER トリガーの再帰呼び出しを可能にします。  
  
OFF  
AFTER トリガーの直接再帰呼び出しだけが実行できなくなります。 AFTER トリガーの間接再帰呼び出しも無効にするには、**sp_configure** を使用して、nested triggers サーバー オプションを **0** に設定します。  
  
> [!NOTE]  
>  RECURSIVE_TRIGGERS が OFF の場合は、直接再帰呼び出しのみが回避されます。 間接再帰呼び出しを無効にするには、nested triggers サーバー オプションを 0 に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_recursive_triggers_on 列、または DATABASEPROPERTYEX 関数の IsRecursiveTriggersEnabled プロパティを調べてください。  

**\<target_recovery_time_option> ::=**  
  
間接的なチェックポイントの生成頻度をデータベースごとに指定します。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降、新しいデータベースに対する既定値は 1 分であり、これはデータベースが間接チェックポイントを使用することを示します。 旧バージョンの既定値は 0 です。これは、データベースが自動チェックポイントを使用することを示し、その頻度はサーバー インスタンスの復旧間隔の設定によって異なります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、ほとんどのシステムに対して 1 分をお勧めします。  
  
TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
*target_recovery_time*  
クラッシュが発生した場合、指定したデータベースが復旧に要する時間の上限を指定します。  
  
SECONDS  
*target_recovery_time* が秒単位で表されていることを示します。  
  
MINUTES  
*target_recovery_time* が分単位で表されていることを示します。  
  
間接的なチェックポイントについて詳しくは、「[データベース チェックポイント](../../relational-databases/logs/database-checkpoints-sql-server.md)」をご覧ください。  
  
**WITH \<termination> ::=**  
  
データベースの状態が変更されるときに、未完了のトランザクションをいつロールバックするかを指定します。 データベースがロックされている場合に終了句を省略すると、ALTER DATABASE ステートメントが無限に待機します。 指定できる終了句は 1 つだけで、SET 句の後に指定します。  
  
> [!NOTE]  
>  すべてのデータベース オプションで WITH \<termination> 句が使用できるわけではありません。 詳細については、この記事の「解説」セクションの「[オプションの設定](#SettingOptions)」にある表をご覧ください。  
  
ROLLBACK AFTER "*整数*" [SECONDS] | ROLLBACK IMMEDIATE  
指定した秒数の後、または直ちにロールバックするかどうかを指定します。  
  
NO_WAIT  
要求されたデータベースの状態またはオプションの変更をすぐに完了できない場合、トランザクションが独自にコミットまたはロールバックするのを待機せずに、要求が失敗します。  
  
##  <a name="SettingOptions"></a> オプションの設定  
データベース オプションの現在の設定を取得するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューまたは [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) を使用します。  
  
データベース オプションを設定すると、変更は直ちに有効になります。  
  
新しく作成するデータベースのデータベース オプションの既定値を変更するには、model データベース内の適切なデータベース オプションを変更してください。  
  
データベース オプションの中には、WITH \<termination> 句を使用しないものや、他のオプションと組み合わせて指定できないものもあります。 次の表では、そのようなオプションについて説明します。  
  
|オプションのカテゴリ|他のオプションとの組み合わせの可否|WITH \<termination> 句の使用の可否|  
|----------------------|-----------------------------------------|---------------------------------------------|  
|\<auto_option>|[ユーザー アカウント制御]|いいえ|  
|\<change_tracking_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<cursor_option>|[ユーザー アカウント制御]|いいえ|  
|\<db_encryption_option>|[ユーザー アカウント制御]|いいえ|  
|\<db_update_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<db_user_access_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<delayed_durability_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<parameterization_option>|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|ALLOW_SNAPSHOT_ISOLATION|いいえ|いいえ|  
|READ_COMMITTED_SNAPSHOT|いいえ|[ユーザー アカウント制御]|  
|MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|DATE_CORRELATION_OPTIMIZATION|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
|\<sql_option>|[ユーザー アカウント制御]|いいえ|  
|\<target_recovery_time_option>|いいえ|[ユーザー アカウント制御]|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-the-database-to-readonly"></a>A. データベースを READ_ONLY に設定する  
データベースまたはファイル グループの状態を READ_ONLY または READ_WRITE に変更するには、データベースに対する排他的アクセスが必要です。 次の例では、アクセスを制限するために、データベースを `RESTRICTED_USER` モードに設定します。 次に、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの状態を `READ_ONLY` に設定し、データベースへのアクセス権をすべてのユーザーに戻します。  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET RESTRICTED_USER;  
GO  
ALTER DATABASE AdventureWorks2012  
SET READ_ONLY  
GO  
ALTER DATABASE AdventureWorks2012  
SET MULTI_USER;  
GO  
  
```  
  
### <a name="b-enabling-snapshot-isolation-on-a-database"></a>B. データベースの SNAPSHOT 分離を有効にする  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに対する SNAPSHOT 分離フレームワーク オプションを有効にします。  
  
```sql  
USE AdventureWorks2012;  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET ALLOW_SNAPSHOT_ISOLATION ON;  
GO  
-- Check the state of the snapshot_isolation_framework  
-- in the database.  
SELECT name, snapshot_isolation_state,   
    snapshot_isolation_state_desc AS description  
FROM sys.databases  
WHERE name = N'AdventureWorks2012';  
GO  
  
```  
  
結果セットは、SNAPSHOT 分離フレームワークが有効であることを示しています。  
  
|NAME |snapshot_isolation_state |description|  
|-------------------- |------------------------  |----------|  
|AdventureWorks2012   |1                        | ON |  
  
### <a name="c-enabling-modifying-and-disabling-change-tracking"></a>C. 変更の追跡を有効化、変更、および無効化する  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更の追跡を有効にし、保有期間を `2` 日に設定します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);  
```  
  
次の例では、保有期間を `3` 日に変更する方法を示します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);  
```  
  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更の追跡を無効にする方法を示します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF;  
```  
  
### <a name="d-enabling-the-query-store"></a>D. クエリのストアを有効にします。  
  
次の例では、クエリのストアを有効にして、ストアのクエリ パラメーターを構成します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET QUERY_STORE = ON   
    (  
      OPERATION_MODE = READ_WRITE   
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 )  
    , DATA_FLUSH_INTERVAL_SECONDS = 900   
    , MAX_STORAGE_SIZE_MB = 1024   
    , INTERVAL_LENGTH_MINUTES = 60   
    );  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
[ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
[統計](../../relational-databases/statistics/statistics.md)   
[CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldbls)   
[変更の追跡の有効化と無効化](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)   
[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
[SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
[sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
[クエリ ストアを使用する際の推奨事項](../../relational-databases/performance/best-practice-with-the-query-store.md) 
  
# <a name="sql-db-managed-instancetabsqldbmi"></a>[SQL DB Managed Instance](#tab/sqldbmi)

互換性レベルは `SET` のオプションですが、「[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」で説明されています。  
  
> [!NOTE]  
> 多くのデータベース設定オプションは、[SET ステートメント](../../t-sql/statements/set-statements-transact-sql.md)を使用して現在のセッション用に構成できます。これらは多くの場合、接続するアプリケーションによって構成されます。 セッション レベルの SET オプションは、**ALTER DATABASE SET** の値をオーバーライドします。 次のデータベース オプションは、セッション用に設定できる値であり、他の SET オプションの値は明示的に指定されていません。  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE { database_name | Current }  
SET   
{  
    <optionspec> [ ,...n ] 
}  
;  

<optionspec> ::=
{  
    <auto_option>   
  | <change_tracking_option>   
  | <cursor_option>   
  | <db_encryption_option>    
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option>   
  | <target_recovery_time_option>   
  | <termination>  
  | <temporal_history_retention>
}  
;  
<auto_option> ::= 
{  
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] } 
  | AUTO_SHRINK { ON | OFF } 
  | AUTO_UPDATE_STATISTICS { ON | OFF } 
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}  

<change_tracking_option> ::=  
{  
  CHANGE_TRACKING 
   { 
       = OFF  
     | = ON [ ( <change_tracking_option_list > [,...n] ) ] 
     | ( <change_tracking_option_list> [,...n] )  
   }  
}  

   <change_tracking_option_list> ::=  
   {  
       AUTO_CLEANUP = { ON | OFF } 
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }  
   }  

<cursor_option> ::= 
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF } 
}  
  
<db_encryption_option> ::=  
  ENCRYPTION { ON | OFF }  
  
<delayed_durability_option> ::=  DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<parameterization_option> ::=  
  PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
  QUERY_STORE 
  {  
    = OFF 
    | = ON [ ( <query_store_option_list> [,... n] ) ]  
    | ( < query_store_option_list> [,... n] )  
    | CLEAR [ ALL ]  
  }  
} 
  
<query_store_option_list> ::=  
{  
  OPERATION_MODE = { READ_WRITE | READ_ONLY } 
  | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )  
  | DATA_FLUSH_INTERVAL_SECONDS = number 
  | MAX_STORAGE_SIZE_MB = number 
  | INTERVAL_LENGTH_MINUTES = number 
  | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
  | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
  | MAX_PLANS_PER_QUERY = number  
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }  
}  
<sql_option> ::= 
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}

<temporal_history_retention>  ::=  TEMPORAL_HISTORY_RETENTION { ON | OFF }
```  

## <a name="arguments"></a>引数  
*database_name*  
変更するデータベースの名前を指定します。  
  
CURRENT  
`CURRENT` を指定すると、現在のデータベースでアクションが実行されます。 `CURRENT` は、すべてのコンテキスト内のすべてのオプションでサポートされるわけではありません。 `CURRENT` でエラーが発生した場合は、データベース名を指定してください。 
  
**\<auto_option> ::=**
  
自動オプションを制御します。  
<a name="auto_create_statistics"></a> AUTO_CREATE_STATISTICS { ON | OFF }  
ON  
クエリ プランを改善してクエリのパフォーマンスを向上させるために、クエリ オプティマイザーが必要に応じてクエリ述語内の列に対して 1 列ずつ統計を作成します。 これらの統計は、クエリ オプティマイザーがクエリをコンパイルするときに作成されます。 1 列ずつの統計は、まだ既存の統計オブジェクトの最初の列になっていない列についてのみ作成されます。  
  
既定値は ON です。 ほとんどのデータベースで既定の設定を使用することをお勧めします。  
  
OFF  
クエリ オプティマイザーがクエリをコンパイルするときにクエリ述語内の列の 1 列ずつの統計が作成されません。 このオプションを OFF に設定すると、最適ではないクエリ プランが作成されて、クエリのパフォーマンスが低下することがあります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_create_stats_on 列、または DATABASEPROPERTYEX 関数の IsAutoCreateStatistics プロパティを調べてください。  
  
詳細については、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
INCREMENTAL = ON | OFF  
AUTO_CREATE_STATISTICS が ON の場合に INCREMENTAL を ON に設定すると、増分統計がサポートされているときは常に、自動的に作成される統計が増分統計となります。 既定値は OFF です。 詳しくは、「[CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)」をご覧ください。  
  
<a name="auto_shrink"></a> AUTO_SHRINK { ON | OFF }  
ON  
データベース ファイルを定期的な圧縮処理の対象とします。  
  
データ ファイルとログ ファイルの両方を、自動的に圧縮できます。 AUTO_SHRINK では、データベースが単純復旧モデルに設定されている場合や、ログがバックアップされている場合にのみ、トランザクション ログのサイズが圧縮されます。 OFF に設定すると、未使用領域の定期チェックの際に、データベース ファイルは自動的に圧縮されません。  
  
AUTO_SHRINK オプションを使用すると、ファイル領域の 25% を超える領域が未使用の場合にファイルが圧縮されます。 未使用領域がファイル領域の 25% になるサイズ、またはそのファイルが作成された時点でのサイズの、どちらか大きい方のサイズまで圧縮されます。  
  
読み取り専用データベースは圧縮できません。  
  
OFF  
データベース ファイルは、未使用領域の定期的なチェックの際に、自動的に圧縮されません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_shrink_on 列、または DATABASEPROPERTYEX 関数の IsAutoShrink プロパティを調べてください。  
  
> [!NOTE]  
> AUTO_SHRINK オプションは、包含データベースでは使用できません。  
  
<a name="auto_update_statistics"></a> AUTO_UPDATE_STATISTICS { ON | OFF }  
ON  
クエリで使用される統計が古くなっている可能性がある場合にクエリ オプティマイザーによって更新されるように指定します。 挿入、更新、削除、またはマージの各操作によってテーブルまたはインデックス付きビューのデータの分布が変わると、統計は古くなったと判断されます。 クエリ オプティマイザーでは、統計が前回更新されてから発生したデータ変更の数をカウントし、その変更の数をしきい値と比較することで、統計が古くなっている可能性がないかを判断します。 このしきい値は、テーブルまたはインデックス付きビューの行数に基づいて決められます。  
  
クエリ オプティマイザーによる古い統計の確認は、クエリをコンパイルする前と、キャッシュされたクエリ プランを実行する前に行われます。 クエリをコンパイルする前は、クエリ オプティマイザーで、クエリ述語内の列、テーブル、およびインデックス付きビューを使用して古くなっている可能性がある統計が判断されます。 キャッシュされたクエリ プランを実行する前は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で、クエリ プランが最新の統計を参照しているかどうかが確認されます。  
  
AUTO_UPDATE_STATISTICS オプションは、インデックスに対して作成された統計、クエリ述語内の列に対して 1 列ずつ作成された統計、および CREATE STATISTICS ステートメントを使用して作成された統計に適用されます。 また、フィルター選択された統計情報にも適用されます。  
  
既定値は ON です。 ほとんどのデータベースで既定の設定を使用することをお勧めします。  
  
統計を同期的に更新するか非同期的に更新するかを指定するには、AUTO_UPDATE_STATISTICS_ASYNC オプションを使用します。  
  
OFF  
クエリで使用される統計が古くなっている可能性がある場合にクエリ オプティマイザーによって更新されないように指定します。 このオプションを OFF に設定すると、最適ではないクエリ プランが作成されて、クエリのパフォーマンスが低下することがあります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_update_stats_on 列、または DATABASEPROPERTYEX 関数の IsAutoUpdateStatistics プロパティを調べてください。  
  
詳細については、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
<a name="auto_update_statistics_async"></a> AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
ON  
AUTO_UPDATE_STATISTICS オプションの統計の更新を非同期更新にするように指定します。 クエリ オプティマイザーは、統計の更新が完了するのを待たずにクエリをコンパイルします。  
  
AUTO_UPDATE_STATISTICS が ON に設定されていなければ、このオプションを ON に設定しても、効果はありません。  
  
既定では、AUTO_UPDATE_STATISTICS_ASYNC オプションは OFF に設定されており、クエリ オプティマイザーによる統計の更新は同期更新になります。  
  
OFF  
AUTO_UPDATE_STATISTICS オプションの統計の更新を同期更新にするように指定します。 クエリ オプティマイザーは、統計の更新が完了するのを待ってからクエリをコンパイルします。  
  
AUTO_UPDATE_STATISTICS が ON に設定されていなければ、このオプションを OFF に設定しても、効果はありません。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_auto_update_stats_async_on 列を調べてください。  
  
統計の同期更新と非同期更新をそれぞれどのような場合に使用するのかについては、「[統計](../../relational-databases/statistics/statistics.md)」の「データベース全体の統計オプションの使用」セクションを参照してください。  
  
**\<change_tracking_option> ::=**  
  
変更の追跡のオプションを制御します。 変更の追跡の有効化、オプションの設定、オプションの変更、および変更の追跡の無効化が可能です。 例については、後の「例」のセクションをご覧ください。  
  
ON  
データベースの変更の追跡を有効にします。 変更の追跡を有効にすると、AUTO CLEANUP オプションと CHANGE RETENTION オプションも設定できます。  
  
AUTO_CLEANUP = { ON | OFF }  
ON  
指定した保有期間を過ぎると、変更追跡情報が自動的に削除されます。  
  
OFF  
変更追跡データがデータベースから削除されません。  
  
CHANGE_RETENTION =*retention_period* { DAYS | HOURS | MINUTES }  
データベースに変更追跡情報を保持する最低限の期間を指定します。 データは、AUTO_CLEANUP の値が ON のときにのみ削除されます。  
  
*retention_period* は、保有期間の数値部分を指定する整数です。  
  
既定の保有期間は 2 日です。 最小保有期間は 1 分です。 保有期間の既定の型は DAYS です。  
  
OFF  
データベースの変更の追跡を無効にします。 データベースの変更の追跡を無効にする前に、すべてのテーブルで変更の追跡を無効にする必要があります。  
  
**\<cursor_option> ::=**  
  
カーソル オプションを制御します。  
  
CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
ON  
トランザクションのコミットまたはロールバック時に開いていたすべてのカーソルが閉じます。  
  
OFF  
トランザクションがコミットされても、カーソルは開いたままになります。トランザクションをロールバックすると、INSENSITIVE または STATIC として定義されているカーソルを除き、すべてのカーソルが閉じます。  
  
SET ステートメントを使用した接続レベルの設定は、CURSOR_CLOSE_ON_COMMIT の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの CURSOR_CLOSE_ON_COMMIT を OFF に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_cursor_close_on_commit_on 列、または DATABASEPROPERTYEX 関数の IsCloseCursorsOnCommitEnabled プロパティを調べてください。 接続が切断されたときだけカーソルが暗黙的に割り当てを解除されます。 詳しくは、「[DECLARE CURSOR](../../t-sql/language-elements/declare-cursor-transact-sql.md)」をご覧ください。  
  
**\<db_encryption_option> ::=**  
  
データベース暗号化の状態を制御します。  
  
ENCRYPTION {ON | OFF}  
データベースを暗号化する (ON) か、暗号化しない (OFF) かを設定します。 データベース暗号化について詳しくは、「[透過的なデータ暗号化](../../relational-databases/security/encryption/transparent-data-encryption.md)」および「[Azure SQL Database での Transparent Data Encryption](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)」をご覧ください。  
  
データベース レベルで暗号化を有効にすると、すべてのファイル グループが暗号化されます。 すべての新しいファイル グループに、その暗号化プロパティが継承されます。 データベースに **READ ONLY** に設定されているファイル グループがあると、データベースの暗号化操作は失敗します。  
  
データベースの暗号化の状態を確認するには、[sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) 動的管理ビューを使用します。  
  
**\<db_update_option> ::=**  
  
データベースで更新を許可するかどうかを制御します。  
  
READ_ONLY  
ユーザーは、データベースのデータを読み取ることができますが、変更はできません。  
  
> [!NOTE]  
>  クエリのパフォーマンスを向上させるには、データベースを READ_ONLY に設定する前に統計を更新します。 データベースを READ_ONLY に設定した後に追加の統計が必要な場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] によって統計が tempdb に作成されます。 読み取り専用データベースの統計について詳しくは、「[統計](../../relational-databases/statistics/statistics.md)」をご覧ください。  
  
READ_WRITE  
データベースに対して読み取りおよび書き込み操作を行うことができます。  
  
この状態を変更するには、データベースに対する排他的アクセスが必要になります。   
  
**\<db_user_access_option> ::=**  
  
データベースへのユーザー アクセスを制御します。  
  
RESTRICTED_USER  
RESTRICTED_USER モードでは、db_owner 固定データベース ロールと、dbcreator 固定サーバー ロールおよび sysadmin 固定サーバー ロールのメンバーのみが、データベースに接続できます。ただし、接続ユーザー数に制限はありません。 データベースに対するすべての接続は、ALTER DATABASE ステートメントの終了句で指定した時間枠内に接続解除されます。 データベースが RESTRICTED_USER 状態に移行すると、資格のないユーザーによる接続の試みは拒否されます。  **RESTRICTED_USER** は、SQL Database Managed Instance では変更できません。
  
MULTI_USER  
データベースに接続するための適切な権限を持つすべてのユーザーが許可されます。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの user_access 列、または DATABASEPROPERTYEX 関数の UserAccess プロパティを調べてください。  
  
**\<delayed_durability_option> ::=**  
  
トランザクションを完全持続性または遅延持続性のどちらとしてコミットするかどうかを制御します。  
  
DISABLED  
SET DISABLED 以後のトランザクションはすべて完全持続性です。 ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションは無視されます。  
  
ALLOWED  
SET ALLOWED 以後のトランザクションはすべて、ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションに応じて、完全持続性または遅延持続性です。  
  
FORCED  
SET FORCED 以後のトランザクションはすべて遅延持続性です。 ATOMIC ブロックまたは COMMIT ステートメントで設定された持続性オプションは無視されます。  
  
**\<PARAMETERIZATION_option> ::=**  
  
パラメーター化オプションを制御します。  
  
PARAMETERIZATION { SIMPLE | FORCED }  
SIMPLE  
クエリは、データベースの既定の動作に基づいてパラメーター化されます。  
  
FORCED  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、データベース内にあるすべてのクエリをパラメーター化します。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_parameterization_forced 列を調べてください。  
  
**\<query_store_options> ::=**  
  
ON |オフ |[すべて] をオフに  
コントロールは、このデータベースにクエリ ストアが有効になっている場合とそのコントロールが、クエリのストアの内容を削除します。  
  
ON  
クエリのストアを有効にします。  
  
OFF  
クエリのストアを無効にします。  これが既定値です。   
  
CLEAR  
クエリ ストアの内容を削除します。  
  
OPERATION_MODE  
クエリのストアの操作モードをについて説明します。 有効な値は、READ_ONLY、READ_WRITE はします。 READ_WRITE モードでは、クエリのストアは、収集し、クエリ プランとランタイム実行の統計情報が引き続き発生すます。 READ_ONLY モードでは、クエリのストアから情報を読み取ることができますが、新しい情報は追加されません。 クエリのストアを変更は、最大値が割り当てられているクエリのストアの領域が不足している場合は操作モードを READ_ONLY にします。  
  
CLEANUP_POLICY  
クエリのストアのデータ保有ポリシーをについて説明します。 STALE_QUERY_THRESHOLD_DAYS をクエリの情報は、クエリのストアに保存日数の数を決定します。 STALE_QUERY_THRESHOLD_DAYS は **bigint** 型です。  
  
DATA_FLUSH_INTERVAL_SECONDS  
クエリに書き込まれるデータ ストアが永続化する頻度を決定をディスクにします。 パフォーマンスを最適化するには、クエリのストアで収集したデータ非同期的にディスクに書き込まれます。 この非同期転送が発生する頻度を構成するには、DATA_FLUSH_INTERVAL_SECONDS 引数を使用します。 DATA_FLUSH_INTERVAL_SECONDS は **bigint** 型です。  
  
MAX_STORAGE_SIZE_MB  
クエリのストアに割り当てられた領域を判断します。 MAX_STORAGE_SIZE_MB は **bigint** 型です。  
  
INTERVAL_LENGTH_MINUTES  
クエリのストアにランタイムの実行の統計データを集計する時間間隔を決定します。 領域の使用状況を最適化するには、実行時の統計データ ストアでランタイム実行の統計は、一定の時間のウィンドウで集計されます。 この固定された時間帯を構成するには、INTERVAL_LENGTH_MINUTES 引数を使用します。 INTERVAL_LENGTH_MINUTES は **bigint** 型です。  
  
SIZE_BASED_CLEANUP_MODE  
かどうかのクリーンアップが自動的にアクティブになるデータの合計サイズを取得する最大サイズに近いかを制御します。  
  
OFF  
サイズ ベースのクリーンアップは自動的にアクティブ化されません。 
  
AUTO  
ディスクのサイズが **max_storage_size_mb** の 90% に達すると、サイズ ベースのクリーンアップが自動的にアクティブ化されます。 サイズのクリーンアップでは、まず最も安価で最も古いクエリを削除します。 **max_storage_size_mb** の約 80% で停止します。  これは、既定の構成値です。  
  
SIZE_BASED_CLEANUP_MODE は **nvarchar** 型です。  
  
QUERY_CAPTURE_MODE  
現在アクティブなクエリのキャプチャ モードを指定します。  
  
ALL すべてのクエリがキャプチャされます。 これは、既定の構成値です。
  
AUTO 実行の数とリソースの消費量に基づいて関連するクエリをキャプチャします。  これは、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] の既定の構成値です。
  
NONE 新しいクエリのキャプチャを停止します。 クエリ ストアは、既にキャプチャされたクエリのコンパイルと実行時の統計情報を収集し続けます。 重要なクエリをキャプチャするされない場合がありますので、注意してこの構成を使用します。  
  
QUERY_CAPTURE_MODE は **nvarchar** 型です。  
  
max_plans_per_query  
各クエリに対して保持の計画の最大数を表す整数。 既定値は 200 です。  
  
**\<snapshot_option> ::=**  
  
トランザクション分離レベルを決定します。  
  
ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
ON  
データベース レベルでのスナップショット オプションを有効にします。 有効にした場合、スナップショット分離を使用するトランザクションがなくても、DML ステートメントによって、行バージョンの生成が開始されます。 このオプションを有効にすると、トランザクションで SNAPSHOT トランザクション分離レベルを指定できます。 SNAPSHOT 分離レベルでトランザクションが実行されると、すべてのステートメントはトランザクション開始時のデータのスナップショットを参照します。 SNAPSHOT 分離レベルで実行されているトランザクションが複数のデータベースのデータにアクセスする場合は、すべてのデータベースで ALLOW_SNAPSHOT_ISOLATION が ON に設定されている必要があります。ALLOW_SNAPSHOT_ISOLATION が OFF になっているデータベース内のテーブルにアクセスする場合は、トランザクション内の各ステートメントで、FROM 句内のすべての参照に対してロック ヒントを使用する必要があります。  
  
OFF  
データベース レベルでのスナップショット オプションを無効にします。 トランザクションに、SNAPSHOT トランザクション分離レベルを指定できません。  
  
ALLOW_SNAPSHOT_ISOLATION を新しい状態に (ON から OFF へ、または OFF から ON へ) 設定した場合、ALTER DATABASE は、データベース内にあるすべての既存のトランザクションがコミットされるまで、呼び出し元に制御を返しません。 データベースが既に ALTER DATABASE ステートメントで指定した状態にある場合には、制御は呼び出し元に直ちに返されます。 ALTER DATABASE ステートメントがすぐに制御を返さない場合には、[sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) を使用して、長時間実行されているトランザクションがあるかどうかを確認できます。 ALTER DATABASE ステートメントが取り消された場合、データベースは、ALTER DATABASE が開始された時点での状態に留まります。 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューに、データベース内のスナップショット分離トランザクションの状態が表示されます。 **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON の場合、ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF は 6 秒間待ってから、操作を再試行します。  
  
データベースが OFFLINE の場合には、ALLOW_SNAPSHOT_ISOLATION の状態を変更できません。  
  
READ_ONLY のデータベースで ALLOW_SNAPSHOT_ISOLATION を設定すると、このデータベースが後に READ_WRITE に設定された場合でも、この設定が保持されます。  
  
master、model、msdb、および tempdb データベースでは、ALLOW_SNAPSHOT_ISOLATION 設定を変更できます。 tempdb でこの設定を変更すると、この設定は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが停止および再起動されるたびに保持されます。 model でこの設定を変更すると、この設定は、tempdb を除く新たに作成されたすべてのデータベースの既定値となります。  
  
master および msdb データベースでは、このオプションは既定で ON になります。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの snapshot_isolation_state 列を調べてください。  
  
READ_COMMITTED_SNAPSHOT { ON | OFF }  
ON  
データベース レベルでの Read Committed スナップショット オプションを有効にします。 有効にした場合、スナップショット分離を使用するトランザクションがなくても、DML ステートメントによって、行バージョンの生成が開始されます。 このオプションを有効にすると、READ COMMITTED 分離レベルを指定しているトランザクションは、ロックではなく、行のバージョン管理を使用します。 トランザクションが READ_COMMITTED 分離レベルで実行されている場合、すべてのステートメントは、ステートメントの開始時に存在していたデータのスナップショットを参照します。  
  
OFF  
データベース レベルでの Read Committed スナップショット オプションを無効にします。 READ COMMITTED 分離レベルを指定しているトランザクションは、ロックを使用します。  
  
READ_COMMITTED_SNAPSHOT を ON または OFF に設定するには、ALTER DATABASE コマンドを実行している接続以外にデータベースへのアクティブな接続が存在しないようにする必要があります。 データベースがシングル ユーザー モードになっている必要はありません。 データベースが OFFLINE の場合には、このオプションの状態は変更できません。  
  
READ_ONLY のデータベースで READ_COMMITTED_SNAPSHOT を設定すると、このデータベースが後で READ_WRITE に設定された場合でも、この設定が保持されます。  
  
master、tempdb、または msdb システム データベースでは、READ_COMMITTED_SNAPSHOT を ON に設定することはできません。 model でこの設定を変更すると、この設定は、tempdb を除く新たに作成されたすべてのデータベースの既定値となります。  
  
このオプションの現在の設定を確認するには、sys.databases カタログ ビューの is_read_committed_snapshot_on 列を調べてください。  
  
> [!WARNING]  
>  **DURABILITY = SCHEMA_ONLY** でテーブルが作成される場合、**READ_COMMITTED_SNAPSHOT** がその後 **ALTER DATABASE** を使用して変更されると、テーブル内のデータは失われます。  
  
MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }  
  
ON  
トランザクション分離レベルが SNAPSHOT より低い分離レベル (たとえば、READ COMMITTED または READ UNCOMMITTEDREAD) に設定されている場合は、メモリ最適化テーブル上で解釈されたすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作が SNAPSHOT 分離レベルで実行されます。 この動作は、トランザクション分離レベルがセッション レベルで明示的に設定されているか、既定値が暗黙的に使用されるかに関係なく実行されます。  
  
OFF  
メモリ最適化テーブル上で解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作のトランザクション分離レベルは引き上げられません。  
  
データベースが OFFLINE の場合には、MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT の状態を変更できません。  
  
既定では、このオプションは OFF になっています。  
  
このオプションの現在の設定を確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの **is_memory_optimized_elevate_to_snapshot_on** 列を調べてください。  
  
**\<sql_option> ::=**  
  
ANSI 準拠のオプションをデータベース レベルで制御します。  
  
ANSI_NULL_DEFAULT { ON | OFF }  
CREATE TABLE ステートメントまたは ALTER TABLE ステートメントで NULL を許可するかどうかが明示的に定義されていない場合に、列または [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)の既定値を NULL と NOT NULL のどちらにするかを指定します。 制約によって定義された列は、この設定に関係なく制約のルールに従います。  
  
ON  
既定値は NULL になります。  
  
OFF  
既定値は NOT NULL になります。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_NULL_DEFAULT に関するデータベースレベルの既定の設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_NULL_DEFAULT を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)」をご覧ください。  
  
ANSI 互換性を確保するために、データベース オプション ANSI_NULL_DEFAULT を ON に設定すると、データベースの既定値が NULL に変更されます。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_null_default_on 列、または DATABASEPROPERTYEX 関数の IsAnsiNullDefault プロパティを調べてください。  
  
ANSI_NULLS { ON | OFF }  
ON  
NULL 値との比較結果は、すべて UNKNOWN になります。  
  
OFF  
UNICODE 以外の値と NULL 値の比較結果は、両方の値が NULL 値である場合には TRUE になります。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ANSI_NULLS が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_NULLS の既定のデータベース設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_NULLS を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)」をご覧ください。  
  
SET ANSI_NULLS は、計算列やインデックス付きビューのインデックスを作成または変更する場合にも、ON に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_nulls_on 列、または DATABASEPROPERTYEX 関数の IsAnsiNullsEnabled プロパティを調べてください。  
  
ANSI_PADDING { ON | OFF }  
ON  
文字列は、**varchar** または **nvarchar** データ型に変換または挿入される前に、埋め込まれて同じ長さになります。  
  
**varchar** 型または **nvarchar** 型の列に挿入された文字値の末尾の空白も、**varbinary** 型の列に挿入されたバイナリ値の末尾の 0 も、切り捨てられません。 列の長さに合わせるためにパディングされることはありません。  
  
OFF  
**varchar** 型または **nvarchar** 型に対する末尾の空白、および **varbinary** 型に対する末尾の 0 は、切り捨てられます。  
  
OFF を指定した場合、この設定は新しい列の定義にのみ影響します。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ANSI_PADDING が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 ANSI_PADDING は常に ON に設定することをお勧めします。 計算列やインデックス付きビューのインデックスを作成または操作するときには、ANSI_PADDING を ON に設定する必要があります。  
  
**char(*n*)** および **binary(*n*)** 列が NULL を許容する場合は、ANSI_PADDING を ON に設定すると、列の長さに合うようにパディングが行われますが、ANSI_PADDING を OFF に設定すると、末尾の空白および 0 は切り捨てられます。 **char(*n*)** および **binary(*n*)** 列が NULL を許容しない場合は、常に列の長さに合うようにパディングが行われます。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_PADDING に関するデータベースレベルの既定の設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、そのセッションの ANSI_PADDING を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_padding_on 列、または DATABASEPROPERTYEX 関数の IsAnsiPaddingEnabled プロパティを調べてください。  
  
ANSI_WARNINGS { ON | OFF }  
ON  
集計関数で、0 除算などの条件が発生したり、NULL 値が出現した場合に、エラーまたは警告が発行されます。  
  
OFF  
0 除算などの条件が発生しても、警告は発行されず、NULL 値が返されます。  
  
SET ANSI_WARNINGS は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
SET ステートメントを使用した接続レベルの設定は、ANSI_WARNINGS の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの ANSI_WARNINGS を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_ansi_warnings_on 列、または DATABASEPROPERTYEX 関数の IsAnsiWarningsEnabled プロパティを調べてください。  
  
ARITHABORT { ON | OFF }  
ON  
クエリ実行中にオーバーフローまたは 0 除算エラーが発生したとき、クエリは終了します。  
  
OFF  
これらのエラーが発生すると、警告メッセージが表示されますが、クエリ、バッチ、トランザクションは、エラーが発生しなかったかのように処理を続行します。  
  
SET ARITHABORT は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_arithabort_on 列、または DATABASEPROPERTYEX 関数の IsArithmeticAbortEnabled プロパティを調べてください。  
  
COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
詳しくは、「[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」をご覧ください。  
  
CONCAT_NULL_YIELDS_NULL { ON | OFF }  
ON  
オペランドのいずれかが NULL の場合、連結操作の結果は NULL になります。 たとえば、文字列 "This is" と NULL を連結すると、結果は "This is" ではなく NULL になります。  
  
OFF  
NULL 値は、空の文字列として扱われます。  
  
CONCAT_NULL_YIELDS_NULL は、計算列やインデックス付きビューのインデックスを作成または変更する場合には、ON に設定する必要があります。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CONCAT_NULL_YIELDS_NULL が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
SET ステートメントを使用した接続レベルの設定は、CONCAT_NULL_YIELDS_NULL の既定のデータベース設定をオーバーライドします。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、セッションの CONCAT_NULL_YIELDS_NULL を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_concat_null_yields_null_on 列か、または DATABASEPROPERTYEX 関数の IsNullConcat プロパティを調べてください。  
  
QUOTED_IDENTIFIER { ON | OFF }  
ON  
二重引用符は区切られた識別子を囲むために使用できます。  
  
二重引用符で囲まれた文字列はすべて、オブジェクト識別子として解釈されます。 引用符で囲まれた識別子は、[!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子の規則に従う必要はありません。 引用符で囲まれた識別子はキーワードにすることができ、通常は [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子として使用できない文字を含めることもできます。 単一引用符 (') がリテラル文字列の一部になっている場合は、それを二重引用符 (") で表記できます。  
  
OFF  
識別子は、引用符で囲むことはできず、[!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子に関するすべての規則に従う必要があります。 リテラルは単一引用符と二重引用符のどちらで区切ることもできます。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では識別子を角かっこ ([ ]) で囲むこともできます。 角かっこで囲まれた識別子は、QUOTED_IDENTIFIER オプションの設定に関係なくいつでも使用できます。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
テーブルを作成するときに QUOTED IDENTIFIER オプションが OFF に設定されている場合でも、作成されるテーブルのメタデータでは、このオプションは常に ON として格納されます。  
  
SET ステートメントを使用した接続レベルの設定は、QUOTED_IDENTIFIER の既定のデータベース設定よりもオーバーライドされます。 既定では、ODBC クライアントと OLE DB クライアントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、QUOTED_IDENTIFIER を ON に設定する接続レベルの SET ステートメントを実行します。 詳しくは、「[SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_quoted_identifier_on 列、または DATABASEPROPERTYEX 関数の IsQuotedIdentifiersEnabled プロパティを調べてください。  
  
NUMERIC_ROUNDABORT { ON | OFF }  
ON  
式の精度が低下した場合にエラーが生成されます。  
  
OFF  
有効桁数が失われてもエラー メッセージが生成されず、結果を格納する列または変数の有効桁数に丸められます。  
  
NUMERIC_ROUNDABORT は、計算列やインデックス付きビューのインデックスを作成または変更する場合は、OFF に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_numeric_roundabort_on 列、または DATABASEPROPERTYEX 関数の IsNumericRoundAbortEnabled プロパティを調べてください。  
  
RECURSIVE_TRIGGERS { ON | OFF }  
ON  
AFTER トリガーの再帰呼び出しを可能にします。  
  
OFF  
AFTER トリガーの直接再帰呼び出しだけが実行できなくなります。 AFTER トリガーの間接再帰呼び出しも無効にするには、**sp_configure** を使用して、nested triggers サーバー オプションを **0** に設定します。  
  
> [!NOTE]  
>  RECURSIVE_TRIGGERS が OFF の場合は、直接再帰呼び出しのみが回避されます。 間接再帰呼び出しを無効にするには、nested triggers サーバー オプションを 0 に設定する必要があります。  
  
このオプションの状態を確認するには、sys.databases カタログ ビューの is_recursive_triggers_on 列、または DATABASEPROPERTYEX 関数の IsRecursiveTriggersEnabled プロパティを調べてください。  

**\<target_recovery_time_option> ::=**  
  
間接的なチェックポイントの生成頻度をデータベースごとに指定します。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降、新しいデータベースに対する既定値は 1 分であり、これはデータベースが間接チェックポイントを使用することを示します。 旧バージョンの既定値は 0 です。これは、データベースが自動チェックポイントを使用することを示し、その頻度はサーバー インスタンスの復旧間隔の設定によって異なります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、ほとんどのシステムに対して 1 分をお勧めします。  
  
TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
*target_recovery_time*  
クラッシュが発生した場合、指定したデータベースが復旧に要する時間の上限を指定します。  
  
SECONDS  
*target_recovery_time* が秒単位で表されていることを示します。  
  
MINUTES  
*target_recovery_time* が分単位で表されていることを示します。  
  
間接的なチェックポイントについて詳しくは、「[データベース チェックポイント](../../relational-databases/logs/database-checkpoints-sql-server.md)」をご覧ください。  
  
ROLLBACK AFTER "*整数*" [SECONDS] | ROLLBACK IMMEDIATE  
指定した秒数の後、または直ちにロールバックするかどうかを指定します。  
  
NO_WAIT  
要求されたデータベースの状態またはオプションの変更をすぐに完了できない場合、トランザクションが独自にコミットまたはロールバックするのを待機せずに、要求が失敗します。  
  
##  <a name="SettingOptions"></a> オプションの設定  
データベース オプションの現在の設定を取得するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューまたは [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) を使用します。  
  
データベース オプションを設定すると、変更は直ちに有効になります。  
  
新しく作成するデータベースのデータベース オプションの既定値を変更するには、model データベース内の適切なデータベース オプションを変更してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-the-database-to-readonly"></a>A. データベースを READ_ONLY に設定する  
データベースまたはファイル グループの状態を READ_ONLY または READ_WRITE に変更するには、データベースに対する排他的アクセスが必要です。 次の例では、アクセスを制限するために、データベースを `RESTRICTED_USER` モードに設定します。 次に、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの状態を `READ_ONLY` に設定し、データベースへのアクセス権をすべてのユーザーに戻します。  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET RESTRICTED_USER;  
GO  
ALTER DATABASE AdventureWorks2012  
SET READ_ONLY  
GO  
ALTER DATABASE AdventureWorks2012  
SET MULTI_USER;  
GO  
  
```  
  
### <a name="b-enabling-snapshot-isolation-on-a-database"></a>B. データベースの SNAPSHOT 分離を有効にする  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに対する SNAPSHOT 分離フレームワーク オプションを有効にします。  
  
```sql  
USE AdventureWorks2012;  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET ALLOW_SNAPSHOT_ISOLATION ON;  
GO  
-- Check the state of the snapshot_isolation_framework  
-- in the database.  
SELECT name, snapshot_isolation_state,   
    snapshot_isolation_state_desc AS description  
FROM sys.databases  
WHERE name = N'AdventureWorks2012';  
GO  
  
```  
  
結果セットは、SNAPSHOT 分離フレームワークが有効であることを示しています。  
  
|NAME |snapshot_isolation_state |description|  
|-------------------- |------------------------  |----------|  
|AdventureWorks2012   |1                        | ON |  
  
### <a name="c-enabling-modifying-and-disabling-change-tracking"></a>C. 変更の追跡を有効化、変更、および無効化する  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更の追跡を有効にし、保有期間を `2` 日に設定します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);  
```  
  
次の例では、保有期間を `3` 日に変更する方法を示します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);  
```  
  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更の追跡を無効にする方法を示します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF;  
```  
  
### <a name="d-enabling-the-query-store"></a>D. クエリのストアを有効にします。  
  
次の例では、クエリのストアを有効にして、ストアのクエリ パラメーターを構成します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET QUERY_STORE = ON   
    (  
      OPERATION_MODE = READ_WRITE   
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 )  
    , DATA_FLUSH_INTERVAL_SECONDS = 900   
    , MAX_STORAGE_SIZE_MB = 1024   
    , INTERVAL_LENGTH_MINUTES = 60   
    );  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
[ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
[統計](../../relational-databases/statistics/statistics.md)   
[CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldbmi)   
[変更の追跡の有効化と無効化](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)   
[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
[SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
[sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
[クエリ ストアを使用する際の推奨事項](../../relational-databases/performance/best-practice-with-the-query-store.md) 
  
