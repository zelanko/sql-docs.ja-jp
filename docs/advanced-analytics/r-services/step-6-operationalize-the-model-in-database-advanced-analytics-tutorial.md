---
title: "手順 6: モデルを運用する (高度な分析 (データベース内) のチュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
  - "TSQL"
ms.assetid: 52b05828-11f5-4ce3-9010-59c213a674d1
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# 手順 6: モデルを運用する (高度な分析 (データベース内) のチュートリアル)
この手順では、ストアド プロシージャを利用し、モデルを*運用する*方法について説明します。 このストアド プロシージャを他のアプリケーションから直接呼び出し、新しい観察を予測できます。  
  
この手順では、ストアド プロシージャから R モデルを呼び出す 2 通りの方法について説明します。  
  
-   **一括スコア付けモード**: SELECT クエリを利用し、複数行のデータを提供します。 このストアド プロシージャは、入力ケースに対応する観察のテーブルを返します。  
  
-   **個別スコア付けモード**: 個々のパラメーター セットを入力として渡します。  このストアド プロシージャは、1 つの行または値を返します。  
  
まず、一般的なスコア付け方法を見てみましょう。  
  
## 基本のスコア付け  
ストアド プロシージャ _PredictTip_ は、ストアド プロシージャで予測呼び出しをラップする基本構文を示します。  
  
```  
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max)  
AS  
BEGIN  
  
  DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
  FROM nyc_taxi_models);  
  EXEC sp_execute_external_script @language = N'R',  
                                  @script = N'  
mod <- unserialize(as.raw(model));  
print(summary(mod))  
OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
          predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
str(OutputDataSet)  
print(OutputDataSet)  
',  
                                  @input_data_1 = @inquery,  
                                  @params = N'@model varbinary(max)',  
                                  @model = @lmodel2  
  WITH RESULT SETS ((Score float));  
  
END  
  
GO  
  
```  
  
-   SELECT ステートメントは、シリアル化されたモデルをデータベースから取得し、R を利用してさらに処理するために R 変数 `mod` にモデルを保存します。  
  
