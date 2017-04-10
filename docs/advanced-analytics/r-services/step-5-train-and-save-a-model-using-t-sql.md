---
title: "手順 5: 手順 5: T-SQL を使用してモデルをトレーニングし保存する (高度な分析 (データベース内) のチュートリアル) | Microsoft Docs"
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
ms.assetid: 3282e8ed-b515-4ed5-8543-fcef68629a92
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# 手順 5: 手順 5: T-SQL を使用してモデルをトレーニングし保存する (高度な分析 (データベース内) のチュートリアル)
この手順では、R を使用して機械学習モデルをトレーニングする方法を学習します。R パッケージは既に [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] と共にインストールされているので、ストアド プロシージャからアルゴリズムを呼び出すことができます。 作成したデータ機能を使用してモデルをトレーニングして、トレーニングしたモデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存します。  
  
## ストアド プロシージャを使用して R モデルを構築する  
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]と共にインストールされている R ランタイムへの呼び出しは、[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) システム ストアド プロシージャを使用して実行されます。 ただし、モデルの再トレーニングする必要がある場合、別のストアド プロシージャで sp_execute_exernal_script への呼び出しをカプセル化した方が簡単でしょう。  
  
このセクションでは、準備したばかりのデータを使用してストアド プロシージャを作成し、モデルを構築します。 このストアド プロシージャでは、入力データを定義し、R パッケージを使用してロジスティック回帰モデルを作成します。  
  
#### ストアド プロシージャを作成するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で新しいクエリ ウィンドウを開き、次のステートメントを実行して、ストアド プロシージャ _TrainTipPredictionModel_ を作成します。  
  
    ストアド プロシージャには、既に入力データの定義が含まれているため、入力クエリを提供する必要はありません。  
  
    ```  
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
  
    このストアド プロシージャは、モデルのトレーニングの一環としてこれらの動作を実行します。  
  
    -   モデルのテストに一部のデータが確実にあるよう、データの 70% がタクシー データ テーブルからランダムに選択されます。  
  
    -   SELECT クエリによって、カスタムのスカラー関数 _fnCalculateDistance_ が使用され、乗車位置と降車位置直線距離が計算されます。  クエリの結果は R の既定の入力変数 `InputDataset` に格納されます。  
  
    -   R スクリプトによって、ロジスティック回帰モデルを作成するために、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の拡張 R 関数の 1 つである `rxLogit` 関数が呼び出されます。  
  
        二項変数 _tipped_ が *ラベル*または結果列として使用され、モデルは、_passenger_count_、_trip_distance_、_trip_time_in_secs_、および _direct_distance_ の機能列を使用して調整されます。  
  
    -   R 変数 `logitObj` に保存されたトレーニング済みのモデルはシリアル化され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に出力するためにデータ フレームに入れられます。 その出力は、将来の予測に使用できるようにデータベース テーブル _nyc_taxi_models_ に挿入されます。  
  
2.  ステートメントを実行してストアド プロシージャを作成します。  
  
#### ストアド プロシージャを使用して R モデルを作成する  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でステートメントを実行します。  
  
    ```  
    EXEC TrainTipPredictionModel  
    ```  
  
    データの処理とモデルの調整には、しばらく時間がかかる場合があります。 R の **stdout** ストリームにパイプ出力されるメッセージが、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の **[メッセージ]** ウィンドウに表示されます。 例:  
  
  
*STDOUT message(s) from external script: Rows Read: 1193025, Total Rows Processed: 1193025, Total Chunk Time: 0.093 seconds*       
  
連続したデータ チャンクは読み取られ処理されます。 個別の関数 `rxLogit` の変数とテスト メトリックを示すメッセージが表示される場合もあります。  
  
2.  テーブル *nyc_taxi_models* を開きます。 _model_ 列にシリアル化されたモデルを含む新しい行が 1 つ追加されます。  
  
  
  
*model*  
*0x580A00000002000302020....*  
  
次の手順では、トレーニング済みのモデルを使用して予測を作成します。  
  
## 次の手順  
[手順 6: モデルを運用する](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md)  
  
## 前の手順  
[手順 4: T-SQL を使用してデータ機能を作成する](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## 参照  
[SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
