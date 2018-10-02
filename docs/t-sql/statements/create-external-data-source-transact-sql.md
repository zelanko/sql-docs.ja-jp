---
title: CREATE EXTERNAL DATA SOURCE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL DATA SOURCE
- CREATE_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, data source
- PolyBase, create data source
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39dd5cf772bebf66f8d2a5e827badf4ef0981b66
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708738"
---
# <a name="create-external-data-source-transact-sql"></a>外部データ ソース (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  PolyBase または Elastic Database クエリ用の外部データ ソースを作成します。 シナリオによっては、構文が大幅に異なります。 PolyBase 用に作成された外部データ ソースは、Elastic Database のクエリには使用できません。  同様に、Elastic Database のクエリ用に作成された外部データ ソースは、PolyBase などには使用できません。 
  
> [!NOTE]  
>  PolyBase は、SQL Server 2016 以降、Azure SQL Data Warehouse、および Parallel Data Warehouse でのみサポートされています。 Elastic Database のクエリは、Azure SQL Database v12 以降でのみサポートされています。  
  
 PolyBase のシナリオでは、外部データ ソースは、Hadoop ファイル システム (HDFS)、Azure Storage Blob コンテナー、または Azure Data Lake Store のいずれかになります。 詳細については、「 [PolyBase 入門](../../relational-databases/polybase/get-started-with-polybase.md)」を参照してください。  
  
 Elastic Database クエリのシナリオでは、外部のソースは Shard Map Manager (Azure SQL Database) 、またはリモート データベース (Azure SQL Database) のいずれかになります。  [sp_execute_remote &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-execute-remote-azure-sql-database.md) は、外部データ ソースの作成後に使用します。 詳細については、[Elastic Database クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)に関するページを参照してください。  

  Azure Blob Storage の外部データ ソースでは、PolyBase の Azure Blob Storage とは異なり、`BULK INSERT` と `OPENROWSET` の構文がサポートされます。
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- PolyBase only:  Hadoop cluster as data source   
-- (on SQL Server 2016)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,
        LOCATION = 'hdfs://NameNode_URI[:port]'  
        [, RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI[:port]' ]  
        [, CREDENTIAL = credential_name ]
    )
[;]  
  
-- PolyBase only: Azure Storage Blob as data source   
-- (on SQL Server 2016)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
[;]

-- PolyBase only: Azure Data Lake Store
-- (on Azure SQL Data Warehouse)
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (
    TYPE = HADOOP,
    LOCATION = 'adl://<AzureDataLake account_name>.azuredatalake.net',
    CREDENTIAL = AzureStorageCredential
);

-- PolyBase only: Hadoop cluster as data source
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP, 
        LOCATION = 'hdfs://NameNode_URI[:port]'
        [, JOB_TRACKER_LOCATION = 'JobTracker_URI[:port]' ]
    )
[;]

-- PolyBase only: Azure Storage Blob as data source 
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = BLOB_STORAGE,
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
    )
[;]
  
-- Elastic Database query only: a shard map manager as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = SHARD_MAP_MANAGER,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '\<ElasticDatabase_ShardMapManagerDb'>,  
        CREDENTIAL = <ElasticDBQueryCred>,  
        SHARD_MAP_NAME = '<ShardMapName>'  
    )  
[;]  
  
-- Elastic Database query only: a remote database on Azure SQL Database as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = RDBMS,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '<Remote_Database_Name>',  
        CREDENTIAL = <SQL_Credential>  
    )  
[;]  

-- Bulk operations only: Azure Storage Blob as data source   
-- (on SQL Server 2017 or later, and Azure SQL Database).
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'https://storage_account_name.blob.core.windows.net/container_name'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>引数  
 *data_source_name*: データ ソースのユーザー定義名を指定します。 名前は、SQL Server、Azure SQL Databas、および Azure SQL Data Warehouse のデータベース内で一意にする必要があります。 名前は、Parallel Data Warehouse のサーバー内で一意である必要があります。
  
 TYPE = [ HADOOP | SHARD_MAP_MANAGER | RDBMS | BLOB_STORAGE]  
 データ ソースの型を指定します。 外部データ ソースが Hadoop または Hadoop 用 Azure Storage Blob である場合は、HADOOP を使用します。 Azure SQL Database でのシャーディングの対象とする Elastic Database クエリ用の外部データ ソースを作成する場合は、SHARD_MAP_MANAGER を使用します。 Azure SQL Database で Elastic Database クエリを使用したデータベースにまたがるクエリには、RDBMS と外部データ ソースを使用します。  [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] で [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) または [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) を使用して一括操作を実行する場合は、BLOB_STORAGE を使用します。
  
