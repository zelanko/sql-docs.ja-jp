---
title: R と SQL Server の機能 - SQL Server Machine Learning を使用してデータ機能を作成します。
description: SQL Server の関数を使用したデータベース内分析データの特徴を作成する方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 609896357845aa4f466e874524b8136b34e32b9a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511699"
---
# <a name="create-data-features-using-r-and-sql-server-walkthrough"></a>R と SQL Server (チュートリアル) を使用してデータ機能を作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データ エンジニアリングは、機械学習の重要な部分です。 多くの場合、データは、予測モデリングに使用する前に変換が必要です。 必要な機能がデータにない場合、既存の値からデータをエンジニアリングできます。

このモデリング タスクでは、乗車位置と降車位置の未加工の緯度値と経度値を使用するのではなく、2 つの位置間の距離 (マイル単位) が必要です。 この機能を作成するを使用して、2 つのポイント間の直接の直線距離を計算する、 [haversine 式](https://en.wikipedia.org/wiki/Haversine_formula)します。

この手順では、データから機能を作成するための 2 つの異なる方法を説明します。

> [!div class="checklist"]
> * カスタム R 関数を使用します。
> * カスタム T-SQL 関数を使用してください。 [!INCLUDE[tsql](../../includes/tsql-md.md)]

目標は、新たに作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一連の元の列の名前と、新しい数値機能データ*direct_distance*します。

## <a name="prerequisites"></a>前提条件

この手順では、このチュートリアルで前の手順に基づいて継続的な R セッションを想定しています。 これらの手順で作成された接続文字列およびデータ ソース オブジェクトを使用します。 次のツールとパッケージは、スクリプトの実行に使用されます。

+ Rgui.exe R コマンドを実行するには
+ Management Studio を T-SQL の実行

## <a name="featurization-using-r"></a>R を使用した特徴の生成

R 言語は統計ライブラリが豊富なことで知られていますが、カスタム データの変換の作成も必要になることがあります。

最初に、R ユーザーに慣れているやってみましょう: ラップトップ上にデータを取得し、カスタムの R 関数を実行*ComputeDist*緯度と経度の値で指定した 2 点間の直線距離を計算します。

1. 先ほど作成したデータ ソース オブジェクトが上位 1000 行のみを取得することに注意してください。 すべてのデータを取得するクエリを定義しましょう。

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. クエリを使用して、新しいデータ ソース オブジェクトを作成します。

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata)を引数として指定された有効な SELECT クエリで構成されるクエリを実行することができます、 _sqlQuery_パラメーター、またはとして指定された、テーブル オブジェクトの名前、_テーブル_パラメーター。
    
    - 使用する必要がある、テーブルからデータをサンプリングする場合、 _sqlQuery_パラメーターは、T-SQL TABLESAMPLE 句を使用してサンプリング パラメーターを定義し、設定、 _rowBuffering_引数を FALSE にします。

3. カスタム R 関数を作成する次のコードを実行します。 ComputeDist を 2 組の緯度と経度の値で受け取り、距離をマイルで返すそれらの間の直線距離を計算します。

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
  
    + 1 行目で新しい環境を定義します。 R では、環境を使用して、パッケージなどの名前空間をカプセル化できます。 `search()` 関数を使用すると、ワークスペース内の環境を確認できます。 特定の環境内にあるオブジェクトを確認するには、「 `ls(<envname>)`」と入力します。
    + `$env.ComputeDist` から始まる行には、ヘイバーサイン式を定義するコードが含まれています。この式で、球面上にある 2 点間の *大圏距離* を計算します。

4. 関数を定義に適用する新しい機能列を作成するデータ*direct_distance*します。 変換を実行する前に、ローカル コンピューティング コンテキストを変更します。

    ```R
    rxSetComputeContext("local");
    ```

