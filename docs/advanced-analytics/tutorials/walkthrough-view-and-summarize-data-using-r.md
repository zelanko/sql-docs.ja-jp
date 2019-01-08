---
title: 表示、および SQL Server Machine Learning の R 関数を使用して SQL Server データの概要
description: データベース内分析は、SQL Server で R 関数を使用して、統計サマリーを生成し、視覚化する方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 368caa21545e534c393aca29ce8fd3a59f9d9837
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644561"
---
# <a name="view-and-summarize-sql-server-data-using-r-walkthrough"></a>表示し、R (チュートリアル) を使用した SQL Server データの概要
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンでは関数に、 **RevoScaleR**パッケージ化し、次のタスクの手順します。

> [!div class="checklist"]
> * SQL Server への接続
> * 必要なデータを含むクエリを定義するか、テーブルまたはビューを指定します。
> * R コードの実行時に使用する計算コンテキストを 1 つまたは複数定義します。
> * 必要に応じて、元の読み取り中には、データ ソースに適用される変換を定義します。

## <a name="define-a-sql-server-compute-context"></a>SQL Server の計算コンテキストを定義します。

クライアント ワークステーションで R 環境で R の次のステートメントを実行します。 このセクションで、 [Microsoft R Client でのデータ サイエンス ワークステーション](../r/set-up-a-data-science-client.md)RevoScaleR パッケージだけでなく、基本的な軽量な R ツールのセットが含まれているため、します。 たとえば、Rgui.exe を使用して、このセクションでは、R スクリプトを実行することができます。

1. 場合、 **RevoScaleR**パッケージがまだ読み込まれていない、R コードの行を実行します。

    ```R
    library("RevoScaleR")
    ```

     引用符は、します推奨ここでは、省略可能な。
     
     エラーが発生する場合は、R 開発環境が RevoScaleR パッケージが含まれているライブラリを使用することを確認します。 コマンドを使用して`.libPaths()`を現在のライブラリ パスを表示します。

2. SQL Server の接続文字列を作成し、それを R 変数に保存*connStr*します。

   有効な SQL Server インスタンス名に"your_server_name"プレース ホルダーを変更する必要があります。 サーバー名、インスタンスの名前を使用できる場合があります。 またはネットワークによって、名前、完全に修飾する必要があります。
    
   SQL Server 認証の場合は、接続の構文がとおりです。

    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Windows 認証の場合、構文が少し異なります。
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    通常、R コードでのパスワードの保存されないように、可能な場合は、Windows 認証を使用することをお勧めします。

3. 使用して作成、新しい変数を定義*コンピューティング コンテキスト*します。 計算コンテキスト オブジェクトを作成した後は、SQL Server インスタンス上の R コードの実行に使用できます。

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューター間で双方向に R オブジェクトをシリアル化する際、R では、一時ディレクトリが使用されます。 *sqlShareDir*として使用されるローカル ディレクトリを指定するか、既定のものをそのまま利用できます。
  
    - 使用*sqlWait*を R サーバーからの結果を待機するかどうかを示します。  待機時間のないジョブとの比較の詳細については、次を参照してください。[分散し、Microsoft R で RevoScaleR の並列コンピューティング](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing)します。
  
    - 引数を使用して*sqlConsoleOutput*に R コンソールからの出力を確認しないことを示します。

4. 呼び出す、 [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver)変数と、既に定義されている接続文字列で計算コンテキスト オブジェクトを作成し、R 変数に新しいオブジェクトを保存するコンス トラクター *sqlcc*します。
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. 既定では、コンピューティング コンテキストがローカルで明示的に設定する必要があるため、 *active*コンピューティング コンテキスト。

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext)を返す、以前にアクティブなコンピューティング コンテキスト視覚的を使用できるように
    + [rxGetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext)アクティブなコンピューティング コンテキストを返します
    
    コンピューティング コンテキストの設定のみに影響する関数を使用する操作に注意してください、 **RevoScaleR**パッケージは、コンピューティング コンテキストでは、オープン ソース R 操作を実行する方法には影響しません。

## <a name="create-a-data-source-using-rxsqlserver"></a>RxSqlServer を使用してデータ ソースを作成します。

RevoScaleR と MicrosoftML などの Microsoft R ライブラリを使用する場合、*データソース*RevoScaleR 関数を使用して作成するオブジェクトです。 データ ソース オブジェクトには、モデルのトレーニングや機能の抽出などのタスクを使用するデータのセットを指定します。 さまざまな SQL Server を含むソースからデータを取得できます。 現在サポートされているソースの一覧で、次を参照してください。 [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource)します。

