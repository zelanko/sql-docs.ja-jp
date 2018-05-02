---
title: PolyBase クエリ | Microsoft Docs
ms.custom: ''
ms.date: 12/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: polybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: ''
ms.topic: article
keywords:
- PolyBase
helpviewer_keywords:
- PolyBase, import and export
- Hadoop, import with PolyBase
- Hadoop, export with PolyBase
- Azure blob storage, import with PolyBase
- Azure blob storage, export with PolyBase
ms.assetid: 2c5aa2bd-af7d-4f57-9a28-9673c2a4c07e
caps.latest.revision: 18
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b6544e06a8b0d07e4a2eda1f8371cd0440c172f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="polybase-queries"></a>PolyBase Queries
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  この記事では、SQL Server (2016 以降) の [PolyBase](../../relational-databases/polybase/polybase-guide.md) 機能を使用するクエリの例を示します。 これらの例を使用する前に、PolyBase (「[PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)」をご覧ください) の設定に必要な T-SQL ステートメントを理解する必要があります。
  
## <a name="queries"></a>クエリ  
 外部テーブルを照会するには、外部テーブルに対して Transact-SQL ステートメントを実行するか、または BI ツールを使用します。
  
## <a name="select-from-external-table"></a>外部テーブルからの SELECT  
 定義済みの外部テーブルからデータを返す単純なクエリです。  
  
```sql  
SELECT TOP 10 * FROM [dbo].[SensorData];   
```
  
 述語を含む単純なクエリです。

```
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65;
```

## <a name="join-external-tables-with-local-tables"></a>外部テーブルをローカル テーブルと結合する

```
SELECT InsuranceCustomers.FirstName,   
                           InsuranceCustomers.LastName,   
                           SensorData.Speed  
FROM InsuranceCustomers INNER JOIN SensorData    
ON InsuranceCustomers.CustomerKey = SensorData.CustomerKey   
WHERE SensorData.Speed > 65   
ORDER BY SensorData.Speed DESC  
  
```  
  
## <a name="pushdown-computation-to-hadoop"></a>Hadoop へのプッシュダウン計算

ここでは、プッシュダウンのバリエーションを紹介します。

### <a name="pushdown-for-selecting-a-subset-of-rows"></a>行のサブセットを選択するプッシュダウン

外部テーブルから行のサブセットを選択するクエリのパフォーマンスを改善するには、述語のプッシュダウンを使用します。

この例では、SQL Server 2016 は map-reduce ジョブを開始して、Hadoop で述語 `customer.account_balance < 200000` である行を取得します。 このクエリは、テーブルのすべての行をスキャンせずに完了できるため、述語の条件に合う行のみが SQL Server にコピーされます。 この方法で時間が大幅に短縮され、残高が 200000 未満の顧客数が、口座残高が 200000 以上の顧客数と比較して少ない場合に、一時的な記憶域が少なくなります。

```
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="pushdown-for-selecting-a-subset-of-columns"></a>列のサブセットを選択するプッシュダウン

外部テーブルから列のサブセットを選択するクエリのパフォーマンスを改善するには、述語のプッシュダウンを使用します。

このクエリでは、SQL Server で map-reduce ジョブを開始し、Hadoop の区切られたテキスト ファイルを前処理して、customer.name と customer.zip_code という 2 列のデータのみが SQL Server PDW にコピーされるようにします。

```
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>基本的な式と演算子のプッシュダウン

SQL Server では、述語のプッシュダウンに次の基本的な式と演算子を使用できます。

+ 数値、日付値、時間値の 2 項比較演算子 (\<、>、=、!=、<>、>=、<=)。

+ 算術演算子 (+、-、*、/、%)。

+ 論理演算子 (AND、OR)。

+ 単項演算子 (NOT、IS NULL、IS NOT NULL)。

演算子 BETWEEN、NOT、IN、LIKE はプッシュダウンできる場合があります。 実際の動作は、クエリ オプティマイザーが演算子式をどのように基本的な関係演算子を使用する一連のステートメントとして書き換えるかに依存します。

