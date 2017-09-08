---
title: "手順 6: 運用モデル |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b33f3876f054d7e7150a18967d5cfa37dd2d82bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="step-6-operationalize-the-model"></a>手順 6: モデルを運用する

この手順で学習する*運用*モデルをトレーニングして、前の手順で保存します。 ここでは「スコアリングのためには、実稼働環境にモデルの配置」手段を使用できるようにします。 ストアド プロシージャに、Python コードが含まれている場合に簡単です。 予測を行う新しい観測上のアプリケーションからストアド プロシージャを呼び出すことができます。

ストアド プロシージャから Python モデルを呼び出すための 2 つのメソッドをについて説明します。

- **一括スコア付けモード**: SELECT クエリを利用し、複数行のデータを提供します。 このストアド プロシージャは、入力ケースに対応する観察のテーブルを返します。
- **個別スコア付けモード**: 個々のパラメーター セットを入力として渡します。  このストアド プロシージャは、1 つの行または値を返します。

## <a name="scoring-using-the-scikit-learn-model"></a>Scikit を使用してスコア付けのモデルの学習

ストアド プロシージャ_PredictTipSciKitPy_ scikit を使用して、モデルを学習します。 このストアド プロシージャは、ストアド プロシージャ内の Python 予測呼び出しをラップするための基本構文を示しています。

- 使用するモデルの名前は、ストアド プロシージャへの入力パラメーターとして提供されます。 
- ストアド プロシージャは、データベース テーブルからシリアル化されたモデルを読み込むし`nyc_taxi_models`.table、ストアド プロシージャで SELECT ステートメントを使用します。
- シリアル化されたモデルが Python 変数に格納されている`mod`Python を使用してさらに処理します。
- スコアを付ける必要がある新しいケースがから取得した、[!INCLUDE[tsql](../../includes/tsql-md.md)]で指定されたクエリ`@input_data_1`です。 クエリ データが読み取られると、行が既定のデータ フレーム `InputDataSet`に保存されます。
- このデータ フレームに渡される、`predict_proba`ロジスティック回帰モデルの関数`mod`scikit を使用することで作成された-モデルを学習します。 
- `predict_proba`関数 (`probArray = mod.predict_proba(X)`) を返します、 **float** (任意の量) のヒントが指定される確率を表すです。
- また、ストアド プロシージャには、精度メトリック、AUC (曲線の下の領域) が計算されます。 AUC などの精度の基準は、先のラベル (つまり、先端がの列) を提供する場合にのみ生成できます。 予測では、先のラベルは必要はありません (変数`y`)、正確性メトリックの計算が、します。

  そのため、スコアを付けるデータのターゲットのラベルを持っていない場合、AUC 計算を削除するストアド プロシージャを変更して単純に、機能からヒント確率を返す (変数`X`ストアド プロシージャで)。

```SQL
CREATE PROCEDURE [dbo].[PredictTipSciKitPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
  EXEC sp_execute_external_script
    @language = N'Python',
    @script = N'
        import pickle;
        import numpy;
        import pandas;
        from sklearn import metrics
        
        mod = pickle.loads(lmodel2)
        
        X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
        y = numpy.ravel(InputDataSet[["tipped"]])
        
        probArray = mod.predict_proba(X)
        probList = []
        for i in range(len(probArray)):
          probList.append((probArray[i])[1])
        
        probArray = numpy.asarray(probList)
        fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
        aucResult = metrics.auc(fpr, tpr)
        print ("AUC on testing data is: " + str(aucResult))
        
        OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
        ',  
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="scoring-using-the-revoscalepy-model"></a>Revoscalepy モデルを使用してスコア付け

ストアド プロシージャ_PredictTipRxPy_を使用して作成されたモデルを使用して、 **revoscalepy**ライブラリです。 動作とほぼ同じ方法、 _PredictTipSciKitPy_手順がいくつかの変更を**revoscalepy**関数。

```SQL
CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict_ex(mod, X)
      probList = []
      for i in range(len(probArray._results["tipped_Pred"])):
        probList.append((probArray._results["tipped_Pred"][i]))
      
      probArray = numpy.asarray(probList)
      fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
      aucResult = metrics.auc(fpr, tpr)
      print ("AUC on testing data is: " + str(aucResult))
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',    
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="batch-scoring-using-a-select-query"></a>SELECT クエリを利用した一括スコア付け

ストアド プロシージャ**PredictTipSciKitPy**と**PredictTipRxPy** 2 つの入力パラメーターを必要とします。 

- スコアリングのためのデータを取得するクエリ
- トレーニング済みモデルの名前