以前、接続文字列を定義し、R 変数にその情報を保存します。 取得するデータを指定する接続情報を再利用することができます。

1. SQL クエリを文字列変数として保存します。 クエリは、モデルのトレーニング データを定義します。

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    物事を高速に実行するためにここで、TOP 句を使用しましたが、実際のクエリによって返される行は順序によって異なります。 そのため、集計結果が異なる次のものも可能性があります。 TOP 句を削除してもかまいません。

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
    
    + 引数  *colClasses* により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R の間でデータを移動するときに使用する列の型が指定されます。これが重要なのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が R と異なるデータ型とその他のデータ型を使用するためです。 詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)します。
  
    + 引数*rowsPerRead*がメモリ使用量と効率的な計算を管理するために重要です。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 内の拡張分析関数の大部分は、データをチャンク単位で処理し、中間結果を蓄積していきます。すべてのデータを読み取ったら、最終的な計算結果を返します。  追加することで、 *rowsPerRead*パラメーター、データの行の数は、処理のためには、各チャンクに読み取られるかを制御できます。  このパラメーターの値が大きすぎる場合は、データの大きなチャンクを効率的に処理するための十分なメモリがあるないため、データ アクセスが低速あります。  システムによっては、 *rowsPerRead*極端に小さい値にもできるパフォーマンスが低下します。

3. この時点では、作成した、 *inDataSource*オブジェクトが、データは含まれません。 データは、関数を実行するまでには、ローカル環境に SQL クエリから召集されません[rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep)または[rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary)します。

    ただし、データ オブジェクトを定義したら、これでは、他の関数に引数として使用できます。

## <a name="use-the-sql-server-data-in-r-summaries"></a>SQL Server のデータを使用して、R の概要

このセクションで提供される機能のいくつかを試してみましょう[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]そのサポート リモート計算コンテキスト。 R 関数をデータ ソースに適用すると、探索、まとめると、してグラフ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。

1. 関数を呼び出す[rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo)をデータ ソースとそのデータ型の変数の一覧を取得します。

    **rxGetVarInfo**便利な関数は、; 任意のデータ フレームを呼び出すことができますか、リモート データ オブジェクト内のデータのセットに最大と最小値などの情報を取得する値をデータ型、因子列内のレベルの数。
    
    あらゆる種類のデータ入力、機能変換、または機能エンジニアリングの後にこの関数を実行することを検討してください。 これにより、予想されるデータのモデルで使用する機能は、すべてを入力し、エラーを回避することを確認できます。
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **結果**
    
    ```R
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

2. ここで、RevoScaleR 関数を呼び出す[rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary)個々 の変数に関するより詳細な統計情報を取得します。

    rxSummary は R に基づいて`summary`関数しますが、いくつか追加の機能と利点があります。 rxSummary では、複数のコンピューティング コンテキストで動作し、チャンクをサポートします。  使用することも要素のレベルに基づいて、値の変換や集計 rxSummary します。
    
    この例では、乗客の数に基づいて料金を要約します。
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + RxSummary の最初の引数は、数式または語を集計するを指定します。 ここでは、`F()`内の値に変換する関数が使用される_乗客\_カウント_因子を集計する前にします。 最小値 (1) と最大値 (6) を指定する必要が、_乗客\_カウント_因子変数。
    + 出力する統計情報を指定しない場合は、既定で rxSummary 出力と、平均、StDev、最小、最大、有効であり、不足している所見の数。
    + この例には、パフォーマンスを比較できるように、関数の開始時間と終了時間を追跡するコードも含まれています。
  
    **結果**

    RxSummary 関数が正常に実行されている場合、このような結果が表示カテゴリごとの統計情報のリストが続きます。 

    ```R
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>ビッグ データの補足的な演習

すべての行を持つ新しいクエリ文字列を定義することをお試しください。 この実験を新しいデータ ソース オブジェクトを設定することをお勧めします。 変更もみて、 *rowsToRead*パラメーターをスループットに与える影響を参照してください。

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
> これの実行中などのツールを使用することができます[Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx)または SQL Profiler、接続を確立する方法を確認して、R コードが SQL Server サービスを使用して実行します。
> 
> これらを使用して SQL Server で実行される R ジョブを監視することも[カスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)します。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [R を利用してグラフやプロットを作成する](walkthrough-create-graphs-and-plots-using-r.md)