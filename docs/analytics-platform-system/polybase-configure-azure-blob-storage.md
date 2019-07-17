---
title: Azure Blob storage 内の外部データにアクセスする PolyBase の構成 |Microsoft Docs
description: 外部の Hadoop に接続するための Parallel Data Warehouse で PolyBase を構成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 82c57ef57a01cabf2786c71fc53aed3660289451
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960288"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Azure Blob storage 内の外部データへのアクセスに PolyBase を構成します。

この記事では、Azure Blob storage 内の外部データのクエリを SQL Server インスタンスで PolyBase を使用する方法について説明します。

> [!NOTE]
> 標準の general purpose v1 のローカル冗長 (LRS) の Azure Blob ストレージをサポートのみ、現在 AP しています。

## <a name="prerequisites"></a>前提条件

 - サブスクリプションで azure Blob storage。
 - Azure Blob ストレージで作成したコンテナーです。

### <a name="configure-azure-blob-storage-connectivity"></a>Azure Blob ストレージへの接続を構成します。

最初に、Azure Blob storage を使用するアクセス ポイントを構成します。

1. 実行[sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)で 'hadoop connectivity' を Azure Blob ストレージ プロバイダーに設定します。 プロバイダーの値を見つけるには、[PolyBase 接続構成 ](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)に関する記事を参照してください。

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure Blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. APS リージョンのサービスの状態のページを使用して再起動[アプライアンス Configuration Manager](launch-the-configuration-manager.md)します。
  
## <a name="configure-an-external-table"></a>外部テーブルを構成する

Azure Blob storage 内のデータを照会するには、TRANSACT-SQL クエリで使用する外部テーブルを定義する必要があります。 次の手順では、外部テーブルを構成する方法を説明します。

1. データベースにマスター キーを作成します。 資格情報シークレットを暗号化することが必要です。

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

1. Azure Blob storage のデータベース スコープ資格情報を作成します。

   ```sql
   -- IDENTITY: any string (this is not used for authentication to Azure storage).  
   -- SECRET: your Azure storage account key.  
   CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
   WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';
   ```

1. [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md) を使用して外部ファイル形式を作成します。

   ```sql
   -- FORMAT TYPE: Type of format in Azure Blob storage (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   -- In this example, the files are pipe (|) delimited
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

1. [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md)を使用して、Azure ストレージに格納されているデータをポイントする外部テーブルを作成します。 この例では、外部データには車両センサー データが含まれています。

   ```sql
   -- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
   CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
         [SensorKey] int NOT NULL,
         [CustomerKey] int NOT NULL,
         [GeographyKey] int NULL,
         [Speed] float NOT NULL,
         [YearMeasured] int NOT NULL  
   )  
   WITH (LOCATION='/Demo/',
         DATA_SOURCE = AzureStorage,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

1. 外部テーブルの統計を作成します。

   ```sql
   CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
   ```

## <a name="polybase-queries"></a>PolyBase クエリ

PolyBase が適している機能には、次の 3 つがあります。  
  
- 外部テーブルに対するアドホック クエリ。  
- データのインポート。  
- データのエクスポート。  

次のクエリでは、架空の車両センサー データの例を示します。

### <a name="ad-hoc-queries"></a>アドホック クエリ  

次のアドホック クエリは、Azure Blob storage 内リレーショナル データを結合します。 35 mph、結合の構造化された顧客データを Azure Blob storage に格納されている車両センサー データを SQL Server に格納されているよりも高速化を推進する顧客を選択します。  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
```  

### <a name="importing-data"></a>インポート、データ  

次のクエリでは、AP に外部データをインポートします。 この例より詳細な解析を行う AP に高速のドライバーのデータをインポートします。 パフォーマンスを向上させるのには、AP で列ストア テクノロジを活用します。  

```sql
CREATE TABLE Fast_Customers
WITH
(CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH (CustomerKey))
AS
SELECT DISTINCT
      Insured_Customers.CustomerKey, Insured_Customers.FirstName, Insured_Customers.LastName,   
      Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
from Insured_Customers INNER JOIN   
(  
      SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
```  

### <a name="exporting-data"></a>データのエクスポート  

次のクエリは、AP から Azure Blob storage にデータをエクスポートします。 Azure Blob へのリレーショナル データをアーカイブするために使用できるクエリを実行できるストレージのままです。

```sql
-- Export data: Move old data to Azure Blob storage while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = AzureStorage,  
      FILE_FORMAT = TextFileFormat
)  
AS
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  

## <a name="view-polybase-objects-in-ssdt"></a>SSDT での PolyBase オブジェクトを表示します。  

SQL Server Data tools、外部テーブルが別のフォルダーに表示されます。**外部テーブル**します。 外部データ ソースおよび外部ファイル形式は、 **[外部リソース]** の下のサブフォルダーにあります。  
  
![SSDT での PolyBase オブジェクト](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>次の手順

PolyBase について詳しくは、「[PolyBase とは](../relational-databases/polybase/polybase-guide.md)」をご覧ください。 

