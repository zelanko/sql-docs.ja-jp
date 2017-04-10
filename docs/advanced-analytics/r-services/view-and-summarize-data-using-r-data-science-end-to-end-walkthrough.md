---
title: "R を使用したデータの表示と集計 (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
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
ms.assetid: 358e1431-8f47-4d32-a02f-f90e519eef49
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# R を使用したデータの表示と集計 (データ サイエンスのエンド ツー エンド チュートリアル)
ここで、R コードを使用して同じデータを操作します。 さらに、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]に含まれている **RevoScaleR** パッケージの関数を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーのコンテキストでデータの集計を生成し、結果を R 環境に返送する方法についても学習します。  

R スクリプトは、このチュートリアルで提供しており、データ オブジェクトの作成、集計の生成、モデルの構築に必要なすべてのコードを含んでいます。 R スクリプト ファイル **RSQL_RWalkthrough.R**は、スクリプト ファイルをインストールした場所にあります。  
+ R の使用経験がある場合、一度にすべてスクリプトを実行できます。
+ RevoScaleR の使用方法を学習中の人のために、このチュートリアルでスクリプトを 1 行ずつ説明します。
+ スクリプトから個別行を実行するには、ファイル内の行を強調表示し、Ctrl を押しながら ENTER を押します。    
  
> [!TIP]  このチュートリアルの残りの部分を後で実行する場合は、R ワークスペースを保存します。  こうすることで、データ オブジェクトとその他の変数を再利用する準備ができます。   

## <a name="defining-sql-server-data-sources-and-compute-contexts"></a>SQL Server のデータ ソースと計算コンテキストの定義
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを取得し、R コードで使用するには、次の操作が必要です。  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続を作成します。  
- 必要なデータを含むクエリを定義するか、テーブルまたはビューを指定します。    
- R コードの実行時に使用する計算コンテキストを 1 つまたは複数定義します。    
-   任意で、データ ソースに適用できる関数を定義します。  
 

### <a name="load-the-revoscaler-library"></a>RevoScaleR ライブラリを読み込みます。