この例のクエリには、Hadoop にプッシュダウンできる述語が複数あります。 SQL Server は、map-reduce ジョブを Hadoop にプッシュして、述語 `customer.account_balance <= 200000` を実行できます。 `BETWEEN 92656 and 92677` の式もまた、Hadoop にプッシュできる 2 項演算子と論理演算子とで構成されます。 `customer.account_balance and customer.zipcode` 内の論理**積**が最後の式です。

この述語の組み合わせで、map-reduce ジョブですべての WHERE 句を実行できます。 SELECT 条件を満たすデータのみが SQL Server PDW にコピーされます。

```
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677
```

### <a name="force-pushdown"></a>プッシュダウンを強制する

```
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

### <a name="disable-pushdown"></a>プッシュダウンを無効にする

```
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="import-data"></a>データのインポート

Hadoop または Azure ストレージからデータを永続的なストレージの SQL Server にインポートします。 SELECT INTO を使用して、SQL Server の永続記憶装置に、外部テーブルで参照されるデータをインポートします。 リレーショナル テーブルをその場で作成し、2 番目の手順でテーブル上に列ストア インデックスを作成します。

```sql
-- PolyBase scenario - import external data into SQL Server
-- Import data for fast drivers into SQL Server to do more in-depth analysis
-- Leverage columnstore technology
  
SELECT DISTINCT   
        Insured_Customers.FirstName, Insured_Customers.LastName,   
        Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
INTO Fast_Customers from Insured_Customers INNER JOIN   
(  
        SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
ORDER BY YearlyIncome  
  
CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
```

## <a name="export-data"></a>データのエクスポート

Hadoop または Azure ストレージに SQL Server からのデータをエクスポートします。 

まず、'allow polybase export' の `sp_configure` 値を 1 に設定してエクスポート機能を有効にします。 次に、変換先ディレクトリを指す外部テーブルを作成します。 CREATE EXTERNAL TABLE ステートメントは、変換先ディレクトリが存在しない場合にそれを作成します。 次に、ローカルの SQL Server テーブルからのデータを外部データ ソースをエクスポートするのに INSERT INTO を使用します。 

SELECT ステートメントの結果セットは、指定したファイル形式で指定した場所にエクスポートされます。 外部ファイルの名前は *QueryID_date_time_ID.format*です ( *ID* は増分識別子、 *format* はエクスポートされるデータ形式)。 たとえば、あるファイルの名前は QID776_20160130_182739_0.orc となります。


> [!NOTE]
> データを PolyBase 経由で Hadoop または Azure Blob Storage にエクスポートする場合、データだけがエクスポートされ、CREATE EXTERNAL TABLE コマンドで定義した列名 (メタデータ) はエクスポートされません。

```sql  
-- PolyBase scenario  - export data from SQL Server to Hadoop
-- Create an external table
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
        [FirstName] char(25) NOT NULL,   
        [LastName] char(25) NOT NULL,   
        [YearlyIncome] float NULL,   
        [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
        LOCATION='/old_data/2009/customerdata',  
        DATA_SOURCE = HadoopHDP2,  
        FILE_FORMAT = TextFileFormat,  
        REJECT_TYPE = VALUE,  
        REJECT_VALUE = 0  
);  
  
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```

## <a name="new-catalog-views"></a>新しいカタログ ビュー

次の新しいカタログ ビューには、外部のリソースが表示されます。
  
```sql
SELECT * FROM sys.external_data_sources;   
SELECT * FROM sys.external_file_formats;  
SELECT * FROM sys.external_tables;  
```
  
 テーブルが外部テーブルかどうかを判断するには、次を使用します: `is_external`  
  
```sql  
SELECT name, type, is_external FROM sys.tables WHERE name='myTableName'   
```  
  
## <a name="next-steps"></a>次の手順  

トラブルシューティングの詳細については、「 [PolyBase のトラブルシューティング](../../relational-databases/polybase/polybase-troubleshooting.md)」を参照してください。
