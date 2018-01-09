---
title: "作成し、R スクリプト (SQL と R deep dive) を実行 |Microsoft ドキュメント"
ms.date: 12/14/2017
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
- SQL Server 2017
dev_langs: R
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 302068f7ee9f1fe04bc7a3b1558e510274b2bc0d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="create-and-run-r-scripts-sql-and-r-deep-dive"></a>作成し、R スクリプト (SQL と R deep dive) を実行します。

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

データ ソースを設定し、1 つまたは複数のコンピューティング コンテキストを確立したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を利用し、高性能な R スクリプトを実行できます。  このレッスンでは、サーバーのコンピューティング コンテキストを使用してをいくつか共通機械学習のタスクを行うには。

- データを視覚化し、概要統計情報を生成する
- 線形回帰モデルを作成する
- ロジスティック回帰モデルを作成する
- 新しいデータにスコアを付け、スコアのヒストグラムを作成する

## <a name="change-compute-context-to-the-server"></a>変更をサーバーにコンテキストを計算します。

R コードを実行する前に、 *現行* のコンピューティング コンテキストまたは *アクティブ* なコンピューティング コンテキストを指定する必要があります。

1. R を使用して既に定義したコンピューティング コンテキストをアクティブにするには、ここに示すように **rxSetComputeContext** 関数を利用します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
    すべての後続の計算のテキストが行われるこのステートメントを実行するようになったら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されたコンピューター、 *sqlCompute*パラメーター。
  
2. ワークステーションで R コードを実行する場合、  **local** キーワードを利用し、コンピューティング コンテキストをローカル コンピューターに再び切り替えることができます。
  
    ```R
    rxSetComputeContext ("local")
    ```
  
    この関数でサポートされているその他のキーワードの一覧が必要な場合、R コマンド ラインに「 `help("rxSetComputeContext")` 」と入力してください。
  
3. コンピューティング コンテキストを指定すると、変更するまでアクティブな状態が維持されます。 ただし、リモート サーバー コンテキストで実行 *できない* R スクリプトはローカルで実行されます。

## <a name="compute-some-summary-statistics"></a>いくつかの概要統計情報を計算します。

コンピューティング コンテキストの動作を確認するには、概要統計情報を使用して一部の生成を再試行してください、`sqlFraudDS`データ ソース。  ただし、データ ソース オブジェクトには、使用するデータだけを定義しますコンピューティング コンテキストは変更されません。

+ 実行するにはローカルに集計を使用して**rxSetComputeContext**を指定し、_ローカル_キーワード。
+ SQL Server コンピューターで同じ計算を行うには、先に定義した SQL コンピューティング コンテキストに切り替えます。

1. 呼び出す、 [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary)関数し、数式やデータ ソースなどの必須引数を渡すし、結果を変数に代入`sumOut`です。
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    R 言語には、多くの集計関数が用意されていますが、 **rxSummary**など、さまざまなリモート計算コンテキストで実行をサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 同様の機能については、次を参照してください。 [RevoScaleR を使用したデータの要約](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries)です。
  
2. 内容を印刷するには処理が完了したら、`sumOut`変数をコンソールにします。
  
    ```R
    sumOut
    ```
  
    > [!NOTE]
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターから返される前に結果を出力しないでください。出力すると、エラーが表示されることがあります。

**結果**

*Summary Statistics Results for: ~gender + balance + numTrans +*

 *numIntlTrans + creditLine*

 *Data: sqlFraudDS (RxSqlServerData Data Source)*

 *Number of valid observations: 10000*

 *Name  Mean    StdDev  Min Max ValidObs    MissingObs*

 *balance       4075.0318 3926.558714            0   25626 100000*

 *numTrans        29.1061   26.619923 0     100 10000    0           100000*

 *numIntlTrans     4.0868    8.726757 0      60 10000    0           100000*

 *creditLine 9.1856 9.870364 1 75 10000 0 100000*

 *性別カテゴリのカウント*

 *Number of categories: 2*

 *Number of valid observations: 10000*

 *Number of missing observations: 0*

 *gender Counts*

 *Male   6154*

  *Female 3846*

## <a name="add-maximum-and-minimum-values"></a>最大値と最小値を追加します。

計算された概要統計情報に基づき、後続の計算で使用するためにデータ ソースに入力するデータに関する有益な情報がいくつか得られました。 たとえば、ヒストグラムを計算する最小値と最大値を使用できます。 このため、上限と下限値を追加してみましょう、 **RxSqlServerData**データ ソース。

さいわい[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]カテゴリ要素のデータに整数型のデータを効率的に変換する最適化された関数が含まれています。

1. まず、仮の変数をいくつか設定します。
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. 先に作成した変数 `ccColInfo` を利用し、データ ソースに列を定義します。
  
    また、いくつかの新しい計算列を追加 (`numTrans`、 `numIntlTrans`、および`creditLine`) を列のコレクション。
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")),
        cardholder = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
    ```
  
3. 最新バージョンを作成するには、次のステートメントを適用する列のコレクションを更新すること、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]前に定義したデータ ソース。
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    `sqlFraudDS`データ ソースを使用して追加された新しい列を含むようになりました`ccColInfo`です。
  

この時点では、変更が R; でデータ ソース オブジェクトに影響します。新しいデータが書き込まれていないデータベース テーブルにまだです。 ただしでキャプチャしたデータを使用することができます、`sumOut`視覚エフェクトと集計を作成する変数。 次の手順では、計算コンテキストの切り替え中にこれを行う方法を説明します。

> [!TIP]
> 使用しているコンピューティング コンテキストを忘れた場合は、実行`rxGetComputeContext()`です。  「RxLocalSeq コンピューティング コンテキスト」の戻り値は、ローカルの計算コンテキストで実行していることを示します。

## <a name="next-step"></a>次の手順

[R を使用して SQL Server のデータを表示する](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)

## <a name="previous-step"></a>前の手順

[計算コンテキストの定義と使用](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
