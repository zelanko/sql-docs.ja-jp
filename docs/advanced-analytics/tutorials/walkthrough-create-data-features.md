---
title: R と SQL (チュートリアル) を使用してデータの機能を作成 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 226b8f2977f527d22a09fcbb4ab460e05285f858
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-data-features-using-r-and-sql-walkthrough"></a>R と SQL (チュートリアル) を使用してデータ機能を作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データ エンジニアリングは、機械学習の重要な部分です。 多くの場合、データは、予測モデリングに使用する前に変換が必要です。 必要な機能がデータにない場合、既存の値からデータをエンジニアリングできます。

このモデリング タスクでは、乗車位置と降車位置の未加工の緯度値と経度値を使用するのではなく、2 つの位置間の距離 (マイル単位) が必要です。 この機能を作成するには直接線形間の距離を使用して、2 つの点を計算する、[球面上の数式](https://en.wikipedia.org/wiki/Haversine_formula)です。

このステップでは、データから機能を作成するための 2 つの異なるメソッドを比較します。

- カスタムの R 関数を使用します。
- カスタム T-SQL 関数を使用します。 [!INCLUDE[tsql](../../includes/tsql-md.md)]

目標は、新しいを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一連の元の列と、新しい数値機能が含まれるデータ*direct_distance*です。

## <a name="featurization-using-r"></a>R を使用して特徴化

R 言語は統計ライブラリが豊富なことで知られていますが、カスタム データの変換の作成も必要になることがあります。

最初に、R ユーザーに慣れているやってみましょう: ノート パソコン上にデータを取得し、カスタムの R 関数を実行し、 *ComputeDist*緯度と経度の値で指定した 2 つのポイント間の線形の距離を計算します。

1. 以前に作成したデータ ソース オブジェクトが上位 1000 行のみを取得することに注意してください。 では、すべてのデータを取得するクエリを定義します。

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. クエリを使用して、新しい SQL Server データ ソースを作成します。

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata)を引数として指定された有効な SELECT クエリから成る、クエリがかかることができます、 _sqlQuery_パラメーター、またはとして指定された、テーブル オブジェクトの名前、_テーブル_パラメーター。
    
    - 使用する必要がありますをテーブルからデータをサンプリングする場合、 _sqlQuery_パラメーター、T-SQL は、TABLESAMPLE 句を使用してサンプリング パラメーターを定義し、設定、 _rowBuffering_ FALSE に渡す引数。

3. カスタムの R 関数を作成する次のコードを実行します。 ComputeDist は、2 組の緯度と経度の値をマイル内の距離を返す、両者間の線形距離を計算します。

    ```R
    env <- new.env();
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
  
    + 1 行目で新しい環境を定義します。 R では、環境を使用して、パッケージなどの名前空間をカプセル化できます。  `search()` 関数を使用すると、ワークスペース内の環境を確認できます。 特定の環境内にあるオブジェクトを確認するには、「 `ls(<envname>)`」と入力します。
    + `$env.ComputeDistance` から始まる行には、ヘイバーサイン式を定義するコードが含まれています。この式で、球面上にある 2 点間の *大圏距離* を計算します。

4. 関数を定義に適用する新しい特徴の列を作成するデータ*direct_distance*です。 ただし、変換を実行する前に、ローカル コンピューティング コンテキストを変更します。

    ```R
    rxSetComputeContext("local");
    ```

5. 呼び出す、 [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep)データ、エンジニア リング機能を取得する関数を適用、`env$ComputeDist`メモリ内のデータへの関数。

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureEngineeringQuery,
    transforms = list(direct_distance=ComputeDist(pickup_longitude,pickup_latitude, dropoff_longitude, dropoff_latitude),
    tipped = "tipped", fare_amount = "fare_amount", passenger_count = "passenger_count",
    trip_time_in_secs = "trip_time_in_secs",  trip_distance="trip_distance",
    pickup_datetime = "pickup_datetime",  dropoff_datetime = "dropoff_datetime"),
    transformEnvir = env,
    rowsPerRead=500,
    reportProgress = 3);
  
    used.time <- proc.time() - start.time;
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""));
    ```

    + RxDataStep 関数には、場所にデータを変更するためのさまざまな方法がサポートしています。 詳細については、この記事を参照してください: [Microsft R のデータを変換およびサブセットする方法](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    ただし、いくつかの rxDataStep に関する注意点。 
    
    引数を使用する他のデータ ソースに*varsToKeep*と*varsToDrop*、SQL Server データ ソースに対してはサポートされていませんが、します。 そのため、この例では使用した、_変換_パススルー列と変換後の列の両方を指定する引数。 また、ときに実行されている SQL Server で、計算コンテキストを_末尾_引数は、SQL Server データ ソースのみを取得できます。

    上記のコードより大きなデータ セットで実行時の警告メッセージも生成できます。 行の数が数をタイムアウト時に超えています (既定では 3,000,000) 値の設定を作成する列の rxDataStep、警告を返し、返されるデータ フレーム内の行の数は切り捨てられます。 変更することができます、警告を除去する、 _maxRowsByCols_ rxDataStep 関数の引数。 ただし場合、 _maxRowsByCols_が大きすぎるため、データ フレームをメモリに読み込むときに問題が発生する可能性があります。

7. 呼び出すことができます必要に応じて、 [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo)を変換後のデータ ソースのスキーマを検査します。

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Transact-SQL を使用した特性付け

ここで、カスタムの SQL 関数を作成*ComputeDist*、カスタムの R 関数と同じタスクを実行します。

1. *fnCalculateDistance* という、新しいカスタムの SQL 関数を定義します。 このユーザー定義の SQL 関数のコードは、データベースの作成と構成に使用した PowerShell スクリプトの一部として提供されています。  そのため、この関数はデータベースに既に含まれているはずです。

    含まれていない場合は、SQL Server Management Studio を利用し、タクシーのデータが保存されているものと同じデータベースで関数を生成します。

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS
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

2. 関数の動作を確認するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] をサポートするアプリケーションから次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。

    ```sql
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
    FROM nyctaxi_sample
    ```
