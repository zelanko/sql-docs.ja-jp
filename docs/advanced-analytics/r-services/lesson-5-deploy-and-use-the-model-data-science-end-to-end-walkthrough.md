---
title: "レッスン 5: モデルの配置と使用 (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# レッスン 5: モデルの配置と使用 (データ サイエンスのエンド ツー エンド チュートリアル)
このレッスンでは、永続化されたモデルをストアド プロシージャでラップすることにより、運用環境で R モデルを使用します。 R または [!INCLUDE[tsql](../../includes/tsql-md.md)] をサポートするアプリケーション プログラミング言語 (C#、Java、Python など) からストアド プロシージャを呼び出すことで、モデルを使用して新しい観察結果を予測します。  
  
2 つの異なる方法で、スコアリングのためにモデルを呼び出すことができます。  
  
-   **バッチ スコアリング モード** では、SELECT クエリからの入力に基づいて複数の予測を作成できます。  
  
-   **個別スコアリング モード** では、個々のケースの機能の値のセットをストアド プロシージャ (結果として単一予測やその他の値を返す) に渡すことによって、一度に 1 つずつ予測を作成できます。  
  
個別スコアリングとバッチ スコアリングの両方の手法を使用して予測を作成する方法を学習します。  
  
## <a name="batch-scoring"></a>バッチ スコアリング  
便宜上、レッスン 1 で最初に PowerShell スクリプトを実行したときに作成されたストアド プロシージャを使用することができます。 このストアド プロシージャでは次の処理が行われます。  
  
-   SQL クエリとして一連の入力データを取得する    
-   前のレッスンで保存したトレーニング済みのロジスティック回帰モデルを呼び出す    
-   運転手がチップを受け取ることができる確率を予測する  
  
### <a name="use-the-stored-procedure-predicttipbatchmode"></a>ストアド プロシージャ PredictTipBatchMode を使用する

1. 少し時間を割いて、ストアド プロシージャ *PredictTipBatchMode* を定義するスクリプトについて説明します。 このスクリプトは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して、モデルを操作できるようにする方法のさまざまな側面を示しています。  
  
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

    + 保存されたモデルを呼び出す SELECT ステートメントに注意してください。 **varbinary (max)**型の列を使用することで、SQL テーブル内にトレーニング済みのモデルを格納できます。 このコードでは、モデルがテーブルから取得され、SQL 変数 _@lmodel2_ に格納された後、パラメーター *mod* としてシステム ストアド プロシージャ [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) に渡されます。
    + スコアリングに使用される入力データは、文字列としてストアド プロシージャに渡されます。  
  
        この特定のモデルの入力データを定義するには、有効なデータを返すクエリを作成します。 データがデータベースから取得されるとき、データは *InputDataSet*と呼ばれるデータ フレームに保存されます。 このデータ フレーム内のすべての行が、バッチ スコアリングに使用されます。
        + *InputDataSet* が [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) プロシージャへの入力データの既定の名前です。必要に応じて、別の変数名を定義できます。
        + スコアを生成するために、ストアド プロシージャは **RevoScaleR** ライブラリの *rxPredict* 関数を呼び出します。
    + このストアド プロシージャの戻り値 *Score*は、運転手がチップを受け取ることができる予測確率です。  
  
2.  (省略可能) 戻り値に特定の種類のフィルターを適用して、戻り値を "チップあり" グループと "チップなし" グループに容易に分類できます。  たとえば、確率が 0.5 よりも小さい場合、チップをもらえない可能性が高いと考えられます。  
  
3.  バッチ モードでストアド プロシージャを呼び出します。  
  
    ```R  
    input = "N' 
      SELECT TOP 10 
          a.passenger_count AS passenger_count,   
          a.trip_time_in_secs AS trip_time_in_secs,  
          a.trip_distance AS trip_distance,  
          a.dropoff_datetime AS dropoff_datetime,    
          dbo.fnCalculateDistance(
            pickup_latitude, 
            pickup_longitude, 
            dropoff_latitude,
            dropoff_longitude) AS direct_distance   
      FROM  
      
      (SELECT medallion, hack_license, pickup_datetime,   
      passenger_count,trip_time_in_secs,trip_distance,    
      dropoff_datetime, pickup_latitude, pickup_longitude,   
      dropoff_latitude, dropoff_longitude from nyctaxi_sample)a  
      
      LEFT OUTER JOIN  
 
      ( SELECT medallion, hack_license, pickup_datetime 
        FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b  

      ON a.medallion=b.medallion 
        AND a.hack_license=b.hack_license 
        AND a.pickup_datetime=b.pickup_datetime  

      WHERE b.medallion is null  
    '"  
    q<-paste("EXEC PredictTipBatchMode @inquery = ", input, sep="")  
    sqlQuery (conn, q)  
  
    ```  
  
## <a name="single-row-scoring"></a>単一行のスコアリング  

クエリを使用して、保存されている R モデルに入力値を渡す代わりに、ストアド プロシージャに引数として特徴を提供することができます。  

### <a name="use-the-stored-procedure-predicttipsinglemode"></a>ストアド プロシージャ PredictTipSingleMode を使用する
1.  少し時間を割いて、次のコードが、既にデータベースに作成されているストアド プロシージャ *PredictTipSingleMode* 用であることを確認します。  
  
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
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, 
            @trip_distance,  
            @trip_time_in_secs,  
            @pickup_latitude,  
            @pickup_longitude,  
            @dropoff_latitude,  
            @dropoff_longitude)  
        '  
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
      @params = N'@model varbinary(max),
                @passenger_count int,
                @trip_distance float,
                @trip_time_in_secs int ,  
                @pickup_latitude float ,
                @pickup_longitude float ,
                @dropoff_latitude float ,
                @dropoff_longitude float',  
                @model = @lmodel2,  
                @passenger_count =@passenger_count ,  
                @trip_distance=@trip_distance,  
                @trip_time_in_secs=@trip_time_in_secs,    
                @pickup_latitude=@pickup_latitude,  
                @pickup_longitude=@pickup_longitude,  
                @dropoff_latitude=@dropoff_latitude,  
                @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END    
    ```  
  
    このストアド プロシージャは、乗客数、乗車距離などの機能の値を入力として取得し、保存されている R モデルを使用してこれらの機能にスコアを付け、スコアを出力します。  
  
### <a name="call-the-stored-procedure-and-pass-parameters"></a>ストアド プロシージャを呼び出してパラメーターを渡す

1. SQL Server Management Studio で、[!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** を使用して、ストアド プロシージャを呼び出し、必要な入力に渡すことができます。 」を参照してください。  
    ```tsql  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303   
    ```  
  
    ここで渡される値は、それぞれ、変数 _passenger_count_、 _trip_distance_、 _trip_time_in_secs_、 _pickup_latitude_、 _pickup_longitude_、 _dropoff_latitude_、 _dropoff_longitude_に対応します。  
  
2.  R コードからこの同じ呼び出しを実行するには、ストアド プロシージャの呼び出しをすべて含む R 変数を定義するだけです。 
  
    ```R  
    q = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 "  
    ```  
  
    ここで渡される値は、それぞれ、変数 _passenger_count_、 _trip_distance_、 _trip_time_in_secs_、 _pickup_latitude_、 _pickup_longitude_、 _dropoff_latitude_、 _dropoff_longitude_に対応します。  
  
### <a name="generate-scores"></a>スクリプトの生成

1. **RODBC** パッケージの *sqlQuery* 関数を呼び出して、ストアド プロシージャの呼び出しを含む、接続文字列と文字列変数を渡します。  
  
    ```R  
    # predict with stored procedure in single mode  
    sqlQuery (conn, q)   
    ```  
  
    **RODBC** の詳細については、[http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery](http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery) をご覧ください。  
  
## <a name="conclusion"></a>まとめ  
ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを使用し、トレーニング済みの R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に保持する方法を学習したので、このデータセットに基づいて比較的容易にいくつか追加のモデルを作成できます。 たとえば、次のようなモデルを作成できます。  
  
-   チップの金額を予測する回帰モデル    
-   チップが多い、普通、少ないのいずれになるかを予測するマルチクラス分類モデル  

これらの追加のサンプルおよびリソースの一部を確認することもお勧めします。 
+ [データ サイエンスのシナリオとソリューション テンプレート](../../advanced-analytics/r-services/data-science-scenarios-and-solution-templates.md)
+ [高度な分析 (データベース内)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)
+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r) (Microsoft R - データ分析を確認する)
+ [その他のリソース](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)
## <a name="previous-lesson"></a>前のレッスン  
[レッスン 4: モデルの構築と保存 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>参照  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
