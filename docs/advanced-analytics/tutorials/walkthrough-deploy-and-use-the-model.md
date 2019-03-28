---
title: SQL Server - SQL Server Machine Learning で予測のため、R モデルをデプロイします。
description: データベース内分析用の SQL Server で R モデルをデプロイする方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: f1c684aff9c4b31049a04add04e8def642dca1d2
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510599"
---
# <a name="deploy-the-r-model-and-use-it-in-sql-server-walkthrough"></a>R モデルを展開し、SQL Server (チュートリアル) で使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンでは、ストアド プロシージャからトレーニング済みモデルを呼び出すことによって、運用環境で R モデルをデプロイする方法を説明します。 R またはサポートするアプリケーション プログラミング言語からストアド プロシージャを呼び出すことができます[!INCLUDE[tsql](../../includes/tsql-md.md)](などC#、Java、Python、およびなど) と、モデルを使用して新しい観察結果を予測します。

この記事では、スコアリングにモデルを使用する 2 つの最も一般的な方法を示しています。

> [!div class="checklist"]
> * **バッチ スコアリング モード**複数の予測を生成します。
> * **個別スコアリング モード**一度に 1 つずつ予測を生成します。

## <a name="batch-scoring"></a>バッチ スコアリング

ストアド プロシージャの作成*PredictTipBatchMode*、SQL クエリまたはテーブルを入力として渡す複数の予測を生成します。 結果のテーブルが返されます、直接テーブルに挿入したり、ファイルに書き込む可能性があります。

- SQL クエリとして一連の入力データを取得する
- 前のレッスンで保存したトレーニング済みのロジスティック回帰モデルを呼び出す
- ドライバーが、0 以外のヒントを取得する確率を予測します。

1. Management Studio で、新しいクエリ ウィンドウを開き PredictTipBatchMode ストアド プロシージャを作成する次の T-SQL スクリプトを実行します。
  
    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipBatchMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @input nvarchar(max)
    AS
    BEGIN
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);
      EXEC sp_execute_external_script @language = N'R',
         @script = N'
           mod <- unserialize(as.raw(model));
           print(summary(mod))
           OutputDataSet<-rxPredict(modelObject = mod,
             data = InputDataSet,
             outData = NULL,
             predVarNames = "Score", type = "response",
             writeModelVars = FALSE, overwrite = TRUE);
           str(OutputDataSet)
           print(OutputDataSet)',
      @input_data_1 = @input,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

    + SQL テーブルから、格納されたモデルを呼び出すには、SELECT ステートメントを使用します。 モデルがテーブルから取得した**varbinary (max)** SQL 変数に格納されたデータを _\@lmodel2_、およびパラメーターとして渡された*mod*システムにストアド プロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

    + スコア付けは SQL クエリとして定義され、文字列として、SQL 変数に格納されているは、入力として使用されるデータ_\@入力_します。 呼ばれるデータ フレームに格納されているように、データベースからデータを取得すると、 *InputDataSet*への入力データの既定の名前だけである、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)プロシージャを定義できます別の変数名、パラメーターを使用して必要な場合は  *_\@input_data_1_name_* します。

    + スコアを生成するには、ストアド プロシージャはから rxPredict 関数を呼び出します。、 **RevoScaleR**ライブラリ。

    + 戻り値、*スコア*、確率、そのドライバー モデルを指定するには、ヒントを取得します。 必要に応じて、ある種のフィルターは、戻り値を「ヒント」と「チップなし」グループに分類に返される値を簡単に適用できます。  たとえば、確率が 0.5 よりも小さいでは、ヒントはほとんどありませんが意味します。
  
2.  バッチ モードでは、ストアド プロシージャを呼び出して、ストアド プロシージャへの入力として必要なクエリを定義します。 それが動作することを確認する SSMS 内で実行する SQL クエリを次に示します。

    ```sql
    SELECT TOP 10
      a.passenger_count AS passenger_count,
      a.trip_time_in_secs AS trip_time_in_secs,
      a.trip_distance AS trip_distance,
      a.dropoff_datetime AS dropoff_datetime,
      dbo.fnCalculateDistance( pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance
      FROM 
        (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude 
        FROM nyctaxi_sample)a 
      LEFT OUTER JOIN
      ( SELECT medallion, hack_license, pickup_datetime
      FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b
      ON a.medallion=b.medallion
      AND a.hack_license=b.hack_license
      AND a.pickup_datetime=b.pickup_datetime
      WHERE b.medallion is null
    ```

