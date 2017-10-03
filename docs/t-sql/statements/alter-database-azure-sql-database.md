---
title: "ALTER DATABASE (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 09/25/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e3c781449a8f7a1b236508cd21b8c00ff175774f
ms.openlocfilehash: f525c0ca01f49be05c1920897951059b126c83e9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/30/2017

---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  変更、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。 データベース、結合、柔軟なプール、およびデータベース オプションのセットのデータベースでは、エディションおよびサービス目標の名前を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name }  
{  
    MODIFY NAME = new_database_name  
  | MODIFY ( <edition_options> [, ... n] )   
  | SET { <option_spec> [ ,... n ] }   
  | ADD SECONDARY ON SERVER <partner_server_name>  
      [WITH ( <add-secondary-option>::= [, ... n] ) ]  
  | REMOVE SECONDARY ON SERVER <partner_server_name>  
  | FAILOVER  
  | FORCE_FAILOVER_ALLOW_DATA_LOSS  
}  
[;] 

<edition_options> ::=   
{  

      MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }    
    | EDITION = { 'basic' | 'standard' | 'premium' | 'premiumrs' }   
    | SERVICE_OBJECTIVE = 
                 {  <service-objective>
                 | { ELASTIC_POOL (name = <elastic_pool_name>) }   
                 }   
}  

<add-secondary-option> ::=  
   {  
      ALLOW_CONNECTIONS = { ALL | NO }  
     | SERVICE_OBJECTIVE =   
                 {  <service-objective> 
                 | { ELASTIC_POOL ( name = <elastic_pool_name>) }   
                 }   
   }  

<service-objective> ::=  { 'S0' | 'S1' | 'S2' | 'S3'| 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |
                 | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15' | 
                 | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' | }

```  
  
```
-- SET OPTIONS AVAILABLE FOR SQL Database  
-- Full descriptions of the set options are available in the topic   
-- ALTER DATABASE SET Options. The supported syntax is listed here.  

<optionspec> ::=   
{  
    <auto_option>   
  | <compatibility_level_option>  
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
  
<auto_option> ::=   
{  
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }   
  | AUTO_SHRINK { ON | OFF }   
  | AUTO_UPDATE_STATISTICS { ON | OFF }   
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}  
  
<compatibility_level_option>::=  
COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }  
  
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
  
