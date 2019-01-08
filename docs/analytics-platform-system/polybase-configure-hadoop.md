---
title: Hadoop 内の外部データにアクセスするように PolyBase を構成する | Microsoft Docs
description: 外部の Hadoop に接続するための Parallel Data Warehouse で PolyBase を構成する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 94c8d399f7b6ba36b48b4c5aa7f35bbd67ce6909
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527809"
---
# <a name="configure-polybase-to-access-external-data-in-hadoop"></a>Hadoop 内の外部データにアクセスするように PolyBase を構成する

この記事では、Hadoop の外部データのクエリを APS アプライアンスで PolyBase を使用する方法について説明します。

## <a name="prerequisites"></a>前提条件

PolyBase は、Hortonworks Data Platform (HDP) と Cloudera Distributed Hadoop (CDH) の 2 つの Hadoop プロバイダーをサポートしています。 Hadoop では、新規リリースについて "Major.Minor.Version" パターンを採用しており、サポートされているメジャーおよびマイナー リリース内のすべてのバージョンがサポートされています。 次の Hadoop プロバイダーがサポートされています。
 - Linux/Windows Server 上の Hortonworks HDP 1.3  
 - Linux 上の Hortonworks HDP 2.1 2.6
 - Windows Server 上の Hortonworks HDP 2.1 - 2.3  
 - Linux 上の Cloudera CDH 4.3  
 - Cloudera CDH 5.1-5.5、5.9-5.13 on Linux

### <a name="configure-hadoop-connectivity"></a>Hadoop 接続を構成する

最初に、APS、特定の Hadoop プロバイダーを使用するを構成します。

1. 'hadoop connectivity' を使用して [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を実行し、プロバイダーに対する適切な値を設定します。 プロバイダーの値を見つけるには、[PolyBase 接続構成 ](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)に関する記事を参照してください。 

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. APS リージョンのサービスの状態のページを使用して再起動[アプライアンス Configuration Manager](launch-the-configuration-manager.md)します。
  
## <a id="pushdown"></a> プッシュダウン計算を有効にする  

クエリ パフォーマンスを高めるには、Hadoop クラスターへのプッシュダウン計算を有効にします。  
  
1. PDW 管理ノードへのリモート デスクトップ接続を開きます。

2. ファイルを見つける**yarn-site.xml**コントロールのノード上。 通常、このパスは次のとおりです。  

   ```xml  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\  
   ```  

3. Hadoop コンピューターで、Hadoop 構成ディレクトリ内の対応するファイルを検索します。 このファイル内の構成キー yarn.application.classpath の値をコピーします。  
  
4. コントロールのノード上で、 **yarn.site.xml ファイル**検索、 **yarn.application.classpath**プロパティ。 Hadoop コンピューターからこの値要素に値を貼り付けます。  
  
5. すべての CDH 5.X バージョンで、yarn.site.xml file の最後か mapred-site.xml file に mapreduce.application.classpath 構成パラメーターを追加する必要があります。 HortonWorks では、yarn.application.classpath 構成内にこれらの構成が含まれます。 例については、「[PolyBase の構成](../relational-databases/polybase/polybase-configuration.md)」を参照してください。

## <a name="configure-an-external-table"></a>外部テーブルを構成する

Hadoop データ ソース内のデータのクエリを実行するには、Transact-SQL クエリで使用する外部テーブルを定義する必要があります。 次の手順では、外部テーブルを構成する方法を説明します。

1. データベースにマスター キーを作成します。 資格情報シークレットを暗号化することが必要です。

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

2. Kerberos でセキュリティ保護された Hadoop クラスターのデータベース スコープ資格情報を作成します。

   ```sql
   -- IDENTITY: the Kerberos user name.  
   -- SECRET: the Kerberos password  
   CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
   WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
   ```

3. [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。

   ```sql
   -- LOCATION (Required) : Hadoop Name Node IP address and port.  
   -- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
   -- CREDENTIAL (Optional):  the database scoped credential, created above.  
   CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
         TYPE = HADOOP,
         LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',
         RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',
         CREDENTIAL = HadoopUser1
   );  
   ```

4. [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md) を使用して外部ファイル形式を作成します。

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

5. [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md)を使用して、Hadoop に格納されているデータをポイントする外部テーブルを作成します。 この例では、外部のデータには、車のセンサー データが含まれています。

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
         DATA_SOURCE = MyHadoopCluster,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

6. 外部テーブルの統計を作成します。

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

次のアドホック クエリがリレーショナル Hadoop データを結合します。 35 mph、結合の構造化された顧客データを Hadoop に格納されている車両センサー データのアクセス ポイントに格納されているよりも高速化を推進する顧客を選択します。  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
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

次のクエリは、AP からデータを Hadoop にエクスポートします。 Hadoop にリレーショナル データをアーカイブするために使用できる while はまだそれをクエリできるようにします。

```sql
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = HadoopHDP2,  
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

Hadoop セキュリティの設定」をご覧ください[Hadoop セキュリティの構成](polybase-configure-hadoop-security.md)します。<br>
PolyBase について詳しくは、「[PolyBase とは](../relational-databases/polybase/polybase-guide.md)」をご覧ください。 
 
