---
title: "手順 6: 運用 SQL Server を使用して、Python モデル |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: d69c5272f52dc77ff1027e1bc127f413ebd01d44
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="step-6-operationalize-the-python-model-using-sql-server"></a>手順 6: 運用 SQL Server を使用して、Python モデル

この記事では、チュートリアルのパート[SQL 開発者のためのデータベースでの Python analytics](sqldev-in-database-python-for-sql-developers.md)です。 

このステップでする方法を学習*運用*モデルをトレーニングして、前の手順で保存します。

このシナリオでは、使用は、スコアリングのためには、実稼働環境にモデルの配置を意味します。 SQL Server と統合できるためこのとても簡単ですがストアド プロシージャでの Python コードを埋め込むことができます。 新しい入力に基づき、モデルから予測を取得するには、アプリケーションからストアド プロシージャを呼び出すし、新しいデータを渡します。

このレッスンは、Python モデルに基づいて予測を作成するための 2 つの方法を示します。 バッチ スコアリング、と、1 行ずつをスコア付けします。

- **バッチ スコアリング:**複数行の入力データを提供する SELECT クエリを引数として、ストアド プロシージャに渡します。 結果は、観測値が、入力ケースに対応するテーブルです。
- **個々 のスコア付け:**一連の個別のパラメーター値を入力として渡します。  このストアド プロシージャは、1 つの行または値を返します。

スコアリングのために必要なすべての Python コードは、ストアド プロシージャの一部として提供されます。

| ストアド プロシージャの名前 | バッチまたは単一 | モデルのソース|
|----|----|----|
|PredictTipRxPy|バッチ (batch)| revoscalepy モデル|
|PredictTipSciKitPy|バッチ (batch) |scikit のモデルの学習|
|PredictTipSingleModeRxPy|1 つの行| revoscalepy モデル|
|PredictTipSingleModeSciKitPy|1 つの行| scikit のモデルの学習|

## <a name="batch-scoring"></a>バッチ スコアリング

最初の 2 つのストアド プロシージャは、ストアド プロシージャ内の Python 予測呼び出しをラップするための基本構文を示しています。 両方のストアド プロシージャでは、入力として、データのテーブルが必要です。

- 使用する正確なモデルの名前は、ストアド プロシージャへの入力パラメーターとして提供されます。 ストアド プロシージャが、データベース テーブルからシリアル化されたモデルを読み込んだ`nyc_taxi_models`.table、ストアド プロシージャで SELECT ステートメントを使用します。
- シリアル化されたモデルが Python 変数に格納されている`mod`Python を使用してさらに処理します。
- スコアを付ける必要がある新しいケースがから取得した、[!INCLUDE[tsql](../../includes/tsql-md.md)]で指定されたクエリ`@input_data_1`です。 クエリ データが読み取られると、行が既定のデータ フレーム `InputDataSet`に保存されます。
- 両方のストアド プロシージャから関数を使用して`sklearn`AUC (曲線の下の領域)、正確性メトリックを計算します。 AUC などの精度の基準は、先のラベルを提供する場合にのみ生成されます (、_先が_列)。 予測では、先のラベルは必要はありません (変数`y`)、正確性メトリックの計算が、します。

    そのため、スコアを付けるデータのターゲットのラベルを持っていない場合、AUC 計算を削除するストアド プロシージャを変更して、機能からヒント確率のみを返す (変数`X`ストアド プロシージャで)。

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

ストアド プロシージャが既に作成されている必要があります。 検出できない場合は、ストアド プロシージャを作成するのには、次の T-SQL ステートメントを実行します。

このストアド プロシージャには、scikit に基づいてモデルが必要です-そのパッケージに固有の関数を使用しているため、パッケージを説明します。

+ 入力を含むデータ フレームに渡される、`predict_proba`ロジスティック回帰モデルの関数`mod`です。 `predict_proba`関数 (`probArray = mod.predict_proba(X)`) を返します、 **float** (任意の量) のヒントが指定される確率を表すです。

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

### <a name="predicttiprxpy"></a>PredictTipRxPy

このストアド プロシージャは、同じ入力を使用してと以前のストアド プロシージャとスコアの同じ型を作成しますから関数を使用して、 **revoscalepy**機械学習の SQL Server に用意されているパッケージ。

