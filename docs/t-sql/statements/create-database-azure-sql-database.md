---
title: CREATE DATABASE (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SERVICE_OBJECTIVE
- SERVICE_OBJECTIVE_TSQL
- ELASTIC_POOL
- ELASTIC_POOL_TSQL
- EDITION
- EDITION_TSQL
- MAXSIZE
- MAXSIZE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVICE_OBJECTIVE
- ELASTIC_POOL
- EDITION SQL Database
- MAXSIZE SQL Database
ms.assetid: 22b167f7-ae86-490b-adb3-ec02ca1c1508
caps.latest.revision: 62
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 646072361fe637daa24175742b36309252663cf4
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="create-database-azure-sql-database"></a>CREATE DATABASE (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  新しいデータベースを作成します。  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

## <a name="syntax"></a>構文  

``` 
  
CREATE DATABASE database_name [ COLLATE collation_name ]  
{  
   (<edition_options> [, ...n]) 
}  

[ WITH CATALOG_COLLATION = { DATABASE_DEFAULT | SQL_Latin1_General_CP1_CI_AS }  ]
  
<edition_options> ::= 
{  

  MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }  
  | ( EDITION = {  'basic' | 'standard' | 'premium' | 'GeneralPurpose' | 'BusinessCritical' } 
  | SERVICE_OBJECTIVE = 
    {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
      | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' 
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 
      | { ELASTIC_POOL(name = <elastic_pool_name>) } }  ) 
}  

 [;]  
  

```  

```
To copy a database:  
CREATE DATABASE database_name  
    AS COPY OF [source_server_name.] source_database_name  
    [ ( SERVICE_OBJECTIVE = 
      {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |  
        | 'P1' | 'P2' | 'P4'| 'P6' | 'P11' | 'P15'  
        | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' 
        | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 
        | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
  ]  
 [;] 
 
```  
  
## <a name="arguments"></a>引数  
 この構文ダイアグラムは、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]で使用できる引数を示しています。  
  
*database_name* 
 
新しいデータベースの名前。 この名前は、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] データベースと [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] データベースの両方をホストでき、ID の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の規則に従う、SQL Server に固有のものである必要があります。 詳細については、「[データベース識別子](http://go.microsoft.com/fwlink/p/?LinkId=180386)」を参照してください。  
  
*Collation_name*  

データベースの既定の照合順序を指定します。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 指定しない場合、既定の照合順序である SQL_Latin1_General_CP1_CI_AS がデータベースに割り当てられます。  
  
Windows と SQL の照合順序名の詳細については、[COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx) に関するページを参照してください。  
  
CATALOG_COLLATION  

メタデータ カタログの既定の照合順序を指定します。 *DATABASE_DEFAULT* では、データベースの既定の照合順序と一致させるためにシステム ビューとシステム テーブルで使用されたメタデータ カタログが照合されることが指定されます。  これは、SQL Server で見られる動作です。 

*SQL_Latin1_General_CP1_CI_AS* では、固定照合順序 SQL_Latin1_General_CP1_CI_AS に対してシステム ビューとテーブルで使用されたメタデータ カタログが照合されることが指定されます。  指定がない場合、これは Azure SQL Database の既定の設定です。

EDITION
 
データベースのサービス層を指定します。 使用可能な値は、'basic'、'standard'、'premium'、'GeneralPurpose' および 'BusinessCritical' です。 'premiumrs' のサポートは削除されました。 質問については、電子メール エイリアス premium-rs@microsoft.com を使用してください。
  
 EDITION が指定されいても MAXSIZE が指定されていない場合、MAXSIZE は、そのエディションでサポートされる最も小さなサイズに設定されます。  
  
 MAXSIZE

データベースの最大サイズを指定します。 MAXSIZE は、指定されている EDITION (サービス層) に対して有効である必要があります。各サービス層でサポートされる MAXSIZE 値と既定値 (D) は次のとおりです。

**DTU に基づくモデル**

|**MAXSIZE**|**基本**|**S0-S2**|**S3-S12**|**P1-P6**| **P11-P15** | 
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
|300 GB|なし|なし|√|√|√|
|400 GB|なし|なし|√|√|√|
|500 GB|なし|なし|√|√ (D)|√|
|750 GB|なし|なし|√|√|√|
|1024 GB|なし|なし|√|√|√ (D)|
|1024 GB から 4096 GB (256 GB ずつ増分)* |なし|なし|なし|なし|√|√|  
  
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
  
- EDITION が指定され、MAXSIZE が指定されていない場合は、エディションの既定値が使用されます。 たとえば、EDITION が Standard に設定され、MAXSIZE が指定されていない場合、MAXSIZE は自動的に 250 MB に設定されます。  
- MAXSIZE も EDITION が指定されている場合、EDITION は、標準 (S0) に設定し、MAXSIZE は 250 GB に設定します。  

SERVICE_OBJECTIVE

パフォーマンス レベルを指定します。 サービスの目標に使用できる値は、`S0`、`S1`、`S2`、`S3`、`S4`、`S6`、`S7`、`S9`、`S12`、`P1`、`P2`、`P4`、`P6`、`P11`、`P15`、`GP_GEN4_1`、`GP_GEN4_2`、`GP_GEN4_4`、`GP_GEN4_8`、`GP_GEN4_16`、`BC_GEN4_1`、`BC_GEN4_2`、`BC_GEN4_4`、`BC_GEN4_8`、`BC_GEN4_16` です。 

サービス目標に関する説明およびサイズ、エディション、サービス目標の組み合わせの詳細については、「[Azure SQL データベースのサービス階層](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers)」をご覧ください。 指定した SERVICE_OBJECTIVE が EDITION によってサポートされていません、エラーが表示されます。 SERVICE_OBJECTIVE の値を 1 つの階層から別の階層に変更する場合 (たとえば、S1 から P1) は、EDITION の値も変更する必要があります。 サービス目標に関する説明およびサイズ、エディション、サービス目標の組み合わせの詳細については、「[Azure SQL Database サービス レベル概要](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)」、「[DTU-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits)」(DTU に基づくリソースの制限)、「[vCore-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits)」(vCore に基づくリソースの制限) を参照してください。  PRS サービスの目標のサポートはなくなりました。 質問については、電子メール エイリアス premium-rs@microsoft.com を使用してください。 
  
ELASTIC_POOL (name = \<elastic_pool_name>)
 
弾力性のあるデータベース プールで新しいデータベースを作成するには、データベースの SERVICE_OBJECTIVE を ELASTIC_POOL に設定し、プールの名前を指定します。 詳細については、[SQL Database エラスティック データベースプールの作成と管理 (プレビュー)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/) に関するページを参照してください。  
  
AS COPY OF [source_server_name.]source_database_name

データベースを同じ [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーにコピーするか別のサーバーにコピーするかを指定します。  
  
*source_server_name*  

ソース データベースが配置されている [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーの名前。 このパラメーターは、ソース データベースと対象データベースが同じ [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバー上にある場合は省略可能です。  
  
> [!NOTE]
> `AS COPY OF` 引数で一意の完全修飾ドメイン名を使用することはできません。 つまり、サーバーの完全修飾ドメイン名が `serverName.database.windows.net` である場合は、`serverName` のみをデータベース コピー中に使用します。  
  
*source_database_name*

コピーするデータベースの名前。  
  
[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] で `CREATE DATABASE` ステートメントを使用する場合、次の引数およびオプションはサポートされません。  
  
- \<filespec> や \<filegroup> などの、ファイルの物理的な場所に関連するパラメーター  
  
- 外部アクセス オプション (DB_CHAINING、TRUSTWORTHY など)  
  
- データベースをアタッチする  
  
- Service Broker オプション (ENABLE_BROKER、NEW_BROKER、ERROR_BROKER_CONVERSATIONS など)  
  
- データベース スナップショット  
  
引数と `CREATE DATABASE` ステートメントの詳細については、「[CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks
 
[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 内のデータベースについては、データベースの作成時に設定される既定の設定がいくつかあります。 これらの既定の設定の詳細については、「[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)」の値の一覧を参照してください。  
  
MAXSIZE を使用して、データベースのサイズを制限できます。 データベースのサイズが MAXSIZE に達すると、エラー コード 40544 が返されます。 このエラーが発生すると、データを挿入または更新したり、新しいオブジェクト (テーブル、ストアド プロシージャ、ビュー、関数など) を作成したりできなくなります。 データの読み取りと削除、テーブルの切り捨て、テーブルとインデックスの削除、およびインデックスの再構築は引き続き可能です。 これを解決するには、MAXSIZE を現在のデータベースのサイズより大きい値にするか、一部のデータを削除してストレージ領域を解放します。 新しいデータを挿入できるようになるまでに、最大で 15 分の遅延が生じる可能性があります。  
  
> [!IMPORTANT]  
>  `CREATE DATABASE` ステートメントが [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内の唯一のステートメントである必要があります。 
  
後からサイズ、エディション、またはサービス目標の値を変更するには、[ALTER DATABASE &#40;Azure SQL Database&#41;](../../t-sql/statements/alter-database-azure-sql-database.md) を使用します。  

CATALOG_COLLATION 引数はデータベースの作成中にのみ使用できます。 
  
## <a name="database-copies"></a>データベース コピー  

`CREATE DATABASE` ステートメントを使用したデータベースのコピーは、非同期操作です。 したがって、コピー プロセスが完了するまで [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーに接続している必要はありません。 `CREATE DATABASE` ステートメントは、sys.databases へのエントリが作成された後、データベース コピー操作が完了する前に、制御をユーザーに戻します。 つまり、`CREATE DATABASE` ステートメントは、データベース コピーがまだ進行しているときに正常に復帰します。  
  
- [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] サーバーでのコピー プロセスの監視: [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) の `percentage_complete` または `replication_state_desc` 列、もしくは **sys.databases** ビューの `state` 列にクエリを発行します。 [sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) ビューを使用できるだけでなく、このビューからデータベース コピーを含むデータベース操作の状態も返されます。  
  
コピー プロセスが正常に完了した時点で、ソース データベースに対するトランザクションが対象データベースに反映されています。  
  
`AS COPY OF` 引数を使用する際、次の構文および意味上の規則が適用されます。  
  
- コピー先のサーバー名としてコピー元のサーバー名と同じ名前を使用することも別の名前を使用することもできます。 名前が同じである場合、このパラメーターは省略可能であり、現在のセッションのサーバー コンテキストが既定で使用されます。  
  
- ソース データベースと対象データベースの名前を指定する必要があります。これらの名前は、一意であり、識別子に関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の規則に準拠している必要があります。 詳細については、「[データベース識別子](http://go.microsoft.com/fwlink/p/?LinkId=180386)」を参照してください。  
  
- `CREATE DATABASE` ステートメントは、新しいデータベースが作成される [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーの master データベースのコンテキスト内で実行される必要があります。 
- コピーの完了後、対象データベースは個別のデータベースとして管理される必要があります。 `ALTER DATABASE` ステートメントと `DROP DATABASE` ステートメントは、ソース データベースに影響を与えることなく、新しいデータベースに対して実行できます。  新しいデータベースを別の新しいデータベースにコピーすることもできます。  
  
- データベース コピーが進行中でも、ソース データベースには引き続きアクセスできます。  
  
 詳細については、[Transact-SQL を使った Azure SQL Database のコピーの作成](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/)に関するページを参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 データベースを作成するには、次のいずれかでログインする必要があります。  
  
- サーバー レベル プリンシパル ログイン  
  
- ローカルの Azure SQL Server の Azure AD 管理者  
  
- `dbmanager` データベース ロールのメンバーであるログイン  
  
 **`CREATE DATABASE ... AS COPY OF` 構文を使用するための追加要件:** ローカル サーバー上でステートメントを実行しているログインは少なくともソース サーバー上の `db_owner` である必要があります。 ログインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証に基づいている場合、ローカル サーバー上でステートメントを実行しているログインが、ソース [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバー上にも同じ名前とパスワードで含まれている必要があります。  
  
## <a name="examples"></a>使用例  
SQL Server Management Studio を使用して Azure SQL Database に接続する方法を示すクイック スタート チュートリアルは、「[Azure SQL Database: Use SQL Server Management Studio to connect and query data](/azure/sql-database/sql-database-connect-query-ssms)」(Azure SQL Database: SQL Server Management Studio を使用してデータへの接続とクエリを行う) を参照してください。  
  
### <a name="simple-example"></a>簡単な例  
 データベースを作成するための簡単な例です。  
  
```sql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>エディションでの簡単な例  
 標準的なデータベースを作成するための簡単な例です。  
  
```sql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>追加のオプションの使用例  
 複数のオプションを使用する例です。  
  
```sql  
CREATE DATABASE hito 
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS 
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>コピーを作成します。  
 データベースのコピーを作成する例です。  
  
```sql  
CREATE DATABASE escuela 
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>柔軟なプールにデータベースを作成します。  
 S3M100 をという名前のプールには、新しいデータベースを作成します。  
  
```sql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>別のサーバーにデータベースのコピーを作成します。  
 次の例では、単一データベースの P2 パフォーマンス レベルで db_original database のコピーである named db_copy を作成します。  これは、柔軟なプールまたは 1 つのデータベースのパフォーマンス レベルでの db_original がいるかどうかに関係なく当てはまります。  
  
```sql  
CREATE DATABASE db_copy 
  AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 次の例では、ep1 という名前のエラスティック プールに db_original database のコピーである named db_copy を作成します。  これは、柔軟なプールまたは 1 つのデータベースのパフォーマンス レベルでの db_original がいるかどうかに関係なく当てはまります。  db_original が異なる名前のエラスティック プールにある場合、db_copy は引き続き ep1 に作成されます。  
  
```sql  
CREATE DATABASE db_copy 
  AS COPY OF ozabzw7545.db_original 
  (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>指定したカタログ照合順序の値のデータベースを作成する

次の例では、データベース作成中のカタログ照合順序を DATABASE_DEFAULT に設定します。これにより、カタログ照合順序がデータベースの照合順序と同じに設定されます。

```sql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
  WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>参照  

-  [sys.dm_database_copies &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

- [ALTER DATABASE &#40;Azure SQL Database&#41;](alter-database-azure-sql-database.md) 
  
  

