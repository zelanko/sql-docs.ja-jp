---
title: "作成し、R スクリプトを実行 |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5afb4be84373a1002d7a141fdc743a3a91d1ac8
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="create-and-run-r-scripts"></a>作成し、R スクリプトを実行します。

データ ソースを設定し、1 つまたは複数のコンピューティング コンテキストを確立したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を利用し、高性能な R スクリプトを実行できます。  このレッスンでは、サーバー コンピューティング コンテキストを利用し、次のような一般的な機械学習タスクを実行します。

- データを視覚化し、概要統計情報を生成する
- 線形回帰モデルを作成する
- ロジスティック回帰モデルを作成する
- 新しいデータにスコアを付け、スコアのヒストグラムを作成する

## <a name="change-compute-context-to-the-server"></a>コンピューティング コンテキストをサーバーに変更する

R コードを実行する前に、 *現行* のコンピューティング コンテキストまたは *アクティブ* なコンピューティング コンテキストを指定する必要があります。

1. R を使用して既に定義したコンピューティング コンテキストをアクティブにするには、ここに示すように **rxSetComputeContext** 関数を利用します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
    このステートメントを実行すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlCompute *パラメーターに指定されている* コンピューターで直後に後続のすべての計算が行われます。
  
2. ワークステーションで R コードを実行する場合、  **local** キーワードを利用し、コンピューティング コンテキストをローカル コンピューターに再び切り替えることができます。
  
    ```R
    rxSetComputeContext ("local")
    ```
  
    この関数でサポートされているその他のキーワードの一覧が必要な場合、R コマンド ラインに「 `help("rxSetComputeContext")` 」と入力してください。
  
3. コンピューティング コンテキストを指定すると、変更するまでアクティブな状態が維持されます。 ただし、リモート サーバー コンテキストで実行 *できない* R スクリプトはローカルで実行されます。

## <a name="compute-summary-statistics"></a>概要統計情報を計算する

コンピューティング コンテキストの動作を確認するには、 *sqlFraudDS* データ ソースを利用して概要統計情報を生成してみてください。  データ ソース オブジェクトは使用するデータを定義するだけのものであり、コンピューティング コンテキストは変更されないことに注意してください。

+ 概要をローカルで実行するには、 **rxSetComputeContext** を使用し、"local" キーワードを指定します。
+ SQL Server コンピューターで同じ計算を行うには、先に定義した SQL コンピューティング コンテキストに切り替えます。

1. **rxSummary** 関数を呼び出し、式やデータ ソースなど、必須の引数を渡し、結果を変数 *sumOut*に代入します。
  
    ```R
    sumOut \<- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    R 言語には、多くの集計関数が用意されていますが、rxSummary など、さまざまなリモート計算コンテキストで実行をサポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  同様の関数に関する詳細については、 [ScaleR 参照](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries) の「 [Data Summaries](https://msdn.microsoft.com/microsoft-r/scaler/scaler)」 (データの概要) を参照してください。
  
2. 処理が完了したら、 *sumOut* 変数のコンテンツをコンソールに出力できます。
  
    ```R
    sumOut
    ```
  
    > [!NOTE]
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターから返される前に結果を出力しないでください。出力すると、エラーが表示されることがあります。


**[結果]**

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

## <a name="add-maximum-and-minimum-values"></a>最小値と最大値を追加する

計算された概要統計情報に基づき、後続の計算で使用するためにデータ ソースに入力するデータに関する有益な情報がいくつか得られました。 たとえば、RxSqlServerData データ ソースへの高値と低値を追加するために、ヒストグラムを計算する最小値と最大値を使用できます。

幸いなことに、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] には、整数データを分類別の要因データに非常に効率的に変換できるように最適化された関数が含まれています。

1. まず、仮の変数をいくつか設定します。
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. 先に作成した変数 *ccColInfo* を利用し、データ ソースに列を定義します。
  
    また、列コレクションに新しく計算された列をいくつか追加します (*numTrans*、 *numIntlTrans*、 *creditLine*)。
  
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
  
3. 列コレクションを更新しているので、次のステートメントを適用し、先に定義した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースの更新版を作成できます。
  
    ```R
    sqlFraudDS \<- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    これで、 *sqlFraudDS* データ ソースに、 *ccColInfo*に追加された新しい列が含まれます。
  
  以上の変更は R のデータ ソース オブジェクトにのみ影響を与えます。新しいデータはデータベース テーブルにまだ書き込まれていません。 ただし、 *sumOut* 変数でキャプチャされたデータを使用し、視覚化と概要を作成できます。 次の手順では、これを行い、同時にコンピューティング コンテキストを切り替える方法について説明します。

> [!TIP]
> 使用しているコンピューティング コンテキストを忘れた場合は、実行`rxGetComputeContext()`です。  戻り値の`RxLocalSeq Compute Context`ローカル コンピューティング コンテキストで実行していることを示します。

## <a name="next-step"></a>次の手順

[R を使用する SQL Server データを視覚化します。](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)

## <a name="previous-step"></a>前の手順

[定義し、計算コンテキストを使用します。](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

