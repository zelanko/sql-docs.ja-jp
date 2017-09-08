---
title: "外部データ ソース (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.assetid: 75d8a220-0f4d-4d91-8ba4-9d852b945509
caps.latest.revision: 58
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c2a0a43aefe59bc11f16445b5ee0c781179a33fa
ms.openlocfilehash: 477d2f682da2c91ba8e4bfd42186c4b1b9735f85
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="create-external-data-source-transact-sql"></a>外部データ ソース (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  PolyBase、柔軟なデータベース クエリ、または Azure Blob ストレージの外部データ ソースを作成します。 シナリオによっては、構文が大幅に異なります。 PolyBase 用に作成されたデータ ソースは、弾力性データベースのクエリは使用できません。  同様に、PolyBase などの柔軟なデータベース クエリ用に作成されたデータ ソースを使用できません。 
  
> [!NOTE]  
>  PolyBase は、SQL Server 2016、Azure SQL Data Warehouse、および並列データ ウェアハウスでのみサポートされます。 弾力性データベースにクエリには、Azure SQL Database v12 でのみ、またはそれ以降はサポートされています。  
  
 PolyBase のシナリオで、外部データ ソースは、Hadoop ファイル システム (HDFS)、Azure ストレージ blob コンテナーの場合、または Azure Data Lake Store のいずれかです。 詳細については、「 [PolyBase 入門](../../relational-databases/polybase/get-started-with-polybase.md)」を参照してください。  
  
 弾力性データベース クエリ シナリオでは、外部のソースはシャードのマップ マネージャー (Azure SQL データベース) もありますが、上またはリモートのデータベース (Azure SQL データベース) 上のいずれかです。  使用して[sp_execute_remote & #40 です。Azure SQL データベース &#41;](../../relational-databases/system-stored-procedures/sp-execute-remote-azure-sql-database.md)外部データ ソースを作成した後です。 詳細については、次を参照してください。[柔軟なデータベース クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)です。  

  Azure Blob ストレージの外部データ ソースのサポートしている`BULK INSERT`と`OPENROWSET`構文、PolyBase の Azure Blob ストレージとは異なるとします。
    
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
-- (on SQL Server 2016 and Azure SQL Data Warehouse)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,  
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
        TYPE = HADOOP,
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
 *data_source_name*データ ソースのユーザー定義名を指定します。 名前は、SQL Server、Azure SQL データベース、および Azure SQL Data Warehouse でのデータベース内で一意にする必要があります。 名前は、Parallel Data Warehouse ではサーバー内で一意である必要があります。
  
 種類 = [HADOOP |SHARD_MAP_MANAGER |RDBMS |BLOB_STORAGE]  
 データ ソースの種類を指定します。 HADOOP を使用して、外部データ ソースが Hadoop または Azure ストレージ blob の Hadoop のです。 Azure SQL Database でシャーディングの柔軟なデータベース クエリの外部データ ソースを作成する場合は、SHARD_MAP_MANAGER を使用します。 RDBMS を外部データ ソースと Azure SQL データベースでエラスティック データベース クエリを使用してデータベースにまたがるクエリを使用します。  使用して一括操作を実行するときに、BLOB_STORAGE を使用して[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)または[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]です。
  
場所 = \<location_path > **HADOOP**    
Hadoop, Hadoop クラスターの Uniform Resource Indicator (URI) を指定します。  
`LOCATION = 'hdfs:\/\/*NameNode\_URI*\[:*port*\]'`  
NameNode_URI: マシン名または IP アドレスの Hadoop クラスター Namenode です。  
ポート: Namenode IPC ポートです。 これは、Hadoop fs.default.name 構成パラメーターによって示されます。 値が指定されていない場合、8020 は既定で使用されます。  
例:`LOCATION = 'hdfs://10.10.10.10:8020'`

Hadoop と Azure blob ストレージ、Azure blob ストレージに接続するための URI を指定します。  
`LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'`  
wasb [s]: Azure blob ストレージのプロトコルを指定します。 [S] は省略可能であり、セキュリティ保護された SSL 接続を指定します。SQL Server から送信されたデータは SSL プロトコルを使って安全に暗号化されます。 'Wasb' ではなく ' wasbs' を使用を強くお勧めします。 場所は wasb [s] ではなく asv [s] を使用できることに注意してください。 Asv [s] 構文は推奨されていません、将来のリリースでは削除されます。  
コンテナー: Azure blob ストレージ コンテナーの名前を指定します。 ドメインのストレージ アカウントのルート コンテナーを指定するには、コンテナー名ではなく、ドメイン名を使用します。 ルート コンテナーは、データをバックアップ コンテナーに書き込むことはできませんのでは読み取り専用です。  
account_name: Azure のストレージ アカウントの完全修飾ドメイン名 (FQDN) です。  
例:`LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'`

Azure Data Lake Store には、場所は、Azure Data Lake Store に接続するための URI を指定します。



**SHARD_MAP_MANAGER**   
 Shard_map_manager、シャードのマップ マネージャーで、Azure SQL データベースまたは Azure の仮想マシン上の SQL Server データベースをホストする論理サーバー名を指定します。
 
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

ステップ バイ ステップ チュートリアルでは、次を参照してください。[柔軟なクエリ (水平パーティション分割) シャーディングの概要](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)です。
  
**RDBMS**   
Rdbms では、Azure SQL データベースでリモート データベースの論理サーバー名を指定します。  

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
  
RDBMS のステップ バイ ステップ チュートリアルでは、次を参照してください。[データベースにまたがるクエリ (縦方向のパーティション分割) の概要](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/)です。  

**BLOB_STORAGE**   
一括操作のみ、`LOCATION`有効にする必要がありますの Azure Blob ストレージとコンテナーの URL。 配置しない **/** 、ファイル名、または共有アクセス署名のパラメーターの最後に、 `LOCATION` URL。   
使用して、使用する資格情報を作成する必要があります`SHARED ACCESS SIGNATURE`id として。 Shared Access Signature に関する詳細については、「[Shared Access Signature (SAS) を使用](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)」を参照してください。 Blob ストレージへのアクセスの例は、の例 F を参照してください。 [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)です。 

  
 RESOURCE_MANAGER_LOCATION = '*ResourceManager_URI*[:*ポート*]'  
 Hadoop のリソース マネージャーの場所を指定します。 指定した場合、クエリ オプティマイザーは MapReduce で Hadoop の計算の機能を使用して、PolyBase クエリのデータを事前処理コストベースの判断になります。 述語のプッシュ ダウンが呼び出されると、この Hadoop と SQL の間で転送されるデータ量を大幅に削減し、クエリのパフォーマンス向上します。  
  
 これは、指定しない場合、PolyBase クエリの計算を Hadoop にプッシュが無効です。  
 
ポートが指定されていない場合は、'hadoop connectivity' の設定の現在の設定を使用して、既定値が決まります。

|Hadoop 接続|リソース マネージャーの既定のポート|
|-------------------|-----------------------------|
|1|50300|
|2|50300|
|3|8021|
|4|8032|
|5|8050|
|6|8032|
|7|8050|

Hadoop ディストリビューションと各接続値でサポートされているバージョンの一覧については、次を参照してください。 [PolyBase 接続構成 (TRANSACT-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)です。
  
> [!IMPORTANT]  
>  RESOURCE_MANAGER_LOCATION 値は文字列であり、外部データ ソースを作成するときに検証されません。 正しくない値を入力すると、場所にアクセスするときに将来の遅延が発生することができます。  
  
 Hadoop の例:  
  
-   Hortonworks HDP 2.0、2.1、2.2 です。 Windows の 2.3:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
-   1.3 Windows 上の Hortonworks HDP:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Hortonworks HDP 2.0、2.1、2.2、Linux の 2.3:   
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
  
-   Linux 上の Cloudera 5.1 5.11:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
 資格情報 = *credential_name*  
 外部データ ソースへの認証の資格情報をデータベース スコープを指定します。 例については、次を参照してください。 [C. が Azure blob ストレージの外部データ ソースを作成する](../../t-sql/statements/create-external-data-source-transact-sql.md#credential)です。 資格情報を作成するを参照してください。[資格情報の作成 (TRANSACT-SQL)](../../t-sql/statements/create-credential-transact-sql.md)です。 資格情報が匿名アクセスを許可するパブリック データ セットに必要ないことに注意してください。 
  
 DATABASE_NAME = *'QueryDatabaseName'*  
 (RDBMS) のシャードのマップ マネージャー (を SHARD_MAP_MANAGER) として機能するデータベースまたはリモートのデータベースの名前。  
  
 SHARD_MAP_NAME = *'ShardMapName'*  
 Shard_map_manager のみです。 シャードのマップの名前。 シャード マップの作成の詳細については、次を参照してください[柔軟なデータベース クエリの概要。](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)  
  
## <a name="polybase-specific-notes"></a>PolyBase 固有の注意事項  
サポートされている外部データ ソースの完全な一覧を参照してください。 [PolyBase 接続構成 (TRANSACT-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)です。

 PolyBase を使用するのには、これら 3 つのオブジェクトを作成する必要があります。  
  
-   外部データ ソースです。  
  
-   形式は、外部のファイル形式と  
  
-   外部データ ソースと外部のファイル形式を参照する外部テーブルです。  
  
## <a name="permissions"></a>Permissions  
 SQL データ ウェアハウス、SQL Server、AP 2016 および SQL DB 内のデータベースに対する CONTROL 権限が必要です。

> [!IMPORTANT]  
>  PDW の以前のリリースでは、外部データ ソースのために必要な ALTER ANY EXTERNAL DATA SOURCE のアクセス許可を作成します。
  
  
## <a name="error-handling"></a>エラー処理  
 外部の Hadoop のデータ ソースは、一貫性のあるは、定義されている RESOURCE_MANAGER_LOCATION がない場合、実行時エラーが発生します。 つまり、同じ Hadoop クラスターとしのいずれかと、他のないリソース マネージャーの場所を提供することを参照する 2 つの外部データ ソースを指定できません。  
  
 SQL エンジンでは、外部データ ソースのオブジェクトの作成時に、外部データ ソースの存在は検証されません。 データ ソースが存在しない場合、クエリの実行中にエラーが発生します。  
  
## <a name="general-remarks"></a>全般的な解説  
PolyBase, 外部データ ソースは SQL Server と SQL データ ウェアハウスのデータベース スコープです。 これはサーバー スコープ Parallel Data Warehouse でです。
  
PolyBase, RESOURCE_MANAGER_LOCATION または JOB_TRACKER_LOCATION が定義されている場合、クエリ オプティマイザーを検討してください上のジョブ、外部の Hadoop ソースと計算をプッシュを削減するマップを開始することによって、各クエリの最適化します。 これは、コストベースの判断ではまったくです。  

Hadoop NameNode フェールオーバーが発生した場合の成功の PolyBase クエリには、仮想 IP アドレスを使用して、Hadoop クラスターの NameNode を検討してください。 Hadoop NameNode の仮想 IP アドレスを使用しない場合、Hadoop NameNode フェールオーバーが発生する必要が新しい場所を指す ALTER EXTERNAL DATA SOURCE オブジェクト。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 Hadoop クラスターの同じ場所で定義されているすべてのデータ ソースは、RESOURCE_MANAGER_LOCATION または JOB_TRACKER_LOCATION の同じ設定を使用する必要があります。 不整合がある場合は、実行時エラーが発生します。  
  
 Hadoop クラスターは、名前のセットアップ、外部データ ソースは、IP アドレスを使用してクラスターの場所の場合は、PolyBase をデータ ソースを使用する場合に、クラスター名を解決できないする必要があります。 名前を解決するのには、DNS フォワーダーを有効にする必要があります。  
  
## <a name="locking"></a>ロック  
 外部データ ソース オブジェクト上には、共有ロックを取得します。  
  
##  <a name="examples"></a>例: SQL Server 2016  
  
### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Hadoop を参照する外部データ ソースを作成します。  
Hortonworks または Cloudera Hadoop クラスターを参照する外部データ ソースを作成するには、マシン名または Hadoop Namenode とポートの IP アドレスを指定します。  
  
```tsql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);

```  
  
### <a name="b-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>B. プッシュ ダウンを有効になっている Hadoop を参照する外部データ ソースを作成します。  
PolyBase クエリの Hadoop にプッシュ ダウン計算を有効にする RESOURCE_MANAGER_LOCATION オプションを指定します。 有効にすると、PolyBase はコストベースの判断を使用して、クエリの計算を Hadoop にプッシュする必要がありますか、SQL Server で、クエリの処理にすべてのデータを移動するかを判断します。
  
```tsql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
);

```
  
###  <a name="credential"></a> C. Kerberos でセキュリティ保護された Hadoop を参照する外部データ ソースを作成します。  
Hadoop クラスターが Kerberos でセキュリティ保護されたことを確認するには、Hadoop core-site.xml hadoop.security.authentication プロパティの値を確認します。 Kerberos でセキュリティ保護された Hadoop クラスターを参照するには、Kerberos のユーザー名とパスワードを含むデータベース スコープ資格情報を指定する必要があります。 データベース マスター _ キーはデータベース スコープの資格情報シークレットの暗号化に使用されます。 
  
```tsql  
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

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>D. Azure blob ストレージを参照する外部データ ソースを作成します。
Azure blob ストレージ コンテナーを参照する外部データ ソースを作成するには、Azure blob ストレージ URI と、Azure ストレージ アカウント キーを含むデータベース スコープ資格情報を指定します。

この例では、外部データ ソースは、Azure のストレージ アカウント名 myaccount の下にある dailylogs と呼ばれる Azure blob ストレージ コンテナーはします。 Azure ストレージの外部データ ソースはデータ転送だけです。述語のプッシュ ダウンをサポートしていません。

この例では、Azure ストレージへの認証データベース スコープ資格情報を作成する方法を示します。 データベースの資格情報シークレットでは、Azure ストレージ アカウント キーを指定します。 任意の文字列でデータベース スコープ資格情報 id、Azure ストレージへの認証は使用されませんを指定します。 次に、資格情報は、外部データ ソースを作成するステートメントで使用されます。

```
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
    TYPE = HADOOP, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```

## <a name="examples-azure-sql-database"></a>例: Azure SQL データベース

### <a name="e-create-a-shard-map-manager-external-data-source"></a>E. シャードのマップ manager の外部データ ソースを作成します。
SHARD_MAP_MANAGER を参照する外部データ ソースを作成するには、Azure SQL Database または Azure の仮想マシンで SQL Server データベースにシャードのマップ manager をホストする論理サーバー名を指定します。

```tsql
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

### <a name="f-create-an-rdbms-external-data-source"></a>F. RDBMS の外部データ ソースを作成します。
RDBMS を参照する外部データ ソースを作成するには、Azure SQL データベースでリモート データベースの論理サーバー名を指定します。

```tsql
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

### <a name="g-create-external-data-source-to-reference-azure-blob-storage"></a>G. Azure blob ストレージを参照する外部データ ソースを作成します。
Azure blob ストレージ コンテナーを参照する外部データ ソースを作成するには、Azure blob ストレージ URI と、Azure ストレージ アカウント キーを含むデータベース スコープ資格情報を指定します。

この例では、外部データ ソースは、Azure のストレージ アカウント名 myaccount の下にある dailylogs と呼ばれる Azure blob ストレージ コンテナーはします。 Azure ストレージの外部データ ソースがデータ転送だけ、述語のプッシュ ダウンをサポートしていません。

この例では、Azure ストレージへの認証データベース スコープ資格情報を作成する方法を示します。 データベースの資格情報シークレットでは、Azure ストレージ アカウント キーを指定します。 任意の文字列でデータベース スコープ資格情報 id、Azure ストレージへの認証は使用されませんを指定します。 次に、資格情報は、外部データ ソースを作成するステートメントで使用されます。

```tsql
-- Create a database master key if one does not already exist. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage 
WITH (
    TYPE = HADOOP, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```
### <a name="h-create-external-data-source-to-reference-azure-data-lake-store"></a>H. Azure Data Lake Store を参照する外部データ ソースを作成します。
Azure Data lake Store の接続は、ADLS URI と、Azure のアクティブなディレクトリ アプリケーションのサービス プリンシパルに基づいています。 このアプリケーションを作成するドキュメントはあります[Active Directory を使用してデータ lake store 認証](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory)です。

```tsql
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



## <a name="examples-parallel-data-warehouse"></a>例: 並列データ ウェアハウス

### <a name="i-create-external-data-source-to-reference-hadoop"></a>I. Hadoop を参照する外部データ ソースを作成します。
Hortonworks または Cloudera Hadoop クラスターを参照する外部データ ソースを作成するには、マシン名または Hadoop Namenode とポートの IP アドレスを指定します。

```tsql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);
```

### <a name="j-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>J. プッシュ ダウンを有効になっている Hadoop を参照する外部データ ソースを作成します。
PolyBase クエリの Hadoop にプッシュ ダウン計算を有効にする JOB_TRACKER_LOCATION オプションを指定します。 有効にすると、PolyBase はコストベースの判断を使用して、クエリの計算を Hadoop にプッシュする必要がありますか、SQL Server で、クエリの処理にすべてのデータを移動するかを判断します。 

```tsql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    JOB_TRACKER_LOCATION = '10.10.10.10:8050'
);
```

### <a name="k-create-external-data-source-to-reference-azure-blob-storage"></a>K. Azure blob ストレージを参照する外部データ ソースを作成します。
外部を作成するには、データ ソース、外部のデータとして Azure blob ストレージ URI を指定する、Azure blob ストレージ コンテナーを参照するソースの場所。 認証用の PDW core-site.xml ファイルを Azure ストレージ アカウント キーを追加します。

この例では、外部データ ソースは、Azure のストレージ アカウント名 myaccount の下にある dailylogs と呼ばれる Azure blob ストレージ コンテナーはします。 Azure ストレージの外部データ ソースがデータ転送だけ、述語のプッシュ ダウンをサポートしていません。

```tsql
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
        TYPE = HADOOP, 
        LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'
);
```

## <a name="examples-bulk-operations"></a>例: 一括操作   
### <a name="l-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>L. 一括操作が Azure Blob ストレージからデータを取得する外部データ ソースを作成します。   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]」を参照してください。   
一括操作を使用して次のデータ ソースを使用して[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)または[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)です。 使用して、使用する資格情報を作成する必要があります`SHARED ACCESS SIGNATURE`id として。 Shared Access Signature に関する詳細については、「[Shared Access Signature (SAS) を使用](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)」を参照してください。   
```tsql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = AccessAzureInvoices
    );   
```   
この例では、使用してを参照してください[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)です。
  
## <a name="see-also"></a>参照
[外部データ ソース (TRANSACT-SQL) を変更します](../../t-sql/statements/alter-external-data-source-transact-sql.md)  
[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
[EXTERNAL TABLE AS SELECT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[テーブルとして選択 &#40; を作成します。Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
[sys.external_data_sources (TRANSACT-SQL)](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)  
  
  


