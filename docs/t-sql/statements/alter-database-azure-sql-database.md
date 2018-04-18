---
title: ALTER DATABASE (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 02/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ddec688efe7ce468b7af1c05389b9cc1e86cf4c4
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] を変更します。 データベース、結合、柔軟なプール、およびデータベース オプションのセットのデータベースでは、エディションおよびサービス目標の名前を変更します。  
  
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
  | EDITION = { 'basic' | 'standard' | 'premium' | 'GeneralPurpose' | 'BusinessCritical'} 
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
       | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' 
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 
      }

```  
  
```
-- SET OPTIONS AVAILABLE FOR SQL Database  
-- Full descriptions of the set options are available in the topic 
-- ALTER DATABASE SET Options. The supported syntax is listed here.  

<option_spec> ::= 
{  
    <auto_option> 
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
  | COMPATIBILITY_LEVEL = { 100 | 110 | 120 | 130 | 140 }  
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
  
 設定オプションについて詳しくは、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」および「[ALTER DATABASE (TRANSACT-SQL) の互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」をご覧ください。  
  
## <a name="arguments"></a>引数  

*database_name*  

変更するデータベースの名前を指定します。  
  
CURRENT  

使用中の現在のデータベースを変更することを指定します。  
  
MODIFY NAME **=***new_database_name*  

データベースの名前を、*new_database_name* で指定した名前に変更します。 次の例では、`db1` データベースの名前を `db2` に変更します。   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

MODIFY (EDITION **=** ['basic' | 'standard' | 'premium' |'GeneralPurpose' | 'BusinessCritical'])    

データベースのサービス階層を変更します。 'premiumrs' のサポートは削除されました。 質問については、電子メール エイリアス premium-rs@microsoft.com を使用してください。

次の例では、エディションを `premium` に変更します。
  
```  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

データベースの MAXSIZE プロパティがそのエディションでサポートされる有効な範囲内の値に設定されていない場合、EDITION の変更は失敗します。  

MODIFY (MAXSIZE **=** [100 MB | 500 MB | 1 | 1024…4096] GB)  

データベースの最大サイズを指定します。 最大サイズは、データベースの EDITION プロパティの有効な値セットに準拠している必要があります。 データベースの最大サイズを変更すると、データベースの EDITION も変更される場合があります。 次の表では、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サービス層でサポートされる MAXSIZE 値と既定値 (D) を示します。  
  
**DTU に基づくモデル**

|**MAXSIZE**|**基本**|**S0-S2**|**S3-S12**|**P1-P6**|**P11-P15**|  
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
|1024 GB から 4096 GB (256 GB ずつ増分)*|なし|なし|なし|なし|√|√|  
  
\* P11 と P15 では 1024 GB を既定のサイズとして MAXSIZE が 4 TB まで許可されます。  P11 と P15 では、追加料金なしで付属のストレージを 4 TB まで使用できます。 次の地域の Premium レベルでは、現在 1 TB を超える MAXSIZE を使用できます: 米国東部 2、米国西部、米国政府バージニア、西ヨーロッパ、ドイツ中部、東南アジア、東日本、オーストラリア東部、カナダ中部、カナダ東部。 DTU に基づくモデルのリソースの制限事項に関する詳細については、「[DTU-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits)」(DTU に基づくリソースの制限) を参照してください。  

DTU に基づくモデルの MAXSIZE 値。指定すると、上記の表に示すように指定されたサービス層で有効な値である必要があります。
 
**vCore に基づくモデル**

**一般的な目的のサービス層**

|MAXSIZE|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|
|:--- | --: |--: |--: |--: |--: |
|データの最大サイズ (GB)|1024|1024|1536|3072|4096|

**ビジネスに不可欠なサービス層**

|パフォーマンス レベル|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|
|:--- | --: |--: |--: |--: |--: |
|データの最大サイズ (GB)|1024|1024|1536|2048|2048|

vCore モデルを使用する場合に `MAXSIZE` 値が設定されていない場合、既定値は 32 GB です。 vCore に基づくモデルのリソースの制限事項に関する詳細については、「[vCore-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits)」(vCore に基づくリソースの制限) を参照してください。
  
引数 MAXSIZE および EDITION には、以下の規則が適用されます。  
  
- EDITION が指定され、MAXSIZE が指定されていない場合は、エディションの既定値が使用されます。 たとえばは、EDITION が Standard に設定し、MAXSIZE が指定されていない場合、MAXSIZE は自動的に 500 MB に設定します。  
  
- MAXSIZE も EDITION が指定されている場合、EDITION は、標準 (S0) に設定し、MAXSIZE は 250 GB に設定します。  

MODIFY (SERVICE_OBJECTIVE = \<service-objective>)  

パフォーマンス レベルを指定します。 次の例では、Premium データベースのサービスの目標を `P6` に変更します。
 
```sql  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  

パフォーマンス レベルを指定します。 サービスの目標に使用できる値は、`S0`、`S1`、`S2`、`S3`、`S4`、`S6`、`S7`、`S9`、`S12`、`P1`、`P2`、`P4`、`P6`、`P11`、`P15`、`GP_GEN4_1`、`GP_GEN4_2`、`GP_GEN4_4`、`GP_GEN4_8`、`GP_GEN4_16`、`BC_GEN4_1`、`BC_GEN4_2`、`BC_GEN4_4`、`BC_GEN4_8`、`BC_GEN4_16` です。 

サービス目標に関する説明およびサイズ、エディション、サービス目標の組み合わせの詳細については、「[Azure SQL Database サービス レベル概要](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)」、「[DTU-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits)」(DTU に基づくリソースの制限)、「[vCore-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits)」(vCore に基づくリソースの制限) を参照してください。 PRS サービスの目標のサポートはなくなりました。 質問については、電子メール エイリアス premium-rs@microsoft.com を使用してください。 
  
MODIFY (SERVICE_OBJECTIVE = ELASTIC\_POOL (name = \<elastic_pool_name>)  

柔軟なプールには、既存のデータベースを追加するには、ELASTIC_POOL にデータベースの SERVICE_OBJECTIVE を設定し、柔軟なプールの名前を指定します。 同じサーバー内の別の柔軟なプールにデータベースを変更するのに、このオプションを使用することもできます。 詳しくは、[SQL Database エラスティック プールの作成と管理](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)に関するページをご覧ください。 柔軟なプールからデータベースを削除するには、ALTER DATABASE を使用して、SERVICE_OBJECTIVE を 1 つのデータベースのパフォーマンス レベルに設定します。  

ADD SECONDARY ON SERVER \<partner_server_name>  

主キー、地理的レプリケーションにローカルのデータベースを作成して、パートナー サーバーで同じ名前での地理的レプリケーションのセカンダリ データベースを作成し、非同期的に新しいセカンダリへのプライマリからのデータのレプリケーションを開始します。 セカンダリ上に同じ名前のデータベースが既に存在する場合、コマンドは失敗します。 コマンドは、プライマリとなるローカル データベースをホストしているサーバーの master データベースで実行されます。  
  
WITH ALLOW_CONNECTIONS { **ALL** | NO }  

ALLOW_CONNECTIONS が指定されていない場合は、既定では ALL に設定されます。 ALL に設定されている場合は、適切なアクセス許可を持つすべてのログインに接続を許可する読み取り専用データベースになります。  
  
WITH SERVICE_OBJECTIVE {  `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16` }  

SERVICE_OBJECTIVE が指定されていない場合、セカンダリ データベースがプライマリ データベースと同じサービス レベルで作成します。 SERVICE_OBJECTIVE を指定した場合は、指定したレベルにセカンダリ データベースが作成されます。 このオプションは、低価格のサービス レベルで地理的レプリケーションのセカンダリの作成をサポートします。 指定する SERVICE_OBJECTIVE は、ソースと同じエディション内でなければなりません。 たとえば、エディションが Premium の場合、S0 を指定することはできません。  
  
ELASTIC_POOL (name = \<elastic_pool_name)  

ELASTIC_POOL が指定されていない場合、セカンダリ データベースはエラスティック プールに作成されません。 ELASTIC_POOL が指定されている場合、セカンダリ データベースが指定されたプールに作成されます。  
  
> [!IMPORTANT]  
>  セカンダリを追加のコマンドを実行するユーザーは、DBManager をプライマリ サーバー上にある、セカンダリ サーバー上でローカルのデータベースでは、および DBManager db_owner のメンバーシップがある必要があります。  
  
REMOVE SECONDARY ON SERVER  \<partner_server_name>  

指定した地理的レプリケーションのセカンダリ データベースに、指定したサーバーを削除します。 コマンドは、プライマリ データベースをホストしているサーバーの master データベースで実行されます。  
  
> [!IMPORTANT]  
>  セカンダリの削除のコマンドを実行するユーザーは、プライマリ サーバーの DBManager をする必要があります。  
  
FAILOVER  

セカンダリ データベースをコマンドをプライマリが実行され、降格されますが、現在のプライマリになる新しいセカンダリ geo レプリケーションの連携を昇格させます。 このプロセスの一環として、地理的レプリケーションのモードが一時的に非同期モードからに切り替える同期モードです。 フェールオーバー中。  
  
1.  プライマリでは、新しいトランザクションの処理を停止します。  
  
2.  すべての未処理のトランザクションは、セカンダリにフラッシュされます。  
  
3.  セカンダリがプライマリになり、古いプライマリで非同期の地理的レプリケーションを開始すると、新しいセカンダリです。  
  
このシーケンスは、データの損失が発生しないことを保証します。 両方のデータベースは使用できません期間は、役割の交代中に、0 ～ 25 の数秒です。 合計の操作は、約 1 分以内で実行する必要があります。 このコマンドが実行されたときにプライマリ データベースが使用できない場合、プライマリ データベースが使用できないことを示すエラー メッセージで、コマンドは失敗します。 場合は、フェールオーバー プロセスが完了しない、スタックが表示されます、強制フェールオーバー コマンドを使用してデータが失われるをそのまま使用し、次に、データの損失を回復する必要がある場合は、呼び出す devops 失われたデータを回復するには、(CSS) およびできます。  
  
> [!IMPORTANT]  
>  フェールオーバー コマンドを実行するユーザーは、プライマリ サーバーとセカンダリ サーバーの両方で DBManager をする必要があります。  
  
FORCE_FAILOVER_ALLOW_DATA_LOSS  

セカンダリ データベースをコマンドをプライマリが実行され、降格されますが、現在のプライマリになる新しいセカンダリ geo レプリケーションの連携を昇格させます。 現在のプライマリが使用できない場合にのみ、このコマンドを使用します。 設計されていますディザスター リカバリーのみの可用性を復元することが重要といくつかのデータの損失を許容します。  
  
: 強制フェールオーバー中に  
  
1. 指定したセカンダリ データベースはすぐに、プライマリ データベースになり、新しいトランザクションの受け入れを開始します。  
  
2. 元のプライマリは、新しいプライマリに再接続できますと、増分バックアップが元のプライマリ、新しいセカンダリが元のプライマリになります。  
  
3. 古いプライマリのこの増分バックアップからデータを復旧するには、ユーザーは devops/CSS である必要があります。  
  
4. その他のセカンダリがある場合は、自動的に再構成されて新しいプライマリのセカンダリになります。 このプロセスは非同期で、このプロセスが完了するまで、遅延が発生にすることがあります。 再構成が完了するまで、セカンダリは古いプライマリのセカンダリであり続けます。  
  
> [!IMPORTANT]  
>  Force_failover_allow_data_loss の各コマンドを実行するユーザーは、プライマリ サーバーとセカンダリ サーバーの両方で DBManager をする必要があります。  
  
## <a name="remarks"></a>Remarks  

データベースを削除するには、[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) を使用します。  
データベースのサイズを縮小するには、[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md) を使用します。  
  
ALTER DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。  
  
プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 プラン キャッシュ内のキャッシュストアが消去されるたびに、"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、一部のデータベース メンテナンス操作または再構成操作により、'%s' キャッシュストア (プラン キャッシュの一部) のキャッシュストア フラッシュを %d 個検出しました" という情報メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに含まれます。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
プロシージャ キャッシュは、次のシナリオでもフラッシュされます。  
  
- AUTO_CLOSE データベース オプションが ON に設定されている。 データベースを参照 (または使用) するユーザー接続が 1 つも存在しない場合、バックグラウンド タスクがデータベースを自動的に閉じてシャットダウンすることを試みます。  
  
- 既定のオプションが設定されているデータベースに対して複数のクエリを実行した。 データベースはその後削除されます。  
  
- データベースのトランザクション ログを正常に再構築した。  
  
- データベースのバックアップを復元した。  
  
- データベースをデタッチした。  
  
## <a name="viewing-database-information"></a>データベース情報の表示  

カタログ ビュー、システム関数、およびシステム ストアド プロシージャを使用して、データベース、ファイルおよびファイル グループについての情報を返すことができます。  
  
## <a name="permissions"></a>アクセス許可  

データベースを変更できるのは、(準備プロセスによって作成される) サーバーレベルのプリンシパルのログイン、または `dbmanager` データベース ロールのメンバーだけです。  
  
> [!IMPORTANT]  
>  データベースの所有者であっても `dbmanager` ロールのメンバーでない場合は、データベースを変更できません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. エディション オプションを確認して変更します。

```sql
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>B. データベースを別の柔軟なプールに移動します。  

pool1 という名前のプールに既存のデータベースを移動します。  
  
```sql  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>C. 地理的レプリケーション セカンダリを追加します。  

ローカル サーバー上の db1 のサーバー `secondaryserver` に読み取り可能なセカンダリ データベース db1 を作成します。  
  
```sql  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = ALL )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>D. セカンダリ Geo レプリケーションを削除します。  
 
サーバー `secondaryserver` 上のセカンダリ データベース db1 を削除します。  
  
```sql  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>E. 地理的レプリケーションのセカンダリにフェールオーバー  

サーバー `secondaryserver` で実行されると、サーバー `secondaryserver` 上のセカンダリ データベース db1 を昇格させて新しいプライマリ データベースにします。  
  
```sql  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>参照
  
[CREATE DATABASE - Azure SQL データベース](../../t-sql/statements/create-database-azure-sql-database.md)   
 [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [システム データベース](../../relational-databases/databases/system-databases.md)  
  
  
