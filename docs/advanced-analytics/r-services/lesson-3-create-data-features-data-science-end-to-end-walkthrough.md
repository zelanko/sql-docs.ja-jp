---
title: "レッスン 3: データ機能の作成 (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
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
ms.assetid: 4981d4eb-0874-4fe9-82e1-edf99890e27a
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# レッスン 3: データ機能の作成 (データ サイエンスのエンド ツー エンド チュートリアル)
データ エンジニアリングは、機械学習の重要な部分を占める要素の 1 つです。 多くの場合、データを予測モデリングに使用するには、データを変換する必要があります。 必要な機能がデータにない場合、既存の値からデータをエンジニアリングできます。  
  
このモデリング タスクでは、乗車位置と降車位置の未加工の緯度値と経度値を使用するのではなく、2 つの位置間の距離 (マイル単位) が必要です。 この機能を作成するには、 [ヘイバーサイン式](https://en.wikipedia.org/wiki/Haversine_formula)を使用して 2 点間の直線距離を計算します。  
データから機能を作成するには、2 つの方法があります。  
  
-   R と `rxDataStep` 関数を使用する    
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] でカスタム関数を使用する  
  
いずれの方法でも、コードの結果は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソース オブジェクト `featureDataSource`になり、新しい数値機能の `direct_distance`が含まれます。  
  
## <a name="creating-features-using-r"></a>R を使用した機能の作成  

R 言語は統計ライブラリが豊富なことで知られていますが、カスタム データの変換の作成も必要になることがあります。 

+ 新しい R 関数 `ComputeDist` を作成します。この関数で、緯度値と経度値を指定した 2 点間の直線距離を計算します。  
+ 先に作成した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトのデータを変換する関数を呼び出し、新しいデータ ソースの `featureDataSource` に保存します。  

### <a name="create-the-transformation-function"></a>変換関数を作成する  
1.  カスタム R 関数 `ComputeDist` を作成します。 この関数は、緯度値と経度値の 2 組を引数に使用して、2 点間の直線距離を計算します。  この関数は、距離をマイル単位で返します。
  
    ```R  
    env <- new.env()  
    env$ComputeDist <- function(pickup_long, pickup_lat, dropoff_long, dropoff_lat){  
      R <- 6371/1.609344 #radius in mile  
      delta_lat <- dropoff_lat - pickup_lat  
      delta_long <- dropoff_long - pickup_long  
      degrees_to_radians = pi/180.0  
      a1 <- sin(delta_lat/2*degrees_to_radians)  
      a2 <- as.numeric(a1)^2  
      a3 <- cos(pickup_lat*degrees_to_radians)  
      a4 <- cos(dropoff_lat*degrees_to_radians)  
      a5 <- sin(delta_long/2*degrees_to_radians)  
      a6 <- as.numeric(a5)^2  
      a <- a2+a3*a4*a6  
      c <- 2*atan2(sqrt(a),sqrt(1-a))  
      d <- R*c  
      return (d)  
    }  
    ```  
  
    + 1 行目で新しい環境を定義します。 R では、環境を使用して、パッケージなどの名前空間をカプセル化できます。
    + `search()` 関数を使用すると、ワークスペース内の環境を確認できます。 特定の環境内にあるオブジェクトを確認するには、「 `ls(<envname>)`」と入力します。 
    + `$env.ComputeDistance` から始まる行には、ヘイバーサイン式を定義するコードが含まれています。この式で、球面上にある 2 点間の *大圏距離* を計算します。  
 
  
### <a name="apply-the-transformation-function-to-data"></a>変換関数をデータに適用する

関数を定義したら、データに適用して *direct_distance* という新しい機能列を作成します。

