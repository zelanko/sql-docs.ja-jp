---
title: SQL Server を使用して、Python モデルを運用化 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d95edb081edc0f18a3734025a5902d13f8e9a295
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806812"
---
# <a name="operationalize-the-python-model-using-sql-server"></a>SQL Server を使用して、Python モデルを運用化します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルの一部[SQL 開発者向けの in-database Python analytics](sqldev-in-database-python-for-sql-developers.md)します。 

この手順で学習する*運用*トレーニングし、前の手順で保存したモデル。

このシナリオでは、運用化は、モデルのスコア付けには、実稼働環境に配置を意味します。 SQL Server の統合、これはかなり簡単ためストアド プロシージャで Python コードを埋め込むことができます。 に新しい入力に基づき、モデルから予測を取得するには、アプリケーションからストアド プロシージャを呼び出すし、新しいデータを渡します。

このレッスンは、Python モデルに基づく予測を作成するための 2 つの方法を示しています。 バッチ スコアリング、とで、1 行のスコア付けします。

- **バッチ スコアリング:** 複数行の入力データを提供する SELECT クエリを引数として、ストアド プロシージャに渡します。 結果は、入力ケースに対応する観察のテーブルです。
- **個々 のスコア付け:** 一連の個別のパラメーター値を入力として渡します。  このストアド プロシージャは、1 つの行または値を返します。

スコア付けに必要なすべての Python コードは、ストアド プロシージャの一部として提供されます。

| ストアド プロシージャ名 | バッチまたは 1 つ | モデルのソース|
|----|----|----|
|PredictTipRxPy|バッチ (batch)| revoscalepy モデル|
|PredictTipSciKitPy|バッチ (batch) |scikit-モデルを説明します。|
|PredictTipSingleModeRxPy|1 つの行| revoscalepy モデル|
|PredictTipSingleModeSciKitPy|1 つの行| scikit-モデルを説明します。|

## <a name="batch-scoring"></a>バッチ スコアリング

最初の 2 つのストアド プロシージャは、ストアド プロシージャで Python 予測呼び出しをラップするための基本的な構文を示しています。 両方のストアド プロシージャでは、入力としてデータのテーブルが必要です。

- 使用する正確なモデルの名前は、ストアド プロシージャへの入力パラメーターとして提供されます。 ストアド プロシージャでは、シリアル化されたモデルを読み込み、データベース テーブルから`nyc_taxi_models`.table、ストアド プロシージャで SELECT ステートメントを使用します。
- シリアル化されたモデルが Python 変数に格納されている`mod`さらに処理するためには、Python を使用します。
- スコア付けする必要がある新しいケースがから取得した、[!INCLUDE[tsql](../../includes/tsql-md.md)]で指定されたクエリ`@input_data_1`します。 クエリ データが読み取られると、行が既定のデータ フレーム `InputDataSet`に保存されます。
- 両方のストアド プロシージャから関数を使用して、 `sklearn` AUC (曲線下面積)、正確性メトリックを計算します。 AUC などの精度メトリックは、先のラベルを提供する場合にのみ生成できます (、 _tipped_列)。 予測では、先のラベルは必要はありません (変数`y`)、精度のメトリックの計算が、します。

    そのため、スコア付けするデータのターゲットのラベルを持っていない場合、AUC 計算を削除するストアド プロシージャを変更して、機能からヒント確率のみを返す (変数`X`ストアド プロシージャで)。

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

ストアド プロシージャが既に作成されている必要があります。 検出できない場合は、ストアド プロシージャを作成するのには、次の T-SQL ステートメントを実行します。

このストアド プロシージャには、scikit に基づいてモデルが必要です-そのパッケージに固有の関数を使用しているため、パッケージをについて説明します。

+ 渡される入力を含むデータ フレーム、 `predict_proba` 、ロジスティック回帰モデルの関数`mod`します。 `predict_proba`関数 (`probArray = mod.predict_proba(X)`) を返します、 **float** (金額) のチップが支払われる確率を表します。

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

このストアド プロシージャ、同じ入力を使用し、前のストアド プロシージャと同じ型のスコアを作成しますから関数を使用して、 **revoscalepy** SQL Server machine learning で提供されるパッケージ。

