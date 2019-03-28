---
title: RevoScaleR rxDataStep - SQL Server Machine Learning を使用したチャンク分析を実行します。
description: SQL Server で R 言語を使用して、分散分析用のデータをチャンクする方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: dfa11ed4db8985d64bbac511ed7a4ee88166cebe
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512469"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>RxDataStep (SQL Server と RevoScaleR チュートリアル) を使用したチャンク分析を実行します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

このレッスンでは使用して、 **rxDataStep**データセット全体がメモリに読み込まれ、従来の R のように、一度に処理が必要とするのではなく、チャンク単位でデータを処理する関数**RxDataStep**関数を読み取り、チャンク内のデータがデータの各チャンクをさらに、R 関数を適用し、各チャンクの集計結果を共通に保存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース。 すべてのデータが読み取られると、結果を結合します。

> [!TIP]
> このレッスンを使用して予備のテーブルを計算する、**テーブル**r. 関数この例は説明のみを目的のもの。 
> 
> 使用することをお勧め実際のデータ セットを集計する必要がある場合、 **rxCrossTabs**または**rxCube**関数**RevoScaleR**、この種の最適化操作です。

## <a name="partition-data-by-values"></a>値によるデータのパーティション

1. R を呼び出すカスタム R 関数を作成**テーブル**、データの各チャンクに対して関数を新しい関数の名前と**ProcessChunk**します。
  
    ```R
    ProcessChunk <- function( dataList) {
    # Convert the input list to a data frame and compute contingency table
    chunkTable <- table(as.data.frame(dataList))
  
    # Convert table output to a data frame with a single row
    varNames <- names(chunkTable)
    varValues <- as.vector(chunkTable)
    dim(varValues) <- c(1, length(varNames))
    chunkDF <- as.data.frame(varValues)
    names(chunkDF) <- varNames
  
    # Return the data frame, which has a single row
    return( chunkDF )
    }
    ```

2. コンピューティング コンテキストをサーバーに設定します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
3. 処理するデータを保持する SQL Server データ ソースを定義します。 最初に SQL クエリを変数に代入します。 その変数を使用して、 *sqlQuery*新しい SQL Server データ ソースの引数。
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. 必要に応じて、実行**rxGetVarInfo**でこのデータ ソース。 この時点では、1 つの列が含まれています。*Var 1:DayOfWeek, Type: factor、ファクター レベルはありません。*
     
5. この因子変数をソース データに適用する前に、中間結果を保持するための別のテーブルを作成します。 だけを使用する、もう一度、 **RxSqlServerData**同じ名前の既存のテーブルを削除するように、データを定義する関数。
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  カスタム関数を呼び出す**ProcessChunk**としてを使用して、読み取られると、データを変換する、 *transformFunc*への引数、 **rxDataStep**関数。
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  中間結果を表示する**ProcessChunk**の結果を割り当てる**rxImport**の変数とし、コンソールに結果を出力します。
  
    ```R
    iroResults <- rxImport(iroDataSource)
    iroResults
    ```

    **結果の一部**

    |      |    1  |   2   |  3   |  4   |  5  |   6   |  7 |
    | --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
    | 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
    | 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |

9. チャンク全体の最終結果を計算するには、列を合計し、結果をコンソールに表示します。

    ```R
    finalResults <- colSums(iroResults)
    finalResults
    ```

    **結果**

    1  |   2  |   3  |   4  |   5  |   6  |   7
    ---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
    97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. 中間結果テーブルを削除するへの呼び出しを行い**rxSqlServerDropTable**します。
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [SQL Server の R チュートリアル](sql-server-r-tutorials.md)