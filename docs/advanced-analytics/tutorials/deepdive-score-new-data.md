---
title: "新しいデータを (SQL と R deep dive) スコア付け |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 54cc4dd297357407592c953b54e04d0ae024f7aa
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="score-new-data-sql-and-r-deep-dive"></a>新しいデータを (SQL と R deep dive) スコア付け

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このステップでは、入力として同じ独立変数を使用する別のデータ セットのスコアを作成する前に作成したロジスティック回帰モデルを使用します。

> [!NOTE]
> 次の手順の一部の DDL 管理者特権を必要があります。

## <a name="generate-and-save-scores"></a>生成し、スコアの保存
  
1. 以前に設定したデータ ソースを更新`sqlScoreDS`、必須の列情報を追加します。
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. 結果が失われないようにするには、新しいデータ ソース オブジェクトを作成します。 新しいテーブルを作成する新しいデータ ソース オブジェクトを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    この時点では、テーブルは作成されていません。 これはデータのコンテナーを定義するためだけのステートメントです。
     
3. 現在のコンピューティング コンテキストを確認し、必要に応じてコンピューティング コンテキストをサーバーに設定します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. 結果を生成する予測関数を実行する前に、既存の出力テーブルの存在を確認する必要があります。 それ以外の場合、新しいテーブルを作成しようとしたときに、エラーを得られます。
  
    この処理を実行するには、入力としてテーブル名を渡して、関数 **rxSqlServerTableExists** と **rxSqlServerDropTable**を呼び出します。
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    -  関数 **rxSqlServerTableExists** は ODBC ドライバーに対してクエリを実行し、テーブルが存在する場合は TRUE、それ以外の場合は FALSE を返します。
    -  関数は、 **rxSqlServerDropTable** DDL を実行し、テーブルが正常に場合は TRUE。 削除すると、FALSE それ以外の場合を返します。
    - 参照は、どちらの関数をご覧ください: [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)
  
5. これで、使用する準備ができたら、 [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) 、スコアを作成する機能、データ ソースで定義されている新しいテーブルに保存`sqlScoreDS`です。
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    **rxPredict** 関数も、リモート計算コンテキストでの実行をサポートする関数です。 **rxLinMod** 、 [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)、または [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)を使用して作成したモデルからスコアを作成する場合に [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm)関数を使用できます。
  
    - ここで *writeModelVars* パラメーターは **TRUE** に設定されます。 これは見積もりに使用された変数が新しいテーブルに追加されることを意味します。
  
    - *predVarNames* パラメーターにより、結果が保存される変数が指定されます。 ここで、新しい変数を渡している`ccFraudLogitScore`です。
  
    - *rxPredict* の **type** パラメーターで、予測の計算方法を定義します。 キーワードを指定**応答**応答変数の小数点以下桁数に基づくスコアを生成します。 また、キーワードを使用して**リンク**ロジスティック スケールを使用している場合、基になるリンク関数に基づいてスコアを生成する予測が作成されます。

6. 少し時間をおいて Management Studio でテーブルの一覧を更新すると、新しいテーブルとそのデータを確認することができます。

7. 出力予測に変数を追加するには、*extraVarsToWrite* 引数を使用します。  たとえば、次のコードでは、変数で`custID`がスコア付けのデータ テーブルからの予測の出力テーブルに追加します。
  
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

## <a name="display-scores-in-a-histogram"></a>ヒストグラムのスコアを表示

新しいテーブルが作成された後は、コンピューティングし、10,000 の予測スコアのヒストグラムを表示します。 場合は、低、高の値を指定、ので、データベースから取得、作業データに追加、計算を高速です。

1. 新しいデータ ソースの作成`sqlMinMax`、低、高の値を取得するデータベースのクエリを実行します。
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     この例を見ると、 **RxSqlServerData** データ ソース オブジェクトを使用して SQL クエリ、関数、またはストアド プロシージャに基づいて任意のデータセットを定義し、それを R コードで使用するのが簡単だということがわかります。 この変数には実際の値は格納されず、データ ソースの定義のみが格納されます。 **rxImport**など関数で使用する場合にのみ、このクエリを実行して値を生成します。
      
2. 呼び出す、 [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)コンピューティング コンテキスト間で共有できるデータ フレームの値を格納する関数。
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **結果**
     
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3. 最大値と最小値を使用可能値を使用して、生成されたスコアの別のデータ ソースを作成します。
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. データ ソース オブジェクトを使用して`sqlOutScoreDS`スコアの取得を計算し、ヒストグラムを表示します。 必要に応じて、計算コンテキストを設定するコードを追加してください。
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **結果**
  
    ![R で作成された複雑なヒストグラム](media/rsql-sue-complex-histogram.png "R で作成された複雑なヒストグラム")
  
## <a name="next-step"></a>次の手順

[R を使用したデータの変換](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>前の手順

[モデルを作成する](../../advanced-analytics/tutorials/deepdive-create-models.md)


