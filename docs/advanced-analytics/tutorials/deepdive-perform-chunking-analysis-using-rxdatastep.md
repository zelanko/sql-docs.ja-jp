---
title: "RxDataStep を使用して、チャンキング分析を実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: 17
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: af375ddf99794b748699355203becd137227fbcd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="perform-chunking-analysis-using-rxdatastep"></a>rxDataStep を使用したチャンク分析の実行

**rxDataStep** 関数を利用すれば、従来の R のように、データセット全体をメモリに読み込み、一度に処理することを要求せず、データをチャンク単位で処理できます。データをチャンク単位で読み込み、R 関数を利用してデータの各チャンクを順々に処理し、各チャンクのまとめ結果を共通の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースに書き込みます。

このレッスンでは、演習でこの手法を使用して、`table`コンティンジェンシー テーブルを計算、R 内の関数。

> [!TIP]
> この例は説明のみを目的としています。 使用することをお勧め実際のデータ セットを集計する必要がある場合、 **rxCrossTabs**または**rxCube**関数**RevoScaleR**、この種の最適化されます操作。

## <a name="partition-data-by-values"></a>値によるデータのパーティション分割

1. カスタムの R 関数を呼び出すを最初に、作成、*テーブル*、データの各チャンクに対して機能し、名前を付けます`ProcessChunk`です。
  
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
    rxSetComputeContext( sqlCompute )
    ```
  
3. 処理しているデータを保持する SQL Server データ ソースを定義します。 最初に SQL クエリを変数に代入します。
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    ```

4. 新しい *データ ソースの* sqlQuery [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引数にその変数を挿入します。
  
    ```R
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
     このデータ ソースで *rxGetVarInfo* を実行した場合、それに「 *Var 1: DayOfWeek, Type: factor, no factor levels available*」という列が 1 つだけ含まれていることがわかります。
     
5. この因子変数をソース データに適用する前に、中間結果を保持するための別のテーブルを作成します。 もう一度、先ほど RxSqlServerData 関数を使用して、データを定義し、同じ名前の既存のテーブルを削除します。
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  これで、ユーザー定義関数を呼び出すあります`ProcessChunk`としてそれを使用して、読み取られると、データを変換する、 *transformFunc* rxDataStep 関数に渡す引数。
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  中間結果を表示する`ProcessChunk`rxImport の結果を変数に割り当て、およびコンソールに結果を出力します。
  
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

 **[結果]**
  1  |   2  |   3  |   4  |   5  |   6  |   7
---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. 中間結果のテーブルを削除するには、rxSqlServerDropTable に対して別の呼び出しを確認します。
  
    ```R
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)
    ```

## <a name="next-step"></a>次の手順

[ローカル コンピューティング コンテキストにあるデータを分析します。](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>前の手順

[RxDataStep を使用して、新しい SQL Server のテーブルを作成します。](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)