+  **RevoScaleR** パッケージがまだ読み込まれていない場合、次を実行します。
    ```R
    library("RevoScaleR")`.  
    ```  
    エラーが発生した場合は、R 開発環境で RevoScaleR パッケージを含むライブラリを使用していることを確認します。 現在のパスを表示するには、`.libPaths())` のようなコマンドを使用します。  

    初めて **RevoScaleR** パッケージを使用する場合は、`help("RevoScaleR")` または `help("RxSqlServerData")` と入力して、R 環境でオンライン ヘルプを取得してください。  

### <a name="create-connection-strings"></a>接続文字列を作成する


1. 接続文字列を定義します。 このチュートリアルでは、SQL ログインと Windows 統合認証の両方の例を提供しています。 R コードにパスワードが保存されないように、可能であれば、Windows 認証の使用が推奨されます。

    使用するアカウントには、データを読み取り、指定されたデータベースに新しいテーブルを作成するアクセス許可が必要です。 SQL データベースにユーザーを追加し、それらに正しいアクセス許可を与える方法については、「[アップグレードとインストールに関してよく寄せられる質問 (SQL Server R Services)](../Topic/Post-Installation%20Server%20Configuration%20(SQL%20Server%20R%20Services).md)」を参照してください。 

    ```R  
    # SQL authentication  
    connStrSql <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;    Uid=<user_name>;Pwd=<user password>"  

    # Windows authentication  
    connStrWin <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;Trusted_Connection=Yes" 
    
    # Use one of the connection strings
    connStr <- connStrWin 
    ```
    > [!NOTE] サーバー名、データベース名、ユーザー名、およびパスワードを必要に応じて編集します。 
      
  
### <a name="define-and-set-a-compute-context"></a>計算コンテキストを定義し、設定する  

次に、SQL Server コンピューターで R コードの実行を可能にする*計算コンテキスト*を定義します。 一般に、R を使用している場合、すべての操作がコンピューター上のメモリ内で実行します。 ただし、R 操作を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで実行するように指示した場合、いくつかのタスクを並列実行できます。サーバー リソースが活かされます。  

既定では、計算コンテキストはローカルです。つまり、操作に合わせ、計算コンテキストを明示的に設定する必要があります。  


1.  まず、コンピューティング コンテキストを作成するために使用するいくつかの変数を定義します。  
  
    ```R    
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")  
    sqlWait <- TRUE  
    sqlConsoleOutput <- FALSE    
    ```    
    -   ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューター間で双方向に R オブジェクトをシリアル化する際、R では、一時ディレクトリが使用されます。 *sqlShareDir* として使用されるローカル ディレクトリを指定するか、既定のものをそのまま利用できます。  
  
    -   *sqlWait* を利用し、R に結果を待機させるかどうかを指示します。  待機するジョブと待機しないジョブの詳細については、「[ScaleR Distributed Computing](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing)」 (ScaleR 分散コンピューティング) を参照してください。
  
    -   引数 *sqlConsoleOutput* を使用し、R コンソールから出力を表示しないことを指示します。  
  
2.  既に定義されている変数と接続文字列で計算コンテキスト オブジェクトを作成し、R 変数 *sqlcc* に保存します。  
  
    ```  
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir,   
                        wait = sqlWait, consoleOutput = sqlConsoleOutput)  
    ```  

4. コンピューティング コンテキストを設定します。
    ```R
    rxSetComputeContext(sqlcc)  
    ```  
   + `rxSetComputeContext` は以前にアクティブな計算コンテキストを非表示で返すので、それを利用できます。
   + `rxGetComputeContext` はアクティブな計算コンテキストを返します  
  
    計算コンテキストの設定は、**RevoScaleR** パッケージ内の関数を使用する操作にのみ影響を与えます。計算コンテキストは、オープン ソース R 操作を実行する方法には影響しません。  
  
### <a name="create-an-rxsqlserver-data-object"></a>RxSqlServer データ オブジェクトの作成  

操作する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続を定義したので、そのデータ接続オブジェクトを基準として使用して、さまざまなデータ ソースを定義できます。 *データソース* は、トレーニング機能、探索機能、スコア付け機能、生成機能など、タスクに使用するデータのセットを指定します。  
    
SQL Server データのセットを定義します。*RxSqlServer* 関数を使用し、接続文字列と取得するデータの定義を渡します。  
  
1. SQL ステートメントを文字列変数として保存します。 このクエリにより、モデルのトレーニングに使用するデータが定義されます。    
    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, 
           passenger_count,trip_time_in_secs,trip_distance,   
           pickup_datetime, dropoff_datetime, pickup_longitude, 
           pickup_latitude, dropoff_longitude,    
           dropoff_latitude 
           FROM nyctaxi_sample"  
    ```

