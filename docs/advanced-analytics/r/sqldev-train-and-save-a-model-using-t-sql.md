---
title: レッスン 5 のトレーニングと R と T-SQL (SQL Server の Machine Learning) を使用して、モデルを保存 |Microsoft ドキュメント
description: SQL Server で R を埋め込む方法を示すチュートリアル ストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bd5bdc7d256a22dbab6662a74dc39073892dbb4d
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250065"
---
# <a name="lesson-5-train-and-save-a-model-using-t-sql"></a>レッスン 5: トレーニングおよび T-SQL を使用してモデルを保存します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

このレッスンでは r です。 を使用して、機械学習モデルをトレーニングする方法が学習します。前のレッスンで作成したデータの機能を使用して、モデルのトレーニングをでトレーニング済みモデルを保存し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 この場合、R パッケージが既にインストールされてで[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]ので、SQL からすべて実行できます。

## <a name="create-the-stored-procedure"></a>ストアド プロシージャを作成します。

システム ストアド プロシージャを使用する T-SQL から R を呼び出すときに[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。 ただし、プロセスを繰り返して、モデルを再トレーニングなど多くの場合、その方が簡単ですへの呼び出しをカプセル化する`sp_execute_exernal_script`別のストアド プロシージャです。

1.  最初に、tip 予測モデルの構築に R コードを含むストアド プロシージャを作成します。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を新しく開きます**クエリ**ウィンドウとストアド プロシージャを作成するには、次のステートメントの実行_TrainTipPredictionModel_です。 このストアド プロシージャでは、入力データを定義し、R パッケージを使用してロジスティック回帰モデルを作成します。

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTipPredictionModel]
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
      -- Insert the trained model into a database table
      INSERT INTO nyc_taxi_models
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model and put it in data frame
    trained_model <- data.frame(model=as.raw(serialize(logitObj, NULL)));
    ',
      @input_data_1 = @inquery,
      @output_data_1_name = N'trained_model'
      ;
    
    END
    GO
    ```

    - ただし、一部のデータが、モデルのテストに残されたことには、データの 70% ランダムに選択されますタクシー データ テーブルからです。
    
    - SELECT クエリによって、カスタムのスカラー関数 _fnCalculateDistance_ が使用され、乗車位置と降車位置直線距離が計算されます。  クエリの結果は R の既定の入力変数 `InputDataset`に格納されます。
  
    - R スクリプトの呼び出し、`rxLogit`には強化された R 機能のいずれかの関数が含まれている[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、ロジスティック回帰モデルを作成します。
  
        二項変数 _tipped_ が *ラベル* または結果列として使用され、モデルは、  _passenger_count_、 _trip_distance_、 _trip_time_in_secs_、および _direct_distance_の機能列を使用して調整されます。
  
    -   R 変数 `logitObj`に保存されたトレーニング済みのモデルはシリアル化され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に出力するためにデータ フレームに入れられます。 その出力は、将来の予測に使用できるようにデータベース テーブル _nyc_taxi_models_に挿入されます。
  
2.  存在しない場合は、ストアド プロシージャを作成するステートメントを実行します。

## <a name="generate-the-r-model-using-the-stored-procedure"></a>ストアド プロシージャを使用して R モデルを生成します。

ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

1. R モデルを生成するには、その他のパラメーターを使用せず、ストアド プロシージャを呼び出します。

    ```SQL
    EXEC TrainTipPredictionModel
    ```

2. ウォッチ、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]r のパイプ、メッセージの**stdout**このメッセージのように、ストリーム。 

    "外部スクリプトからの STDOUT メッセージ: Rows Read: 1193025、合計行が処理: 1193025、チャンク時間の合計: 0.093 秒"

    また、個々 の関数に固有のメッセージを表示することも可能性があります。`rxLogit`変数を表示し、モデルの作成の一部として生成されたメトリックをテストします。

3.  ステートメントが完了したら、テーブルを開く*nyc_taxi_models*です。 データの処理と、モデルの調整を行う時間がかかります。

    _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    ```
    model
    ------
    0x580A00000002000302020....
    ```

次の手順では、トレーニング済みのモデルを使用して予測を作成します。

## <a name="next-lesson"></a>次のレッスン

[レッスン 6: 運用モデル](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 4: R と T-SQL で関数を使用してデータ機能を作成します。](..//tutorials/sqldev-create-data-features-using-t-sql.md)

