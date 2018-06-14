---
title: レッスン 6 Predict 潜在的なを使用して結果 R モデル (SQL Server の Machine Learning) |Microsoft ドキュメント
description: SQL Server で R を埋め込む方法を示すチュートリアル ストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/08/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 32984626dfac11bd2465cb783c583f6b210f6b68
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249855"
---
# <a name="lesson-6-predict-potential-outcomes-using-an-r-model-in-a-stored-procedure"></a>レッスン 6: ストアド プロシージャで R モデルを使用して潜在的な結果を予測します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

この手順では、新しい観測に対してモデルを使用して潜在的な結果の予測を学習します。 モデルは、他のアプリケーションによって直接呼び出すことができるストアド プロシージャでラップされます。 このチュートリアルでは、スコア付けを実行するいくつかの方法を示しています。

- **バッチ モードのスコアリング**: ストアド プロシージャへの入力として選択クエリを使用します。 このストアド プロシージャは、入力ケースに対応する観察のテーブルを返します。

- **個別スコア付けモード**: 個々のパラメーター セットを入力として渡します。  このストアド プロシージャは、1 つの行または値を返します。

まず、一般的なスコア付け方法を見てみましょう。

## <a name="basic-scoring"></a>基本スコア付け

ストアド プロシージャ **PredictTip** は、ストアド プロシージャで予測呼び出しをラップする基本構文を示します。

```SQL
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max) 
AS 
BEGIN 
  
DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);  
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

+ SELECT ステートメントは、データベースからシリアル化されたモデルを取得し、R 変数に、モデルを格納`mod`R. を使用してさらに処理

+ スコアリングのための新しいケースがから取得した、[!INCLUDE[tsql](../../includes/tsql-md.md)]で指定されたクエリ`@inquery`、ストアド プロシージャの最初のパラメーターです。 クエリ データが読み取られると、行が既定のデータ フレーム `InputDataSet`に保存されます。 このデータ フレームに渡される、 [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)で機能[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)スコアが生成されます。
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    data.frame には 1 つの行を含めることができるため、一括または 1 回のスコア付けに同じコードを利用できます。
  
+ によって返される値、`rxPredict`関数は、 **float**ドライバーを任意の量のヒントを取得する確率を表すです。

## <a name="batch-scoring"></a>バッチ スコアリング

それでは一括スコア付けの動作を確認しましょう。

1.  まず、少量の入力データを用意します。 このクエリは、予測に必要な乗客数とその他の機能を利用し、乗車の "上位 10" 一覧を作成します。
  
    ```SQL
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **サンプルの結果**
    
    ```
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

    このクエリは、ストアド プロシージャへの入力として使用できる**PredictTipMode**ダウンロードの一部として指定します。

2. ストアド プロシージャのコードをレビューする分ほどかかる**PredictTipMode**で[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]です。

    ```SQL
    /****** Object:  StoredProcedure [dbo].[PredictTipMode]  ******/
    CREATE PROCEDURE [dbo].[PredictTipMode] @inquery nvarchar(max)
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
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

3.  変数にクエリ テキストを指定し、ストアド プロシージャにパラメーターとして渡します。

    ```SQL
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'

    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[PredictTip] @inquery = @query_string;
    ```
  
4. ストアド プロシージャでは、一連の上位 10 トリップの各予測を表す値を返します。 最上位のトリップもドライバーは、ヒントを取得する可能性がない、比較的短い形式のトリップ距離で単一乗客トリップです。
  

> [!TIP]
> 
> 「はいヒント」と「no ヒント」結果だけを返すのではなくした可能性があります、予測の確率のスコアを返すことも適用して WHERE 句を_スコア_「ヒントする可能性が」としてスコアを分類する列の値または"低いヒント"、0.5 または 0.7 などのしきい値の値を使用してください。 この手順はストアド プロシージャに含まれていませんが、導入は簡単です。

## <a name="single-row-scoring"></a>単一行のスコア付け

アプリケーションから個々の値を渡し、その値に基づいて 1 つの結果を得ることが望まれる場合もあります。 たとえば、ストアド プロシージャを呼び出し、ユーザーが入力または選択した値を指定するように Excel ワークシート、Web アプリケーション、Reporting Services レポートを設定できます。

このセクションでは、ストアド プロシージャを使用して 1 つの予測を作成する方法を学習します。

1. ストアド プロシージャのコードをレビューする分ほどかかる**PredictTipSingleMode**ダウンロードの一部として含まれています。
  
    ```SQL
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
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
  
    - このストアド プロシージャは、乗客数や走行距離など、複数の単一値を入力として取得します。
  
        外部アプリケーションからストアド プロシージャを呼び出す場合は、データが、R モデルの要件と一致することを確認します。 場合によっては、入力データを R データ型にキャストまたは変換できなければなりません。あるいは、データ型やデータ長を検証する必要があります。 
  
    -   このストアド プロシージャは、保存された R モデルに基づいてスコアを作成します。
  
2. 手動で値を指定し、お試しください。
  
    新しく開きます**クエリ**ウィンドウ、および各パラメーターの値を提供する、ストアド プロシージャの呼び出しです。 パラメーターは、モデルで使用される機能の列を表し、必要な。

    ```
    EXEC [dbo].[PredictTipSingleMode] @passenger_count = 0,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = 73.977303
    ```

    またはのサポートされているこの短い形式を使用して[ストアド プロシージャにパラメーター](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. 結果は、単一乗客のトリップ距離が比較的短い形式はすべてためのヒントを取得する確率が、これらのトップ 10 トリップで不足しているを示します。

## <a name="conclusions"></a>結論

これでチュートリアルは終わりです。 これで、ストアド プロシージャで R コードを埋め込むには既に学習した独自のモデルを作成ヒントに従えばを拡張できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] との統合により、R モデルを展開して予測することと、企業データ ワークフローの一部としてモデルを組み込み、維持することが簡単になります。

## <a name="previous-lesson"></a>前のレッスン

[レッスン 5: トレーニングおよび T-SQL を使用して R モデルを保存します。](../r/sqldev-train-and-save-a-model-using-t-sql.md)