LOCATION = \<location_path> **HADOOP**    
HADOOP の場合、Hadoop クラスターの Uniform Resource Indicator (URI) を指定します。  
`LOCATION = 'hdfs:\/\/*NameNode\_URI*\[:*port*\]'`  
NameNode_URI: Hadoop クラスター Namenode のマシン名または IP アドレスです。  
port: Namenode IPC ポートです。 これは、Hadoop では、fs.default.name 構成パラメーターによって示されます。 値が指定されていない場合、8020 が既定で使用されます。  
例: `LOCATION = 'hdfs://10.10.10.10:8020'`

Hadoop を使用する Azure Blob Storage の場合、Azure Blob Storage に接続するための URI を指定します。  
`LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'`  
wasb[s]: Azure Blob Storage のプロトコルを指定します。 [S] は省略可能であり、セキュリティ保護された SSL 接続を指定します。SQL Server から送信されたデータは SSL プロトコルを使って安全に暗号化されます。 'Wasb' ではなく ' wasbs' を使用を強くお勧めします。 LOCATION は、wasb [s] の代わりに asv [s] を使用できます。 Asv [s] 構文は非推奨とされており、将来のリリースでは削除されます。  
container: Azure Blob Storage コンテナーの名前を指定します。 ドメインのストレージ アカウントのルート コンテナーを指定するには、コンテナー名ではなく、ドメイン名を使用します。 ルート コンテナーは、データをバックアップ コンテナーに書き込むことはできませんのでは読み取り専用です。  
account_name: Azure ストレージ アカウントの完全修飾ドメイン名 (FQDN) です。  
例: `LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'`

Azure Data Lake Store の場合、LOCATION は、お使いの Azure Data Lake Store に接続するための URI を指定します。



**SHARD_MAP_MANAGER**   
 SHARD_MAP_MANAGER の場合、Azure SQL Database または Azure 仮想マシン上の SQL Server データベースで Shard Map Manager をホストする論理サーバー名を指定します。
 
 ```
 CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH
  (TYPE = SHARD_MAP_MANAGER,
  LOCATION = '<server_name>.database.windows.net',
  DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
  CREDENTIAL = ElasticDBQueryCred,
  SHARD_MAP_NAME = 'CustomerIDShardMap'
) ;
```

チュートリアルについては、[シャーディングのエラスティック クエリの概要 (行方向のパーティション分割)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/) のトピックを参照してください。
  
**RDBMS**   
RDBMS の場合、Azure SQL Database でリモート データベースの論理サーバーの名前を指定します。  

```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';  
  
CREATE DATABASE SCOPED CREDENTIAL SQL_Credential    
WITH IDENTITY = '<username>',  
SECRET = '<password>';  
  
CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH   
    (TYPE = RDBMS,   
    LOCATION = '<server_name>.database.windows.net',   
    DATABASE_NAME = 'Customers',   
    CREDENTIAL = SQL_Credential   
) ;   
```  
  
RDBMS のチュートリアルについては、[クロスデータベース クエリの概要 (列方向のパーティション分割)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/) のトピックを参照してください。  