5. 呼び出す、 [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) 、データ エンジニア リング機能を取得する関数を適用、`env$ComputeDist`関数をメモリ内のデータ。

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureDataSource,
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

    + RxDataStep 関数では、データの場所を変更するさまざまなメソッドをサポートしています。 詳細については、この記事を参照してください。[Microsft R でデータを変換およびサブセットする方法](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    ただし、いくつかの rxDataStep に関する注意すべき点。 
    
    引数を使用する他のデータ ソースで*varsToKeep*と*varsToDrop*が SQL Server データ ソースはサポートされていません。 そのため、この例で使用しました、_変換_パススルー列と変換後の列の両方を指定する引数。 また、ときに実行中の SQL Server でコンピューティング コンテキストを_inData_引数は、SQL Server のデータ ソースにのみ使用できます。

    上記のコードでは、大規模なデータ セットで実行されると、警告メッセージも生成できます。 行の数し、列の作成中 (既定では 3,000,000) セットの値を超えた、rxDataStep が、警告を返します、返されるデータ フレーム内の行の数は切り捨てられます。 変更することができます、警告を削除する、 _maxRowsByCols_ rxDataStep 関数の引数。 ただし場合、 _maxRowsByCols_が大きすぎるため、データ フレームをメモリに読み込むときに問題が発生する可能性があります。

7. 呼び出すことができます必要に応じて、 [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo)に変換されたデータ ソースのスキーマを検査します。

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Transact-SQL を使用した特性付け

この演習では、カスタムの R 関数ではなく SQL 関数を使用して同じタスクを実行する方法を説明します。 

切り替える[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)または T-SQL スクリプトを実行する別のクエリ エディター。

1. という名前の SQL 関数を使用*fnCalculateDistance*します。 関数は、NYCTaxi_Sample データベースに既に存在する必要があります。 オブジェクト エクスプ ローラーでは、このパスを移動して、関数の存在を確認します。データベース > NYCTaxi_Sample > プログラミング > 関数 > スカラー値関数 > dbo.fnCalculateDistance します。

    関数が存在しない場合は、SQL Server Management Studio を使用して、NYCTaxi_Sample データベースで関数を生成します。

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

2. Management Studio では、新しいクエリ ウィンドウで、次を実行[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントをサポートする任意のアプリケーションから[!INCLUDE[tsql](../../includes/tsql-md.md)]関数の動作を確認します。

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude 
    FROM nyctaxi_sample
    ```
3. 追加することができます (最初に作成する必要がある) 新しいテーブルに直接値を挿入するのには、 **INTO**句テーブル名を指定します。

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. R コードから SQL 関数を呼び出すこともできます。 Rgui に戻ると、特徴の生成の SQL クエリを R 変数に格納します。

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > このチュートリアルを速く、データの小さなサンプルを取得するには、このクエリを変更されています。 TABLESAMPLE 句を削除するには、すべてのデータを取得する場合ただし、環境によっては、その可能性がありますできないエラーが発生している R に完全なデータセットを読み込むこともできます。
  
5. 次のコード行を使用して R 環境から [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を呼び出し、*featureEngineeringQuery* に定義されているデータに適用します。
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
        dropoff_longitude = "numeric", dropoff_latitude = "numeric",
        passenger_count  = "numeric", trip_distance  = "numeric",
        trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  これで、新しい機能を作成すると、呼び出す**rxGetVarsInfo**機能テーブルにデータの概要を作成します。
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    **結果**

    ```R
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
    > 場合によっては、次のようなエラーが発生する可能性があります。*EXECUTE 権限がオブジェクト 'fnCalculateDistance' で拒否されました*その場合は、ログインを使用しているスクリプトを実行し、インスタンスでだけでなく、データベースのオブジェクトを作成するアクセス許可があることを確認します。
    > FnCalculateDistance、オブジェクトのスキーマを確認します。 オブジェクトがデータベースの所有者によって作成されたログインは db_datareader ロールに属している場合は、ログインのスクリプトを実行する明示的なアクセス許可を付与する必要があります。

## <a name="comparing-r-functions-and-sql-functions"></a>R 関数と SQL 関数の比較

R コードにかかる時間を使用するコードのこの部分を覚えていますか。

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

SQL 関数を呼び出すときに、どのくらいの時間のデータの変換には参照する SQL ユーザー定義関数の例を使用するこれを試すことができます。 また、rxSetComputeContext のコンピューティング コンテキストを切り替えてみてくださいし、タイミングを比較します。

時間は、ネットワークの速度、およびお客様のハードウェア構成によって大幅に異なる場合があります。 テスト構成、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数のアプローチがカスタム R 関数を使用するよりも高速化します。 そのため、使用してきた、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数は、以降の手順でこれらの計算。

> [!TIP]
> 非常に多くの場合は、機能を使用してエンジニア リング[!INCLUDE[tsql](../../includes/tsql-md.md)]R. よりも高速になりますたとえば、T-SQL に高速ウィンドウ化と移動平均のロールバックなどの一般的なデータ サイエンス計算に適用できる、順位付け関数が含まれていますと*n*-タイル。 データとタスクに基づいて、最も効率的な方法を選択してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [R モデルを構築し、SQL に保存](walkthrough-build-and-save-the-model.md)

