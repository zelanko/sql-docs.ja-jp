---
title: レッスン 3 のトレーニングと R と T-SQL - SQL Server Machine Learning を使用してモデルの保存
description: トレーニング、シリアル化し、R モデルを保存する方法を示すチュートリアル SQL Server を使用してストアド プロシージャと T-SQL 関数します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1953e2a5cfa1671a81630a66a4e6c3589929d1bb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961834"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>レッスン 3: トレーニングし、T-SQL を使用してモデルを保存
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R を使用する方法に関する SQL 開発者向けのチュートリアルの一部です。

このレッスンで R を使用して機械学習モデルをトレーニングする方法を学習します前のレッスンで作成したデータの機能を使用して、モデルをトレーニングし、トレーニング済みのモデルを保存し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 ここで、R パッケージを既にと共にインストール[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]ので、SQL からすべて実行できます。

## <a name="create-the-stored-procedure"></a>ストアド プロシージャを作成します。

システム ストアド プロシージャを使用する T-SQL から R を呼び出すときに[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 一方、プロセスを繰り返して、モデルを再トレーニングなど多くの場合、別のストアド プロシージャで sp_execute_exernal_script への呼び出しをカプセル化する簡単です。

1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、新しく開きます**クエリ**ウィンドウ。

2. ストアド プロシージャを作成する次のステートメントを実行して**RxTrainLogitModel**します。 このストアド プロシージャは、入力データを定義しを使用して**rxLogit** RevoScaleR ロジスティック回帰モデルを作成するからです。

    ```sql
    CREATE PROCEDURE [dbo].[RxTrainLogitModel] (@trained_model varbinary(max) OUTPUT)
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
    
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model 
    trained_model <- as.raw(serialize(logitObj, NULL));
    ',
      @input_data_1 = @inquery,
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT; 
    END
    GO
    ```

    - 一部のデータが残されていることをモデルをテストするためには、データの 70% がトレーニングのためのタクシー データ テーブルからランダムに選択します。

    - SELECT クエリによって、カスタムのスカラー関数 *fnCalculateDistance* が使用され、乗車位置と降車位置直線距離が計算されます。 クエリの結果が、既定の R の入力変数に格納されている`InputDataset`します。
  
    - R スクリプトの呼び出し、 **rxLogit**関数、拡張 R 関数のいずれかに含まれる[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、ロジスティック回帰モデルを作成します。
  
        二項変数 _tipped_ が *ラベル* または結果列として使用され、モデルは、  _passenger_count_、 _trip_distance_、 _trip_time_in_secs_、および _direct_distance_の機能列を使用して調整されます。
  
    - R 変数に保存されたトレーニング済みのモデル`logitObj`はシリアル化され、出力パラメーターとして返されます。

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>トレーニングおよびストアド プロシージャを使用して、R モデルのデプロイ

ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

1. トレーニングを R モデルのデプロイは、ストアド プロシージャを呼び出すし、データベース テーブルに挿入_nyc_taxi_models_の将来の予測に使用できるようにします。

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. ウォッチ、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に R のパイプ メッセージ**stdout**このメッセージのように、ストリーム。 

    "外部スクリプトからの STDOUT メッセージ。行の読み取り:処理された合計行、1193025:1193025、チャンクの合計時間:0.093 秒"

    個々 の関数に固有のメッセージも、`rxLogit`変数を表示し、モデルの作成の一部として生成されるメトリックをテストします。

3.  テーブルを開き、ステートメントが完了したら、 *nyc_taxi_models*します。 データの処理とモデルの調整を行うに時間がかかる場合があります。

    列にシリアル化されたモデルが含まれていますが、その 1 つの新しい行が追加されたを参照してください_モデル_とモデル名**RxTrainLogit_model**列_名前_します。

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

次の手順では、予測を生成するのにトレーニング済みモデルを使用します。

## <a name="next-lesson"></a>次のレッスン

[レッスン 4:ストアド プロシージャで R モデルを使用して潜在的な結果を予測します。](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 2:R と T-SQL 関数を使用してデータ機能を作成します。](..//tutorials/sqldev-create-data-features-using-t-sql.md)

