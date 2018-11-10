---
title: レッスン 3 のトレーニングと R と T-SQL (SQL Server Machine Learning) を使用して、モデルの保存 |Microsoft Docs
description: SQL Server に R を埋め込む方法を示すチュートリアルはストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 23387a6074f0c4a1dd6b4cb675b84f7aaced2a06
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033560"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>レッスン 3: トレーニングし、T-SQL を使用してモデルを保存
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R を使用する方法に関する SQL 開発者向けのチュートリアルの一部です。

このレッスンで R を使用して機械学習モデルをトレーニングする方法を学習します前のレッスンで作成したデータの機能を使用して、モデルをトレーニングし、トレーニング済みのモデルを保存し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 ここで、R パッケージを既にと共にインストール[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]ので、SQL からすべて実行できます。

## <a name="create-the-stored-procedure"></a>ストアド プロシージャを作成します。

システム ストアド プロシージャを使用する T-SQL から R を呼び出すときに[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 一方、プロセスを繰り返して、モデルを再トレーニングなど多くの場合、別のストアド プロシージャで sp_execute_exernal_script への呼び出しをカプセル化する簡単です。

1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、新しく開きます**クエリ**ウィンドウ。

2. ストアド プロシージャを作成する次のステートメントを実行して**RxTrainLogitModel**します。 このストアド プロシージャは、入力データを定義しを使用して**rxLogit** RevoScaleR ロジスティック回帰モデルを作成するからです。

    ```SQL
    CREATE PROCEDURE [dbo].[RxTrainLogitModel]
    
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

    -をいくつかのデータが残されていることをモデルをテストすることを確認するには、データの 70% がトレーニングのためのタクシー データ テーブルからランダムに選択します。

    - SELECT クエリによって、カスタムのスカラー関数 *fnCalculateDistance* が使用され、乗車位置と降車位置直線距離が計算されます。 クエリの結果が、既定の R の入力変数に格納されている`InputDataset`します。
  
    - R スクリプトの呼び出し、 **rxLogit**関数、拡張 R 関数のいずれかに含まれる[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、ロジスティック回帰モデルを作成します。
  
        二項変数 _tipped_ が *ラベル* または結果列として使用され、モデルは、  _passenger_count_、 _trip_distance_、 _trip_time_in_secs_、および _direct_distance_の機能列を使用して調整されます。
  
    -   R 変数 `logitObj`に保存されたトレーニング済みのモデルはシリアル化され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に出力するためにデータ フレームに入れられます。 その出力は、将来の予測に使用できるようにデータベース テーブル _nyc_taxi_models_に挿入されます。

## <a name="generate-the-r-model-using-the-stored-procedure"></a>ストアド プロシージャを使用して、R モデルを生成します。

ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

1. R モデルを生成するには、他のパラメーターなしのストアド プロシージャを呼び出します。

    ```SQL
    EXEC RxTrainLogitModel
    ```

2. ウォッチ、**メッセージ**のウィンドウ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に R のパイプ メッセージ**stdout**このメッセージのように、ストリーム。 

    "外部スクリプトからの STDOUT メッセージ: Rows Read: 1193025、Total Rows Processed: 1193025、Total Chunk Time: 0.093 秒"

    個々 の関数に固有のメッセージも、`rxLogit`変数を表示し、モデルの作成の一部として生成されるメトリックをテストします。

3.  テーブルを開き、ステートメントが完了したら、 *nyc_taxi_models*します。 データの処理とモデルの調整を行うに時間がかかる場合があります。

    _model_列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。

    ```
    model
    ------
    0x580A00000002000302020....
    ```

次の手順では、予測を生成するのにトレーニング済みモデルを使用します。

## <a name="next-lesson"></a>次のレッスン

[レッスン 4: ストアド プロシージャで R モデルを使用して潜在的な結果を予測します。](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 2: R と T-SQL 関数を使用してデータ機能を作成します。](..//tutorials/sqldev-create-data-features-using-t-sql.md)

