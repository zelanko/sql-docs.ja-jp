---
title: "rxDataStep を使用したチャンク分析の実行 (データ サイエンスの詳細) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# rxDataStep を使用したチャンク分析の実行 (データ サイエンスの詳細)
*rxDataStep* 関数を利用すれば、従来の R のように、データセット全体をメモリに読み込み、一度に処理することを要求せず、データをチャンク単位で処理できます。データをチャンク単位で読み込み、R 関数を利用してデータの各チャンクを順々に処理し、各チャンクのまとめ結果を共通の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースに書き込みます。  
  
このレッスンでは、R の *table* 関数を使用して予備のテーブルを計算する方法でこの手法を実践します。  
  
> [!TIP]  
> この例は説明のみを目的としています。 実世界のデータセットを表にする場合、**RevoScaleR** に組み込まれている *rxCrossTabs* 関数または *rxCube* 関数の使用が推奨されます。この種類の操作のために最適です。  
  
## 値によるデータのパーティション分割  
  
1.  最初に「*ProcessChunk*」という名前の R 関数を作成します。これはデータの各チャンクで *table* 関数を呼び出します。  
  
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
 
  
2.  コンピューティング コンテキストをサーバーに設定します。  
  
    ```R  
    rxSetComputeContext( sqlCompute )   
    ```  
  
3.  処理しているデータを保持する SQL Server データ ソースを定義します。 最初に SQL クエリを変数に代入します。   
  
    ```R  
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"   
    ```  

4.  新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースの *sqlQuery* 引数にその変数を挿入します。  
  
    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,  
        connectionString = sqlConnString,    
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",   
            levels = as.character(1:7))))    
    ```  
     このデータ ソースで *rxGetVarInfo* を実行した場合、それに「*Var 1: DayOfWeek, Type: factor, no factor levels available*」という列が 1 つだけ含まれていることがわかります。
     
5.  この因子変数をソース データに適用する前に、中間結果を保持するための別のテーブルを作成します。 もう一度 *RxSqlServerData* 関数を使用してデータを定義し、同じ名前の既存テーブルを削除します。   
  
    ```R  
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)   
    # Check whether the table already exists.  
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }   
    ```  
  
7.  次にカスタム関数の *ProcessChunk* 関数を呼び出し、読み込まれると同時にデータを変換します。そのとき、データを *rxDataStep* 関数の *transformFunc* 引数として使用します。  
  
    ```R  
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)   
    ```  
  
8.  *ProcessChunk* の中間結果を表示するには、*rxImport* の結果を変数に代入し、結果をコンソールに出力します。  
  
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
  
10. 中間結果テーブルを削除するには、別に *rxSqlServerDropTable* を呼び出します。  
  
    ```R  
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)    
    ```  
  
## 次の手順  
[レッスン 4: ローカル計算コンテキストでのデータの分析 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## 前の手順  
[rxDataStep を使用した新しい SQL Server テーブルの作成 (データ サイエンスの詳細)](../../advanced-analytics/r-services/create-new-sql-server-table-using-rxdatastep-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
