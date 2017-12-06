---
title: "新しいデータをスコア付け |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83beab637e3740dc41706c34ccfacffe985f2957
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="score-new-data"></a>新しいデータのスコア付け

予測に利用できるモデルが与えられたので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからそれにデータを入力し、いくつかの予測を生成します。

ロジスティック回帰モデル *logitObj*を使用して、同じ独立した変数を入力として使用する別のデータセットのスコアを作成します。

> [!NOTE]
> 手順の一部には、DDL 管理者特権が必要です。

## <a name="generate-and-save-scores"></a>生成し、スコアの保存
  
1. 以前にセットアップしたデータ ソースの *sqlScoreDS*を更新して、必要な列情報を追加します。
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. 結果が失われないように、新しいデータ ソース オブジェクトを作成します。このオブジェクトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに新しいテーブルを作成する際に使用します。
  
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
  
    -  関数 rxSqlServerTableExists では、ODBC ドライバーを照会し、テーブルが存在する場合、FALSE それ以外の場合は TRUE を返します。
    -  関数の rxSqlServerDropTable 関数は、DDL を実行し、テーブルが正常に削除された場合、FALSE それ以外の場合は TRUE を返します。
  
5. これで、 **rxPredict** 関数を使用してスコアを作成し、データ ソース *sqlScoreDS*に定義した新しいテーブルに保存する準備が整いました。
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    RxPredict 関数は、リモート計算コンテキストで実行をサポートする別の関数です。 RxPredict 関数を使用して、rxLinMod、rxLogit、または rxGlm を使用して作成されたモデルからスコアを作成することができます。
  
    - ここで *writeModelVars* パラメーターは **TRUE** に設定されます。 これは見積もりに使用された変数が新しいテーブルに追加されることを意味します。
  
    - *predVarNames* パラメーターにより、結果が保存される変数が指定されます。 ここで、 *ccFraudLogitScore*という新しい変数を渡します。
  
    - *型*rxPredict のパラメーターは、予測を計算する方法を定義します。 キーワード **response** を指定し、応答変数のスケールに基づいてスコアを生成するか、キーワード **link** を使用し、基礎となるリンク関数に基づいてスコアを生成します。リンク関数に基づく場合、予測はロジスティック スケールになります。

6. 少し時間をおいて Management Studio でテーブルの一覧を更新すると、新しいテーブルとそのデータを確認することができます。

7. その他の変数を出力の予測に追加するには、 *extraVarsToWrite* 引数を使用します。  たとえば、次のコードの変数 *custID* は、スコアリング データ テーブルから予測の出力テーブルに追加されています。
  
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

## <a name="display-scores-in-a-histogram"></a>ヒストグラムでスコアを表示する

新しいテーブルが作成されたら、10,000 件の予測スコアのヒストグラムを計算し、表示します。 下限と上限を指定すると (データベースから取得し、作業中のデータに追加する)、計算が速くなります。

1. 新しいデータ ソース *sqlMinMax*を作成します。データベースに対してクエリを実行し、下限と上限を取得するデータ ソースです。
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     この例を RxSqlServerData データ ソース オブジェクトを使用して SQL クエリ、関数、またはストアド プロシージャ、に基づいて任意のデータセットを定義することがいかに簡単を参照して、R コードでそれらを使用します。 データ ソースの定義のみです。 実際の値が変数に格納できません。rxImport のような関数で使用する場合にのみ値を生成するクエリが実行されます。
      
2. コンピューティング コンテキスト間で共有できるデータ フレームの値を格納する rxImport 関数を呼び出します。
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **[結果]**
     
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3. 最大値と最小値を使用可能値を使用して、スコアのデータ ソースを作成します。
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. 最後に、スコア データ ソース オブジェクトを使用してスコアリング データを取得し、ヒストグラムを計算して表示します。 必要に応じて、計算コンテキストを設定するコードを追加してください。
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **[結果]**
  
    ![R で作成された複雑なヒストグラム](media/rsql-sue-complex-histogram.png "R で作成された複雑なヒストグラム")
  
## <a name="next-step"></a>次の手順

[R を使用するデータを変換します。](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>前の手順

[モデルを作成します。](../../advanced-analytics/tutorials/deepdive-create-models.md)


