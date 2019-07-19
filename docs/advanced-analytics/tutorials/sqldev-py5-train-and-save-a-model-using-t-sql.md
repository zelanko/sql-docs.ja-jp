---
title: トレーニングし、T-SQL - SQL Server Machine Learning を使用して、Python モデルの保存
description: Python のトレーニングし、SQL Server で TRANSACT-SQL を使用して、モデルを保存する方法を示すチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f2793c6773dc38ebeb4a420e24c38504deb412d0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961853"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>トレーニングし、T-SQL を使用して Python モデルの保存
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルの一部[SQL 開発者向けの in-database Python analytics](sqldev-in-database-python-for-sql-developers.md)します。 

この手順で Python パッケージを使用して、機械学習モデルをトレーニングする方法について説明します**scikit-学習**と**revoscalepy**。 SQL Server Machine Learning Services では、これらの Python ライブラリはインストールされています。

モジュールを読み込むし、作成および SQL Server ストアド プロシージャを使用して、モデルをトレーニングするために必要な関数を呼び出します。 モデルでは、前のレッスンでエンジニア リング データ機能が必要です。 最後に、トレーニング済みモデルを保存、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>サンプル データをトレーニング セットとテスト セットに分割します。

1. 呼び出されるストアド プロシージャを作成する**PyTrainTestSplit** nyctaxi_sample テーブル内のデータを 2 つの部分に分割する: nyctaxi_sample_training nyctaxi_sample_testing とします。 

    このストアド プロシージャは、既に作成する必要がありますが、作成時に次のコードを実行することができます。

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainTestSplit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. カスタム分割を使用してデータを分割するには、ストアド プロシージャを実行し、トレーニング セットに割り当てられたデータの割合を表す整数を入力します。 たとえば、次のステートメントでは、データをトレーニング セットの 60% を割り当てます。

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>ロジスティック回帰モデルを構築します。

データが準備できたので後、は、モデルのトレーニングに使用できます。 保存を呼び出すことによって、これを行う手順として、いくつかの Python コードを実行しているが、トレーニング データのテーブルを入力します。 このチュートリアルでは、2 つのモデル、両方の二項分類モデルを作成します。

+ ストアド プロシージャ**PyTrainScikit**するヒント予測モデルを作成、 **scikit-学習**パッケージ。
+ ストアド プロシージャ**TrainTipPredictionModelRxPy**するヒント予測モデルを作成、 **revoscalepy**パッケージ。

入力データを使用する各ストアド プロシージャを作成し、ロジスティック回帰モデルのトレーニングを提供します。 すべての Python コードは、システム ストアド プロシージャにラップされて[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

新しいデータでモデルを再トレーニングを容易にできるようには、別のストアド プロシージャで sp_execute_exernal_script への呼び出しをラップし、新しいトレーニング データをパラメーターとして渡します。 このセクションでそのプロセスを説明します。

### <a name="pytrainscikit"></a>PyTrainScikit

1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成する次のステートメントを実行**PyTrainScikit**します。  ストアド プロシージャには、入力クエリを提供する必要はありませんので、入力データの定義が含まれています。

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainScikit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainScikit] (@trained_model varbinary(max) OUTPUT)
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

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    データの処理とモデルの調整を行うには、最小のいくつかをかかる場合があります。 Python にパイプ メッセージ**stdout**ストリームが表示されます、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 例 :

    *外部スクリプトからの STDOUT メッセージ:* 
  *C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. テーブルを開く*nyc\_taxi_models*します。 _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561.*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

このストアド プロシージャは、新しい**revoscalepy**パッケージは、Python 用の新しいパッケージです。 オブジェクト、変換、および R 言語の提供するものと同様のアルゴリズムが含まれている**RevoScaleR**パッケージ。 

使用して**revoscalepy**、リモート計算コンテキストを作成することができます、コンピューティング コンテキスト、データを変換、ロジスティック回帰と線形回帰、デシジョン ツリーなどの人気のあるアルゴリズムを使用して予測モデルをトレーニングの間でデータを移動し、もっとその。 詳細については、次を参照してください。 [SQL Server で revoscalepy モジュール](../python/ref-py-revoscalepy.md)と[revoscalepy 関数リファレンス](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)します。

1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成する次のステートメントを実行_TrainTipPredictionModelRxPy_します。  ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

    ```sql
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

2. 次のように、トレーニング済みの挿入にストアド プロシージャを実行**revoscalepy**モデル テーブルに*nyc_taxi_models*します。

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    データの処理とモデルの調整を行うに時間がかかる場合があります。 Python にパイプ メッセージ**stdout**ストリームが表示されます、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 例 :

    *外部スクリプトからの STDOUT メッセージ:* 
  *C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. テーブル *nyc_taxi_models*を開きます。 _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    *revoscalepy_model* *0x8003637265766F7363616c....*

次の手順では、トレーニング済みモデルを使用して予測を作成します。

## <a name="next-step"></a>次の手順

[ストアド プロシージャに埋め込まれた Python を使用して予測を実行します。](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>前の手順

[T-SQL を使用してデータ機能を作成する](sqldev-py5-train-and-save-a-model-using-t-sql.md)