このセクションでは、モデルとスコアリングに使用するデータの両方を簡単に変更するストアド プロシージャにこれらの引数を渡す方法を学習します。

1. 入力データを定義し、次のようにスコアリングのため、ストアド プロシージャを呼び出します。 この例は、スコア付けを PredictTipSciKitPy ストアド プロシージャを使用し、モデルの名前とクエリ文字列を渡します

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    ストアド プロシージャでは、入力したクエリの一部として渡された各トリップの予測確率を返します。 SSMS (SQL Server Management Studio) を使用して、クエリを実行する場合は、確率が内のテーブルとして表示されます、**結果**ウィンドウです。 **メッセージ**ウィンドウが約 0.56 の値を持つ精度メトリック (AUC または曲線の下の領域) を出力します。

2. 使用する、 **revoscalepy**スコア付けのモデル、ストアド プロシージャを呼び出す**PredictTipRxPy**モデル名およびクエリ文字列を渡して、します。

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="score-individual-rows-using-scikit-learn-model"></a>Scikit を使用して個々 の行をスコア付けのモデルの学習

場合によっては、バッチ スコアリング、代わりにする 1 つのケースで、アプリケーションからの値を取得し、これらの値に基づいて 1 つの結果を取得します。 たとえば、ストアド プロシージャを呼び出し、ユーザーが入力または選択した値を指定するように Excel ワークシート、Web アプリケーション、Reporting Services レポートを設定できます。

このセクションでは、ストアド プロシージャの呼び出しで 1 つの予測を作成する方法を学習します。

1. ストアド プロシージャのコードをレビューする分ほどかかる[PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy)と[PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy)ダウンロードの一部として含まれています。 これらのストアド プロシージャを使用、scikit-学習および revoscalepy モデルでは、次のようにスコアリングを実行し、。

  - モデルの名前および複数の単一の値は、入力として提供されます。 これらの入力には、座席数、トリップ距離などが含まれます。
  - テーブル値関数の場合、`fnEngineerFeatures`を入力値を受け取る、緯度と経度の距離を送信するために変換します。 [レッスン 4](sqldev-py4-create-data-features-using-t-sql.md)このテーブル値関数の説明が含まれています。
  - 外部アプリケーションからストアド プロシージャを呼び出す場合は、入力データが、必要な入力モデルの機能、Python と一致していることを確認します。 キャスト演算または Python のデータ型、または検証するデータ型とデータ長に入力データを変換する可能性があります。
  - ストアド プロシージャでは、保存された Python モデルに基づくスコアを作成します。

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

使用してスコア付けを実行するストアド プロシージャの定義をここでは、 **scikit-学習**モデル。

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeSciKitPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
  SELECT * FROM [dbo].[fnEngineerFeatures]( 
    @passenger_count,
    @trip_distance,
    @trip_time_in_secs,
    @pickup_latitude,
    @pickup_longitude,
    @dropoff_latitude,
    @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      probList = []
      probList.append((mod.predict_proba(X)[0])[1])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
    ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

### <a name="predicttipsinglemoderxpy"></a>PredictTipSingleModeRxPy

使用してスコア付けを実行するストアド プロシージャの定義をここでは、 **revoscalepy**モデル。

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures]( 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict_ex(mod, X)
      
      probList = []
      probList.append(probArray._results["tipped_Pred"])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

2.  これを試すに、新しく開きます**クエリ**ウィンドウ、および呼び出しストアド プロシージャ、特徴列の各パラメーターを入力します。

    ```SQL
    -- Call stored procedure PredictTipSingleModeSciKitPy to score using SciKit-Learn model
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    -- Call stored procedure PredictTipSingleModeRxPy to score using revoscalepy model
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```
    
    7 つの値は順序で、これらの機能列です。
    
    -   *passenger_count*
    -   *trip_distance*
    -   *trip_time_in_secs*
    -   *pickup_latitude*
    -   *pickup_longitude*
    -   *dropoff_latitude*
    -   *dropoff_longitude*

3. どちらの手順からの出力は、上記のパラメーターまたは機能でタクシー旅行の有料されるヒントの確率です。

## <a name="conclusions"></a>結論

このチュートリアルでは、ストアド プロシージャに埋め込まれた Python コードを操作する方法を学びました。 との統合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] Python 予測モデルの展開と企業データ ワークフローの一部として再トレーニング モデルに組み込むにはるかに簡単になります。

## <a name="previous-step"></a>前の手順
[手順 6: モデルを運用する](sqldev-py6-operationalize-the-model.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)

