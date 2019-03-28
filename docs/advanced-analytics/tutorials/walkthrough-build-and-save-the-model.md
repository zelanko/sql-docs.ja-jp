---
title: R モデルを構築し、SQL Server (チュートリアル) - SQL Server Machine Learning に保存
description: SQL Server データベース内分析で使用される R 言語モデルを構築する方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 039e5a8970b2161bfe54b1836f3bd12b48477e1a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513059"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>R モデルを構築し、SQL Server (チュートリアル) に保存
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この手順では、機械学習モデルを構築し、モデルを保存する方法を説明します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 モデルを保存してから直接呼び出すことができます[!INCLUDE[tsql](../../includes/tsql-md.md)]、システム ストアド プロシージャを使用して、コーディング[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)または[PREDICT (T-SQL) 関数](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)します。

## <a name="prerequisites"></a>前提条件

この手順では、このチュートリアルで前の手順に基づいて継続的な R セッションを想定しています。 これらの手順で作成された接続文字列およびデータ ソース オブジェクトを使用します。 次のツールとパッケージは、スクリプトの実行に使用されます。

+ Rgui.exe R コマンドを実行するには
+ Management Studio を T-SQL の実行
+ ROCR パッケージ
+ RODBC パッケージ

### <a name="create-a-stored-procedure-to-save-models"></a>モデルを保存するストアド プロシージャを作成します。

この手順では、ストアド プロシージャを使用して、SQL Server にトレーニング済みモデルを保存します。 この操作を実行するストアド プロシージャの作成により、タスクが容易にします。

ストアド プロシージャを作成する Management Studio でのクエリ ウィンドウで、次の T-SQL コードを実行します。

```sql
USE [NYCTaxi_Sample]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PersistModel')
  DROP PROCEDURE PersistModel
GO

CREATE PROCEDURE [dbo].[PersistModel] @m nvarchar(max)
AS
BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;
    insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
END
GO
```

> [!NOTE]
> エラーが発生した場合、ログインがオブジェクトを作成する権限を持っていることを確認します。 このような T-SQL ステートメントを実行してオブジェクトを作成する明示的なアクセス許可を付与することができます:`exec sp_addrolemember 'db_owner', '<user_name>'`します。

## <a name="create-a-classification-model-using-rxlogit"></a>RxLogit を使用して、分類モデルを作成します。

モデルは、タクシー運転手がかどうかは、特定の乗車でチップを取得する可能性が高いかどうかを予測する二項分類器です。 ロジスティック回帰を使用してチップ分類子をトレーニングする前のレッスンで作成したデータ ソースを使用します。

1. [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) パッケージに含まれる **rxLogit** 関数を呼び出し、ロジスティック回帰モデルを作成します。 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    モデルを構築する呼び出しは、system.time 関数で囲まれます。 これにより、モデルの構築に必要な時間を取得できます。

2. モデルをビルドした後を使用してを検査、`summary`関数、および係数を表示します。

    ```R
    summary(logitObj);
    ```

    **結果**
    
    ```R
     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*
     direct_distance* 
     *Data: featureDataSource (RxSqlServerData Data Source)*
     *Dependent variable(s): tipped*
     *Total independent variables: 5*
     *Number of valid observations: 17068*
     *Number of missing observations: 0*
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*
     *Coefficients:*
     *Estimate Std. Error z value Pr(>|z|)*
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**
     *---*
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*
     *Condition number of final variance-covariance matrix: 48.3933*
     *Number of iterations: 4*
   ```

## <a name="use-the-logistic-regression-model-for-scoring"></a>スコアリングにロジスティック回帰モデルを使用する

モデルが構築されたので、そのモデルを使用して運転手が特定のドライブでチップを受け取る可能性が高いかどうかを予測できます。

1. まず、使用して、 [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata)のスコア付けの結果を格納するデータ ソース オブジェクトを定義する関数。

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + この例を簡素化するには、ロジスティック回帰モデルへの入力には、同じ機能のデータ ソース (`sql_feature_ds`)、モデルをトレーニングするために使用することです。  多くの場合、スコアリングには新しいデータを使用したり、テスト用とトレーニング用のデータを別に確保したりします。
  
    + 予測結果は、テーブルに保存されます_taxiscoreOutput_します。 このテーブルのスキーマが rxSqlServerData を使用して作成するときに定義されないことに注意してください。 スキーマは、rxPredict 出力から取得されます。
  
    + RxSqlServer データ関数を実行する SQL ログインは、予測された値を格納するテーブルを作成するには、データベースの DDL 特権が必要です。 ログインは、テーブルを作成できない場合、ステートメントは失敗します。

2. [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) 関数を呼び出して結果を生成します。

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    ステートメントが成功すると、実行すると時間がかかります。 完了するは、SQL Server Management Studio を開くし、テーブルが作成されたこと、および予想される出力のスコア列およびその他が含まれていることを確認します。

