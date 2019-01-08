---
title: SQL Server Machine Learning の R モデルを使用して、レッスン 4 Predict の潜在的な結果
description: SQL Server で R スクリプトの埋め込みを運用化する方法を示すチュートリアルには、T-SQL 関数を使用したプロシージャが格納されています。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2b22d971764be99c5542c7cd8615c11ebb3e6cba
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644782"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>レッスン 4:ストアド プロシージャに埋め込まれた R を使用して予測を実行します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R を使用する方法に関する SQL 開発者向けのチュートリアルの一部です。

この手順では、新しい観測値に対してモデルを使用して、潜在的な結果を予測するについて説明します。 モデルは、他のアプリケーションで直接呼び出すことができるストアド プロシージャにラップされます。 このチュートリアルでは、スコアリングを実行するいくつかの方法を示しています。

- **バッチ スコアリング モード**:ストアド プロシージャへの入力として選択クエリを使用します。 このストアド プロシージャは、入力ケースに対応する観察のテーブルを返します。

- **個別スコアリング モード**:一連の個別のパラメーター値を入力として渡します。  このストアド プロシージャは、1 つの行または値を返します。

まず、一般的なスコア付け方法を見てみましょう。

## <a name="basic-scoring"></a>基本のスコア付け

ストアド プロシージャ**RxPredict**ストアド プロシージャで RevoScaleR rxPredict 呼び出しをラップするための基本的な構文を示しています。

```sql
CREATE PROCEDURE [dbo].[RxPredict] (@model varchar(250), @inquery nvarchar(max))
AS 
BEGIN 

DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);  
EXEC sp_execute_external_script @language = N'R',
  @script = N' 
    mod <- unserialize(as.raw(model)); 
    print(summary(mod)) 
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE); 
    str(OutputDataSet) 
    print(OutputDataSet) 
    ', 
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2 
  WITH RESULT SETS ((Score float));
END
GO
```

+ SELECT ステートメントは、データベースからシリアル化されたモデルを取得し、R 変数で、モデルを格納`mod`R を使用する処理を続行

+ スコア付けのための新しいケースがから取得した、[!INCLUDE[tsql](../../includes/tsql-md.md)]で指定されたクエリ`@inquery`、ストアド プロシージャの最初のパラメーター。 クエリ データが読み取られると、行が既定のデータ フレーム `InputDataSet`に保存されます。 このデータ フレームに渡される、 [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)関数[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)スコアを生成します。
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    data.frame には 1 つの行を含めることができるため、一括または 1 回のスコア付けに同じコードを利用できます。
  
+ によって返される値、`rxPredict`関数は、 **float**ドライバーが何らかの金額のヒントを取得する確率を表します。

## <a name="batch-scoring-a-list-of-predictions"></a>バッチ スコアリング (予測の一覧)

一般的なシナリオでは、バッチ モードで複数の観測値の予測を生成します。 この手順では、バッチ スコアリングのしくみを見てみましょう。

1.  使用する入力データの小さなセットを取得することで開始します。 このクエリは、予測に必要な乗客数とその他の機能を利用し、乗車の "上位 10" 一覧を作成します。
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **サンプルの結果**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. 呼び出されるストアド プロシージャを作成する**RxPredictBatchOutput**で[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。

    ```sql
    CREATE PROCEDURE [dbo].[RxPredictBatchOutput] (@model varchar(250), @inquery nvarchar(max))
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script 
      @language = N'R',
      @script = N'
        mod <- unserialize(as.raw(model));
        print(summary(mod))
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
        str(OutputDataSet)
        print(OutputDataSet)
      ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  変数にクエリ テキストを提供し、ストアド プロシージャにパラメーターとして渡します。

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
ストアド プロシージャは、一連の予測ごとの上位 10 個の乗車回数を表す値を返します。 ただし、上位の乗車回数が、乗客 1 名のドライバーがチップを受け取る可能性がない、比較的短い乗車距離、乗車ではも。
  

> [!TIP]
> 
> 「はいヒント」と「チップなし」の結果だけを取得するには、代わりには、予測の確率スコアを返すこともし、WHERE 句を適用する可能性があります、_スコア_「ヒントの可能性がある」としてスコアを分類する列の値または"可能性は低いヒント"、0.5 や 0.7 などのしきい値を使用します。 この手順はストアド プロシージャに含まれていませんが、導入は簡単です。

## <a name="single-row-scoring-of-multiple-inputs"></a>単一行が複数の入力のスコア付け

複数の入力値を渡すし、その値に基づいて 1 つの予測を取得する場合があります。 たとえば、Excel ワークシート、web アプリケーション、またはストアド プロシージャを呼び出すし、型指定された、またはそれらのアプリケーションからユーザーが選択の入力を指定する Reporting Services レポートを設定するでした。

このセクションでは、乗客数、乗車距離などの複数の入力を受け取るストアド プロシージャを使用して 1 つの予測を作成する方法について説明します。 ストアド プロシージャは、以前に保存された R モデルに基づいてスコアを作成します。
  
外部アプリケーションからストアド プロシージャを呼び出す場合は、データが、R モデルの要件と一致することを確認します。 場合によっては、入力データを R データ型にキャストまたは変換できなければなりません。あるいは、データ型やデータ長を検証する必要があります。 

1. ストアド プロシージャを作成する**RxPredictSingleRow**します。
  
    ```sql
    CREATE PROCEDURE [dbo].[RxPredictSingleRow] @model varchar(50), @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```

2. 手動で値を指定し、お試しください。
  
    新しく開きます**クエリ**ウィンドウ、および呼び出し、ストアド プロシージャの各パラメーターの値を指定します。 パラメーターは、モデルで使用される機能の列を表しが必要です。

    ```sql
    EXEC [dbo].[RxPredictSingleRow] @model = 'RxTrainLogit_model',
    @passenger_count = 1,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = -73.977303
    ```

    または、この短い方のサポートを使用して[ストアド プロシージャにパラメーター](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. 結果はチップを得る確率が低いことを示し (ゼロ) でこれらの上位 10 個の乗車距離が比較的短い、乗客 1 名の乗車すべてがあるためです。

## <a name="conclusions"></a>結論

これでチュートリアルは終わりです。 ストアド プロシージャに R コードを埋め込むには理解できたら、これで、独自のモデルを構築するためのこれらのプラクティスを拡張できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] との統合により、R モデルを展開して予測することと、企業データ ワークフローの一部としてモデルを組み込み、維持することが簡単になります。

## <a name="previous-lesson"></a>前のレッスン

[レッスン 3:トレーニングし、T-SQL を使用して R モデルの保存](sqldev-train-and-save-a-model-using-t-sql.md)