1. `RxSqlServerData` コンストラクターを利用し、操作するデータ ソースを作成します。  
  
    ```R  
    featureDataSource = RxSqlServerData(table = "features",   
       colClasses = c(pickup_longitude = "numeric", 
       pickup_latitude = "numeric",   
       dropoff_longitude = "numeric", 
       dropoff_latitude = "numeric",  
       passenger_count  = "numeric", 
       trip_distance  = "numeric",  
       trip_time_in_secs  = "numeric", 
       direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
3.  `rxDataStep` 関数を呼び出し、`env$ComputeDist` 関数を指定のデータに適用します。  
    
    ```R  
    start.time <- proc.time()  
  
    rxDataStep(inData = inDataSource, outFile = featureDataSource,  
         overwrite = TRUE,  
         varsToKeep=c("tipped", "fare_amount", passenger_count", "trip_time_in_secs", 
            "trip_distance", "pickup_datetime", "dropoff_datetime", "pickup_longitude",
            "pickup_latitude", "dropoff_longitude", "dropoff_latitude")
         , transforms = list(direct_distance=ComputeDist(pickup_longitude, 
            pickup_latitude, dropoff_longitude, dropoff_latitude)),
            transformEnvir = env, rowsPerRead=500, reportProgress = 3)  
  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```  
  
    + `rxDataStep` 関数で、指定したデータを変更することができます。 引数には、渡す列の文字ベクトル (*varsToKeep*) と、変換を定義した一覧を含めます。
    + 変換されるすべての列は自動的に出力されるので、 *varsToKeep* 引数に含める必要はありません。
    + また、 *varsToDrop* 引数を使用して、指定した変数を除くソースのすべての列を含めるように指定する方法もあります。  
  
4.  最後に、`rxGetVarInfo` を呼び出し、新しいデータ ソースのスキーマを検査します。  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
    *結果*
    
    *"It takes CPU Time=0.74 seconds, Elapsed Time=35.75 seconds to generate features."*  
    *Var 1: tipped, Type: integer*   
    *Var 2: fare_amount, Type: numeric*   
    *Var 3: passenger_count, Type: numeric*   
    *Var 4: trip_time_in_secs, Type: numeric*   
    *Var 5: trip_distance, Type: numeric*   
    *Var 6: pickup_datetime, Type: character*   
    *Var 7: dropoff_datetime, Type: character*   
    *Var 8: pickup_longitude, Type: numeric*   
    *Var 9: pickup_latitude, Type: numeric*   
    *Var 10: dropoff_longitude, Type: numeric*   
    *Var 11: dropoff_latitude, Type: numeric*   
    *Var 12: direct_distance, Type: numeric*   
  
## <a name="creating-features-using-transact-sql"></a>Transact-SQL を使用した機能の作成  
これまでに R 関数を使用して機能を作成する方法について説明しました。次は、カスタム SQL 関数の `ComputeDist` を作成して同じ処理を実行します。 SQL 関数 `ComputeDist` は既存の `RxSqlServerData` データベース オブジェクトを操作して、既存の緯度値と経度値から新しい距離機能を作成します。  
  
変換結果は、R を使用する場合と同様に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトの `featureDataSource`に保存できます。  
  
多くの場合、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用する機能のエンジニアリングは R よりも高速です。実際のデータとタスクに基づいて最も効率的な方法を選択してください。  

### <a name="define-the-t-sql-custom-function"></a>T-SQL カスタム関数の定義
  
1.  新しい SQL 関数 `fnCalculateDistance` を定義します。  
  
    ```tsql  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END  
  
    ```  

    + この SQL *user-defined function* のコードは、データベースの作成と構成に使用した PowerShell スクリプトの一部として提供されています。  そのため、この関数はデータベースに既に含まれているはずです。  含まれていない場合、SQL Server Management Studio を利用し、タクシーのデータが保存されているものと同じデータベースで関数を生成します。

2.  関数の動作を確認するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] をサポートするアプリケーションから次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。   
  
    ```tsql  
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,       
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude   
    FROM nyctaxi_sample  
  
    ```  
### <a name="call-the-sql-function-from-r"></a>R から SQL 関数を呼び出す

1. R 変数でカスタム関数を呼び出す SQL ステートメントを保存します。  
  
    ```R  
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,  
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude  
        FROM nyctaxi_joined_1_percent  
        tablesample (1 percent) repeatable (98052)"    
    ```  
  
    > [!TIP] このクエリは、先に使用した [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリとは少し違います。 このチュートリアルを短時間で終わらせるために、少ないサンプルのデータを使用するように変更されています。  
  
4.  次のコード行を使用して R 環境から [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を呼び出し、 `featureEngineeringQuery`に定義されているデータに適用します。  
  
    ```R  
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,  
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",           
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",  
             passenger_count  = "numeric", trip_distance  = "numeric",  
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
5.  これで新しい機能が作成されました。`rxGetVarsInfo` を呼び出し、機能テーブルの概要を作成します。  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
## <a name="comparing-r-functions-and-sql-functions"></a>R 関数と SQL 関数の比較

実行してみるとわかりますが、このタスクの場合、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数のアプローチの方が、カスタム R 関数よりも高速です。 そのため、以降の手順ではこれらの計算に [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を使用します。  

次のレッスンでは、このデータを使用して予測モデルを構築し、モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存する方法について説明します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 4: モデルの構築と保存 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>前のレッスン  
[レッスン 2: データの表示と調査 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
