---
title: RevoScaleR rxHistogram - SQL Server Machine Learning を使用して SQL Server のデータを視覚化します。
description: SQL Server で R 言語を使用してデータを視覚化する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c39d19807cfe01ca9c96b47de020abb9227c43a0
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513079"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>R (SQL Server と RevoScaleR チュートリアル) を使用した SQL Server のデータを視覚化します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

このレッスンでの値の分布を表示する R 関数を使用して、 *creditLine*性別による列。

> [!div class="checklist"]
> * ヒストグラムの入力の最小-最大変数を作成します。
> * 使用して、ヒストグラムでデータを視覚化**rxHistogram**から**RevoScaleR**
> * 使用して散布による視覚化**levelplot**から**格子**基本の R ディストリビューションに含まれる

このレッスンの例が示すように、同じスクリプトでオープン ソースの Microsoft 固有の関数を組み合わせることができます。

## <a name="add-maximum-and-minimum-values"></a>最大値と最小値を追加します。

前のレッスンから計算された概要統計情報に基づいて、さらに計算のデータ ソースに挿入できるデータに関する有用な情報を検出しました。 たとえば、最小および最大値を使用して、ヒストグラムを計算できます。 この演習で高値と低値を追加、 **RxSqlServerData**データ ソース。

1. まず、仮の変数をいくつか設定します。
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. 変数を使用して*ccColInfo*データ ソースの列を定義する前のレッスンで作成しました。
  
   新しい計算列を追加 (*numTrans*、 *numIntlTrans*、および*creditLine*) を元の定義をオーバーライドする列のコレクション。 次のスクリプトからメモリ内の出力を格納する、sumOut から取得した、最小値と最大値に基づいて要素を追加します**rxSummary**します。 
  
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
  
3. 更新バージョンを作成する次のステートメントを適用する列のコレクションを更新しているので、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]前に定義したデータ ソース。
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    SqlFraudDS データ ソースを使用して追加された新しい列を含むようになりました*ccColInfo*します。
  
この時点では、変更は R; でデータ ソース オブジェクトの影響を与える新しいデータがまだ書き込まれていないデータベース テーブルにします。 ただし、sumOut 変数にキャプチャされたデータを使用して、視覚化と概要を作成することができます。 

> [!TIP]
> 使用するどの計算コンテキストを忘れた場合は、実行**rxGetComputeContext()** します。 「RxLocalSeq 計算コンテキスト」の戻り値は、ローカル計算コンテキストで実行していることを示します。

## <a name="visualize-data-using-rxhistogram"></a>RxHistogram を使用してデータを視覚化します。

1. 次の R コードを使用して [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) 関数を呼び出し、式とデータ ソースを渡します。 ローカルで最初にこの操作を実行することで、予想される結果と、所要時間を確認できます。
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    内部的には、 **rxHistogram** は、 [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) パッケージに含まれる **rxCube** 関数を呼び出します。 **rxCube**とカウント列、式で指定された各変数の 1 つの列を含む、1 つのリスト (またはデータ フレーム) を出力します。
    
2. ここで、リモートの SQL Server コンピューターに、コンピューティング コンテキストを設定し、実行**rxHistogram**もう一度です。
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. 結果は、同じデータ ソースを使用しているが、リモート サーバーで、2 番目の手順で、計算が実行されるため、まったく同じです。 結果は、表示のためにローカル ワークステーションに返されます。
   
  ![ヒストグラム結果](media/rsql-sue-histogramresults.jpg "ヒストグラム結果")


## <a name="visualize-with-scatter-plots"></a>散布図のプロットと視覚化します。

散布図のプロットは、2 つの変数間のリレーションシップを比較するデータの探索中によく使用されます。 このため、組み込みの R パッケージを使用するにはによって提供される入力で**RevoScaleR**関数。

1. 呼び出す、 [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs)の平均を計算する関数*fraudRisk*の組み合わせごと*numTrans*と*numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    グループの平均の計算に使用するグループを指定するには、 `F()` 表記を使用します。 この例で`F(numTrans):F(numIntlTrans)`ことを示します整数変数を`numTrans`と`numIntlTrans`レベルには、各整数値、カテゴリ変数として処理する必要があります。
  
    既定の戻り値の**rxCube**は、 *rxCube オブジェクト*、クロス集計を表します。 
  
2. 呼び出す[rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) R の標準プロット関数のいずれかで簡単に使用できるデータ フレームに結果を変換する関数。
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    **RxCube**関数には、オプションの引数が含まれています。 *returnDataFrame* = **TRUE**、結果をデータ フレームに直接変換を使用できますが、します。 例 :
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    ただし、出力の**rxResultsDF**が簡潔であり、ソース列の名前を保持します。 実行することができます`head(cube1)`続けて`head(cubePlot)`出力を比較します。
  
3. 使用してヒート マップを作成、 **levelplot**関数を**格子**パッケージ、すべての R ディストリビューションに含まれています。
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **結果**
  
    ![散布図の結果](media/rsql-sue-scatterplotresults.jpg "散布図の結果")
  
このクイック分析から、トランザクションの数と国際取引の数の両方で不正行為のリスクが増えることを確認できます。

詳細については、 **rxCube**関数およびクロス集計表が一般に、表示[RevoScaleR を使用してデータを集計](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries)します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [SQL Server のデータを使用して R モデルを作成します。](../../advanced-analytics/tutorials/deepdive-create-models.md)