## <a name="plot-model-accuracy"></a>モデルの精度をプロットします。

モデルの精度のアイデアを取得するには、使用することができます、 [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc)受信者操作特性曲線をプロットする関数。 RxRoc が RevoScaleR パッケージで提供される新しい関数のいずれかであるため、リモート計算コンテキストをサポートする、2 つのオプションがあります。

+ RxRoc 関数を使用して、リモート コンピューティング コンテキストでプロットを実行し、ローカル クライアントに、プロットを返すことができます。

+ また、R クライアント コンピューターにデータをインポートして、他の R プロット関数を使用してパフォーマンス グラフを作成することもできます。

このセクションでは、両方の手法を確認してみます。

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>リモート (SQL Server) コンピューティング コンテキストでプロットを実行する

1. 関数 rxRoc を呼び出すし、入力として以前に定義されているデータを提供します。

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    この呼び出しは、コンピューティング、ROC グラフで使用する値を返します。 ラベル列が_tipped_、実際の結果を予測しようとしているときに、_スコア_列には、予測。

2. 実際には、グラフをプロットするには、ROC オブジェクトを保存し、プロット関数を描画します。 グラフでは、リモート コンピューティング コンテキストで作成され、R 環境に返されます。

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    R グラフィックス デバイスを開くときか、クリックして、グラフを表示、**プロット**RStudio でウィンドウ。

    ![モデルの ROC プロット](media/rsql-e2e-rocplot.png "モデルの ROC プロット")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>SQL Server のデータを使用して、ローカル コンピューティング コンテキストでプロットを作成する

実行して、計算コンテキストはローカルを確認する`rxGetComputeContext()`コマンド プロンプトでします。 戻り値は「RxLocalSeq 計算コンテキスト」になります。

1. ローカル コンピューティング コンテキストのプロセスはほぼ同じは。 使用する、 [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport)ローカルの R 環境に指定されたデータを取り込む関数。

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. ローカル メモリにデータを使用して、読み込む、 **ROCR**パッケージ化、およびそのパッケージの予測関数を使用して、いくつかの新しい予測を作成します。

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. 出力変数に格納されている値に基づいて、ローカルのプロットを生成`pred`します。

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![R を使用したモデルのパフォーマンスのプロット](media/rsql-e2e-performanceplot.png "R を使用したモデルのパフォーマンスのプロット")

> [!NOTE]
> グラフは異なるために使用するデータ ポイントの数に応じて、これらになります。

## <a name="deploy-the-model"></a>モデルの配置

モデルを構築しても実行することを確認したら可能性がありますする、ユーザーまたは組織内ユーザーを利用する、モデルの使用またはおそらくの再トレーニングし、を定期的にモデルを再サイトにデプロイします。 このプロセスが呼ば*運用*モデル。 SQL server の運用化は、ストアド プロシージャに R コードを埋め込むことで実現されます。 の手順では、コードは、SQL Server に接続できる任意のアプリケーションから呼び出すことができます。

外部アプリケーションからモデルを呼び出すことができます、前に、運用環境で使用するデータベースにモデルを保存する必要があります。 トレーニング済みモデル型の 1 つの列にバイナリ形式で格納**varbinary (max)** します。

一般的な展開ワークフローは、次の手順で構成されます。

1. 16 進数の文字列に、モデルをシリアル化します。
2. データベースにシリアル化されたオブジェクトを転送します。
3. Varbinary (max) 列でモデルを保存します。

このセクションでは、ストアド プロシージャを使用して、モデルを永続化し、予測のために使用できるようにする方法を説明します。 このセクションで使用されるストアド プロシージャは、PersistModel です。 PersistModel の定義では、[の前提条件](#prerequisites)します。

1. 既に使用しない場合、ローカルの R 環境に切り替える、モデル、シリアル化し、変数に保存します。

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. 使用して ODBC 接続を開く**RODBC**します。 読み込まれたパッケージが既にある場合は、RODBC への呼び出しを省略できます。

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. プロシージャを呼び出し、PersistModel が格納されている SQL Server で transmite をデータベースにシリアル化されたオブジェクトを列に、モデルのバイナリ表現を格納します。 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Management Studio を使用して、モデルの確認方法が存在します。 オブジェクト エクスプ ローラーを右クリックし、 **nyc_taxi_models**テーブルし、クリックして**上位 1000 行**します。 結果のバイナリ表現が表示されるはずの**モデル**列。

モデルをテーブルへの保存に必要なステートメントは、INSERT のみです。 ただしなどのストアド プロシージャでラップされたときに簡単には多くの場合、 *PersistModel*します。

## <a name="next-steps"></a>次のステップ

では、最後のレッスンを使用して、保存済みのモデルに対してスコアリングを実行する方法を説明します。[!INCLUDE[tsql](../../includes/tsql-md.md)]します。

> [!div class="nextstepaction"]
> [R モデルをデプロイし、SQL で使用](walkthrough-deploy-and-use-the-model.md)
