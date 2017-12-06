---
title: "手順 5: トレーニングおよび T-SQL を使用して、Python モデルを保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: bcad930d7d2a759e66adf1309eba6af144010c82
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="step-5-train-and-save-a-python-model-using-t-sql"></a>手順 5: トレーニングおよび T-SQL を使用して、Python モデルを保存

この記事では、チュートリアルのパート[SQL 開発者のためのデータベースでの Python analytics](sqldev-in-database-python-for-sql-developers.md)です。 

この手順では、Python パッケージを使用する機械学習モデルをトレーニングする方法を学習**scikit-学習**と**revoscalepy**です。 これらの Python ライブラリは、SQL Server マシン ラーニング Services と共にインストールされています。

モジュールを読み込むし、作成し、SQL Server のストアド プロシージャを使用して、モデルのトレーニングに必要な関数を呼び出します。 モデルには、前のレッスンでエンジニア リング データ機能が必要です。 最後に、トレーニング済みモデルを保存、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。

> [!IMPORTANT]
> 複数の変更があった、 **revoscalepy**パッケージで、このチュートリアルのコードに小さな変更が必要です。 参照してください、[変更リスト](sqldev-py6-operationalize-the-model.md#changes)このチュートリアルの最後。 
> 
> Python を SLq Server 2017 のプレリリース版を使用してサービスをインストールした場合は、最新バージョンにアップグレードすることをお勧めします。 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>サンプル データをトレーニング セットとテスト セットに分割します。

1. ストアド プロシージャを使用することができます**TrainTestSplit** 、nyctaxi 内のデータを分割する\_サンプル テーブルを 2 つの部分に: nyctaxi\_サンプル\_トレーニングと nyctaxi\_サンプル\_をテストします。 

    このストアド プロシージャは、既に作成する必要がありますが、それを作成する次のコードを実行することができます。

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. カスタム分割を使用してデータを分割するには、ストアド プロシージャを実行し、トレーニング セットに割り当てられたデータの割合を表す整数を入力します。 たとえば、次のステートメントは、データをトレーニング セットの 60% を割り当てます。

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>ロジスティック回帰モデルを構築します。

データを準備するは、モデルのトレーニングに使用できます。 格納されたを呼び出すことによって、これを行う手順として、いくつかの Python コードを実行しているが、トレーニング データ テーブルを入力します。 このチュートリアルでは、2 つのモデル、両方の二項分類モデルを作成します。

+ ストアド プロシージャ**TrainTipPredictionModelRxPy**ヒント予測モデルを使用して、作成、 **revoscalepy**パッケージです。
+ ストアド プロシージャ**TrainTipPredictionModelSciKitPy**ヒント予測モデルを使用して、作成、 **scikit-学習**パッケージです。

各ストアド プロシージャは、入力データを使用して作成し、ロジスティック回帰モデルのトレーニングを提供します。 すべての Python コードは、システム ストアド プロシージャにラップ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

新しいデータでモデルを再トレーニングを容易にできるようにには、別のストアド プロシージャで sp_execute_exernal_script への呼び出しをラップし、パラメーターとして新しいトレーニング データに渡します。 このセクションでは、そのプロセスを説明します。

### <a name="traintippredictionmodelscikitpy"></a>TrainTipPredictionModelSciKitPy

1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成するには、次のステートメントの実行_TrainTipPredictionModelSciKitPy_です。  ストアド プロシージャには、入力のクエリを指定する必要がないため、入力データの定義が含まれています。

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelSciKitPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelSciKitPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
      EXEC sp_execute_external_script
      @language = N'Python',
      @script = N'
      import numpy
      import pickle
      from sklearn.linear_model import LogisticRegression
      
      ##Create SciKit-Learn logistic regression model
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      SKLalgo = LogisticRegression()
      logitObj = SKLalgo.fit(X, y)
      
      ##Serialize model
      trained_model = pickle.dumps(logitObj)
      ',
      @input_data_1 = N'
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_training
      ',
      @input_data_1_name = N'InputDataSet',
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT;
      ;
    END;
    GO
    ```

2. 次の実行にトレーニング済みモデルを挿入する SQL ステートメントのテーブル nyc\_taxi_models です。

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelSciKitPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    データの処理と、モデルの調整を行うには、最小のいくつかをかかる場合があります。 Python のパイプとメッセージ**stdout**にストリームが表示されます、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 例:

    *外部スクリプトからの STDOUT メッセージ:*
  *C:\Program files \microsoft SQL Server\MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. テーブルを開く*nyc\_taxi_models*です。 _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    *linear_model* *0x800363736B6C6561726E2E6C696E6561 しています.*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

このストアド プロシージャを使用して、新しい**revoscalepy**パッケージは、Python の新しいパッケージです。 オブジェクト、変換、および R 言語のために用意されているようなアルゴリズムが含まれている**RevoScaleR**パッケージです。 

使用して**revoscalepy**、リモート計算コンテキストを作成することができます、間でデータを移動計算コンテキスト、トランス フォーム データ、およびロジスティックと線形回帰、デシジョン ツリーなどのよく使用されるアルゴリズムを使用して予測モデルをトレーニングし、もっとその。 詳細については、次を参照してください。 [revoscalepy は何ですか。](../python/what-is-revoscalepy.md)

1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成するには、次のステートメントの実行_TrainTipPredictionModelRxPy_です。  ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    from revoscalepy.functions.RxLogit import rx_logit
    
    ## Create a logistic regression model using rx_logit function from revoscalepy package
    logitObj = rx_logit("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

    このストアド プロシージャでは、モデルのトレーニングの一部として、次の手順を実行します。

    - SELECT クエリは、カスタムのスカラー関数を適用_fnCalculateDistance_回収と自動仕分け場所の間で直接距離を計算します。 クエリの結果が既定の Python 入力変数に格納されている`InputDataset`です。
    - バイナリ変数_先が_として使用される、*ラベル*結果列、およびモデルが適しているこれらの特徴の列を使用してまたは: _passenger_count_、 _trip_距離_、 _trip_time_in_secs_、および_direct_distance_です。
    - トレーニング済みモデルをシリアル化され、Python 変数に格納されている`logitObj`です。 T-SQL OUTPUT キーワードを追加すると、ストアド プロシージャの出力として、変数を追加できます。 バイナリのコード モデルのデータベース テーブルに挿入する次の手順でその変数が使用される_nyc_taxi_models_です。 このメカニズムが簡単に格納するモデルの再利用します。

2. トレーニング済みの挿入するには、次のようにストアド プロシージャを実行して**revoscalepy**テーブル _nyc にモデル\_タクシー\_モデル。

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    データの処理と、モデルの調整を行う時間がかかります。 Python のパイプとメッセージ**stdout**にストリームが表示されます、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 例:

    *外部スクリプトからの STDOUT メッセージ:*
  *C:\Program files \microsoft SQL Server\MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. テーブル *nyc_taxi_models*を開きます。 _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    *rx_model* *0x8003637265766F7363616c しています.*

次の手順では、トレーニング済みモデルを使用して予測を作成します。

## <a name="next-step"></a>次の手順

[手順 6: 運用 SQL Server を使用して、Python モデル](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>前の手順

[手順 4: T-SQL を使用してデータ機能を作成する](sqldev-py5-train-and-save-a-model-using-t-sql.md)