3. この関数を定義するが容易になる SQL を使用して目的の機能を作成し、新しいテーブルに直接値を挿入します。

    ```
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. ただし、R コードからカスタムの SQL 関数を呼び出す方法を見てみましょう。 最初に、クエリの特性付けを R 変数に格納します。

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > このチュートリアルをより迅速にするためのデータの小さなサンプルを取得するには、このクエリを変更されています。 すべてのデータを取得する場合は、TABLESAMPLE 句を削除することができます。ただし、環境に応じてされませんありますエラーが発生しました、R を完全なデータセットを読み込むことです。
  
5. 次のコード行を使用して R 環境から [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を呼び出し、*featureEngineeringQuery* に定義されているデータに適用します。
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",
             passenger_count  = "numeric", trip_distance  = "numeric",
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  これで、新しい機能を作成すると、呼び出す**rxGetVarsInfo** feature テーブルにデータの概要を作成します。
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    *結果*

    ```
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: numeric
    Var 4: trip_time_in_secs, Type: numeric
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: direct_distance, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: pickup_longitude, Type: numeric
    Var 11: dropoff_latitude, Type: numeric
    Var 12: dropoff_longitude, Type: numeric
    ```

    > [!NOTE]
    > 場合によっては、このようなエラーが発生する可能性があります: *'fnCalculateDistance' オブジェクトに対する EXECUTE 権限が拒否された*場合は、使用しているログインがスクリプトを実行し、データベースでオブジェクトを作成するアクセス許可を持っていることを確認してくださいだけでなく、インスタンス。
    > FnCalculateDistance、オブジェクトのスキーマを確認してください。 オブジェクトがデータベースの所有者によって作成された、ログインがロール db_datareader に属している場合は、ログイン スクリプトを実行する明示的なアクセス許可を付与する必要があります。

## <a name="comparing-r-functions-and-sql-functions"></a>R 関数と SQL 関数の比較

時間で R コードを使用するコードのこの部分を覚えていますか。

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

データの変換にかかる SQL 関数を呼び出すときに参照する SQL ユーザー定義関数の例を使用するこのしようとすることができます。 また、rxSetComputeContext と計算コンテキストの切り替えを再試行し、タイミングを比較します。

時間は、ネットワークの速度、およびハードウェア構成によって大幅に異なる場合があります。 テスト構成、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数アプローチは、カスタムの R 関数を使用するよりも高速でした。 そのため、使用示しました、[!INCLUDE[tsql](../../includes/tsql-md.md)]以降の手順でこれらの計算関数をします。

> [!TIP]
> 非常に多くの場合は、機能を使用してエンジニア リング[!INCLUDE[tsql](../../includes/tsql-md.md)]R. よりも高速になりますたとえば、T-SQL に高速の windowing と移動平均のローリングなどの一般的なデータ科学計算を適用できる、順位付け関数が含まれていますと*n*-タイルです。 データとタスクに基づいて、最も効率的な方法を選択してください。

## <a name="next-lesson"></a>次のレッスン

[R モデルを構築し、SQL に保存](walkthrough-build-and-save-the-model.md)

## <a name="previous-lesson"></a>前のレッスン

[表示して、R を使用するデータの概要](walkthrough-view-and-summarize-data-using-r.md)