> [!NOTE] 
> このストアド プロシージャのコードは、以前のリリース バージョンと revoscalepy パッケージへの変更を反映するように、RTM バージョンの間で若干変更されました。 参照してください、[変更](#changes)詳細については表。

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
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict(mod, X)
      prob_list = prob_array["tipped_Pred"].values 
      
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

## <a name="run-batch-scoring-using-a-select-query"></a>バッチ スコアリング SELECT クエリを使用して実行します。

ストアド プロシージャ**PredictTipSciKitPy**と**PredictTipRxPy** 2 つの入力パラメーターを必要とします。 

- スコアリングのためのデータを取得するクエリ
- トレーニング済みモデルの名前

ストアド プロシージャには、これらの引数を渡すことで、特定のモデルを選択またはスコア付けに使用するデータを変更できます。

1. 使用する、 **scikit-学習**スコア付けのモデル、ストアド プロシージャを呼び出す**PredictTipSciKitPy**モデル名を渡すこと、およびクエリ文字列を入力として。

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    ストアド プロシージャでは、入力したクエリの一部として渡された各トリップの予測確率を返します。 
    
    SSMS (SQL Server Management Studio) を使用して、クエリを実行する場合は、確率が内のテーブルとして表示されます、**結果**ウィンドウです。 **メッセージ**ウィンドウが約 0.56 の値を持つ精度メトリック (AUC または曲線の下の領域) を出力します。

2. 使用する、 **revoscalepy**スコア付けのモデル、ストアド プロシージャを呼び出す**PredictTipRxPy**モデル名を渡すこと、およびクエリ文字列を入力として。

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>単一行のスコア付け

場合によっては、バッチ スコアリング、代わりにことができますを 1 つのケースに渡す、アプリケーションからの値を取得し、それらの値に基づいて 1 つの結果を返すこと。 など、Excel ワークシート、web アプリケーション、またはレポートを呼び出すストアド プロシージャを設定でき、パスを入力または型指定されたユーザーが選択されています。

このセクションでは 2 つのストアド プロシージャを呼び出すことによって、1 つの予測を作成する方法について説明します。

+ [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) scikit を使用して単一行のスコアリングのために設計されていますが、モデルを学習します。
+ [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy)は revoscalepy モデルを使用して単一行のスコアリングのために設計されています。
+ まだモデルをトレーニングしていない場合に戻る[手順 5.](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

座席数、トリップ距離などの単一の値の一連の入力としてモデル take は両方。 テーブル値関数の場合、 `fnEngineerFeatures`、新しい機能への入力からの緯度と経度の値の変換、距離を直接に使用されます。 [レッスン 4](sqldev-py4-create-data-features-using-t-sql.md)このテーブル値関数の説明が含まれています。

両方のストアド プロシージャは、Python モデルに基づいたスコアを作成します。

> [!NOTE]
> 
> Python モデル外部のアプリケーションからストアド プロシージャを呼び出すときに必要なすべての入力機能を提供することが重要です。 エラーを回避するには、キャストするか、入力データを検証するデータ型とデータの長さだけでなく、Python のデータ型に変換する必要があります。

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

コードを確認して、実行するストアド プロシージャを使用してスコア付けの分ほどかかる、 **scikit-学習**モデル。

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

次のストアド プロシージャの実行を使用してスコア付け、 **revoscalepy**モデル。

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
      from revoscalepy.functions.RxPredict import rx_predict;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict(mod, X)
      
      probList = []
      prob_list = prob_array["tipped_Pred"].values
      
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

### <a name="generate-scores-from-models"></a>モデルからスコアを生成します。

ストアド プロシージャを作成した後は、どちらのモデルに基づくスコアを生成する簡単です。 新しいを開くだけ**クエリ**ウィンドウ、および、特徴列の各パラメーターを入力するか貼り付けます。 値は、これらの機能列の順序での 7 つが必要です。
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. 使用して予測を生成する、 **revoscalepy**モデルでは、このステートメントを実行します。
  
    ```SQL
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. 使用して、スコアを生成する、 **scikit-学習**モデルでは、このステートメントを実行します。

    ```SQL
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

どちらの手順からの出力は、指定されたパラメーターや機能のあるタクシー旅行の有料されるヒントの確率です。

### <a name="changes"></a>変更

このセクションでは、このチュートリアルで使用するコードの変更を一覧表示します。 これらの変更は、最新バージョンを反映するように行われた**revoscalepy**バージョン。 API については、次を参照してください。 [Python 関数ライブラリ リファレンス](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)です。

| 変更の詳細 | 注|
| ----|----|
| 削除`import pandas`内のすべてのサンプル| 既定で読み込まれてパンダ|
| 関数`rx_predict_ex`に変更されました`rx_predict`| RTM およびプレリリース バージョンが必要`rx_predict_ex`|
| 関数`rx_logit_ex`に変更されました`rx_logit`| RTM およびプレリリース バージョンが必要`rx_logit_ex`|
| ` probList.append(probArray._results["tipped_Pred"])`変更されました`prob_list = prob_array["tipped_Pred"].values`| API への更新|

Python を SQL Server 2017 のプレリリース版を使用してサービスをインストールした場合、アップグレードすることをお勧めします。 Machine Learning のサーバーの最新のリリースを使用して、Python と R コンポーネントだけをアップグレードすることもできます。 詳細については、次を参照してください。[バインディングを使用して、SQL Server のインスタンスをアップグレードする](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

## <a name="conclusions"></a>結論

このチュートリアルでは、ストアド プロシージャに埋め込まれた Python コードを操作する方法を学びました。 との統合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] Python 予測モデルの展開と企業データ ワークフローの一部として再トレーニング モデルに組み込むにはるかに簡単になります。

## <a name="previous-step"></a>前の手順

[手順 5: トレーニングおよび Python モデルを保存します。](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)
