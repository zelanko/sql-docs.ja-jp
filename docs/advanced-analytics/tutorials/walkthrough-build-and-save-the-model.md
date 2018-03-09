---
title: "R モデルを構築して、SQL Server に保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: d8bd3c158c40accf191c775f0fe8466c05c32203
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="build-an-r-model-and-save-to-sql-server"></a>R モデルを構築して、SQL Server に保存
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

ここでは、機械学習モデルをビルドし、内のモデルを保存する方法を学習[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

## <a name="create-a-classification-model-using-rxlogit"></a>RxLogit を使用して、分類モデルを作成します。

構築するモデルでは、タクシー ドライバーがか、特定の変更に関するヒントを取得する可能性があるかどうかを予測する二項分類器です。 ロジスティック回帰を使用して、ヒントの分類器のトレーニングに前のレッスンで作成したデータ ソースを使用します。

1. [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) パッケージに含まれる **rxLogit** 関数を呼び出し、ロジスティック回帰モデルを作成します。 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = sql_feature_ds));
    ```

    モデルを構築する呼び出しは、system.time 関数で囲まれます。 これにより、モデルの構築に必要な時間を取得できます。

2. モデルを構築した後を使用してを検査、`summary`関数、および係数を表示します。

    ```R
    summary(logitObj);
    ```

     *結果*

     *ロジスティック回帰結果: その先端 ~ passenger_count trip_distance + trip_time_in_secs +* direct_distance *   <br/>*Data: featureDataSource (RxSqlServerData Data Source)*
     <br/>*Dependent variable(s): 先が*
     <br/>*独立変数の合計: 5*
     <br/>*有効な値: 17068*
     <br/>*不足している観測数: 0*
     <br/>*-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*
     <br/>*係数。*
     <br/>*Estimate Std.Error z value Pr(>|z|)*
     <br/>*(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*
     <br/>*passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**
     <br/>*trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**
     <br/>*trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**
     <br/>*direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**
     <br/>*---*
     <br/>*Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’0.1 ‘ ’ 1*
     <br/>*条件の最終的な差異共分散マトリックスの数: 48.3933*
     <br/>*Number of iterations: 4*

## <a name="use-the-logistic-regression-model-for-scoring"></a>スコアリングにロジスティック回帰モデルを使用する

モデルが構築されたので、そのモデルを使用して運転手が特定のドライブでチップを受け取る可能性が高いかどうかを予測できます。

1. まず、使用して、 [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata)スコアリング resul を格納するためのデータ ソース オブジェクトを定義する関数

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + この例を簡素化するには、ロジスティック回帰モデルへの入力は、同じ機能のデータ ソース (`sql_feature_ds`) モデルのトレーニングに使用することです。  多くの場合、スコアリングには新しいデータを使用したり、テスト用とトレーニング用のデータを別に確保したりします。
  
    + 予測結果は、テーブルに保存されます_taxiscoreOutput_です。 このテーブルのスキーマが定義されていないこと rxSqlServerData を使用して作成したときに注意してください。 スキーマは、rxPredict 出力から取得されます。
  
    + 予測された値を格納するテーブルを作成するには、rxSqlServer データ関数を実行する SQL ログイン権限が必要 DDL データベースにします。 ログインがテーブルを作成できない場合、ステートメントは失敗します。

2. [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) 関数を呼び出して結果を生成します。

    ```R
    rxPredict(modelObject = logitObj,
        data = sql_feature_ds,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    ステートメントが成功した場合を実行する時間がかかる必要があります。 完了したらは、SQL Server Management Studio を開くし、テーブルの作成し、出力を想定スコア列などが含まれていることを確認します。

## <a name="plot-model-accuracy"></a>モデルの精度をプロットします。

把握するために、モデルの精度を使用することができます、 [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc)受信者オペレーティング曲線をプロットする関数。 RxRoc が RevoScaleR パッケージによって提供される新しい関数のいずれかであるため、リモート計算コンテキストをサポートする、2 つのオプションがあります。

+ RxRoc 関数を使用して、リモート計算コンテキストで、プロットを実行し、ローカル クライアントに、プロットを返すことができます。

+ また、R クライアント コンピューターにデータをインポートして、他の R プロット関数を使用してパフォーマンス グラフを作成することもできます。

このセクションでは、両方の方法を確認してみます。

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>リモート (SQL Server) コンピューティング コンテキストでプロットを実行する

1. 関数 rxRoc を呼び出すし、入力として以前に定義されているデータを提供します。

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    この呼び出しでは、コンピューティング ROC グラフで使用する値を返します。 ラベル列が_先が_、実際の結果を予測しようとしています中に、_スコア_列が予測します。

2. 実際には、チャートのプロットに ROC オブジェクトを保存およびで描画、`plot`関数。 グラフでは、リモート計算コンテキストで作成され、R 環境に返されます。

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    R のグラフィックス デバイスを開くかをクリックして、グラフを表示、**プロット**RStudio ウィンドウです。

    ![モデルの ROC プロット](media/rsql-e2e-rocplot.png "モデルの ROC プロット")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>SQL Server のデータを使用して、ローカル コンピューティング コンテキストでプロットを作成する

1. ローカル コンピューティング コンテキストのプロセスではほぼ同じです。 使用する、 [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport)に、ローカルの R 環境に指定されたデータを取り込む関数。

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. ローカル メモリにデータを使用して、読み込む、 **ROCR**をパッケージ化を使用して、予測関数そのパッケージからをいくつかの新しい予測を作成します。

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. 出力変数に格納されている値に基づいて、ローカルのプロットを生成する`pred`です。

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![R を使用したモデルのパフォーマンスのプロット](media/rsql-e2e-performanceplot.png "R を使用したモデルのパフォーマンスのプロット")

> [!NOTE]
> グラフに使用したデータ ポイントの数に応じて、これらの異なるなります。

## <a name="deploy-the-model"></a>モデルの配置

モデルを構築しても実行することを確認したら可能性がありますする、ユーザーまたは組織のことができますを利用できるように、モデルのまたはおそらく再トレーニングを定期的にモデルを再サイトに展開します。 このプロセスと呼ぶことが*任せています*モデル。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して R モデルを呼び出すことができます、[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを簡単に、クライアント アプリケーションで R を使用します。

ただし、外部アプリからモデルを呼び出すには、運用に使用するデータベースにモデルを保存する必要があります。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で、トレーニングしたモデルは、 **varbinary(max)**型の 1 列にバイナリ形式で保存されます。

そのため、R から SQL Server にトレーニングしたモデルを移動するには、次の手順を行う必要があります。

+ モデルを 16 進数文字列にシリアル化する

+ シリアル化されたオブジェクトをデータベースに転送する

+ varbinary(max) 列にモデルを保存する

このセクションでは、予測を行うそれを呼び出す方法と、モデルを永続化する方法を学習します。

1. 既に使用していない場合に、ローカルの R 環境に切り替えるし、モデル、シリアル化を変数に保存します。

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. 使用して ODBC 接続を開く**RODBC**です。

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

    読み込まれたパッケージが既にある場合は、RODBC への呼び出しを省略できます。

3. データベース内の列に、モデルのバイナリ表現を格納する、PowerShell スクリプトによって作成されたストアド プロシージャを呼び出します。

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

    モデルをテーブルへの保存に必要なステートメントは、INSERT のみです。 ただしなどのストアド プロシージャでラップされたときに簡単は_PersistModel_です。

    > [!NOTE]
    > など、エラーが発生した場合は、「EXECUTE 権限が拒否されました PersistModel オブジェクトの」を現在のログインが権限を持っているかどうかを確認します。 ストアド プロシージャだけで明示的なアクセス許可を付与するには、次のように T-SQL ステートメントを実行します。 `GRANT EXECUTE ON [dbo].[PersistModel] TO <user_name>`

4. モデルを作成すると、データベースに保存、呼び出せますから直接[!INCLUDE[tsql](../../includes/tsql-md.md)]コードでは、システム ストアド プロシージャを使用して[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

    ただし、モデルでは、頻繁に使用する、カスタム ストアド プロシージャの入力クエリとその他のパラメーターと共に、モデルへの呼び出しをラップする簡単です。

    このような 1 つのストアド プロシージャの完全なコードを次に示します。 管理とで R モデルを更新しやすくようにストアド プロシージャを作成することをお勧め[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

    ```tsql
    CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)
    AS
    BEGIN
      SET NOCOUNT ON;
      INSERT INTO nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
    END
    ```

  > [!NOTE]
  > 使用して、**に SET nocount ON**余分な結果を防ぐために句を SELECT ステートメントに影響を与えない設定します。


使用して、保存済みのモデルに対するスコア付けを実行する方法を学習して、[次へ] および最後のレッスンで[!INCLUDE[tsql](../../includes/tsql-md.md)]です。

## <a name="next-lesson"></a>次のレッスン

[R モデルを展開して SQL の使用](walkthrough-deploy-and-use-the-model.md)

## <a name="previous-lesson"></a>前のレッスン

[R と SQL を使用してデータ機能を作成します。](walkthrough-create-data-features.md)

