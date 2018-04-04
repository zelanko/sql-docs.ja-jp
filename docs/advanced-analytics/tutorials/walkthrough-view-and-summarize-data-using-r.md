---
title: R (チュートリアル) を使用するデータの概要を表示および |Microsoft ドキュメント
ms.date: 11/10/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 80495ecca4ebf9de4c52f33f0c7fc0a7e057e7d7
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="view-and-summarize-data-using-r"></a>表示して、R を使用するデータの概要
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

これで R コードを使用して同じデータを操作してみましょう。 このレッスンでは、関数を使用する方法を学習、 **RevoScaleR**パッケージです。

R スクリプトは、このチュートリアルで提供しており、データ オブジェクトの作成、集計の生成、モデルの構築に必要なすべてのコードを含んでいます。 R スクリプト ファイル **RSQL_RWalkthrough.R**は、スクリプト ファイルをインストールした場所にあります。

+ R の使用経験がある場合、一度にすべてスクリプトを実行できます。
+ RevoScaleR を使用する方法の学習の人々 にとって、このチュートリアルは、スクリプト行を通過します。
+ スクリプトから個別行を実行するには、ファイル内の行を強調表示し、Ctrl を押しながら ENTER を押します。

> [!TIP]
> このチュートリアルの残りの部分を後で実行する場合は、R ワークスペースを保存します。  このようにデータ オブジェクトとその他の変数は、再利用の準備ができてはします。

## <a name="define-a-sql-server-compute-context"></a>SQL Server のコンピューティング コンテキストを定義します。

Microsoft R 簡単にデータを取得する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]R コードで使用します。 このプロセスは次のとおりです。
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続を作成します。
- 必要なデータを含むクエリを定義するか、テーブルまたはビューを指定します。
- R コードの実行時に使用する計算コンテキストを 1 つまたは複数定義します。
- 必要に応じて、ソースから読み取られるときに、データ ソースに適用される変換を定義します。

次の手順では、R コードのすべての一部であるし、R 環境で実行する必要があります。 Microsoft R クライアントを使用する、すべての RevoScaleR パッケージだけでなく、基本的な軽量な一連の R ツールが含まれているためです。

1. 場合、 **RevoScaleR**パッケージは既に読み込まれていない R コードの行を実行します。

    ```R
    library("RevoScaleR")
    ```

     引用符で囲まオプションですが、ここでは、ことをお勧めします。
     
     エラーが発生した場合は、R 開発環境が RevoScaleR パッケージを含むライブラリを使用することを確認します。 などのコマンドを使用して`.libPaths()`を現在のライブラリ パスを表示します。

2. SQL Server の接続文字列を作成し、R 変数に保存_connStr_です。
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=Your_Database_Name;Uid=Your_User_Name;Pwd=Your_Password"
    ```

    サーバー名、インスタンス名のみを使用できる場合があります。 またはによっては、ネットワークの名前を完全に修飾する必要があります。

    Windows 認証の場合は、構文はわずかに異なります。
    
    ```R
    connStr <- "Driver=SQL Server;Server=SQL_instance_name;Database=database_name;Trusted_Connection=Yes"
    ```

    ダウンロード可能な R スクリプトでは、SQL ログインのみを使用します。 一般に、R コードでパスワードを保存されないように、可能な限り Windows 認証を使用することをお勧めします。 ただし、このチュートリアルでは、コードが Github からダウンロードされたコードと一致することを確認するを使用します SQL ログイン、チュートリアルの残りの部分。

3. 新しい作成に使用する変数を定義する_計算コンテキスト_です。 コンピューティング コンテキスト オブジェクトを作成した後は、SQL Server インスタンス上の R コードの実行に使用できます。

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューター間で双方向に R オブジェクトをシリアル化する際、R では、一時ディレクトリが使用されます。 *sqlShareDir*として使用されるローカル ディレクトリを指定するか、既定のものをそのまま利用できます。
  
    - 使用して*sqlWait*を R サーバーから結果を待機するかどうかを示します。  待機中待機時間のないジョブとの比較の詳細については、次を参照してください。[分散し、Microsoft R で ScaleR で並列コンピューティング](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing)です。
  
    - 引数を使用して*sqlConsoleOutput* R コンソールからの出力を表示するしないことを示すためにします。


4. 呼び出す、 [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver)変数および接続文字列が既に定義されているでのコンピューティング コンテキスト オブジェクトを作成し、R 変数に新しいオブジェクトを保存するコンス トラクター *sqlcc*です。
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. 既定では、コンピューティング コンテキストがローカルで明示的に設定する必要がありますので、 *active*コンテキストを計算します。

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + `rxSetComputeContext` は以前にアクティブな計算コンテキストを非表示で返すので、それを利用できます。
    + `rxGetComputeContext` はアクティブな計算コンテキストを返します
    
    計算コンテキストの設定は、 **RevoScaleR** パッケージ内の関数を使用する操作にのみ影響を与えます。計算コンテキストは、オープン ソース R 操作を実行する方法には影響しません。

## <a name="create-a-data-source-using-rxsqlserver"></a>RxSqlServer を使用してデータ ソースを作成します。

Microsoft r、*データソース*RevoScaleR 関数を使用して作成するオブジェクトです。 データ ソース オブジェクトは、一部のモデルのトレーニングまたは機能の抽出などのタスクを使用するデータのセットを指定します。 さまざまなソースからデータを取得することができます。現在サポートされているソースの一覧で、次を参照してください。 [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource)です。

前の接続文字列を定義し、R 変数にその情報を保存します。 取得するデータを指定する接続情報を再利用することができます。

1. SQL クエリは、文字列変数として保存します。 クエリは、モデルのトレーニング データを定義します。

    ```R
    sampleDataQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    TOP 句を次に物事を高速に実行を使用しましたが、順序によって、クエリによって返される実際の行数が異なることができます。 そのため、概要結果を次のものから異なる場合があります。 自由 TOP 句を削除してください。