<delayed_durability_option> ::=    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
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
  | COMPATIBILITY_LEVEL = { 90 | 100 | 110 | 120}  
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
  
 Set オプションの詳しい説明については、次を参照してください。 [ALTER DATABASE SET Options & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md)と[ALTER DATABASE 互換性レベル & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="arguments"></a>引数  
 *database_name*  
 変更するデータベースの名前を指定します。  
  
 CURRENT  
 使用中の現在のデータベースを変更することを指定します。  
  
 MODIFY NAME  **=**  *new_database_name*  
 として指定された名前のデータベースの名前を変更*new_database_name*です。 次の例は、データベースの名前を変更`db1`に`db2`:   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

 MODIFY (EDITION  **=**  ['basic' |'standard' |'premium' |premiumrs'])    
 データベースのサービス階層を変更します。 次の例の変更するにはエディション`premium`:
  
```  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

エディションの変更は、データベースの MAXSIZE プロパティがそのエディションでサポートされている有効な範囲外の値に設定されている場合に失敗します。  

 変更 (MAXSIZE  **=**  [100 MB | 500 MB | 1 | 1024.4096] GB)  
 データベースの最大サイズを指定します。 最大サイズは、データベースの EDITION プロパティの有効な値セットに準拠している必要があります。 データベースの最大サイズを変更すると、データベースの EDITION も変更される場合があります。 次の表のサポートされる MAXSIZE 値と既定値 (D) の一覧、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サービス層です。  
  
|**MAXSIZE**|**基本**|**S0 S2**|**S3 S12**|**P1 P6 と PRS1 PRS6**|**P11 P15**|  
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------|  
|100 MB|√|√|√|√|√|  
|250 MB|√|√|√|√|√|  
|500 MB|√|√|√|√|√|  
|1 GB|√|√|√|√|√|  
|2 GB|√ (D)|√|√|√|√|  
|5 GB|なし|√|√|√|√|  
|10 GB|なし|√|√|√|√|  
|20 GB|なし|√|√|√|√|  
|30 GB|なし|√|√|√|√|  
|40 GB|なし|√|√|√|√|  
|以上は 50 GB|なし|√|√|√|√|  
|100 GB|なし|√|√|√|√|  
|150 GB|なし|√|√|√|√|  
|200 GB|なし|√|√|√|√|  
|250 GB|なし|√ (D)|√ (D)|√|√|  
|300 GB|なし|√|√|√|√|  
|400 GB|なし|√|√|√|√|  
|500 GB|なし|√|√|√ (D)|√|  
|750 GB|なし|√|√|√|√|  
|1024 GB|なし|√|√|√|√ (D)|  
|1024 GB から最大 4096 GB 単位での 256 GB *|なし|なし|なし|なし|√|√|  
  
 \*P11 と P15 MAXSIZE を許可する最大 4 TB 1024 GB が既定のサイズをされているとします。  P11 および P15 は、追加料金なしで最大 4 TB の含まれる記憶域を使用できます。 Premium 階層で MAXSIZE が 1 TB を超えるは次の地域で現在使用可能な: 米国 East2、米国西部、米国 Gov バージニア、西ヨーロッパ、ドイツの中央、南東アジア、東日本、オーストラリア東部、カナダ中央、およびカナダ東部です。 現在の制限については、次を参照してください。[データベースをシングル](https://docs.microsoft.com/azure/sql-database-single-database-resources)です。  

  
 引数 MAXSIZE および EDITION には、以下の規則が適用されます。  
  
-   MAXSIZE 値指定すると場合、は、前の表に示すように有効な値であることができます。  
  
-   EDITION が指定され、MAXSIZE が指定されていない場合は、エディションの既定値が使用されます。 たとえばは、EDITION が Standard に設定し、MAXSIZE が指定されていない場合、MAXSIZE は自動的に 500 MB に設定します。  
  
-   MAXSIZE も EDITION が指定されている場合、EDITION は、標準 (S0) に設定し、MAXSIZE は 250 GB に設定します。  
 

 変更 (SERVICE_OBJECTIVE =\<サービス目標 >)  
 パフォーマンス レベルを指定します。 次の例の変更はサービスに premium データベースの目標`P6`:
 
```  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  
 サービス目標の使用可能な値: `S0`、 `S1`、 `S2`、 `S3`、 `S4`、 `S6`、 `S7`、 `S9`、 `S12`、 `P1`、 `P2`、`P4`、 `P6`、 `P11`、 `P15`、 `PRS1`、 `PRS2`、 `PRS4`、および`PRS6`です。 サービス目標に関する説明と、サイズ、エディション、およびサービス目標の組み合わせの詳細については、次を参照してください。 [Azure SQL データベース サービス階層とパフォーマンス レベル](http://msdn.microsoft.com/library/azure/dn741336.aspx)です。 指定した SERVICE_OBJECTIVE が EDITION によってサポートされていません、エラーが表示されます。 SERVICE_OBJECTIVE の値を 1 つの階層から別の階層に変更する場合 (たとえば、S1 から P1) は、EDITION の値も変更する必要があります。  
  
 変更 (SERVICE_OBJECTIVE 柔軟なを =\_プール (名前 = \<elastic_pool_name >)  
 柔軟なプールには、既存のデータベースを追加するには、ELASTIC_POOL にデータベースの SERVICE_OBJECTIVE を設定し、柔軟なプールの名前を指定します。 同じサーバー内の別の柔軟なプールにデータベースを変更するのに、このオプションを使用することもできます。 詳細については、次を参照してください。[作成し、SQL Database の弾力性プールの管理](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)です。 柔軟なプールからデータベースを削除するには、ALTER DATABASE を使用して、SERVICE_OBJECTIVE を 1 つのデータベースのパフォーマンス レベルに設定します。  

 セカンダリにサーバーの追加\<partner_server_name >  
 主キー、地理的レプリケーションにローカルのデータベースを作成して、パートナー サーバーで同じ名前での地理的レプリケーションのセカンダリ データベースを作成し、非同期的に新しいセカンダリへのプライマリからのデータのレプリケーションを開始します。 セカンダリ上と同じ名前のデータベースが既に存在する場合、コマンドは失敗します。 コマンドは、プライマリとなるローカル データベースをホストしているサーバー上の master データベースで実行されます。  
  
 ALLOW_CONNECTIONS で {すべて |**いいえ**}  
 ALLOW_CONNECTIONS が指定されていない場合は、既定では NO に設定されます。 設定されている場合すべては、読み取り専用データベースを接続する適切なアクセス許可を持つすべてのログインを許可します。  
  
 SERVICE_OBJECTIVE の {'S0' |'S1' |'S2' |' S3"|'S4' |'S6' |'S7' |'S9' |'S12' |'P1' |'P2' |'P4' |'P6' |'P11' |'P15' |'PRS1' |'PRS2' |'PRS4' |PRS6'}  
 SERVICE_OBJECTIVE が指定されていない場合、セカンダリ データベースがプライマリ データベースと同じサービス レベルで作成されます。 SERVICE_OBJECTIVE が指定されている場合は、指定されたレベルで、セカンダリ データベースが作成されます。 このオプションは、低価格のサービス レベルで地理的レプリケーションのセカンダリの作成をサポートします。 指定した SERVICE_OBJECTIVE がソースと同じエディション内になければなりません。 たとえば場合は、edition が premium S0 を指定することはできません。  
  
 ELASTIC_POOL (名前 = \<elastic_pool_name)  
 ELASTIC_POOL が指定されていない場合、セカンダリ データベースは弾力性プールには作成されません。 ELASTIC_POOL が指定されている場合は、指定されたプールで、セカンダリ データベースが作成されます。  
  
> [!IMPORTANT]  
>  セカンダリを追加のコマンドを実行するユーザーは、DBManager をプライマリ サーバー上にある、セカンダリ サーバー上でローカルのデータベースでは、および DBManager db_owner のメンバーシップがある必要があります。  
  
 セカンダリにサーバーの削除\<partner_server_name >  
 指定した地理的レプリケーションのセカンダリ データベースに、指定したサーバーを削除します。 コマンドは、プライマリ データベースをホストしているサーバーの master データベースで実行されます。  
  
> [!IMPORTANT]  
>  セカンダリの削除のコマンドを実行するユーザーは、プライマリ サーバーの DBManager をする必要があります。  
  
 FAILOVER  
 セカンダリ データベースをコマンドをプライマリが実行され、降格されますが、現在のプライマリになる新しいセカンダリ geo レプリケーションの連携を昇格させます。 このプロセスの一環として、地理的レプリケーションのモードが一時的に非同期モードからに切り替える同期モードです。 フェールオーバー中。  
  
1.  プライマリでは、新しいトランザクションの処理を停止します。  
  
2.  すべての未処理のトランザクションは、セカンダリにフラッシュされます。  
  
3.  セカンダリがプライマリになり、古いプライマリで非同期の地理的レプリケーションを開始すると、新しいセカンダリです。  
  
 このシーケンスにより、データ損失は発生しません。 両方のデータベースは使用できません期間は、役割の交代中に、0 ～ 25 の数秒です。 合計の操作は、約 1 分以内で実行する必要があります。 このコマンドが実行されたときに、プライマリ データベースが使用できない場合、コマンドは、プライマリ データベースが使用できないことを示すエラー メッセージで失敗します。 場合は、フェールオーバー プロセスが完了しない、スタックが表示されます、強制フェールオーバー コマンドを使用してデータが失われるをそのまま使用し、次に、データの損失を回復する必要がある場合は、呼び出す devops 失われたデータを回復するには、(CSS) およびできます。  
  
> [!IMPORTANT]  
>  フェールオーバー コマンドを実行するユーザーは、プライマリ サーバーとセカンダリ サーバーの両方で DBManager をする必要があります。  
  
 FORCE_FAILOVER_ALLOW_DATA_LOSS  
 セカンダリ データベースをコマンドをプライマリが実行され、降格されますが、現在のプライマリになる新しいセカンダリ geo レプリケーションの連携を昇格させます。 現在のプライマリが使用可能な不要になった場合にのみ、このコマンドを使用します。 設計されていますディザスター リカバリーのみの可用性を復元することが重要といくつかのデータの損失を許容します。  
  
 : 強制フェールオーバー中に  
  
1.  指定したセカンダリ データベースはすぐに、プライマリ データベースになり、新しいトランザクションの受け入れを開始します。  
  
2.  元のプライマリは、新しいプライマリに再接続できますと、増分バックアップが元のプライマリ、新しいセカンダリが元のプライマリになります。  
  
3.  この増分バックアップでは、古いプライマリからのデータを回復するには、ユーザーには、devops/CSS が関与します。 します。  
  
4.  その他のセカンダリがある場合は、新しいプライマリのセカンダリに自動的に再構成します。 このプロセスは非同期で、このプロセスが完了するまで、遅延が発生にすることがあります。 再構成が完了するまで、セカンダリは、古いプライマリのセカンダリに進みます。  
  
> [!IMPORTANT]  
>  Force_failover_allow_data_loss の各コマンドを実行するユーザーは、プライマリ サーバーとセカンダリ サーバーの両方で DBManager をする必要があります。  
  
## <a name="remarks"></a>解説  
 データベースを削除するには使用[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)です。  
  
 データベースのサイズを小さくを使用して[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)です。  
  
 ALTER DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。  
  
 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 各キャッシュ ストアが消去、プラン キャッシュ内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログには、次の情報メッセージが含まれています:"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュ ストア フラッシュをいくつかのデータベースのため '%s' キャッシュ ストア (プラン キャッシュの一部) を %d 個検出が発生しましたメンテナンス操作または再構成操作"です。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
 次のシナリオでは、プロシージャ キャッシュがフラッシュも。  
  
-   AUTO_CLOSE データベース オプションが ON に設定されている。 データベースを参照 (または使用) するユーザー接続が 1 つも存在しない場合、バックグラウンド タスクがデータベースを自動的に閉じてシャットダウンすることを試みます。  
  
-   既定のオプションが設定されているデータベースに対して複数のクエリを実行した。 データベースはその後削除されます。  
  
-   データベースのトランザクション ログを正常に再構築した。  
  
-   データベースのバックアップを復元した。  
  
-   データベースをデタッチした。  
  
## <a name="viewing-database-information"></a>データベース情報の表示  
 カタログ ビュー、システム関数、およびシステム ストアド プロシージャを使用して、データベース、ファイルおよびファイル グループについての情報を返すことができます。  
  
## <a name="permissions"></a>Permissions  
 データベースを変更できるのは、(準備プロセスによって作成される) サーバーレベルのプリンシパルのログイン、または `dbmanager` データベース ロールのメンバーだけです。  
  
> [!IMPORTANT]  
>  データベースの所有者であっても `dbmanager` ロールのメンバーでない場合は、データベースを変更できません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Edition オプションを確認し、それらを変更します。

```
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>B. データベースを別の柔軟なプールに移動します。  
 Pool1 をという名前のプールに、既存のデータベースを移動します。  
  
```  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>C. 地理的レプリケーション セカンダリを追加します。  
 サーバー上の読み取り不可のセカンダリ データベース db1 の作成`secondaryserver`db1 ローカル サーバー上のです。  
  
```  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = NO )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>D. セカンダリ Geo レプリケーションを削除します。  
 サーバー上のセカンダリ データベース db1 の削除`secondaryserver`です。  
  
```  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>E. 地理的レプリケーションのセカンダリにフェールオーバー  
 サーバー上のセカンダリ データベース db1 の昇格`secondaryserver`に新しいプライマリ データベース サーバーで実行されるときになる`secondaryserver`です。  
  
```  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>参照  
 [DATABASE &#40; を作成します。Azure SQL データベース &#41;](../../t-sql/statements/create-database-azure-sql-database.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.database_mirroring_witnesses & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.data_spaces と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [システム データベース](../../relational-databases/databases/system-databases.md)  
  
  

