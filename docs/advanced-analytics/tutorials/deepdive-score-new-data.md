---
title: RevoScaleR と rxPredict - SQL Server Machine Learning を使用して新しいデータのスコア付け
description: SQL Server で R 言語を使用してデータをスコア付けする方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: b96e70a6002722063a0be42c964c5e423503a0d7
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510349"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>新しいデータ (SQL Server と RevoScaleR チュートリアル) のスコア付け
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

この手順では、同じ独立変数を入力として使用する別のデータ セットのスコアを付け、前のレッスンで作成したロジスティック回帰モデルを使用します。

> [!div class="checklist"]
> * 新しいデータのスコア付け
> * スコアのヒストグラムを作成します。

> [!NOTE]
> 次の手順の一部の DDL 管理者特権を必要があります。

## <a name="generate-and-save-scores"></a>生成し、スコアの保存
  
1. SqlScoreDS データ ソースを更新 (で作成した[レッスン 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)) 前のレッスンで作成された列の情報を使用します。
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. 結果が失われないようにするには、新しいデータ ソース オブジェクトを作成します。 次に、新しいデータ ソース オブジェクトを使用して、RevoDeepDive データベースに新しいテーブルを作成します。
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    この時点では、テーブルは作成されていません。 これはデータのコンテナーを定義するためだけのステートメントです。
     
3. 現在のコンピューティング コンテキストを使用するかを確認**rxGetComputeContext()**、し、必要な場合は、サーバーに、コンピューティング コンテキストを設定します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. 念のため、出力テーブルの存在を確認します。 同じ名前で既に存在する場合に、新しいテーブルを作成する際は、エラーが表示されます。
  
    この処理を実行するには、入力としてテーブル名を渡して、関数 [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) と [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)を呼び出します。
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** ODBC ドライバーを照会し、テーブルが存在する場合、FALSE それ以外の場合は TRUE を返します。
    + **rxSqlServerDropTable** DDL を実行し、TRUE の場合は、テーブルが正常に削除すると、FALSE それ以外の場合を返します。

5. 実行[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)にスコアを作成し、データ ソースの sqlScoreDS で定義されている新しいテーブルに保存します。
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    **rxPredict** 関数も、リモート計算コンテキストでの実行をサポートする関数です。 使用することができます、 **rxPredict**モデルからスコアを作成する関数がに基づいて[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)、 [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)、または[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm)します。
  
    - ここで *writeModelVars* パラメーターは **TRUE** に設定されます。 これは見積もりに使用された変数が新しいテーブルに追加されることを意味します。
  
    - *predVarNames* パラメーターにより、結果が保存される変数が指定されます。 ここで、新しい変数を渡している`ccFraudLogitScore`します。
  
    - *rxPredict* の **type** パラメーターで、予測の計算方法を定義します。 キーワードを指定する**応答**応答変数のスケールに基づいてスコアを生成します。 または、キーワードを使用して**リンク**ロジスティック スケールを使用する場合、基になるリンク関数に基づいてスコアを生成する予測が作成されます。

6. 少し時間をおいて Management Studio でテーブルの一覧を更新すると、新しいテーブルとそのデータを確認することができます。

7. 出力予測に変数を追加するには、*extraVarsToWrite* 引数を使用します。  たとえば、次のコードの変数 *custID* は、スコアリング データ テーブルから予測の出力テーブルに追加されています。
  
    ```R
    rxPredict(modelObject = logitObj,
            data = sqlScoreDS,
            outData = sqlServerOutDS,
            predVarNames = "ccFraudLogitScore",
              type = "link",
            writeModelVars = TRUE,
            extraVarsToWrite = "custID",
            overwrite = TRUE)
    ```

## <a name="display-scores-in-a-histogram"></a>ヒストグラムでスコアを表示

新しいテーブルが作成された後は、コンピューティングし、10,000 の予測スコアのヒストグラムを表示します。 下限と上限値を指定しますのでこれらは、データベースから取得し、作業中のデータを追加するには、計算を高速です。

1. 新しいデータ ソースでは、下限と上限値を取得するデータベースのクエリを実行するには、sqlMinMax を作成します。
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     この例を見ると、 **RxSqlServerData** データ ソース オブジェクトを使用して SQL クエリ、関数、またはストアド プロシージャに基づいて任意のデータセットを定義し、それを R コードで使用するのが簡単だということがわかります。 この変数には実際の値は格納されず、データ ソースの定義のみが格納されます。 **rxImport**など関数で使用する場合にのみ、このクエリを実行して値を生成します。
      
2. 呼び出す、 [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)コンピューティング コンテキスト全体で共有できるデータ フレームに値を格納する関数。
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **結果**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. 最大値と最小値が使用可能な値を使用して、生成されたスコアの別のデータ ソースを作成します。
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. スコアを取得し、コンピューティングし、ヒストグラムを表示するには、データ ソース オブジェクトの sqlOutScoreDS を使用します。 必要に応じて、計算コンテキストを設定するコードを追加してください。
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **結果**
  
    ![R で作成された複雑なヒストグラム](media/rsql-sue-complex-histogram.png "R で作成された複雑なヒストグラム")
  
## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [R を使用したデータの変換](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)