2. [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) 関数にクエリの定義を引数として渡します。

    ```R
    inDataSource <- RxSqlServerData(
      sqlQuery = sampleDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )
    ```
    
    + 引数  *colClasses* により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R の間でデータを移動するときに使用する列の型が指定されます。これが重要なのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が R と異なるデータ型とその他のデータ型を使用するためです。 詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)です。
  
    + 引数*rowsPerRead*メモリ使用量と効率的な計算を管理するため重要です。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 内の拡張分析関数の大部分は、データをチャンク単位で処理し、中間結果を蓄積していきます。すべてのデータを読み取ったら、最終的な計算結果を返します。  追加することによって、 *rowsPerRead*パラメーター、データの行の数は、各チャンクを処理するために読み取られるを制御できます。  このパラメーターの値が大きすぎる場合、そのような大規模なデータ チャンクを効率的に処理するのに十分なメモリは備えていないため、データ アクセスは遅くなる可能性があります。  設定の一部のシステムで*rowsPerRead*を過度に小さい値も指定のパフォーマンスが低下します。

3. この時点では、作成した、 *inDataSource*オブジェクトが、データが含まれていません。 データはなど、関数を実行するまでには、ローカル環境に SQL クエリから召集されません[rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep)または[rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary)です。

    ただし、これで、データ オブジェクトを定義したは、その他の関数の引数として使用できます。

## <a name="use-the-sql-server-data-in-r-summaries"></a>R の概要での SQL Server のデータを使用します。

このセクションで提供される機能のいくつかを試してみましょう[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]そのサポート リモート計算コンテキスト。 R 関数を適用すると、データ ソースに、することができますを探索、要約、およびグラフ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。

1. 関数を呼び出す[rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo)データ ソースとそのデータ型の変数の一覧を取得します。

    **rxGetVarInfo**便利な関数は、以外の場合は、任意のデータ フレームを呼び出せますまたは、リモートのデータ オブジェクトのデータのセットに最大と最小値などの情報を取得する値は、データ型、および係数列内のレベル数。
    
    あらゆる種類のデータ入力、機能変換、または機能エンジニアリングの後にこの関数を実行することを検討してください。 これにより、予期されたデータのモデルで使用する機能は、すべてを入力し、エラーを回避することを確認することができます。
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **結果**
    
    ```
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: integer
    Var 4: trip_time_in_secs, Type: numeric, Storage: int64
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: pickup_longitude, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: dropoff_longitude, Type: numeric
    ```

2. ここで、RevoScaleR 関数を呼び出す[rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary)をそれぞれの変数に関するより詳細な統計情報を取得します。

    R に基づいて rxSummary`summary`関数にはいくつかの追加機能および利点があります。 rxSummary では、複数のコンピューティング コンテキストで動作し、チャンキングをサポートします。  使用することも、変換、または要約 rxSummary が要素のレベルに基づきます。
    
    この例を見せる乗客の数に基づいて運賃量を要約します。
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + RxSummary に最初の引数は、数式またはによって要約する語句を指定します。 ここでは、`F()`内の値を変換する関数が使用される_乗客\_カウント_概要を作成する前に要因にします。 指定する必要が最小値 (1) と最大値 (6) の_乗客\_カウント_因子変数。
    + 出力する統計情報を指定しない場合は、既定では rxSummary 出力平均、StDev、Min、Max、および有効であり、不足しているの観測値の数。
    + この例には、パフォーマンスを比較できるように、関数の開始時間と終了時間を追跡するコードも含まれています。
  
    **結果**

    RxSummary 関数が正常に実行する場合、上記のような結果が表示をカテゴリ別の統計情報のリストが続きます。 

    ```
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>ビッグ データに対する追加の手順

すべての行を持つ新しいクエリ文字列を定義してください。 この実験で新しいデータ ソース オブジェクトを設定することをお勧めします。 可能性がありますも変更しようとする、 *rowsToRead*パラメーターをスループットに与える影響を参照してください。

```R
bigDataQuery  <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"

bigDataSource <- RxSqlServerData(
      sqlQuery = bigDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )

start.time <- proc.time()
rxSummary(~fare_amount:F(passenger_count,1,6), data = bigDataSource)
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
  Elapsed Time=", round(used.time[3],2),
  " seconds to summarize the inDataSource.", sep=""))
```

> [!TIP]
> これの実行中などのツールを使用することができます[プロセス エクスプ ローラー](https://technet.microsoft.com/sysinternals/processexplorer.aspx)または SQL プロファイラをどのように接続していると、R コードが SQL Server サービスを使用して実行します。
> 
> 別のオプションは、これらを使用して SQL Server で実行されている R ジョブを監視する[カスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)です。

## <a name="next-lesson"></a>次のレッスン

[R を利用してグラフやプロットを作成する](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="previous-lesson"></a>前のレッスン

[SQL を使用してデータを探索する](walkthrough-view-and-explore-the-data.md)