**BLOB_STORAGE**   
一括操作の場合のみ、`LOCATION` は Azure Blob Storage とコンテナーの有効な URL にする必要があります。 `LOCATION` URL の末尾に、**/**、ファイル名、または Shared Access Signature パラメーターを配置しないでください。   
使用される資格情報は、`SHARED ACCESS SIGNATURE` を使用して ID として作成する必要があります。 Shared Access Signature に関する詳細については、「[Shared Access Signature (SAS) を使用](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)」を参照してください。 Blob ストレージへのアクセスの例については、例 F の「[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。 
>[!NOTE] 
>Azure Blob Storage から SQL DW または Parallel Data Warehouse に読み込むには、シークレットが Azure Storage キーである必要があります。

  
 RESOURCE_MANAGER_LOCATION = '*ResourceManager_URI*[:*port*]'  
 Hadoop のリソース マネージャーの場所を指定します。 指定した場合、クエリ オプティマイザーは Hadoop の計算の機能と MapReduce を使用して、PolyBase クエリのデータを事前処理することをコストに基づいて決定できます。 述語のプッシュ ダウンが呼び出されると、この Hadoop と SQL の間で転送されるデータ量を大幅に削減し、クエリのパフォーマンス向上します。  
  
 これを指定しない場合、Hadoop への計算のプッシュが、PolyBase クエリに対して無効になります。  
 
ポートが指定されていない場合、'hadoop connectivity' 構成の現在の設定を使用して、既定値が決まります。

|Hadoop Connectivity|Resource Manager の既定のポート|
|-------------------|-----------------------------|
|1|50300|
|2|50300|
|3|8021|
|4|8032|
|5|8050|
|6|8032|
|7|8050|

各接続値でサポートされている Hadoop ディストリビューションとバージョンの一覧については、「[PolyBase 接続構成 (TRANSACT-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。
  
> [!IMPORTANT]  
>  RESOURCE_MANAGER_LOCATION 値は文字列であり、外部データ ソースを作成するときに検証されません。 正しくない値を入力すると、場所にアクセスするときに将来の遅延が発生することができます。  
  
 Hadoop の例:  
  
-   Windows 上の Hortonworks HDP 2.0、2.1、2.2、 2.3:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
-   Windows 上の Hortonworks HDP 1.3:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Linux 上の Hortonworks HDP 2.0、2.1、2.2、2.3:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8050'  
    ```  
  
-   Linux 上の Hortonworks HDP 1.3:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Linux 上の Cloudera 4.3:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8021'  
    ```  
  
-   Linux 上の Cloudera 5.1 - 5.11:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
 CREDENTIAL = *credential_name*  
 外部データ ソースへの認証の資格情報のデータベース スコープを指定します。 例については、[C. Azure blob ストレージの外部データ ソースの作成](../../t-sql/statements/create-external-data-source-transact-sql.md#credential)を参照してください。 資格情報を作成するには、「[CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)」を参照してください。 匿名アクセスを許可するパブリック データ セットには、CREDENTIAL は必要ありません。 
  
 DATABASE_NAME = *'QueryDatabaseName'*  
 Shard Map Manager (SHARD_MAP_MANAGER) またはリモート データベース (RDBMS) として機能するデータベースの名前です。  
  
 SHARD_MAP_NAME = *'ShardMapName'*  
 SHARD_MAP_MANAGER のみの場合。 シャードのマップの名前。 シャード マップ作成の詳細については、[Elastic Database クエリの概要](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)に関するトピックを参照してください。  
  
## <a name="polybase-specific-notes"></a>PolyBase 固有の注意事項  
サポートされている外部データ ソースの一覧については、「[PolyBase 接続構成 (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。

 PolyBase を使用するのには、これら 3 つのオブジェクトを作成する必要があります。  
  
-   外部データ ソースです。  
  
-   形式は、外部のファイル形式と  
  
-   外部データ ソースと外部のファイル形式を参照する外部テーブルです。  
  
## <a name="permissions"></a>アクセス許可  
 SQL DW、SQL Server、APS 2016 および SQL DB 内のデータベースに対する CONTROL アクセス許可が必要です。

> [!IMPORTANT]  
>  PDW の以前のリリースでは、CREATE EXTERNAL DATA SOURCE には、ALTER ANY EXTERNAL DATA SOURCE アクセス許可が必要でした。
  
  
## <a name="error-handling"></a>エラー処理  
 外部の Hadoop のデータ ソースは、一貫性のあるは、定義されている RESOURCE_MANAGER_LOCATION がない場合、実行時エラーが発生します。 つまり、同じ Hadoop クラスターとしのいずれかと、他のないリソース マネージャーの場所を提供することを参照する 2 つの外部データ ソースを指定できません。  
  
 SQL エンジンでは、外部データ ソースのオブジェクトの作成時に、外部データ ソースの存在は検証されません。 データ ソースが存在しない場合、クエリの実行中にエラーが発生します。  
  
## <a name="general-remarks"></a>全般的な解説  
PolyBase の場合、外部データ ソースは SQL Server と SQL Data Warehouse のデータベース スコープです。 これは Parallel Data Warehouse のサーバー スコープです。
  
PolyBase の場合、RESOURCE_MANAGER_LOCATION または JOB_TRACKER_LOCATION が定義されると、クエリ オプティマイザーは、外部の Hadoop ソース上で Map Reduce ジョブを開始して、計算をプッシュダウンすることで、各クエリの最適化を検討します。 これは、コストベースの判断ではまったくです。  

Hadoop NameNode フェールオーバーが発生した場合に PolyBase クエリを確実に成功させるには、Hadoop クラスターの NameNode に仮想 IP アドレスを使用することを検討してください。 Hadoop NameNode に仮想 IP アドレスを使用しない場合、Hadoop NameNode フェールオーバーが発生したときに、ALTER EXTERNAL DATA SOURCE オブジェクトが新しい場所をポイントするようにする必要があります。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 Hadoop クラスターの同じ場所で定義されているすべてのデータ ソースが、RESOURCE_MANAGER_LOCATION または JOB_TRACKER_LOCATION の同じ設定を使用する必要があります。 不整合がある場合は、実行時エラーが発生します。  
  
 Hadoop クラスターは、名前のセットアップ、外部データ ソースは、IP アドレスを使用してクラスターの場所の場合は、PolyBase をデータ ソースを使用する場合に、クラスター名を解決できないする必要があります。 名前を解決するのには、DNS フォワーダーを有効にする必要があります。  
  
## <a name="locking"></a>ロック  
 外部データ ソース オブジェクト上には、共有ロックを取得します。  
  
##  <a name="examples"></a> 例: SQL Server 2016  
  
### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Hadoop を参照する外部データ ソースを作成する  
Hortonworks または Cloudera Hadoop クラスターを参照する外部データ ソースを作成するには、マシン名または Hadoop Namenode とポートの IP アドレスを指定します。  
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);

```  
  
### <a name="b-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>B. プッシュダウンが有効になっている Hadoop を参照する外部データ ソースを作成する  
RESOURCE_MANAGER_LOCATION オプションを指定して、PolyBase クエリの Hadoop への計算のプッシュダウンを有効にします。 有効にすると、PolyBase はクエリの計算を Hadoop にプッシュするか、すべてのデータを移動して SQL Server でクエリを処理するかどうかをコストに基づいて決定します。
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
);

```
  
###  <a name="credential"></a> C. Kerberos でセキュリティ保護された Hadoop を参照する外部データ ソースを作成する  
Hadoop クラスターが Kerberos でセキュリティ保護されていることを確認するには、Hadoop core-site.xml で hadoop.security.authentication プロパティの値を確認します。 Kerberos でセキュリティ保護された Hadoop クラスターを参照するには、ご自分の Kerberos ユーザー名とパスワードを含むデータベース スコープの資格情報を指定する必要があります。 データベース マスター キーは、データベース スコープの資格情報シークレットの暗号化に使用されます。 
  
```sql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1 
WITH IDENTITY = '<hadoop_user_name>', 
SECRET = '<hadoop_password>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (
    TYPE = HADOOP, 
    LOCATION = 'hdfs://10.10.10.10:8050', 
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050', 
    CREDENTIAL = HadoopUser1
);
```

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>D. Azure Blob Storage を参照する外部データ ソースを作成する
お使いの Azure Blob Storage コンテナーを参照する外部データ ソースを作成するには、Azure Blob Storage URI と、ご自分の Azure ストレージ アカウント キーを含むデータベース スコープの資格情報を指定します。

この例では、外部データ ソースは、myaccount という Azure ストレージ アカウントの下の dailylogs という名前の Azure Blob Storage コンテナーです。 Azure ストレージの外部データ ソースはデータ転送のみで、述語のプッシュダウンはサポートされません。

この例では、Azure ストレージへの認証用にデータベース スコープ資格情報を作成する方法を示します。 データベースの資格情報シークレットで、Azure ストレージ アカウント キーを指定します。 Azure ストレージへの認証に使用しない、データベース スコープ資格情報 ID のすべての文字列を指定します。 次に、資格情報は、外部データ ソースを作成するステートメントで使用されます。

```
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
    TYPE = BLOB_STORAGE, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```

## <a name="examples-azure-sql-database"></a>例: Azure SQL Database

### <a name="e-create-a-shard-map-manager-external-data-source"></a>E. Shard Map Manager の外部データ ソースを作成する
SHARD_MAP_MANAGER を参照する外部データ ソースを作成するには、Azure SQL Database または Azure 仮想マシン上の SQL Server データベースで Shard Map Manager をホストする論理サーバー名を指定します。

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = SHARD_MAP_MANAGER,
    LOCATION = '<server_name>.database.windows.net',
    DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
    CREDENTIAL = ElasticDBQueryCred,
    SHARD_MAP_NAME = 'CustomerIDShardMap'
);
```

### <a name="f-create-an-rdbms-external-data-source"></a>F. RDBMS の外部データ ソースを作成する
RDBMS を参照する外部データ ソースを作成するには、Azure SQL Database でリモート データベースの論理サーバー名を指定します。

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL SQL_Credential  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = RDBMS, 
    LOCATION = '<server_name>.database.windows.net', 
    DATABASE_NAME = 'Customers', 
    CREDENTIAL = SQL_Credential 
);
```

## <a name="examples-azure-sql-data-warehouse"></a>例: Azure SQL Data Warehouse

### <a name="g-create-external-data-source-to-reference-azure-data-lake-store"></a>G. Azure Data Lake Store を参照する外部データ ソースを作成する
Azure Data Lake Store の接続は、お使いの ADLS URI と Azure Acitve Directory アプリケーションのサービス プリンシパルに基づいています。 このアプリケーションの作成に関するドキュメントは、「[Data Lake Store での Azure Active Directory を使用したサービス間認証](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory)」で見つかります。

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = '<ADLS URI>'
)
```



## <a name="examples-parallel-data-warehouse"></a>例: Parallel Data Warehouse

### <a name="h-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>H. プッシュダウンが有効になっている Hadoop を参照する外部データ ソースを作成する
JOB_TRACKER_LOCATION オプションを指定して、PolyBase クエリの Hadoop への計算のプッシュダウンを有効にします。 有効にすると、PolyBase はクエリの計算を Hadoop にプッシュするか、すべてのデータを移動して SQL Server でクエリを処理するかどうかをコストに基づいて決定します。 

```sql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    JOB_TRACKER_LOCATION = '10.10.10.10:8050'
);
```

### <a name="i-create-external-data-source-to-reference-azure-blob-storage"></a>I. Azure Blob Storage を参照する外部データ ソースを作成する
お使いの Azure Blob Storage コンテナーを参照するための外部データ ソースを作成するには、Azure Blob Storage URI を外部データ ソースの LOCATION として指定します。 ご自分の Azure ストレージ アカウント キーを認証用の PDW core-site.xml ファイルに追加します。

この例では、外部データ ソースは、myaccount という Azure ストレージ アカウントの下の dailylogs という名前の Azure Blob Storage コンテナーです。 Azure ストレージの外部データ ソースはデータ転送のみで、述語のプッシュダウンはサポートされません。

```sql
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
        TYPE = HADOOP, 
        LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'
);
```

## <a name="examples-bulk-operations"></a>例: 一括操作   
### <a name="j-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>J. Azure Blob Storage からデータを取得する一括操作用の外部データ ソースを作成する   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]」を参照してください。   
[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) または [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) を使用する一括操作に対し、次のデータ ソースを使用します。 使用される資格情報は、`SHARED ACCESS SIGNATURE` を使用して ID として作成する必要があります。 Shared Access Signature に関する詳細については、「[Shared Access Signature (SAS) を使用](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)」を参照してください。   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = AccessAzureInvoices
    );   
```   
この使用例については、「[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)」をご覧ください。
  
## <a name="see-also"></a>参照
[ALTER EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/alter-external-data-source-transact-sql.md)  
[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
[CREATE EXTERNAL TABLE AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[CREATE TABLE AS SELECT &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
[sys.external_data_sources (Transact-SQL)](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)  
  
  

