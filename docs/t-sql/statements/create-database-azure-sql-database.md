---
title: "CREATE DATABASE (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/28/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: e9781bd657f094c7be57ae513cc2c4a026ad4746
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="create-database-azure-sql-database"></a>CREATE DATABASE (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  新しいデータベースを作成します。  
  
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
    | ( EDITION = {  'basic' | 'standard' | 'premium' | 'premiumrs'}   
    | SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
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
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
            | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
    ]  
 [;] 
 
```  
  
## <a name="arguments"></a>引数  
 この構文ダイアグラムは、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]で使用できる引数を示しています。  
  
 *database_name*  
 新しいデータベースの名前。 この名前は、両方をホストできる SQL server 上で一意である必要があります[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]データベースおよび[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]データベースに準拠している、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子の規則。 詳細については、次を参照してください。[識別子](http://go.microsoft.com/fwlink/p/?LinkId=180386)です。  
  
 *Collation_name*  
 データベースの既定の照合順序を指定します。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 指定しない場合、既定の照合順序である SQL_Latin1_General_CP1_CI_AS がデータベースに割り当てられます。  
  
 Windows と SQL の照合順序名の詳細については[COLLATE (TRANSACT-SQL)](http://msdn.microsoft.com/library/ms184391.aspx)です。  
  
 *CATALOG_COLLATION*  
メタデータ カタログに対して既定の照合順序を指定します。 *DATABASE_DEFAULT*メタデータ カタログに使用されることを指定します。 システム ビューと、データベースの既定の照合順序の一致を照合するシステム テーブル。  これは、SQL server の動作です。 

*SQL_Latin1_General_CP1_CI_AS*メタデータ カタログに使用されることを指定します。 システム ビューおよびテーブルを固定 SQL_Latin1_General_CP1_CI_AS 照合順序を照合します。  これは、指定されていない場合、Azure SQL データベースの既定の設定です。

 *エディション*  
 データベースのサービス層を指定します。 使用可能な値が: 'basic'、'standard'、'premium' および 'premiumrs' です。  
  
 EDITION が指定されても、MAXSIZE が指定されていない場合、MAXSIZE は、エディションのでサポートされる最も制限の厳しいサイズに設定されます。  
  
 *MAXSIZE*  
 データベースの最大サイズを指定します。 MAXSIZE は、指定されている EDITION (サービス層) に対して有効である必要があります。各サービス層でサポートされる MAXSIZE 値と既定値 (D) は次のとおりです。  
  
|**MAXSIZE**|**基本**|**S0 S2**|**S3 S12**|**P1 P6 と PRS1 PRS6**| **P11 P15** 
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
|1024 GB から最大 4096 GB 単位での 256 GB * |なし|なし|なし|なし|√|√|  
  
 \*P11 と P15 MAXSIZE を許可する最大 4 TB 1024 GB が既定のサイズをされているとします。  P11 および P15 は、追加料金なしで最大 4 TB の含まれる記憶域を使用できます。 Premium 階層で MAXSIZE が 1 TB を超えるは次の地域で現在使用可能な: 米国 East2、米国西部、米国 Gov バージニア、西ヨーロッパ、ドイツの中央、南東アジア、東日本、オーストラリア東部、カナダ中央、およびカナダ東部です。 現在の制限については、次を参照してください。[データベースをシングル](https://docs.microsoft.com/azure/sql-database-single-database-resources)です。  
  
 引数 MAXSIZE および EDITION には、以下の規則が適用されます。  
  
-   MAXSIZE 値 (指定されている場合) は、上の表に示されている有効値である必要があります。  
  
-   EDITION が指定され、MAXSIZE が指定されていない場合は、エディションの既定値が使用されます。 たとえば、EDITION が Standard に設定されて、MAXSIZE が指定されていない場合は、MAXSIZE は自動的に設定 250 MB。  
  
-   MAXSIZE も EDITION が指定されている場合、EDITION は、標準 (S0) に設定し、MAXSIZE は 250 GB に設定します。  
  
 SERVICE_OBJECTIVE  
 パフォーマンス レベルを指定します。 サービス目標に関する説明と、サイズ、エディション、およびサービス目標の組み合わせの詳細については、次を参照してください[Azure SQL データベース サービス階層とパフォーマンス レベル](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)と[SQL データベースのリソース。制限](https://azure.microsoft.com/documentation/articles/sql-database-resource-limits)です。 指定した SERVICE_OBJECTIVE が EDITION によってサポートされていない場合は、エラーが返されます。  
  
 ELASTIC_POOL (名前 = \<elastic_pool_name >) エラスティック データベース プールで新しいデータベースを作成するには、ELASTIC_POOL にデータベースの SERVICE_OBJECTIVE を設定およびプールの名前を指定します。 詳細については、次を参照してください。[を作成すると、SQL データベース エラスティック データベース プール (プレビュー) 管理](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)です。  
  
 *AS COPY OF [source_server_name]。source_database_name*  
 データベースを同じ [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーにコピーするか別のサーバーにコピーするかを指定します。  
  
 *source_server_name*  
 ソース データベースが配置されている [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーの名前。 このパラメーターは、ソース データベースと対象データベースが同じ [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバー上にある場合は省略可能です。  
  
 注: `AS COPY OF` 引数で一意の完全修飾ドメイン名を使用することはできません。 つまり、サーバーの完全修飾ドメイン名が `serverName.database.windows.net` である場合は、`serverName` のみをデータベース コピー中に使用します。  
  
 *source_database_name*  
 コピーするデータベースの名前。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]使用する場合は、次の引数とオプションをできません、`CREATE DATABASE`ステートメント。  
  
-   ファイルの物理的な配置に関連するようにパラメーター \<filespec > と\<ファイル グループ >  
  
-   外部アクセス オプション (DB_CHAINING、TRUSTWORTHY など)  
  
-   データベースをアタッチする  
  
-   Service Broker オプション (ENABLE_BROKER、NEW_BROKER、ERROR_BROKER_CONVERSATIONS など)  
  
-   データベース スナップショット  
  
 引数の詳細については、`CREATE DATABASE`ステートメントを参照してください[CREATE DATABASE & #40 です。SQL Server TRANSACT-SQL &#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 内のデータベースについては、データベースの作成時に設定される既定の設定がいくつかあります。 これらの既定の設定の詳細については、の値の一覧を参照して[DATABASEPROPERTYEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
 MAXSIZE を使用して、データベースのサイズを制限できます。 データベースのサイズが MAXSIZE に達するとエラー コード 40544 が表示されます。 このエラーが発生すると、データを挿入または更新したり、新しいオブジェクト (テーブル、ストアド プロシージャ、ビュー、関数など) を作成したりできなくなります。 データの読み取りと削除、テーブルの切り捨て、テーブルとインデックスの削除、およびインデックスの再構築は引き続き可能です。 これを解決するには、MAXSIZE を現在のデータベースのサイズより大きい値にするか、一部のデータを削除してストレージ領域を解放します。 新しいデータを挿入できるようになるまでに、最大で 15 分の遅延が生じる可能性があります。  
  
> [!IMPORTANT]  
>  `CREATE DATABASE`ステートメントは唯一のステートメントである必要があります、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。 
  
 後で、サイズ、エディション、またはサービス目標の値を変更する場合は、次のように使用します。 [ALTER DATABASE & #40 です。Azure SQL データベース &#41;](../../t-sql/statements/alter-database-azure-sql-database.md).  

CATALOG_COLLATION 引数ではデータベースの作成中にのみ使用できます。 
  
## <a name="database-copies"></a>データベース コピー  
 使用してデータベースのコピー、`CREATE DATABASE`ステートメントは、非同期操作です。 したがって、コピー プロセスが完了するまで [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーに接続している必要はありません。 `CREATE DATABASE`ステートメントは、sys.databases のエントリが作成されますが、データベースのコピーする前に操作が完了した後、ユーザーにコントロールを返します。 つまり、`CREATE DATABASE` ステートメントは、データベース コピーがまだ進行しているときに正常に復帰します。  
  
-   コピー プロセスの監視、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]サーバー: クエリ、`percentage_complete`または`replication_state_desc`内の列、 [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)または`state`内の列、 **sys.databases**表示します。 [Sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)ビューはデータベースのコピーを含めたデータベース操作のステータスを返すようにも使用できます。  
  
 コピー プロセスが正常に完了した時点で、ソース データベースに対するトランザクションが対象データベースに反映されています。  
  
 `AS COPY OF` 引数を使用する際、次の構文および意味上の規則が適用されます。  
  
-   コピー先のサーバー名としてコピー元のサーバー名と同じ名前を使用することも別の名前を使用することもできます。 それらが同一とこのパラメーターは省略可能な現在のセッションのサーバー コンテキストが既定で使用されます。  
  
-   ソース データベースと対象データベースの名前を指定する必要があります。これらの名前は、一意であり、識別子に関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の規則に準拠している必要があります。 詳細については、次を参照してください。[識別子](http://go.microsoft.com/fwlink/p/?LinkId=180386)です。  
  
-   `CREATE DATABASE` ステートメントは、新しいデータベースが作成される [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーの master データベースのコンテキスト内で実行される必要があります。  
  
-   コピーの完了後、対象データベースは個別のデータベースとして管理される必要があります。 `ALTER DATABASE` ステートメントと `DROP DATABASE` ステートメントは、ソース データベースに影響を与えることなく、新しいデータベースに対して実行できます。  新しいデータベースを別の新しいデータベースにコピーすることもできます。  
  
-   データベース コピーが進行中でも、ソース データベースには引き続きアクセスできます。  
  
 詳細については、次を参照してください。 [Transact SQL を使用して Azure SQL データベースのコピーを作成](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/)です。  
  
## <a name="permissions"></a>Permissions  
 データベース ログインを作成するには、必要があります、次のいずれか。  
  
-   サーバー レベル プリンシパル ログイン  
  
-   ローカルの Azure SQL Server 用 Azure AD 管理者  
  
-   メンバーであるログイン、`dbmanager`データベース ロール  
  
 **使用するための追加要件`CREATE DATABASE ... AS COPY OF`構文:**ステートメントを実行するローカル サーバーにログインする必要がありますには、少なくとも、`db_owner`移行元サーバーでします。 ログインに基づいている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証では、ローカル サーバーで、ステートメントを実行するログインは、ソースで一致するログインを持つ必要があります[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー、同じ名前とパスワードを使用します。  
  
## <a name="examples"></a>使用例  
SQL Server Management Studio を使用して Azure SQL データベースに接続する方法を示すクイック スタート チュートリアルを参照してください。 [Azure SQL Database: 接続してデータをクエリに使用する SQL Server Management Studio](/azure/sql-database/sql-database-connect-query-ssms)です。  
  
### <a name="simple-example"></a>簡単な例  
 データベースを作成するための簡単な例です。  
  
```tsql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>エディションでの簡単な例  
 標準的なデータベースを作成するための簡単な例です。  
  
```tsql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>追加のオプションの使用例  
 複数のオプションを使用する例です。  
  
```tsql  
CREATE DATABASE hito   
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS   
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>コピーを作成します。  
 データベースのコピーを作成する例です。  
  
```tsql  
CREATE DATABASE escuela   
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>柔軟なプールにデータベースを作成します。  
 S3M100 をという名前のプールには、新しいデータベースを作成します。  
  
```tsql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>別のサーバーにデータベースのコピーを作成します。  
 次の例では、P2 パフォーマンス レベルで db_copy 1 つのデータベースの名前が付いた、db_original データベースのコピーを作成します。  これは、柔軟なプールまたは 1 つのデータベースのパフォーマンス レベルでの db_original がいるかどうかに関係なく当てはまります。  
  
```tsql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 次の例では、ep1 という名前の弾力性プールで db_copy をという名前の db_original データベースのコピーを作成します。  これは、柔軟なプールまたは 1 つのデータベースのパフォーマンス レベルでの db_original がいるかどうかに関係なく当てはまります。  別の名前で、弾力性プールでの db_original が、ep1 で db_copy は作成されます。  
  
```tsql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original   
    (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>指定したカタログ照合順序の値を持つデータベースを作成します。

次の例では、データベースの作成は、データベースの照合順序と同じである、カタログ照合順序を設定中に、カタログ照合順序が DATABASE_DEFAULT に設定します。

```tsql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
      WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>参照  

-  [sys.dm_database_copies & #40 です。Azure SQL データベース &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

-   [ALTER DATABASE & #40 です。Azure SQL データベース &#41;](alter-database-azure-sql-database.md)   
    
  


