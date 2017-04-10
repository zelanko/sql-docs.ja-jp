---
title: "レッスン 4: モデルの構築と保存 (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
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
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# レッスン 4: モデルの構築と保存 (データ サイエンスのエンド ツー エンド チュートリアル)
このレッスンでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で機械学習モデルを構築し、モデルを保存する方法について説明します。  
  
## <a name="creating-a-classification-model"></a>分類モデルの作成  
構築するモデルは、タクシー運転手が特定の乗車でチップを受け取る可能性が高いかどうかを予測する二項分類子です。 前のレッスンで作成したデータ ソース `featureDataSource,` を使用し、ロジスティック回帰を使用してチップ分類子をトレーニングします。  
  
このモデルで使用する機能は次のとおりです。  
  
-   passenger_count  
  
-   trip_distance  
  
-   trip_time_in_secs  
  
-   direct_distance  

### <a name="create-the-model-using-rxlogit"></a>rxLogit を使用してモデルを作成する  
1.  **RevoScaleR** パッケージに含まれる *rxLogit* 関数を呼び出し、ロジスティック回帰モデルを作成します。  
  
    ```R  
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource))    
    ```  
  
2.  モデルの構築後に、 `summary` 関数を使用して検査し、係数を確認します。  
  
    ```  
    summary(logitObj)  
    ```  

     *結果*

     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*  
     *direct_distance*  
     *Data: featureDataSource (RxSqlServerData Data Source)*  
     *Dependent variable(s): tipped*  
     *Total independent variables: 5*   
     *Number of valid observations: 17068*  
     *Number of missing observations: 0*   
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*  
     *Coefficients:*  
     *Estimate Std.Error z value Pr(>|z|)*   
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*   
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**  
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**   
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**  
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**   
     *---*  
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’0.1 ‘ ’ 1*  
     *Condition number of final variance-covariance matrix: 48.3933*   
     *Number of iterations: 4*  
  
### <a name="use-the-logistic-regression-model-for-scoring"></a>スコアリングにロジスティック回帰モデルを使用する  
モデルが構築されたので、そのモデルを使用して運転手が特定のドライブでチップを受け取る可能性が高いかどうかを予測できます。  
  
1.  まず、スコアリング結果の保存に使用するデータ オブジェクトを定義します。  
  
    ```R  
    scoredOutput <- RxSqlServerData(  
      connectionString = connStr,  
      table = "taxiScoreOutput"  )  
    ```  
    + この例を単純にするために、ロジスティック回帰モデルへの入力は、モデルのトレーニングに使用したものと同じ `featureDataSource` にします。  多くの場合、スコアリングには新しいデータを使用したり、テスト用とトレーニング用のデータを別に確保したりします。  
  
    + 予測結果は _taxiscoreOutput_というテーブルに保存されます。 このテーブルのスキーマは、 `rxSqlServerData`を使用してテーブルを作成したときには定義されていませんが、 *の* scoredOutput `rxPredict`オブジェクト出力から取得されます。  
  
    + 予測値を保存するテーブルを作成するには、 `rxSqlServer` データ関数を実行する SQL ログインが、データベースの DDL 特権を持っている必要があります。 テーブルを作成できないログインの場合、ステートメントは失敗します。  
  
2.  *rxPredict* 関数を呼び出して結果を生成します。  
  
    ```R  
    rxPredict(modelObject = logitObj, data = featureDataSource, outData = scoredOutput,   
                       predVarNames = "Score", type = "response",   
                       writeModelVars = TRUE, overwrite = TRUE)  
    ```  

  
## <a name="plotting-model-accuracy"></a>モデル精度のプロット  
モデル精度の概要を把握するには、*rxRocCurve* 関数を使用して受信者操作特性曲線をプロットします。 *rxRocCurve* は、リモート コンピューティング コンテキストをサポートする RevoScaleR パッケージが提供する新しい関数の 1 つなので、2 つのオプションがあります。  
  
+ `rxRocCurve` 関数を使用してリモート コンピューター コンテキストでプロットを実行し、プロットをローカル クライアントに返すことができます。
+ また、R クライアント コンピューターにデータをインポートして、他の R プロット関数を使用してパフォーマンス グラフを作成することもできます。  
  
このセクションでは、両方の手法を使用します。  
  
### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>リモート (SQL Server) コンピューティング コンテキストでプロットを実行する  
  
1.  *rxRocCurve* 関数を呼び出して、入力として以前に定義したデータを指定します。  
  
    ```R  
    rxRocCurve( "tipped", "Score", scoredOutput)  
    ```  
  
    チップのラベル列 (予測する対象の変数) と、予測にスコアを付ける列名 (_Score_) も指定する必要があります。  
  
