---
title: R モデルをデプロイし、SQL (チュートリアル) での使用 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a5d8b7ac8bd36a6ce76b895b2dde4a07f5ea96
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085354"
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>R モデルを展開し、SQL で使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンでは、ストアド プロシージャからトレーニング済みモデルを呼び出すことによって、運用環境で R モデルを使用します。 R またはサポートするアプリケーション プログラミング言語からストアド プロシージャを呼び出すことができますし、 [!INCLUDE[tsql](../../includes/tsql-md.md)] (など、c#、Java、Python など)、モデルを使用して新しい観察結果を予測します。

このサンプルでは、スコアリングにモデルを使用する 2 つの最も一般的な方法を示しています。

- **バッチ スコアリング モード**非常に高速に複数の予測を作成、SQL を渡すことによってクエリまたはテーブルとして入力する必要がある場合に使用されます。 結果のテーブルが返されます、直接テーブルに挿入したり、ファイルに書き込む可能性があります。

- **個別スコアリング モード**一度に 1 つずつ予測を作成する必要がある場合に使用されます。 ストアド プロシージャには、一連の個別の値を渡します。 値は、予測を作成するモデルを使用すると、モデル内の機能に対応していますか、確率値などの別の結果を生成します。 アプリケーション、またはユーザーにその値を表示できます。

## <a name="batch-scoring"></a>バッチ スコアリング

バッチ スコアリングのためのストアド プロシージャは、最初に PowerShell スクリプトを実行したときに作成されました。 これは、ストアド プロシージャ、 *PredictTipBatchMode*は次の処理します。

- SQL クエリとして一連の入力データを取得する
- 前のレッスンで保存したトレーニング済みのロジスティック回帰モデルを呼び出す
- ドライバーが、0 以外のヒントを取得する確率を予測します。

1. スクリプト、ストアド プロシージャを調査のために少し時間がかかる*PredictTipBatchMode*します。 このスクリプトは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して、モデルを操作できるようにする方法のさまざまな側面を示しています。
  
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

    + SQL テーブルから、格納されたモデルを呼び出すには、SELECT ステートメントを使用します。 モデルがテーブルから取得した**varbinary (max)** SQL 変数に格納されたデータを _\@lmodel2_、およびパラメーターとして渡された*mod*システムにストアド プロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

    + スコア付けは SQL クエリとして定義され、文字列として、SQL 変数に格納されているは、入力として使用されるデータ_\@入力_します。 呼ばれるデータ フレームに格納されているように、データベースからデータを取得すると、 *InputDataSet*への入力データの既定の名前だけである、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)プロシージャを定義できます別の変数名、パラメーターを使用して必要な場合は  *_\@input_data_1_name_* します。

    + スコアを生成するために、ストアド プロシージャは `rxPredict` RevoScaleR **ライブラリの** 関数を呼び出します。

    + 戻り値、*スコア*、確率、そのドライバー モデルを指定するには、ヒントを取得します。 必要に応じて、ある種のフィルターは、戻り値を「ヒント」と「チップなし」グループに分類に返される値を簡単に適用できます。  たとえば、確率が 0.5 よりも小さいでは、ヒントはほとんどありませんが意味します。
  
2.  バッチ モードでは、ストアド プロシージャを呼び出して、ストアド プロシージャへの入力として必要なクエリを定義します。 次に、SQL クエリ。SSMS の動作の確認をで実行することができます。

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

4. ストアド プロシージャ R からを実行するには、呼び出し、 **sqlQuery**のメソッド、 **RODBC**パッケージ化し、SQL 接続を使用して、`conn`前に定義します。

    ```R
    sqlQuery (conn, q);
    ```

    ODBC エラーが発生する場合は、クエリの構文を確認し、適切な数の引用符があるかどうか。 
    
    アクセス許可エラーが発生する場合は、ログインには、ストアド プロシージャを実行する機能を確認します。

## <a name="single-row-scoring"></a>単一行のスコアリング

行ごとに予測モデルを呼び出すときに、一連の個別の各ケースの機能を表す値を渡します。 ストアド プロシージャは、1 つの予測と確率を返します。 

ストアド プロシージャ*PredictTipSingleMode*この方法を示します。 これは、入力特徴値 (たとえば、乗客数、乗車距離) を表す複数のパラメーター、スコアを格納された R モデルを使用してこれらの機能、およびヒント確率を出力します。

1. 場合、ストアド プロシージャ*PredictTipSingleMode*は作成されませんでした、初期の PowerShell スクリプトによって、今すぐ作成するのには、次の TRANSACT-SQL ステートメントを実行することができます。

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

2. SQL Server Management studio で使用することができます、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC**プロシージャ (または**EXECUTE**)、ストアド プロシージャを呼び出すし、必要な入力を渡すことにします。 たとえば、Management Studio でこのステートメントを実行してみてください。

    ```SQL
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
    > R Tools for Visual Studio (RTVS) は、SQL Server と R. の両方の優れた統合を提供します。RODBC を使用して、SQL Server 接続の例については、この記事を参照してください: [SQL Server と R の使用](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="summary"></a>まとめ

操作する方法を学習する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データをトレーニング済みの R モデルを永続化と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、このデータ セットに基づく新しいモデルを作成するには比較的簡単である必要があります。 たとえば、これらの追加のモデルを作成してみてください可能性があります。

- チップの金額を予測する回帰モデル

- ヒントは、ビッグ、中、または小さいかどうかを予測する多クラス分類モデル

これらの追加のサンプルおよびリソースの一部を確認することもお勧めします。

+ [データ サイエンスのシナリオとソリューション テンプレート](data-science-scenarios-and-solution-templates.md)

+ [高度な分析 (データベース内)](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [その他のリソース](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>前のレッスン

[R モデルを構築し、SQL Server に保存](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>次のステップ

[SQL Server R チュートリアル](sql-server-r-tutorials.md)

[Sqlrutils を使用してストアド プロシージャを作成する方法](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