> [!NOTE] 
> このストアド プロシージャのコードは、以前のリリース バージョンと RTM バージョンの revoscalepy パッケージへの変更を反映するように、若干変更されました。 参照してください、[変更](#changes)詳細テーブル。

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

## <a name="run-batch-scoring-using-a-select-query"></a>SELECT クエリを使用してバッチ スコアリングを実行します。

ストアド プロシージャ**PredictTipSciKitPy**と**PredictTipRxPy** 2 つの入力パラメーターが必要です。 

- スコア付けのデータを取得するクエリ
- トレーニング済みモデルの名前

ストアド プロシージャには、これらの引数を渡すことによって、特定のモデルを選択またはスコア付けに使用されるデータを変更できます。

1. 使用する、 **scikit-について**モデルのスコア付けのため、ストアド プロシージャを呼び出す**PredictTipSciKitPy**モデル名を渡すと、クエリ文字列を入力として。

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    ストアド プロシージャは、入力クエリの一部として渡された各乗車に対して予測の確率を返します。 
    
    内のテーブルとして、確率が表示されますクエリを実行するための SSMS (SQL Server Management Studio) を使用する場合、**結果**ウィンドウ。 **メッセージ**ウィンドウが約 0.56 の値を持つ AUC (曲線下面積)、精度メトリックを出力します。

2. 使用する、 **revoscalepy**モデルのスコア付けのため、ストアド プロシージャを呼び出す**PredictTipRxPy**モデル名を渡すと、クエリ文字列を入力として。

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>単一行のスコアリング

バッチ スコアリング、代わりに必要になるに渡す 1 つのケースで、アプリケーションから値を取得し、それらの値に基づいて 1 つの結果を返します。 など、Excel ワークシート、web アプリケーション、またはレポートをストアド プロシージャを呼び出すを設定して、パスを入力の型指定された、またはユーザーが選択しました。

このセクションでは 2 つのストアド プロシージャを呼び出すことによって、1 つの予測を作成する方法について説明します。

+ [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) scikit を使用して単一行のスコアリングのために設計されていますが、モデルを学習します。
+ [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy)は revoscalepy モデルを使用して単一行のスコアリングのために設計されています。
+ まだモデルをトレーニングしていない場合に戻って[手順 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

一連の乗客数、乗車距離などの 1 つの値を入力としてモデル take は両方です。 テーブル値関数の場合、 `fnEngineerFeatures`、新しい機能への入力からの緯度と経度の値の変換、直線距離に使用されます。 [レッスン 4](sqldev-py4-create-data-features-using-t-sql.md)このテーブル値関数の説明が含まれています。

両方のストアド プロシージャは、Python モデルに基づいてスコアを作成します。

> [!NOTE]
> 
> Python モデルに外部アプリケーションからストアド プロシージャを呼び出すときに必要なすべての入力機能を提供することが重要です。 エラーを回避するには、キャストまたは入力データを検証するデータ型とデータ長に加え、Python のデータ型に変換する必要があります。

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

使用してスコア付けを実行するストアド プロシージャのコードのレビューに少し時間がかかる、 **scikit-学習**モデル。

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

ストアド プロシージャが作成されたら、いずれかのモデルに基づいてスコアを生成する簡単です。 新しいを開くだけ**クエリ**ウィンドウ、および特徴の列の各パラメーターを入力するか貼り付けます。 値は、これらの機能列の順序で、7 つが必要です。
    
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

2. 使用して、スコアを生成する、 **scikit-について説明します**モデルでは、このステートメントを実行します。

    ```SQL
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

どちらの手順からの出力は、中、指定されたパラメーターまたは機能をタクシー乗車で支払われたチップの確率です。

### <a name="changes"></a> 変更

このセクションでは、このチュートリアルで使用するコードの変更が一覧表示します。 これらの変更は、最新バージョンを反映するように行われた**revoscalepy**バージョン。 API のヘルプを参照してください。 [Python 関数ライブラリのリファレンス](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)します。

| 変更の詳細 | 注|
| ----|----|
| 削除`import pandas`ですべてのサンプル| pandas を既定で読み込まれるようになりました|
| 関数`rx_predict_ex`に変更されました `rx_predict`| RTM およびプレリリース バージョンが必要です。 `rx_predict_ex`|
| 関数`rx_logit_ex`に変更されました `rx_logit`| RTM およびプレリリース バージョンが必要です。 `rx_logit_ex`|
| ` probList.append(probArray._results["tipped_Pred"])` 変更するには `prob_list = prob_array["tipped_Pred"].values`| API への更新|

SQL Server 2017 のプレリリース バージョンを使用して Python Services をインストールした場合は、アップグレードすることをお勧めします。 Machine Learning Server の最新リリースを使用して、Python および R のコンポーネントだけをアップグレードすることもできます。 詳細については、次を参照してください。[バインドを使用して SQL Server のインスタンスをアップグレードする](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

## <a name="conclusions"></a>結論

このチュートリアルでは、ストアド プロシージャに埋め込まれた Python コードを操作する方法を学習できました。 統合[!INCLUDE[tsql](../../includes/tsql-md.md)]予測の Python のモデルをデプロイして、企業データ ワークフローの一部としてモデルの再トレーニングを組み込むにははるかに簡単になります。

## <a name="previous-step"></a>前の手順

[トレーニングし、Python モデルの保存](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>関連項目

[SQL Server での Python 拡張機能](../concepts/extension-python.md)