2.  R グラフィック デバイスを開くか、RStudio の [**プロット**] ウィンドウをクリックして、生成されたグラフを表示します。  
  
    ![ROC plot for the model](../../advanced-analytics/r-services/media/rsql-e2e-rocplot.png "ROC plot for the model")  

    このグラフは、リモート コンピューティング コンテキストで作成され、R 環境に返されます。   
    
### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>SQL Server のデータを使用して、ローカル コンピューティング コンテキストでプロットを作成する  
  
1.  *rxImport* 関数を使用して、指定したデータをローカルの R 環境に読み込みます。  
  
    ```R  
    scoredOutput = rxImport(scoredOutput)  
    ```  
  
2.  データをローカル メモリに読み込むと、**ROCR** ライブラリを呼び出していくつかの予測を作成し、プロットを生成することができます。  
  
    ```R  
    library('ROCR')  
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped)  
  
    acc.perf = performance(pred, measure = 'acc')  
    plot(acc.perf)  
    ind = which.max( slot(acc.perf, 'y.values')[[1]] )  
    acc = slot(acc.perf, 'y.values')[[1]][ind]  
    cutoff = slot(acc.perf, 'x.values')[[1]][ind]  
    ```  
  
3.  次のプロットは両方の場合に生成されます。  
  
    ![plotting model performance using R](../../advanced-analytics/r-services/media/rsql-e2e-performanceplot.png "plotting model performance using R")  
  
## <a name="deploying-a-model"></a>モデルの配置  

モデルを構築して、そのパフォーマンスが良好であると確認したら、モデルの "*運用段階*" に移行できます。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを使用して R モデルを呼び出すことができるので、クライアント アプリケーションで簡単に R を使用できるようになります。  
  
ただし、外部アプリからモデルを呼び出すには、運用に使用するデータベースにモデルを保存する必要があります。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で、トレーニングしたモデルは、 **varbinary(max)**型の 1 列にバイナリ形式で保存されます。

そのため、R から SQL Server にトレーニングしたモデルを移動するには、次の手順を行う必要があります。  
  
+ モデルを 16 進数文字列にシリアル化する
+ シリアル化されたオブジェクトをデータベースに転送する
+ varbinary(max) 列にモデルを保存する  
  
このセクションでは、モデルを永続化する方法と、モデルを呼び出して予測する方法について説明します。  
  
### <a name="serialize-the-model"></a>モデルのシリアル化  
  
+  ローカルの R 環境では、モデルをシリアル化して変数に保存します。  
  
    ```R  
    modelbin <- serialize(logitObj, NULL)  
    modelbinstr=paste(modelbin, collapse="")  
    ```  
  
    *serialize* 関数は R の **base** パッケージに含まれており、シリアル化の単純な低レベル インターフェイスを接続に提供します。 詳細については、 [http://www.inside-r.org/r-doc/base/serialize](http://www.inside-r.org/r-doc/base/serialize)を参照してください。  
  
### <a name="move-the-model-to-sql-server"></a>モデルを SQL Server に移動する

+ ODBC 接続を開き、ストアド プロシージャを呼び出してデータベースの列にモデルのバイナリ表現を保存します。 
  
    ```R  
    library(RODBC)  
    conn <- odbcDriverConnect(connStr )  
  
    # persist model by calling a stored procedure from SQL  
    q<-paste("EXEC PersistModel @m='", modelbinstr,"'", sep="")  
    sqlQuery (conn, q)    
    ```  

モデルをテーブルへの保存に必要なステートメントは、INSERT のみです。 ただし、ここではさらに簡単にするために、_PersistModel_ ストアド プロシージャを使用しています。 
 
参考までに、ストアド プロシージャの完全なコードを次に示します。  
  
```tsql  
CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)  
AS  
BEGIN  
        -- SET NOCOUNT ON added to prevent extra result sets from  
        -- interfering with SELECT statements.  
        SET NOCOUNT ON;  
        insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))  
END   
```  
> [!TIP] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での R モデルの管理と更新が簡単になるように、このストアド プロシージャのようなヘルパー関数を作成することをお勧めします。  
  
  
### <a name="invoke-the-saved-model"></a>保存したモデルを呼び出す  
モデルをデータベースに保存した後は、システム ストアド プロシージャ [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードから直接呼び出すことができます。  
  
たとえば、予測を生成するには、データベースに接続し、一部の入力データと共に、保存したモデルを入力として使用するストアド プロシージャを実行します。  
  
ただし、よく使用するモデルがある場合、入力クエリとモデルの呼び出しや、他のパラメーターをカスタム ストアド プロシージャにラップする方が簡単です。  
  
次のレッスンでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、保存したモデルに対してスコアリングを実行する方法について説明します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 5: モデルの配置と使用 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>前のレッスン  
[レッスン 3: データ機能の作成 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  
