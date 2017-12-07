---
title: "R モデルを配置し、SQL (チュートリアル) で使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e1f0d2f1a003b54856645dd4ec740de64464436b
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>SQL で使用して、R モデルの配置

このレッスンでは、ストアド プロシージャからトレーニング済みモデルを呼び出すことによって、運用環境で R モデルを使用します。 R またはサポートするアプリケーション プログラミング言語から、ストアド プロシージャを呼び出すことができますし、 [!INCLUDE[tsql](../../includes/tsql-md.md)] (など、c#、Java、Python など)、新規の観測値を予測するモデルを使用します。

このサンプルでは、スコア付けのモデルを使用する 2 つの最も一般的な方法を示します。

- **バッチ モードのスコアリング**非常に高速に複数の予測を作成、SQL を渡すことによってクエリまたは入力としてテーブルに必要なときに使用します。 結果のテーブルが返されます、直接テーブルに挿入したりファイルに書き込む場合があります。

- **個々 のスコア付けモード**を一度に 1 つずつ予測を作成する必要がある場合に使用します。 ストアド プロシージャには、一連の個別の値を渡します。 値は、モデルでは、予測を作成するモデルを使用して、機能に対応しているか、確率の値などの別の結果を生成します。 アプリケーション、またはユーザーにその値を表示できます。

## <a name="batch-scoring"></a>バッチ スコアリング

バッチ スコアリングのためのストアド プロシージャは、最初に、PowerShell スクリプトを実行したときに作成されました。 これは、ストアド プロシージャ、 *PredictTipBatchMode*は次の実行します。

- SQL クエリとして一連の入力データを取得する
- 前のレッスンで保存したトレーニング済みのロジスティック回帰モデルを呼び出す
- ドライバーが、0 以外のヒントを取得する確率を予測します。

1. 使用するスクリプト、ストアド プロシージャを通して分ほどかかる*PredictTipBatchMode*です。 このスクリプトは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して、モデルを操作できるようにする方法のさまざまな側面を示しています。
  
    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]
    @input nvarchar(max)
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

    + SELECT ステートメントを使用して、SQL テーブルから保存されたモデルを呼び出します。 モデルとしてテーブルから取得された**varbinary (max)** SQL 変数に格納されているデータ _@lmodel2_ 、およびパラメーターとして渡された*mod*格納されているシステムにプロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

    + スコアリングは SQL クエリとして定義され、SQL 変数内の文字列として格納されているために、入力として使用されるデータ _@input_です。 データは、データベースから取得したと呼ばれるデータ フレームで保存され*InputDataSet*への入力データの既定の名前だけである、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)プロシージャを定義できます別の変数名、パラメーターを使用して必要な場合は *_@input_data_1_name_* です。

    + スコアを生成するために、ストアド プロシージャは `rxPredict` RevoScaleR **ライブラリの** 関数を呼び出します。

    + 戻り値、*スコア*、確率、ドライバーを特定のモデル、ヒントを取得します。 必要に応じて、戻り値を「ヒント」と「ヒントなし」グループに分類する戻り値を簡単にいくつかの種類のフィルターを適用する可能性があります。  たとえば、0.5 未満の確率ことになりますが、ヒントはほとんどありません。
  
2.  バッチ モードでストアド プロシージャを呼び出すには、ストアド プロシージャへの入力として必要なクエリを定義します。 次に、SQL クエリです。動作することを確認する SSMS で実行することができます。

    ```SQL
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

4. R からストアド プロシージャを実行する呼び出し、 **sqlQuery**のメソッド、 **RODBC**パッケージ化し、SQL 接続を使用して`conn`前に定義します。

    ```R
    sqlQuery (conn, q);
    ```

    ODBC エラーが発生した場合は、クエリの構文を確認し、正しい数の引用符があるかどうか。 
    
    アクセス許可エラーが発生した場合は、ログインが、ストアド プロシージャを実行する機能を確認します。

## <a name="single-row-scoring"></a>1 つの行のスコア付け

行ごとに予測モデルを呼び出すときに、一連の個別のケースごとの機能を表す値を渡します。 ストアド プロシージャは、単一予測または確率を返します。 

ストアド プロシージャ*PredictTipSingleMode*この方法を示します。 これは、入力特徴値 (たとえば、座席数とトリップ距離) を表す複数のパラメーター、スコア ストアド R モデルを使用してこれらの機能およびヒント確率を出力します。

1. 場合、ストアド プロシージャ*PredictTipSingleMode*は作成されませんでした、初期の PowerShell スクリプトでは、今すぐ作成する次の TRANSACT-SQL ステートメントを実行することができます。

    ```tsql
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

2. SQL Server Management Studio で使用することができます、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC**プロシージャ (または**EXECUTE**) ストアド プロシージャを呼び出すし、必須の入力を渡すことにします。 たとえば、Management Studio でこのステートメントを実行してください。

    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    ここに渡された値は、それぞれ、変数の_乗客\_カウント_、 _trip_distance_、_トリップ\_時間\_で\_秒_、_ピックアップ\_緯度_、_ピックアップ\_経度_、 _dropoff\_緯度_、および_dropoff\_経度_です。

3. R コードでこの同じ呼び出しを実行するには、だけを次のような全体のストアド プロシージャの呼び出しを含む R 変数を定義します。

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    ここに渡された値は、それぞれ、変数の_乗客\_カウント_、_トリップ\_距離_、_トリップ\_時間\_で\_秒_、_ピックアップ\_緯度_、_ピックアップ\_経度_、 _dropoff\_緯度_、および_dropoff\_経度_です。

4. 呼び出す`sqlQuery`(から、 **RODBC**パッケージ) ストアド プロシージャの呼び出しを含む文字列変数と共に、接続文字列を渡します。

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > SQL Server と R. の両方の優れた統合を提供する R ツールの Visual Studio (RTVS)SQL Server 接続 RODBC の併用の例については、この記事を参照してください: [SQL Server と R を使用します。](https://docs.microsoft.com/en-us/visualstudio/rtvs/sql-server)

## <a name="summary"></a>概要

操作する方法を習得する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データをトレーニング済みの R モデルを永続化と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、このデータ セットに基づく新しいモデルを作成するには比較的簡単にする必要があります。 たとえば、これらの追加のモデルを作成してみてください可能性があります。

- チップの金額を予測する回帰モデル

- 先端が大きな、中、または小さいかどうかを予測する多クラス分類モデル

これらの追加のサンプルおよびリソースの一部を確認することもお勧めします。

+ [データ サイエンスのシナリオとソリューション テンプレート](data-science-scenarios-and-solution-templates.md)

+ [高度な分析 (データベース内)](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [その他のリソース](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>前のレッスン

[R モデルを構築し、SQL Server に保存](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>次の手順

[SQL Server R チュートリアル](sql-server-r-tutorials.md)

[Sqlrutils を使用して、ストアド プロシージャを作成する方法](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
