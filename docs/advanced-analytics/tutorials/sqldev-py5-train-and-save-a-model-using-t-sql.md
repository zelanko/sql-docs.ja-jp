---
title: トレーニングし、T-SQL を使用して Python モデルの保存 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2b098af69a454b19cd768995107b3f8c0ec3e141
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806792"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>トレーニングし、T-SQL を使用して Python モデルの保存
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルの一部[SQL 開発者向けの in-database Python analytics](sqldev-in-database-python-for-sql-developers.md)します。 

この手順で Python パッケージを使用して、機械学習モデルをトレーニングする方法について説明します**scikit-学習**と**revoscalepy**。 SQL Server Machine Learning Services では、これらの Python ライブラリはインストールされています。

モジュールを読み込むし、作成および SQL Server ストアド プロシージャを使用して、モデルをトレーニングするために必要な関数を呼び出します。 モデルでは、前のレッスンでエンジニア リング データ機能が必要です。 最後に、トレーニング済みモデルを保存、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。

> [!IMPORTANT]
> いくつかの変更があった、 **revoscalepy**パッケージで、このチュートリアルでは、コードの小さな変更が必要です。 参照してください、[変更リスト](sqldev-py6-operationalize-the-model.md#changes)このチュートリアルの最後にします。 
> 
> SLq Server 2017 のプレリリース バージョンを使用して Python Services をインストールした場合は、最新バージョンにアップグレードすることをお勧めします。 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>サンプル データをトレーニング セットとテスト セットに分割します。

1. ストアド プロシージャを使用する**TrainTestSplit** 、nyctaxi 内のデータを分割する\_サンプル テーブルを 2 つの部分に: nyctaxi\_サンプル\_トレーニングと nyctaxi\_サンプル\_テストします。 

    このストアド プロシージャは、既に作成する必要がありますが、作成時に次のコードを実行することができます。

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

2. カスタム分割を使用してデータを分割するには、ストアド プロシージャを実行し、トレーニング セットに割り当てられたデータの割合を表す整数を入力します。 たとえば、次のステートメントでは、データをトレーニング セットの 60% を割り当てます。

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>ロジスティック回帰モデルを構築します。

データが準備できたので後、は、モデルのトレーニングに使用できます。 保存を呼び出すことによって、これを行う手順として、いくつかの Python コードを実行しているが、トレーニング データのテーブルを入力します。 このチュートリアルでは、2 つのモデル、両方の二項分類モデルを作成します。

+ ストアド プロシージャ**TrainTipPredictionModelRxPy**するヒント予測モデルを作成、 **revoscalepy**パッケージ。
+ ストアド プロシージャ**TrainTipPredictionModelSciKitPy**するヒント予測モデルを作成、 **scikit-学習**パッケージ。

入力データを使用する各ストアド プロシージャを作成し、ロジスティック回帰モデルのトレーニングを提供します。 すべての Python コードは、システム ストアド プロシージャにラップされて[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

新しいデータでモデルを再トレーニングを容易にできるようには、別のストアド プロシージャで sp_execute_exernal_script への呼び出しをラップし、新しいトレーニング データをパラメーターとして渡します。 このセクションでそのプロセスを説明します。

### <a name="traintippredictionmodelscikitpy"></a>TrainTipPredictionModelSciKitPy

1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成する次のステートメントを実行_TrainTipPredictionModelSciKitPy_します。  ストアド プロシージャには、入力クエリを提供する必要はありませんので、入力データの定義が含まれています。

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

2. 次の実行にトレーニング済みモデルを挿入する SQL ステートメントのテーブル nyc\_taxi_models します。

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelSciKitPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    データの処理とモデルの調整を行うには、最小のいくつかをかかる場合があります。 Python にパイプ メッセージ**stdout**ストリームが表示されます、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 以下に例を示します。

    *外部スクリプトからの STDOUT メッセージ:*
  *C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. テーブルを開く*nyc\_taxi_models*します。 _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    *linear_model* *0x800363736B6C6561726E2E6C696E6561.*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

このストアド プロシージャは、新しい**revoscalepy**パッケージは、Python 用の新しいパッケージです。 オブジェクト、変換、および R 言語の提供するものと同様のアルゴリズムが含まれている**RevoScaleR**パッケージ。 

使用して**revoscalepy**、リモート計算コンテキストを作成することができます、コンピューティング コンテキスト、データを変換、ロジスティック回帰と線形回帰、デシジョン ツリーなどの人気のあるアルゴリズムを使用して予測モデルをトレーニングの間でデータを移動し、もっとその。 詳細については、次を参照してください[revoscalepy とは何ですか?。](../python/what-is-revoscalepy.md)

1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成する次のステートメントを実行_TrainTipPredictionModelRxPy_します。  ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

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

    このストアド プロシージャでは、モデルのトレーニングの一環として、次の手順を実行します。

    - SELECT クエリは、カスタムのスカラー関数を適用_fnCalculateDistance_乗車と降車場所間の直線距離を計算します。 クエリの結果が既定の Python 入力変数に格納されている`InputDataset`します。
    - 二項変数_tipped_として提供される、*ラベル*結果列とモデルの機能列を使用してが調整または: _passenger_count_、 _trip_距離_、 _trip_time_in_secs_、および_direct_distance_します。
    - トレーニング済みモデルはシリアル化され、Python の変数に格納されている`logitObj`します。 T-SQL OUTPUT キーワードを追加すると、ストアド プロシージャの出力として、変数を追加できます。 次の手順で、データベース テーブルに、モデルのバイナリ コードを挿入する変数を使用_nyc_taxi_models_します。 このメカニズムは、簡単に格納してモデルの再利用できます。

2. 次のように、トレーニング済みの挿入にストアド プロシージャを実行**revoscalepy**テーブル _nyc にモデル\_タクシー\_モデル。

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    データの処理とモデルの調整を行うに時間がかかる場合があります。 Python にパイプ メッセージ**stdout**ストリームが表示されます、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 以下に例を示します。

    *外部スクリプトからの STDOUT メッセージ:*
  *C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. テーブル *nyc_taxi_models*を開きます。 _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    *rx_model* *0x8003637265766F7363616c....*

次の手順では、トレーニング済みモデルを使用して予測を作成します。

## <a name="next-step"></a>次の手順

[SQL Server を使用して、Python モデルを運用化します。](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>前の手順

[T-SQL を使用してデータ機能を作成する](sqldev-py5-train-and-save-a-model-using-t-sql.md)
