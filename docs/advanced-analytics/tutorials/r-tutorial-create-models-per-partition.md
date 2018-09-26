---
title: 作成、トレーニング、および R (SQL Server Machine Learning Services) でのパーティションに基づくモデルのスコア付けのチュートリアル |Microsoft Docs
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: tutorial
ms.author: heidist
author: HeidiSteen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 51fd17b10ed2fde9d8412c6c47f868458edf7d5c
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715296"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>チュートリアル: SQL Server での R でのパーティションに基づくモデルを作成します。
[!INCLUDE[appliesto-ssvnex-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server の 2019 でパーティション ベースのモデルを作成し、パーティション分割されたデータに対してモデルをトレーニングする機能があります。 地理的リージョン、日付と時間、年齢や性別 - などの特定の分類のスキームに自然に分割する層化データのスクリプトを実行全体のデータ セットに対してモデル化、トレーニング、およびそのままのパーティションでスコア付けすることができます。これらすべての操作。 

2 つの新しいパラメーターを通じてパーティション ベースのモデルが有効になっている[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql):

+ **input_data_1_partition_by_columns**でパーティション分割する列を指定します。
+ **input_data_1_order_by_columns** order by 句に列を指定します。 

このチュートリアルでは、従来の NYC タクシーのサンプル データと R スクリプトを使用してパーティション ベースのモデリングをについて説明します。 パーティション列は、支払い方法です。

> [!div class="checklist"]
> * Payment_type 列に基づいてパーティション。 この列セグメント データ、支払いの種類ごとに 1 つのパーティション内の値。
> * 作成し、各パーティションのモデルのトレーニングしデータベース オブジェクトに格納します。
> * 目的のために予約されているサンプル データを使用して、各パーティション モデル経由でのヒントの結果の確率を予測します。

## <a name="prerequisites"></a>前提条件
 
このチュートリアルを完了するには、次の操作が必要です。

+ Machine Learning サービスと R の機能で、SQL Server 2019 データベース エンジンのインスタンス
+ サンプル データ
+ SQL Server Management Studio などの T-SQL クエリ実行するためのツール

### <a name="system-resources"></a>システム リソース

データ セットが大きいと、トレーニング操作は、リソースを消費します。 可能であれば、少なくとも 8 GB の RAM を持つシステムを使用します。 または、小さいデータ セットを使用して、リソースの制約を回避することができます。 データ セットを縮小する手順については、インラインです。 

### <a name="sql-server-database-engine-with-machine-learning-services"></a>Machine Learning サービスでの SQL Server データベース エンジン

SQL Server 2019 CTP 2.0 以降をインストールおよび構成の Machine Learning サービスが必要です。 Management Studio でサーバーのバージョンを確認するにを実行して`SELECT @@Version`として T-SQL クエリ。 出力になります。"Microsoft SQL Server 2019 (CTP 2.0) - 15.0.x"。

### <a name="r-packages"></a>R パッケージ

このチュートリアルでは、Machine Learning サービスでインストールされている R を使用します。 データベース エンジンのインスタンスに現在インストールされているすべての R パッケージの適切な形式の一覧を返すことによって、R のインストールを確認できます。

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

### <a name="tools-for-query-execution"></a>クエリを実行するためのツール

できます[ダウンロードし、SQL Server Management Studio をインストール](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)、またはリレーショナル データベースに接続し、T-SQL スクリプトを実行する任意のツールを使用します。 Machine Learning サービスのあるデータベース エンジンのインスタンスに接続できることを確認します。

### <a name="sample-data"></a>サンプル データ

データの発生元、 [NYC タクシーのデータセットとリムジン委員会](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)パブリック データ セット。 

+ ダウンロード、 [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak )データベース バックアップ ファイルとデータベース エンジンのインスタンスに復元します。

データベース ファイル名にする必要があります**NYCTaxi_sample**まま変更せずに、次のスクリプトを実行する場合。

## <a name="connect-to-the-database"></a>データベースへの接続します。

Management Studio を起動し、データベース エンジンのインスタンスに接続します。 オブジェクト エクスプ ローラーで確認、 [NYCTaxi_Sample データベース](sqldev-download-the-sample-data.md)存在します。 

## <a name="create-calculatedistance"></a>CalculateDistance を作成します。

デモ データベースのテーブル値関数の計算の距離がストアド プロシージャの動作より優れたスカラー関数が付属します。 次のスクリプト作成を実行、 **CalculateDistance**で使用される関数、[トレーニング手順](#training-step)後でします。

関数が作成されたことを確認するには、\Programmability\Functions\Table-valued 関数を確認してください、 **NYCTaxi_Sample**オブジェクト エクスプ ローラーでデータベース。

```sql
USE NYCTaxi_sample
GO

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE FUNCTION [dbo].[CalculateDistance] (
    @Lat1 FLOAT
    ,@Long1 FLOAT
    ,@Lat2 FLOAT
    ,@Long2 FLOAT
    )
    -- User-defined function calculates the direct distance between two geographical coordinates.
RETURNS TABLE
AS
RETURN

SELECT COALESCE(3958.75 * ATAN(SQRT(1 - POWER(t.distance, 2)) / nullif(t.distance, 0)), 0) AS direct_distance
FROM (
    VALUES (CAST((SIN(@Lat1 / 57.2958) * SIN(@Lat2 / 57.2958)) + (COS(@Lat1 / 57.2958) * COS(@Lat2 / 57.2958) * COS((@Long2 / 57.2958) - (@Long1 / 57.2958))) AS DECIMAL(28, 10)))
    ) AS t(distance)
GO
 ```

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>プロシージャの作成とパーティションごとのモデルのトレーニングを定義します。

このチュートリアルでは、ストアド プロシージャで R スクリプトをラップします。 この手順では、R を使用して、入力データセットの作成、ヒントの結果を予測する分類モデルを構築して、データベースにモデルを保存するストアド プロシージャを作成します。

このスクリプトで使用されるパラメーターの入力、間が表示されます**input_data_1_partition_by_columns**と**input_data_1_order_by_columns**します。 これらのパラメーターは使用されるメカニズムは、モデリングをパーティション分割された取り消しが発生します。 入力として渡されたパラメーター [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)外部スクリプトの実行に 1 回のすべてのパーティションのパーティションの処理をします。 

このストアド プロシージャ、[並列処理を使用して、](#parallel)を完了するまでの時間を短縮します。

このスクリプトを実行した後ことがわかります**train_rxLogIt_per_partition** \Programmability\Stored 手順で、 **NYCTaxi_Sample**オブジェクト エクスプ ローラーでデータベース。 モデルを格納するために使用される新しいテーブルを表示する必要があります: **dbo.nyctaxi_models**します。

```sql
USE NYCTaxi_Sample
GO

CREATE
    OR

ALTER PROCEDURE [dbo].[train_rxLogIt_per_partition] (@input_query NVARCHAR(max))
AS
BEGIN
    DECLARE @start DATETIME2 = SYSDATETIME()
        ,@model_generation_duration FLOAT
        ,@model VARBINARY(max)
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name();

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    # Make sure InputDataSet is not empty. In parallel mode, if one thread gets zero data, an error occurs
    if (nrow(InputDataSet) > 0) {
    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    
    # build classification model to predict a tip outcome
    duration <- system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet))[3];

    # First, serialize a model to and put it into a database table
    modelbin <- as.raw(serialize(logitObj, NULL));

    # Create the data source. To reduce data size, add rowsPerRead=500000 to cut the dataset by half.
    ds <- RxOdbcData(table="ml_models", connectionString=connStr);

    # Store the model in the database
    model_name <- paste0("nyctaxi.", InputDataSet[1,]$payment_type);
    
    rxWriteObject(ds, model_name, modelbin, version = "v1",
    keyName = "model_name", valueName = "model_object", versionName = "model_version", overwrite = TRUE, serialize = FALSE);
    } 
    
    '
        ,@input_data_1 = @input_query
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@input_data_1_order_by_columns = N'passenger_count'
        ,@parallel = 1
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS NONE
END;
GO
```

<a name="parallel"></a>

### <a name="parallel-execution"></a>並列実行

注意、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)入力に含まれる **@parallel= 1**、並列処理を有効にするために使用します。 SQL Server 2019、設定で、以前のリリースとは異なり **@parallel= 1**ずっと高い確率で結果を並列実行を行うクエリ オプティマイザーより強力なヒントを提供します。

既定では、クエリ オプティマイザーは下で動作する傾向がある **@parallel= 1**場合を処理するこの明示的に設定が、256 個を超える行を持つテーブルで **@parallel= 1**これで示すようにスクリプトです。

> [!Tip]
> トレーニングの workoads を使用することができます**@parallel**任意のトレーニング スクリプトを使用しても含め、Microsoft rx ではないアルゴリズムを使用します。 通常、RevoScaleR のアルゴリズムのみ (rx プレフィックス) では、SQL Server のトレーニングのシナリオでの並列処理を提供します。 ただし、新しいパラメーターでその機能エンジニア リングは、オープン ソース R 関数を含む関数を呼び出すスクリプトを並列化できます。 これは、パーティションが特定のスレッド アフィニティに設定するため、特定のスレッドでのパーティションごとにスクリプトで呼び出されるすべての操作を実行するために機能します。

<a name="training-step"></a>

## <a name="run-the-procedure-and-train-the-model"></a>プロシージャを実行し、モデルのトレーニング

このセクションでは、スクリプトは、作成し、前の手順で保存したモデルをトレーニングします。 次の例は、モデルのトレーニングの 2 つの方法を示します。 データ セット全体または部分的なデータを使用します。 

この手順は、しばらく時間がかかるを期待してください。 トレーニングが完了する時間 (分) を取得、計算負荷ではありません。 特にメモリは、システム リソースが、負荷のための十分な場合は、データのサブセットを使用します。 2 番目の例では、構文を提供します。

```sql
--Example 1: train on entire dataset
EXEC train_rxLogIt_per_partition N'
SELECT payment_type, tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

```sql
--Example 2: Train on 20 percent of the dataset to expedite processing.
EXEC train_rxLogIt_per_partition N'
  SELECT tipped, payment_type, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample TABLESAMPLE (20 PERCENT) REPEATABLE (98074)
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

> [!NOTE]
> その他のワークロードを実行している場合は、追加`OPTION(MAXDOP 2)`たった 2 個のコアにクエリの処理を制限する場合は、SELECT ステートメントにします。

## <a name="check-results"></a>チェックの結果

モデルの表に、結果 5 つの支払いの種類によってセグメント化された 5 つのパーティションに基づいた、5 つの異なるモデルがあります。 モデルは、 **ml_models**データ ソース。

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>結果を予測するためのプロシージャを定義します。

スコア付けと同じパラメーターを使用できます。 次の例には、現在処理しているパーティションの適切なモデルを使用して、スコア付けする R スクリプトが含まれています。

同様に、R コードをラップするストアド プロシージャを作成します。

```sql
USE NYCTaxi_Sample
GO

-- Stored procedure that scores per partition. 
-- Depending on the partition being processed, a model specific to that partition will be used
CREATE
    OR

ALTER PROCEDURE [dbo].[predict_per_partition]
AS
BEGIN
    DECLARE @predict_duration FLOAT
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name()
        ,@input_query NVARCHAR(max);

    SET @input_query = 'SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance, payment_type
                          FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)
                          CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d'

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    if (nrow(InputDataSet) > 0) {

    #Get the partition that is currently being processed
    current_partition <- InputDataSet[1,]$payment_type;

    #Create the SQL query to select the right model
    query_getModel <- paste0("select model_object from ml_models where model_name = ", "''", "nyctaxi.",InputDataSet[1,]$payment_type,"''", ";")
    

    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
        
    #Define data source to use for getting the model
    ds <- RxOdbcData(sqlQuery = query_getModel, connectionString = connStr)

    # Load the model
    modelbin <- rxReadObject(ds, deserialize = FALSE)
    # unserialize model
    logitObj <- unserialize(modelbin);

    # predict tipped or not based on model
    predictions <- rxPredict(logitObj, data = InputDataSet, overwrite = TRUE, type = "response", writeModelVars = TRUE
        , extraVarsToWrite = c("payment_type"));        
    OutputDataSet <- predictions
    
    } else {
        OutputDataSet <- data.frame(integer(), InputDataSet[,]);        
    }
    '
        ,@input_data_1 = @input_query
        ,@parallel = 1
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS((
                tipped_Pred INT
                ,payment_type VARCHAR(5)
                ,tipped INT
                ,passenger_count INT
                ,trip_distance FLOAT
                ,trip_time_in_secs INT
                ,direct_distance FLOAT
                ));
END;
GO
```

## <a name="create-a-table-to-store-predictions"></a>予測を格納するテーブルを作成します。

```sql
CREATE TABLE prediction_results (
    tipped_Pred INT
    ,payment_type VARCHAR(5)
    ,tipped INT
    ,passenger_count INT
    ,trip_distance FLOAT
    ,trip_time_in_secs INT
    ,direct_distance FLOAT
    );

TRUNCATE TABLE prediction_results
GO
```

## <a name="run-the-procedure-and-save-predictions"></a>プロシージャを実行し、予測の保存

```sql
INSERT INTO prediction_results (
    tipped_Pred
    ,payment_type
    ,tipped
    ,passenger_count
    ,trip_distance
    ,trip_time_in_secs
    ,direct_distance
    )
EXECUTE [predict_per_partition]
GO
```

## <a name="view-predictions"></a>ビューの予測

予測が格納されるため、結果セットを返す単純なクエリを実行できます。

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>次の手順

このチュートリアルでは使用して[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)をパーティション分割されたデータの操作を反復処理します。 詳細のストアド プロシージャで外部のスクリプトを呼び出すことを確認し、次のチュートリアルでは、RevoScaleR 関数を使用して続行します。

> [!div class="nextstepaction"]
> [R と SQL Server チュートリアル](walkthrough-data-science-end-to-end-walkthrough.md)

<!--
## Old intro

**(Not for production workloads)**

One of the more common approaches for executing R or Python code on SQL data is providing script as an input parameter to the [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure. In this CTP release, SQL Server 2019 adds new parameters to `sp_execute_external_script` to process partitions with the external script executing once for every partition:

| Parameter | Usage |
|-----------|-------|
| **input_data_1_partition_by_columns** | Specifies which columns to partition by. |
| **input_data_1_order_by_columns** | Specifies which columns to order by.  |

Partitions are an organizational mechanism for stratified data that naturally segments into a given classification scheme. Common examples include partitioning by geographic region, by date and time, by age or gender, and so forth. Given the existence of partitioned data, you might want to execute script over the entire data set, with the ability to model, train, and score partitions that remain intact over all these operations. Calling `sp_execute_external_script` with the new parameters allows you to do just that.

You can run this operation in parallel by combining `partition_by` with `@parallel`. If the input query can be parallelized, set `@parallel=1` as part of your arguments to `sp_execute_external_script`. By default, the query optimizer operates under `@parallel=1` on tables having more than 256 rows.

When the scenario is training, one advantage is that any arbitrary training script, even those using non-Microsoft-rx algorithms, can be parallelized by also using the @parallel parameter. Typically, you would have to use RevoScaleR algorithms (with the rx prefix) to obtain parallelism in training scenarios in SQL Server. But with the new parameter, you can parallelize a script that calls functions not specifically engineered with that capability.
-->