3. SQL クエリから、入力文字列を作成するのにには、この R コードを使用します。

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. ストアド プロシージャ R からを実行するには、呼び出し、 **sqlQuery**のメソッド、 **RODBC**パッケージ化し、SQL 接続を使用して、`conn`前に定義します。

    ```R
    sqlQuery (conn, q);
    ```

    ODBC エラーが発生する場合は、構文エラーと適切な数の引用符があるかどうかを確認します。 
    
    アクセス許可エラーが発生する場合は、ログインには、ストアド プロシージャを実行する機能を確認します。

## <a name="single-row-scoring"></a>単一行のスコアリング

個別スコアリング モードは、一連の個別の値を入力としてストアド プロシージャに渡す、一度に 1 つずつ予測を生成します。 値は、予測を作成するモデルを使用すると、モデル内の機能に対応していますか、確率値などの別の結果を生成します。 アプリケーション、またはユーザーにその値を表示できます。

行ごとに予測モデルを呼び出すときに、一連の個別の各ケースの機能を表す値を渡します。 ストアド プロシージャは、1 つの予測と確率を返します。 

ストアド プロシージャ*PredictTipSingleMode*この方法を示します。 これは、入力特徴値 (たとえば、乗客数、乗車距離) を表す複数のパラメーター、スコアを格納された R モデルを使用してこれらの機能、およびヒント確率を出力します。

1. ストアド プロシージャを作成する次の TRANSACT-SQL ステートメントを実行します。

    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipSingleMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,
    @trip_distance float = 0,
    @trip_time_in_secs int = 0,
    @pickup_latitude float = 0,
    @pickup_longitude float = 0,
    @dropoff_latitude float = 0,
    @dropoff_longitude float = 0
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs, @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)'
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);

      EXEC sp_execute_external_script @language = N'R',  @script = N'
            mod <- unserialize(as.raw(model));
            print(summary(mod))
            OutputDataSet<-rxPredict(
              modelObject = mod,
              data = InputDataSet,
              outData = NULL,
              predVarNames = "Score",
              type = "response",
              writeModelVars = FALSE,
              overwrite = TRUE);
            str(OutputDataSet)
            print(OutputDataSet)
            ',
      @input_data_1 = @inquery,
      @params = N'
      -- passthrough columns
      @model varbinary(max) ,
      @passenger_count int ,
      @trip_distance float ,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      -- mapped variables
      @model = @lmodel2 ,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance ,
      @trip_time_in_secs=@trip_time_in_secs ,
      @pickup_latitude=@pickup_latitude ,
      @pickup_longitude=@pickup_longitude ,
      @dropoff_latitude=@dropoff_latitude ,
      @dropoff_longitude=@dropoff_longitude
      WITH RESULT SETS ((Score float));
    END
    ```

2. SQL Server Management studio で使用することができます、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC**プロシージャ (または**EXECUTE**)、ストアド プロシージャを呼び出すし、必要な入力を渡すことにします。 たとえば、Management Studio でこのステートメントを実行してみてください。

    ```sql
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    ここで渡される値は、それぞれ、変数の_乗客\_カウント_、 _trip_distance_、_トリップ\_時間\_で\_秒_、 _pickup\_緯度_、 _pickup\_経度_、_降車\_緯度_、および_降車\_経度_します。

3. R コードからこの同じ呼び出しを実行するには、次のような全体のストアド プロシージャの呼び出しを含む R 変数の定義だけです。

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    ここで渡される値は、それぞれ、変数の_乗客\_カウント_、_トリップ\_距離_、_トリップ\_時間\_で\_秒_、 _pickup\_緯度_、 _pickup\_経度_、_降車\_緯度_、および_降車\_経度_します。

4. 呼び出す`sqlQuery`(から、 **RODBC**パッケージ) ストアド プロシージャの呼び出しを含む文字列変数と共に、接続文字列を渡します。

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > R Tools for Visual Studio (RTVS) は、SQL Server と R. の両方の優れた統合を提供します。RODBC を使用して、SQL Server 接続の例については、この記事を参照してください。[SQL Server と R の使用](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="next-steps"></a>次のステップ

操作する方法を学習する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データをトレーニング済みの R モデルを永続化と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、このデータ セットに基づく新しいモデルを作成するには比較的簡単である必要があります。 たとえば、これらの追加のモデルを作成してみてください可能性があります。

+ チップの金額を予測する回帰モデル
+ ヒントは、ビッグ、中、または小さいかどうかを予測する多クラス分類モデル

これらの他のサンプルおよびリソースを探索する可能性がありますも。

+ [データ サイエンスのシナリオとソリューション テンプレート](data-science-scenarios-and-solution-templates.md)
+ [高度な分析 (データベース内)](sqldev-in-database-r-for-sql-developers.md)
+ [Machine Learning Server ハウツー ガイドします。](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)
+ [Machine Learning Server の他のリソース](https://docs.microsoft.com//machine-learning-server/resources-more)
