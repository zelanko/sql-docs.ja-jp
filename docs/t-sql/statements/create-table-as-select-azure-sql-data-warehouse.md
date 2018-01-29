---
title: "作成テーブルとして選択 (Azure SQL Data Warehouse) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/07/2016
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d1e08f88-64ef-4001-8a66-372249df2533
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 429c2dc727d844c35943fa599e6fbcb911df04ac
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-table-as-select-azure-sql-data-warehouse"></a>テーブルとして選択 (Azure SQL データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

作成テーブルとして選択 (CTAS) は、使用可能な最も重要な T-SQL 機能の 1 つです。 SELECT ステートメントの出力に基づいた新しいテーブルを作成する完全な並列化された操作です。 CTAS は、テーブルのコピーを作成する最も簡単で高速な方法です。   
 
 たとえばに CTAS を使用します。  
  
-   異なるハッシュ ディストリビューション列を含むテーブルを再作成します。
-   レプリケートされると、テーブルを再作成します。   
-   テーブル内の列の一部では、列ストア インデックスを作成します。  
-   クエリを実行または外部データをインポートします。  

> [!NOTE]  
> CTAS は、テーブルを作成するの機能に追加するためこのトピックはテーブルの作成に関するトピックを繰り返さない試行します。 代わりに、CTAS ステートメントと CREATE TABLE ステートメントの違いについて説明します。 詳細については、CREATE TABLE、次を参照してください。 [CREATE TABLE (Azure SQL Data Warehouse)](https://msdn.microsoft.com/library/mt203953/)ステートメントです。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
<a name="syntax-bk"></a>

## <a name="syntax"></a>構文   

```  
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    [ ( column_name [ ,...n ] ) ]  
    WITH ( 
      <distribution_option> -- required
      [ , <table_option> [ ,...n ] ]    
    )  
    AS <select_statement>   
[;]  

<distribution_option> ::=
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN 
      | DISTRIBUTION = REPLICATE
    }   

<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) --default is ASC 
    }  
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] --default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) ) 
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT select_criteria  

```  

<a name="arguments-bk"></a>
  
## <a name="arguments"></a>引数  
詳細については、次を参照してください。、 [「引数」セクション](https://msdn.microsoft.com/library/mt203953/#Arguments)CREATE TABLE でします。  

<a name="column-options-bk"></a>

### <a name="column-options"></a>列のオプション
`column_name` [ ,...`n` ]   
 列名が許可しない、[列オプション](https://msdn.microsoft.com/library/mt203953/#ColumnOptions)テーブルの作成に記載します。  代わりに、新しいテーブルの 1 つまたは複数の列名のオプションのリストを指定できます。 新しいテーブルの列を指定する名前が使用されます。 列名を指定すると、列リスト内の列の数は、select の結果内の列の数と一致する必要があります。 任意の列名を指定しない場合、新しいターゲット テーブルは、select ステートメントの結果で、列名を使用します。 
  
 データ型、照合順序、または null 値許容属性などの列のオプションを指定することはできません。 これらの各属性の結果から派生したが、`SELECT`ステートメントです。 ただし、SELECT ステートメントを使用して、属性を変更することができます。 例については、次を参照してください。[列属性を変更する使用 CTAS](#ctas-change-column-attributes-bk)です。   

<a name="table-distribution-options-bk"></a>

### <a name="table-distribution-options"></a>テーブルの配布オプション

`DISTRIBUTION` = `HASH` ( *distribution_column_name* ) | ROUND_ROBIN | REPLICATE      
CTAS ステートメントは、配布オプションが必要ですし、既定値はありません。 これは、既定値を持つテーブルの作成と異なります。 

詳細については、および最適なディストリビューション列を選択する方法を理解するには、「、[テーブル配布オプション](https://msdn.microsoft.com/library/mt203953/#TableDistributionOptions)テーブルの作成」セクション。 

<a name="table-partition-options-bk"></a>

### <a name="table-partition-options"></a>テーブル パーティションのオプション
CTAS ステートメントは、ソース テーブルがパーティション分割されている場合でも、既定では、非パーティション テーブルを作成します。 CTAS ステートメントを使用して、パーティション テーブルを作成するには、パーティション オプションを指定する必要があります。 

詳細については、次を参照してください。、[テーブル パーティション オプション](https://msdn.microsoft.com/library/mt203953/#TablePartitionOptions)テーブルの作成」セクション。

<a name="select-options-bk"></a>

### <a name="select-options"></a>オプションを選択します
Select ステートメントは、CTAS と CREATE TABLE の基本的な違いです。  

 `WITH` *common_table_expression*  
 共通テーブル式 (CTE) と呼ばれる一時的な名前付き結果セットを指定します。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です](../../t-sql/queries/with-common-table-expression-transact-sql.md)。  
  
 `SELECT` *select_criteria*  
 SELECT ステートメントの結果を新しいテーブルを追加します。 *select_criteria*新しいテーブルにコピーするデータを決定する SELECT ステートメントの本文です。 SELECT ステートメントの概要については、次を参照してください[SELECT &#40;。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-transact-sql.md).  
  
<a name="permissions-bk"></a>  
  
## <a name="permissions"></a>権限  
CTAS 必要`SELECT`で参照されているすべてのオブジェクトに対する権限、 *select_criteria*です。

テーブルを作成するアクセス許可は、次を参照してください。[権限](https://msdn.microsoft.com/library/mt203953/#Permissions)CREATE TABLE でします。 
  
<a name="general-remarks-bk"></a>
  
## <a name="general-remarks"></a>全般的な解説
詳細については、「[全般的な解説](https://msdn.microsoft.com/library/mt203953/#GeneralRemarks)CREATE TABLE でします。

<a name="limitations-bk"></a>

## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
Azure SQL Data Warehouse では、サポートの自動作成] または [統計の更新を自動まだされていません。  クエリから最高のパフォーマンスを取得するためには、CTAS を実行した後、およびデータに大幅な変更が加えられた後は、統計をすべてのテーブルのすべての列を作成する必要があります。 詳細については、「 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)」をご覧ください。

[SET ROWCOUNT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-rowcount-transact-sql.md) CTAS で影響を与えません。 同様の動作を実現するために使用[TOP &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
 
詳細については、「[制限事項と制約](https://msdn.microsoft.com/library/mt203953/#LimitationsRestrictions)CREATE TABLE でします。

<a name="locking-behavior-bk"></a>
  
## <a name="locking-behavior"></a>ロック動作  
 詳細については、「[ロック動作](https://msdn.microsoft.com/library/mt203953/#LockingBehavior)CREATE TABLE でします。
 
<a name="performance-bk"></a>
 
 ## <a name="performance"></a>パフォーマンス 

ハッシュ分散のテーブルの結合と集計のパフォーマンスの向上を実現するために別の配布の列を選択するのに CTAS を使用することができます。 異なるディストリビューション列が目標ではないを選択する場合は、行を再配布これを回避するために、同じディストリビューション列を指定する場合 CTAS パフォーマンスを最適になります。 

指定するかどうかは、CTAS を使用してテーブルを作成して、パフォーマンスは、要素ではありません、`ROUND_ROBIN`ディストリビューション列を決定するしなくても済むようにします。

後続のクエリでデータ移動を避けるためを指定できます`REPLICATE`が増加する記憶域をすべての計算ノード上のテーブルの完全なコピーを読み込むためが欠点です。  


<a name="examples-copy-table-bk"></a>

## <a name="examples-for-copying-a-table"></a>テーブルをコピーするための例

<a name="ctas-copy-table-bk"></a>

### <a name="a-use-ctas-to-copy-a-table"></a>A. CTAS を使用してテーブルをコピーするには 
対象: Azure SQL Data Warehouse と並列データ ウェアハウス

などの最も一般的なのいずれかを使用して`CTAS`DDL を変更することができるように、テーブルのコピーの作成です。 たとえば作成していた場合、テーブルとして`ROUND_ROBIN`としますが、列の分散テーブルを変更しましょう`CTAS`ディストリビューション列を変更する方法は、します。 `CTAS`パーティション分割、インデックス、または列の型を変更するも使用できます。

既定値の分布タイプを使用してこのテーブルを作成したとしましょう`ROUND_ROBIN`分散でディストリビューション列が指定されなかったので、`CREATE TABLE`です。

```sql
CREATE TABLE FactInternetSales
(
    ProductKey int NOT NULL,
    OrderDateKey int NOT NULL,
    DueDateKey int NOT NULL,
    ShipDateKey int NOT NULL,
    CustomerKey int NOT NULL,
    PromotionKey int NOT NULL,
    CurrencyKey int NOT NULL,
    SalesTerritoryKey int NOT NULL,
    SalesOrderNumber nvarchar(20) NOT NULL,
    SalesOrderLineNumber tinyint NOT NULL,
    RevisionNumber tinyint NOT NULL,
    OrderQuantity smallint NOT NULL,
    UnitPrice money NOT NULL,
    ExtendedAmount money NOT NULL,
    UnitPriceDiscountPct float NOT NULL,
    DiscountAmount float NOT NULL,
    ProductStandardCost money NOT NULL,
    TotalProductCost money NOT NULL,
    SalesAmount money NOT NULL,
    TaxAmt money NOT NULL,
    Freight money NOT NULL,
    CarrierTrackingNumber nvarchar(25),
    CustomerPONumber nvarchar(25)
);
```

クラスター化列ストア テーブルのパフォーマンスの利用できるように、クラスター化列ストア インデックスを持つこのテーブルの新しいコピーを作成するようになりました。 また、この列に結合を予測するために、ProductKey でこのテーブルを配布するし、ProductKey 上の結合時にデータの移動を回避します。 最後にも追加する OrderDateKey パーティション分割できるように、古いパーティションを削除することにより簡単に古いデータを削除できます。 新しいテーブルに、古いテーブルのコピーは、CTAS ステートメントを次に示します。

```sql
CREATE TABLE FactInternetSales_new
WITH
(
    CLUSTERED COLUMNSTORE INDEX,
    DISTRIBUTION = HASH(ProductKey),
    PARTITION
    (
        OrderDateKey RANGE RIGHT FOR VALUES
        (
        20000101,20010101,20020101,20030101,20040101,20050101,20060101,20070101,20080101,20090101,
        20100101,20110101,20120101,20130101,20140101,20150101,20160101,20170101,20180101,20190101,
        20200101,20210101,20220101,20230101,20240101,20250101,20260101,20270101,20280101,20290101
        )
    )
)
AS SELECT * FROM FactInternetSales;
```

最後に、新しいテーブルでスワップしてから、古いテーブルを削除するテーブルの名前を変更することができます。

```sql
RENAME OBJECT FactInternetSales TO FactInternetSales_old;
RENAME OBJECT FactInternetSales_new TO FactInternetSales;

DROP TABLE FactInternetSales_old;
```

<a name="examples-column-bk"></a>

## <a name="examples-for-column-options"></a>列のオプションの例

<a name="ctas-change-column-attributes-bk"></a>

### <a name="b-use-ctas-to-change-column-attributes"></a>B. CTAS を使用して、列属性を変更するには 
対象: Azure SQL Data Warehouse と並列データ ウェアハウス

この例では、CTAS を使用して、データ型、null 値許容属性、および DimCustomer2 テーブル内の複数の列の照合順序を変更します。  
  
```  
-- Original table 
CREATE TABLE [dbo].[DimCustomer2] (  
    [CustomerKey] int NOT NULL,  
    [GeographyKey] int NULL,  
    [CustomerAlternateKey] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL  
)  
WITH (CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH([CustomerKey]));  
  
-- CTAS example to change data types, nullability, and column collations  
CREATE TABLE test  
WITH (HEAP, DISTRIBUTION = ROUND_ROBIN)  
AS  
SELECT  
    CustomerKey AS CustomerKeyNoChange,  
    CustomerKey*1 AS CustomerKeyChangeNullable,  
    CAST(CustomerKey AS DECIMAL(10,2)) AS CustomerKeyChangeDataTypeNullable,  
    ISNULL(CAST(CustomerKey AS DECIMAL(10,2)),0) AS CustomerKeyChangeDataTypeNotNullable,  
    GeographyKey AS GeographyKeyNoChange,  
    ISNULL(GeographyKey,0) AS GeographyKeyChangeNotNullable,  
    CustomerAlternateKey AS CustomerAlternateKeyNoChange,  
    CASE WHEN CustomerAlternateKey = CustomerAlternateKey 
        THEN CustomerAlternateKey END AS CustomerAlternateKeyNullable,  
    CustomerAlternateKey COLLATE Latin1_General_CS_AS_KS_WS AS CustomerAlternateKeyChangeCollation  
FROM [dbo].[DimCustomer2]  
  
-- Resulting table 
CREATE TABLE [dbo].[test] (
    [CustomerKeyNoChange] int NOT NULL, 
    [CustomerKeyChangeNullable] int NULL, 
    [CustomerKeyChangeDataTypeNullable] decimal(10, 2) NULL, 
    [CustomerKeyChangeDataTypeNotNullable] decimal(10, 2) NOT NULL, 
    [GeographyKeyNoChange] int NULL, 
    [GeographyKeyChangeNotNullable] int NOT NULL, 
    [CustomerAlternateKeyNoChange] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL, 
    [CustomerAlternateKeyNullable] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NULL, 
    [CustomerAlternateKeyChangeCollation] nvarchar(15) COLLATE Latin1_General_CS_AS_KS_WS NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN);
```
 
最後の手順として行うこともできます[名前の変更 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/rename-transact-sql.md)テーブル名を切り替えるには。 これにより、新しいテーブルを指定する DimCustomer2 です。

```
RENAME OBJECT DimCustomer2 TO DimCustomer2_old;
RENAME OBJECT test TO DimCustomer2;

DROP TABLE DimCustomer2_old;
```

<a name="examples-table-distribution-bk"></a>

## <a name="examples-for-table-distribution"></a>テーブルの配布の例

<a name="ctas-change-distribution-method-bk"></a>

### <a name="c-use-ctas-to-change-the-distribution-method-for-a-table"></a>C. CTAS を使用して、テーブルの配布方法を変更するには
対象: Azure SQL Data Warehouse と並列データ ウェアハウス

この簡単な例は、テーブルの配布方法を変更する方法を示しています。 これを行う方法のしくみを表示するには、ラウンド ロビンをハッシュ分散テーブルが変更され、分散ハッシュに戻るラウンド ロビン テーブルを変更します。 最終的なテーブルでは、元のテーブルと一致します。 

ほとんどの場合は、ラウンド ロビン テーブルにハッシュ分散テーブルを変更する必要はありません。 多くの場合、ハッシュ分散テーブルにラウンド ロビン テーブルを変更する必要があります。 たとえば、ラウンド ロビン方式として新しいテーブルを最初に読み込むように、し、後で結合のパフォーマンスを向上させるハッシュ分散テーブルに移動してください。

この例では、AdventureWorksDW サンプル データベースを使用します。 SQL データ ウェアハウスのバージョンを読み込むには、次を参照してください[SQL Data Warehouse にサンプル データを読み込む。](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-load-sample-databases/)
 
```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a round-robin table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];

```  
次に、ハッシュ分散テーブルに変更します。

```
-- You just made DimSalesTerritory a round-robin table.
-- Change it back to the original hash-distributed table. 
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH(SalesTerritoryKey) 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
<a name="ctas-change-to-replicated-bk"></a>

### <a name="d-use-ctas-to-convert-a-table-to-a-replicated-table"></a>D. CTAS を使用してレプリケートされたテーブルにテーブルを変換するには  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス 

この例は、レプリケートされたテーブルにラウンド ロビンまたはハッシュ分散テーブルへの変換に適用されます。 この例は、ディストリビューションの種類をさらに一歩を変更する前のメソッドを受け取ります。  DimSalesTerritory がディメンションと可能性がありますより小さいテーブルであるために、他のテーブルに結合する際に、データ移動を回避するレプリケートされると、テーブルを再作成できます。 

```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a replicated table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = REPLICATE 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
### <a name="e-use-ctas-to-create-a-table-with-fewer-columns"></a>E. CTAS を使用して、列数が少ないテーブルを作成するには
対象: Azure SQL Data Warehouse と並列データ ウェアハウス 

次の例では、という名前のラウンドロビン分散テーブル`myTable (c, ln)`です。 新しいテーブルには、2 つの列のみにします。 列の名前、SELECT ステートメントで列の別名を使用します。  
  
```  
CREATE TABLE myTable  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT CustomerKey AS c, LastName AS ln  
    FROM dimCustomer;  
  
```  

<a name="examples-query-hints-bk"></a>

## <a name="examples-for-query-hints"></a>クエリ ヒントの例

<a name="ctas-query-hint-bk"></a>

### <a name="f-use-a-query-hint-with-create-table-as-select-ctas"></a>F. 作成するテーブルとの間でのクエリ ヒントを使用する (CTAS) を選択します。  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス
  
このクエリは、CTAS ステートメントを使用してクエリの結合ヒントを使用するための基本構文を示しています。 クエリが送信されると、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]各個 々 の配布のクエリ プランを生成するときに、ハッシュ結合の方法を適用します。 ハッシュ結合のクエリ ヒントの詳細については、次を参照してください。 [OPTION 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
CREATE TABLE dbo.FactInternetSalesNew  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN   
  )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  

<a name="examples-external-tables"></a>

## <a name="examples-for-external-tables"></a>外部テーブルの例

<a name="ctas-azure-blob-storage-bk"></a>

### <a name="g-use-ctas-to-import-data-from-azure-blob-storage"></a>G. CTAS を使用して Azure Blob ストレージからデータをインポートするには  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス  

外部テーブルからデータをインポートするには、だけで作成表を使用する AS 外部テーブルからを選択します。 外部テーブルからデータを選択するための構文[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]は通常のテーブルからデータを選択するための構文と同じです。  
  
 次の例では、Azure blob ストレージ アカウント内のデータに対して、外部テーブルを定義します。 使用して、テーブルとして選択の作成、外部テーブルからを選択します。 これには、Azure blob ストレージのテキスト区切りファイルからデータをインポートされ、新しいデータを格納[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]テーブル。  
  
```  
--Use your own processes to create the text-delimited files on Azure blob storage.  
--Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION='/logs/clickstream/2015/',  
    DATA_SOURCE = MyAzureStorage,  
    FILE_FORMAT = TextFileFormat)  
;  
  
--Use CREATE TABLE AS SELECT to import the Azure blob storage data into a new   
--SQL Data Warehouse table called ClickStreamData  
CREATE TABLE ClickStreamData   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;  
```  

<a name="ctas-import-Hadoop-bk"></a>
  
### <a name="h-use-ctas-to-import-hadoop-data-from-an-external-table"></a>H. CTAS を使用して、外部テーブルから Hadoop のデータをインポートするには  
適用されます。[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
外部テーブルからデータをインポートするには、だけで作成表を使用する AS 外部テーブルからを選択します。 外部テーブルからデータを選択するための構文[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]は通常のテーブルからデータを選択するための構文と同じです。  
  
 次の例では、Hadoop クラスター上、外部テーブルを定義します。 使用して、テーブルとして選択の作成、外部テーブルからを選択します。 これには、Hadoop テキスト区切りファイルからデータをインポートされ、新しいデータを格納[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]テーブル。  
  
```  
-- Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION = 'hdfs://MyHadoop:5000/tpch1GB/employee.tbl',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|')  
)  
;  
  
-- Use your own processes to create the Hadoop text-delimited files 
-- on the Hadoop Cluster.  
  
-- Use CREATE TABLE AS SELECT to import the Hadoop data into a new 
-- table called ClickStreamPDW  
CREATE TABLE ClickStreamPDW   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;   
```  
 
<a name="examples-workarounds-bk"></a>
 
## <a name="examples-using-ctas-to-replace-sql-server-code"></a>CTAS を使用して、SQL Server のコードを置換する例

いくつかサポートされていない機能を回避するには、CTAS を使用します。 データ ウェアハウスで、コードを実行できるだけでなく、CTAS を使用する既存のコードの書き直し通常パフォーマンスが向上します。 これは、完全に並列化された設計の結果です。 

> [!NOTE]
> 考えてみてください"CTAS 最初"です。 使用して、問題を解決できると思われる場合`CTAS`しする場合は、一般に対処する最善の方法でもより多くのデータを記述するためです。
>

<a name="ctas-replace-select-into-bk"></a>

### <a name="i-use-ctas-instead-of-selectinto"></a>I. CTAS を使用して、選択ではなく.に  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス

SQL Server のコードは、通常、SELECT を使用.INTO テーブルの SELECT ステートメントの結果に設定することです。 これは、SQL Server SELECT の例です.INTO ステートメントです。

```sql
SELECT *
INTO    #tmp_fct
FROM    [dbo].[FactInternetSales]
```

この構文は SQL Data Warehouse と Parallel Data Warehouse でサポートされていません。 この例は、以前の選択を書き換える方法を示しています.CTAS ステートメントとしてステートメントです。 CTAS の構文では説明されている配布オプションのいずれかを選択できます。 この例では、ROUND_ROBIN 配布方法を使用します。

```sql
CREATE TABLE #tmp_fct
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
AS
SELECT  *
FROM    [dbo].[FactInternetSales]
;
```

<a name="ctas-replace-implicit-joins-bk"></a>

### <a name="j-use-ctas-and-implicit-joins-to-replace-ansi-joins-in-the-from-clause-of-an-update-statement"></a>J. CTAS と暗黙の結合に ANSI 結合の置換を使用して、`FROM`の句、`UPDATE`ステートメント  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス  

一緒に ANSI 結合構文を使用して更新または削除を実行する 2 つ以上のテーブルを結合する複雑な更新があることがあります。

このテーブルを更新する必要がありました想像してください。

```sql
CREATE TABLE [dbo].[AnnualCategorySales]
(   [EnglishProductCategoryName]    NVARCHAR(50)    NOT NULL
,   [CalendarYear]                  SMALLINT        NOT NULL
,   [TotalSalesAmount]              MONEY           NOT NULL
)
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
;
```

次のように、元のクエリが説明しました。

```sql
UPDATE  acs
SET     [TotalSalesAmount] = [fis].[TotalSalesAmount]
FROM    [dbo].[AnnualCategorySales]     AS acs
JOIN    (
        SELECT  [EnglishProductCategoryName]
        ,       [CalendarYear]
        ,       SUM([SalesAmount])              AS [TotalSalesAmount]
        FROM    [dbo].[FactInternetSales]       AS s
        JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
        JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
        JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
        JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
        WHERE   [CalendarYear] = 2004
        GROUP BY
                [EnglishProductCategoryName]
        ,       [CalendarYear]
        ) AS fis
ON  [acs].[EnglishProductCategoryName]  = [fis].[EnglishProductCategoryName]
AND [acs].[CalendarYear]                = [fis].[CalendarYear]
;
```

結合を ANSI SQL データ ウェアハウスがサポートされていないため、`FROM`の句、`UPDATE`ステートメントでは、少し変更することがなく経由では、この SQL Server コードを使用することはできません。

組み合わせを使用することができます、`CTAS`と暗黙の結合にこのコードを置き換えます。

```sql
-- Create an interim table
CREATE TABLE CTAS_acs
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT  ISNULL(CAST([EnglishProductCategoryName] AS NVARCHAR(50)),0)    AS [EnglishProductCategoryName]
,       ISNULL(CAST([CalendarYear] AS SMALLINT),0)                      AS [CalendarYear]
,       ISNULL(CAST(SUM([SalesAmount]) AS MONEY),0)                     AS [TotalSalesAmount]
FROM    [dbo].[FactInternetSales]       AS s
JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
WHERE   [CalendarYear] = 2004
GROUP BY
        [EnglishProductCategoryName]
,       [CalendarYear]
;

-- Use an implicit join to perform the update
UPDATE  AnnualCategorySales
SET     AnnualCategorySales.TotalSalesAmount = CTAS_ACS.TotalSalesAmount
FROM    CTAS_acs
WHERE   CTAS_acs.[EnglishProductCategoryName] = AnnualCategorySales.[EnglishProductCategoryName]
AND     CTAS_acs.[CalendarYear]               = AnnualCategorySales.[CalendarYear]
;

--Drop the interim table
DROP TABLE CTAS_acs
;
```

<a name="ctas-replace-ansi-joins-bk"></a>

### <a name="k-use-ctas-to-specify-which-data-to-keep-instead-of-using-ansi-joins-in-the-from-clause-of-a-delete-statement"></a>K. CTAS を使用して、DELETE ステートメントの FROM 句で ANSI を使用する代わりに保持するデータの結合の指定  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス  

使用してデータを削除するための最善の方法があります`CTAS`です。 単にデータを削除するのではなく、残しておきたいデータを選択します。 この特に`DELETE`ansi で結合を SQL Data Warehouse では、ANSI をサポートしていないため、結合の構文を使用するステートメント、`FROM`の句、`DELETE`ステートメントです。

変換された DELETE ステートメントの例は、下入手できます。

```sql
CREATE TABLE dbo.DimProduct_upsert
WITH
(   Distribution=HASH(ProductKey)
,   CLUSTERED INDEX (ProductKey)
)
AS -- Select Data you wish to keep
SELECT     p.ProductKey
,          p.EnglishProductName
,          p.Color
FROM       dbo.DimProduct p
RIGHT JOIN dbo.stg_DimProduct s
ON         p.ProductKey = s.ProductKey
;

RENAME OBJECT dbo.DimProduct        TO DimProduct_old;
RENAME OBJECT dbo.DimProduct_upsert TO DimProduct;
```

<a name="ctas-simplify-merge-bk"></a>

### <a name="l-use-ctas-to-simplify-merge-statements"></a>L. CTAS を使用して、merge ステートメントを簡略化  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス  

Merge ステートメントで置換できる、少なくとも一部を使用して`CTAS`です。 統合することができます、`INSERT`と`UPDATE`単一のステートメントにします。 削除されたレコードは、オフ、2 番目のステートメントで終了する必要があります。

例、`UPSERT`は以下を使用します。

```sql
CREATE TABLE dbo.[DimProduct_upsert]
WITH
(   DISTRIBUTION = HASH([ProductKey])
,   CLUSTERED INDEX ([ProductKey])
)
AS
-- New rows and new versions of rows
SELECT      s.[ProductKey]
,           s.[EnglishProductName]
,           s.[Color]
FROM      dbo.[stg_DimProduct] AS s
UNION ALL  
-- Keep rows that are not being touched
SELECT      p.[ProductKey]
,           p.[EnglishProductName]
,           p.[Color]
FROM      dbo.[DimProduct] AS p
WHERE NOT EXISTS
(   SELECT  *
    FROM    [dbo].[stg_DimProduct] s
    WHERE   s.[ProductKey] = p.[ProductKey]
)
;

RENAME OBJECT dbo.[DimProduct]          TO [DimProduct_old];
RENAME OBJECT dbo.[DimpProduct_upsert]  TO [DimProduct];

```

<a name="ctas-data-type-and-nullability-bk"></a>

### <a name="m-explicitly-state-data-type-and-nullability-of-output"></a>M. データ型を明示的に状態と出力の null 値許容属性  
対象: Azure SQL Data Warehouse と並列データ ウェアハウス  

SQL Server のコードを SQL Data Warehouse に移行したときにこの種類のコーディング パターンの間で実行することがあります。

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE result
(result DECIMAL(7,2) NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN)

INSERT INTO result
SELECT @d*@f
;
```

本能、CTAS にこのコードを移行する必要があります。 また正しいはすると思われる場合があります。 ただし、ここで非表示の問題があります。

次のコードでは、同じ結果を生成しません。

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455
;

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT @d*@f as result
;
```

「結果」列が式のデータ型と null 許可属性の値で実行フォワードことに注意してください。 これは、注意が必要でない場合、値の微妙な差異に可能性があります。

例として、次を試してください。

```sql
SELECT result,result*@d
from result
;

SELECT result,result*@d
from ctas_r
;
```

格納されている結果の値が異なるです。 結果列に永続化された値が他の式で使用されるので、エラーは、さらに大きなになります。

![CREATE TABLE AS SELECT results](../../t-sql/statements/media/create-table-as-select-results.png)

これは、データ移行のため特に重要です。 2 番目のクエリはより正確な記述しても問題があります。 データが異なることが、ソース システムと比較して、移行での整合性の質問につながります。 これは、「が正しくありません」の応答が実際には右側の 1 つをそれらのまれなケースのいずれかです。

2 つの結果の間でこのような違いが見理由は、暗黙的な型キャストまでです。 最初の例では、テーブルは、列定義を定義します。 行が挿入されたときに、暗黙的な型変換が発生します。 2 番目の例ではありません暗黙の型変換式、列のデータ型を定義します。 また一方、最初の例でことはできませんがある 2 番目の例では、列を null 許容の列として定義されていることに注意してください。 テーブルが、最初の例の列の null 値で作成されたときを明示的に定義されました。 2 番目のだけ残さ式および既定でこの例は、NULL 定義になります。  

これらの問題を解決する必要があります明示的に設定する型変換とで null 値許容属性、`SELECT`の部分、`CTAS`ステートメントです。 作成するテーブルの部分では、これらのプロパティを設定できません。

次の例では、コードを修正する方法を示します。

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT ISNULL(CAST(@d*@f AS DECIMAL(7,2)),0) as result
```

次のことを考慮してください。
- CAST または CONVERT を使用できた
- COALESCE ではない null 許容属性を強制的に ISNULL を使用します。
- ISNULL は最も外側の関数
- ISNULL の 2 番目の部分は、定数つまり 0

> [!NOTE]
> 正しく設定される null 値許容属性が使用する重要`ISNULL`および not`COALESCE`です。 `COALESCE`決定的関数ではないため、式の結果には null 値が必ず. `ISNULL`異なります。 これは、決定的です。 そのためときの 2 番目の部分、`ISNULL`関数は、定数またはリテラルは、結果の値は NOT NULL します。

このヒントは、計算の結果の整合性の確保に役立つだけではありません。 テーブル パーティション切り替え用に重要です。 ファクトとして定義されているこのテーブルがある場合を想像してください。

```sql
CREATE TABLE [dbo].[Sales]
(
    [date]      INT     NOT NULL
,   [product]   INT     NOT NULL
,   [store]     INT     NOT NULL
,   [quantity]  INT     NOT NULL
,   [price]     MONEY   NOT NULL
,   [amount]    MONEY   NOT NULL
)
WITH
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101,20020101
                    ,20030101,20040101,20050101
                    )
                )
)
;
```

ただし、値フィールドは、ソース データの一部ではない計算式です。

こうことができます、パーティション分割されたデータセットを作成します。

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   [quantity]*[price]  AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create')
;
```

クエリは、適切に機能が実行されます。 この問題は、partition switch を実行しようとするときに得られます。 テーブルの定義が一致しません。 テーブルの定義を CTAS を一致させるには、変更する必要があります。

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   ISNULL(CAST([quantity]*[price] AS MONEY),0) AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create');
```

そのため、型の整合性と、CTAS で null 値許容プロパティを維持するがわかりますエンジニア リング最適なことをお勧めします。 計算の結果の整合性を維持するのに役立ち、パーティションの切り替えができるようになります。
 
## <a name="see-also"></a>参照  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [EXTERNAL TABLE AS SELECT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [TABLE &#40; を作成します。Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) [TABLE &#40; を削除TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [外部テーブル &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-external-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER EXTERNAL TABLE &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/4ae1b23c-67f6-41d0-b614-7a8de914d145)  
  
  