2. SQL Server データ ソースにクエリの定義を引数として渡します。 *colClasses* 引数により、SQL がマッピングされ、返すデータのスキーマが指定されます。 

    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, 
         connectionString = connStr,
         colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
         dropoff_longitude = "numeric", dropoff_latitude = "numeric"),  
         rowsPerRead=500)  
    ```
    
    + 引数 *colClasses* により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R の間でデータを移動するときに使用する列の型が指定されます。これが重要なのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が R と異なるデータ型とその他のデータ型を使用するためです。 詳細については、「[R データ型の処理](../../advanced-analytics/r-services/working-with-r-data-types.md)」を参照してください。  
  
    + 引数 *rowsPerRead* はメモリ使用量を管理し効率的な計算を行うために重要な役割を果たします。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 内の拡張分析関数の大部分は、データをチャンク単位で処理し、中間結果を蓄積していきます。すべてのデータを読み取ったら、最終的な計算結果を返します。  `rowsPerRead` パラメーターを追加して、各チャンクに読み取られる処理対象のデータ行の数を制御できます。  このパラメーターの値が大きすぎる場合、そのような大規模なデータ チャンクを効率的に処理するのに十分なメモリは備えていないため、データ アクセスは遅くなる可能性があります。  システムによっては、 `rowsPerRead` の値が小さすぎる場合も、パフォーマンスが低下することがあります。  

> [!TIP] *inDataSource* データ オブジェクトを作成したら、必要な回数だけこのオブジェクトを再利用し、使用されているデータと変数に関する基本情報を取得したり、データを操作および変換したり、またはモデルのトレーニングに使用したりすることができます。  ただし、*inDataSource* オブジェクト自体には、SQL クエリからのデータは何もまだ含まれていません。 *rxImport* や *rxSummary* のような関数を実行するまで、データはローカル環境に入りません。          
  
## <a name="using-the-sql-server-data-in-r"></a>R で SQL Server データを使用する  
これで、データ ソースに R 関数を適用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データの探索、集計、グラフの作成ができます。 ここでは、リモート コンピューティング コンテキストをサポートする [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で提供されている機能のいくつかを試してみましょう。  
  
-   `rxGetVarInfo`: リモート データ オブジェクト内の任意のデータ フレームまたはデータのセット (さらにいくつかのリストやマトリックス) でこの関数を使用して、最大値や最小値、データ型、因子列内のレベル数などの情報を取得します。  
  
    あらゆる種類のデータ入力、機能変換、または機能エンジニアリングの後にこの関数を実行することを検討してください。 そうすることで、モデルで使用するすべての機能が予期したデータ型を持つことを確認し、エラーを回避できます。  
 
  
-   `rxSummary`: この関数を使用して、個々の変数に関するより詳細な統計情報を取得します。 さらに、値の変換、因子水準を使用した集計の計算、および再利用のための集計の保存もできます。  
  
  
### <a name="inspect-variables-in-the-data-source"></a>データ ソース内の変数を検査する  
    
+ データ ソース `rxGetVarInfo`を引数として使用して、関数  `inDataSource` を呼び出し、データ ソース内の変数とそれらのデータ型の一覧を取得します。  
  
    ```R  
    rxGetVarInfo(data = inDataSource)  
    ```  
  
    *結果:*  
    *Var 1: tipped, Type: integer*  
    *Var 2: fare_amount, Type: numeric*  
    *Var 3: passenger_count, Type: integer*  
    *Var 4: trip_time_in_secs, Type: numeric, Storage: int64*  
    *Var 5: trip_distance, Type: numeric*  
    *Var 6: pickup_datetime, Type: character*  
    *Var 7: dropoff_datetime, Type: character*  
    *Var 8: pickup_longitude, Type: numeric*  
    *Var 9: pickup_latitude, Type: numeric*  
    *Var 10: dropoff_longitude, Type: numeric*  
  
### <a name="create-a-summary-using-r"></a>R を使用して概要を作成する

+ RevoScaleR 関数 `rxSummary` を呼び出し、乗客の数に基づいて料金を集計します。 
    ```R  
    start.time <- proc.time()  
    rxSummary(~fare_amount:F(passenger_count), data = inDataSource)  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2), 
      " seconds to summarize the inDataSource.", sep=""))
    ```  
 
    + `rxSummary` への最初の引数は、集計する数式または語を指定します。 ここでは、集計する前に、`F()` 関数を使用して、passenger_count 内の値を因子に変換します。  
    + 出力する統計情報を指定しない場合、 `rxSummary` は平均、StDev、最小、最大、有効な結果と不足している結果の数を出力します。  
    + この例には、パフォーマンスを比較できるように、関数の開始時間と終了時間を追跡するコードも含まれています。  
  
    *結果*  
    *rxSummary(formula = ~fare_amount:F(passenger_count), data = inDataSource)*  
    *Summary Statistics Results for: ~fare_amount:F(passenger_count)*  
    *Data: inDataSource (RxSqlServerData Data Source)*  
    *Number of valid observations: 1000*   
    *Name                          Mean    StdDev   Min Max ValidObs MissingObs*  
    *fare_amount:F_passenger_count 12.4875 9.682605 2.5 64  1000     0*   
    *Statistics by category (6 categories):   *Category                             F_passenger_count Means    StdDev    Min*   
    *fare_amount for F(passenger_count)=1 1                 12.00901  9.219458  2.5*  
    *fare_amount for F(passenger_count)=2 2                 11.61893  8.858739  3.0*  
    *fare_amount for F(passenger_count)=3 3                 14.40196 10.673340  3.5*  
    *fare_amount for F(passenger_count)=4 4                 13.69048  8.647942  4.5*  
    *fare_amount for F(passenger_count)=5 5                 19.30909 14.122969  3.5*  
    *fare_amount for F(passenger_count)=6 6                 12.00000        NA 12.0*  
    *Max ValidObs*  
    *55  666*   
    *52  206*   
    *52   51*   
    *39   21*   
    *64   55*   
    *12    1*   
    *"It takes CPU Time=0.5 seconds, Elapsed Time=4.59 seconds to summarize the inDataSource."*  
  

  
## <a name="next-step"></a>次の手順  
[R を使用したグラフとプロットの作成 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>前のレッスン  
[レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
