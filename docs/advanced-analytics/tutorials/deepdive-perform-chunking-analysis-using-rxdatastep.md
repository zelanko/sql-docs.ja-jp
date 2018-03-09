---
title: "RxDataStep (SQL と R deep dive) を使用してチャンクの分析を実行 |Microsoft ドキュメント"
ms.custom: 
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
dev_langs:
- R
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5b5ba8c59ca5dfb84a7c062a8c09b40e0528fb5d
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-and-r-deep-dive"></a>RxDataStep (SQL と R deep dive) を使用してチャンクの分析を実行します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このレッスンで使用し、 **rxDataStep**データセット全体がメモリに読み込まれるおよび R. 従来と同様に、同時に処理されるを必要とするのではなく、チャンクのデータを処理する関数**RxDataStep**関数を読み取り、チャンク内のデータが R 関数をさらに、データの各チャンクに適用し、各チャンクの概要の結果を共通に保存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース。 すべてのデータが読み取られると、結果は結合されます。

> [!TIP]
> このレッスンを使用して代替表を計算する、 `table` R. 関数この例は、説明だけを目的のものです。 
> 
> 使用することをお勧め実際のデータ セットを集計する必要がある場合、 **rxCrossTabs**または**rxCube**関数**RevoScaleR**、この種の最適化されます操作。

## <a name="partition-data-by-values"></a>値によってデータのパーティション分割

1. R を呼び出すカスタム R 関数を作成`table`、データの各チャンクに対して機能し、新しい関数の名前`ProcessChunk`です。
  
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
  
3. 処理しているデータを保持するために SQL Server データ ソースを定義します。 最初に SQL クエリを変数に代入します。 次でその変数を使用して、 *sqlQuery*新しいの引数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース。
  
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
4. 必要に応じて、実行することができます**rxGetVarInfo**このデータ ソース。 この時点では、1 つの列を含む: *Var 1: DayOfWeek、型: 係数、要素レベルはありません*
     
5. この因子変数をソース データに適用する前に、中間結果を保持するための別のテーブルを作成します。 もう一度、makign を同じ名前の既存のテーブルを削除するのにことを確認して、データを定義する、だけ RxSqlServerData 関数を使用します。
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  ユーザー定義関数を呼び出す`ProcessChunk`としてそれを使用して、読み取られると、データを変換する、 *transformFunc*への引数、 **rxDataStep**関数。
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  中間結果を表示する`ProcessChunk`の結果を割り当てる**rxImport**変数にし、コンソールに結果を出力します。
  
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

10. 削除するには、中間結果のテーブルへの呼び出しを行う**rxSqlServerDropTable**です。
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-step"></a>次の手順

[ローカル計算コンテキストでデータを分析する](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>前の手順

[rxDataStep を使用した新しい SQL Server テーブルの作成](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