-   保存される新しいケースは、ストアド プロシージャの最初のパラメーター、`@inquery` で指定された [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリから取得されます。 クエリ データが読み取られると、行が既定のデータ フレーム `InputDataSet` に保存されます。 このデータ フレームは R の `rxPredict` 関数に渡され、スコアが生成されます。  
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,            predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`  
  
    data.frame には 1 つの行を含めることができるため、一括または 1 回のスコア付けに同じコードを利用できます。  
  
-   `rxPredict` 関数により返される値は、(何らかの金額の) チップが与えられる確率を表す**浮動小数**です。  
  
## SELECT クエリを利用した一括スコア付け  
それでは一括スコア付けの動作を確認しましょう。  
  
1.  まず、少量の入力データを用意します。  
  
    ```  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
    (  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null  
    ```  
  
    このクエリは、予測に必要な乗客数とその他の機能を利用し、乗車の "上位 10" 一覧を作成します。  
  
 **[結果]**  
  
*passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance*  
*1  283 0.7 2013-03-27 14:54:50.000   0.5427964547*  
*1  289 0.7 2013-02-24 12:55:29.000   0.3797099614*  
*1  214 0.7 2013-06-26 13:28:10.000   0.6970098661*  
*1  276 0.7 2013-06-27 06:53:04.000   0.4478814362*  
*1  282 0.7 2013-02-21 07:59:54.000   0.5340645749*  
*1  260 0.7 2013-03-27 15:40:49.000   0.5513900727*  
*1  230 0.7 2013-02-05 09:47:59.000   0.5161578519*  
*1  250 0.7 2013-05-08 14:35:51.000   0.5626440915*  
*1  280 0.7 2013-05-11 12:22:01.000   0.5598517959*  
*1  308 0.7 2013-04-10 08:06:00.000   0.4478814362*  
  
このクエリを (ダウンロードに含まれる) ストアド プロシージャ _PredictTipBatchMode_ の入力値として利用します。  
  
2.  まず、少しの時間を取り、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のストアド プロシージャ _PredictTipBatchMode_ のコードを確認します。  
  
    ```  
    /****** Object:  StoredProcedure [dbo].[PredictTipBatchMode]  ******/  
    SET ANSI_NULLS ON  
    GO  
    SET QUOTED_IDENTIFIER ON  
    GO  
  
    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @inquery nvarchar(max)  
    AS  
    BEGIN  
  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
                                      @input_data_1 = @inquery,  
                                      @params = N'@model varbinary(max)',  
                                      @model = @lmodel2  
      WITH RESULT SETS ((Score float));  
  
    END  
    ```  
  
3.  予測を作成するには、変数にクエリ テキストを指定し、次のような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを利用してストアド プロシージャにパラメーターとして渡します。  
  
    ```  
    -- Specify input query  
  
    DECLARE @query_string nvarchar(max)  
    SET @query_string='  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null'  
  
    -- Call stored procedure for scoring  
    EXEC [dbo].[PredictTip] @inquery = @query_string;  
  
    ```  
  
4.  ストアド プロシージャは、"上位 10 の乗車" のそれぞれの予測を表す一連の値を返します。 入力値を見ると、"上位 10 の乗車" のすべてが比較的走行距離の短い、乗客 1 名の乗車です。 このデータに基づくと、このような乗車で運転手がチップを得る確率は非常に少なくなります。  
  
    チップあり/チップなしの結果だけを返すのではなく、予測の確率スコアを返し、WHERE 句を _Score_ 列値に適用し、0.5 や 0.7 などのしきい値を利用して "チップを得る確率が高い" や "チップを得る確率が低い" のようにスコアを分類することもできます。 この手順はストアド プロシージャに含まれていませんが、導入は簡単です。  
  
## 個々の行のスコア付け  
アプリケーションから個々の値を渡し、その値に基づいて 1 つの結果を得ることが望まれる場合もあります。 たとえば、ストアド プロシージャを呼び出し、ユーザーが入力または選択した値を指定するように Excel ワークシート、Web アプリケーション、Reporting Services レポートを設定できます。  
  
このセクションでは、ストアド プロシージャを利用して 1 つの予測を作成する方法について説明します。  
  
1.  少しの時間を取り、(ダウンロードに含まれる) ストアド プロシージャ _PredictTipSingleMode_ のコードを確認してください。  
  
    ```  
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
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
    @input_data_1 = @inquery,  
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  
    @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float',  
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
  
    -   このストアド プロシージャは、乗客数や走行距離など、複数の単一値を入力として取得します。  
  
        外部アプリケーションからこのストアド プロシージャを呼び出す場合、データを R モデルの要件に一致させてください。 場合によっては、入力データを R データ型にキャストまたは変換できなければなりません。あるいは、データ型やデータ長を検証する必要があります。 詳細については、「[R データ型の処理](https://msdn.microsoft.com/library/mt590948.aspx)」を参照してください。  
  
    -   このストアド プロシージャは、保存された R モデルに基づいてスコアを作成します。  
  
2.  手動で値を指定し、お試しください。  
  
    新しい**クエリ** ウィンドウを開き、ストアド プロシージャを呼び出します。機能列のそれぞれにパラメーターを入力します。  
  
    ```  
  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303  
  
    ```  
  
    値は次の機能に利用されます。次の順に並んでいます。  
  
    -   *trip_time_in_secs*  
    -   *pickup_latitude*  
    -   *pickup_longitude*  
    -   *dropoff_latitude*  
    -   *dropoff_longitude*  
  
3.  この結果は、上位 10 の乗車ではチップを得る確率が非常に低いことを示します。すべて比較的走行距離が短く、乗客は 1 名です。  
  
## 結論  
このチュートリアルでは、ストアド プロシージャに埋め込まれた R コードを操作する方法について説明しました。 [!INCLUDE[tsql](../../includes/tsql-md.md)] との統合により、R モデルを展開して予測することと、企業データ ワークフローの一部としてモデルを組み込み、維持することが簡単になります。  
  
  
## 前の手順  
[手順 4: T-SQL を使用してデータ機能を作成する](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## 参照  
[SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
