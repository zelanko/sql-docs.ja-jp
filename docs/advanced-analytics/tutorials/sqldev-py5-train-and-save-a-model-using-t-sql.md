---
title: "手順 5: T-SQL を使用してモデルをトレーニングし保存する | Microsoft Docs"
ms.custom: 
ms.date: 07/26/2017
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
ms.openlocfilehash: 80a47819dfbb2e96162a49730e0dcf0b1b340f07
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="step-5-train-and-save-a-model-using-t-sql"></a>手順 5: トレーニングおよび T-SQL を使用してモデルを保存します。

この手順では、Python パッケージを使用する機械学習モデルをトレーニングする方法を学習**scikit-学習**と**revoscalepy**です。 これらの Python ライブラリは、モジュールを読み込むし、ストアド プロシージャ内から必要な関数を呼び出すことができますのでに既に SQL Server Machine Learning のサービスと共にインストールされます。 作成したデータ機能を使用してモデルをトレーニングして、トレーニングしたモデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存します。

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>サンプル データをトレーニング セットとテスト セットに分割します。

1. Nyctaxi 内のデータを分割するストアド プロシージャを作成する次の T-SQL コマンド実行\_サンプル テーブルを 2 つの部分に: nyctaxi\_サンプル\_トレーニングと nyctaxi\_サンプル\_テストします。

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

2. ストアド プロシージャを実行し、トレーニング セットに割り当てられたデータの割合を表す整数を入力します。 たとえば、次のステートメントは、データをトレーニング セットの 60% を割り当てます。 トレーニング セットとテスト データは、2 つの独立したテーブルに格納されます。

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model-using-scikit-learn"></a>ビルド scikit を使用して、ロジスティック回帰モデルの学習

このセクションでは、準備が完了したトレーニング データを使用して、モデルのトレーニングに使用できるストアド プロシージャを作成します。 このストアド プロシージャは、入力データを定義しを使用して、 **scikit-学習**ロジスティック回帰モデルをトレーニングする関数。 システム ストアド プロシージャを使用して SQL Server と共にインストールされている Python ランタイムを呼び出す[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

モデルを再トレーニングを容易にできるように、別のストアド プロシージャに sp_execute_exernal_script への呼び出しをラップして、パラメーターとして新しいトレーニング データを渡すことができます。 このセクションでは、そのプロセスを説明します。

1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成するには、次のステートメントの実行_TrainTipPredictionModelSciKitPy_です。  入力クエリを指定する必要がないために、ストアド プロシージャは、入力データの定義を含んでいます。 注意してください。

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
      import pandas
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

## <a name="build-a-logistic-model-using-the-revoscalepy-package"></a>ロジスティック モデルを使用して、ビルド、 _revoscalepy_パッケージ

ここで、新しいを使用する別のストアド プロシージャを作成**revoscalepy**ロジスティック回帰モデルのトレーニングにパッケージします。 **Revoscalepy**用 Python には、オブジェクト、変換、および R 言語のために用意されているようなアルゴリズムが含まれています。 パッケージ**RevoScaleR**パッケージです。 このライブラリには、コンピューティング コンテキストを作成する、計算コンテキスト、データを変換およびロジスティックと線形回帰、デシジョン ツリーなどのよく使用されるアルゴリズムを使用して予測モデルのトレーニングの間でデータを移動できます。 詳細については、次を参照してください。 [revoscalepy は何ですか。](../python/what-is-revoscalepy.md)

1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成するには、次のステートメントの実行_TrainTipPredictionModelRxPy_です。  このモデルは、準備が完了したトレーニング データにも使用します。 ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

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
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
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

    - Nyctaxi で revoscalepy パッケージを使用して、ロジスティック回帰モデルのトレーニング\_サンプル\_トレーニング データです。
    - SELECT クエリによって、カスタムのスカラー関数 _fnCalculateDistance_ が使用され、乗車位置と降車位置直線距離が計算されます。 クエリの結果が既定の Python 入力変数に格納されている`InputDataset`です。
    - Python スクリプト関数 revoscalepy の LogisticRegression に含まれている[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、ロジスティック回帰モデルを作成します。
    - 二項変数 _tipped_ が *ラベル* または結果列として使用され、モデルは、  _passenger_count_、 _trip_distance_、 _trip_time_in_secs_、および _direct_distance_の機能列を使用して調整されます。
    - Python 変数に格納されている、トレーニング済みモデル`logitObj`がシリアル化され、出力パラメーターとして配置[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 出力が、データベース テーブルに挿入される_nyc_taxi_models_、と共に、新しい行とその名前を取得したり、将来の予測に使用できるようにします。

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

[手順 6: 運用モデル](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>前の手順

[手順 4: T-SQL を使用してデータの機能を作成します。](sqldev-py5-train-and-save-a-model-using-t-sql.md)

