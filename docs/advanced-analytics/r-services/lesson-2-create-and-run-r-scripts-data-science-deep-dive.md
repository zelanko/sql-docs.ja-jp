---
title: "レッスン 2: R スクリプトの作成と実行 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/26/2016"
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
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# レッスン 2: R スクリプトの作成と実行 (データ サイエンスの詳細情報)
データ ソースを設定し、1 つまたは複数のコンピューティング コンテキストを確立したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を利用し、高性能な R スクリプトを実行できます。  このレッスンでは、サーバー コンピューティング コンテキストを利用し、次のような一般的な機械学習タスクを実行します。  
  
-   データを視覚化し、概要統計情報を生成する    
-   線形回帰モデルを作成する    
-   ロジスティック回帰モデルを作成する    
-   新しいデータにスコアを付け、スコアのヒストグラムを作成する  
  
## コンピューティング コンテキストをサーバーに変更する  
R コードを実行する前に、*現行*のコンピューティング コンテキストまたは*アクティブ*なコンピューティング コンテキストを指定する必要があります。  
  
1.  R を使用して既に定義したコンピューティング コンテキストをアクティブにするには、ここに示すように *rxSetComputeContext* 関数を利用します。  
  
    ```R  
    rxSetComputeContext(sqlCompute)   
    ```  
  
    このステートメントを実行すると、*sqlCompute* パラメーターに指定されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで直後に後続のすべての計算が行われます。  
  
  
2.  ワークステーションで R コードを実行する場合、  **local** キーワードを利用し、コンピューティング コンテキストをローカル コンピューターに再び切り替えることができます。  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
    この関数でサポートされているその他のキーワードの一覧が必要な場合、R コマンド ラインに「 `help("rxSetComputeContext")` 」と入力してください。  
  
> [!NOTE]  
> コンピューティング コンテキストを指定すると、変更するまでアクティブな状態が維持されます。 ただし、リモート サーバー コンテキストで実行 *できない* R スクリプトはローカルで実行されます。  
  
## 概要統計情報を計算する  
コンピューティング コンテキストの動作を確認するには、*sqlFraudDS* データ ソースを利用して概要統計情報を生成してみてください。  データ ソース オブジェクトは使用するデータを定義するだけのものであり、コンピューティング コンテキストは変更されないことに注意してください。

+ 概要をローカルで実行するには、*rxSetComputeContext* を使用し、"local" キーワードを指定します。
+ SQL Server コンピューターで同じ計算を行うには、先に定義した SQL コンピューティング コンテキストに切り替えます。  

  
1.  *rxSummary* 関数を呼び出し、式やデータ ソースなど、必須の引数を渡し、結果を変数 *sumOut* に代入します。  
  
    ```R  
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)  
  
    ```  
  
    R 言語はさまざまな概要関数を提供しますが、*rxSummary* は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を含む、さまざまなリモート コンピューティング コンテキストでの実行をサポートします。  同様の関数に関する詳細については、[ScaleR 参照](https://msdn.microsoft.com/microsoft-r/scaler/scaler)の「[Data Summaries](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries)」 (データの概要) を参照してください。
  
2.  処理が完了したら、*sumOut* 変数のコンテンツをコンソールに出力できます。  
  
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
 *creditLine       9.1856    9.870364 1      75 10000    0          100000 Category Counts for gender*    
 *Number of categories: 2*    
 *Number of valid observations: 10000*   
 *Number of missing observations: 0*    
 *gender Counts*    
 *Male   6154*    
  *Female 3846*  
  
## 最小値と最大値を追加する  
計算された概要統計情報に基づき、後続の計算で使用するためにデータ ソースに入力するデータに関する有益な情報がいくつか得られました。 たとえば、最小値と最大値を利用し、ヒストグラムを計算できます。*RxSqlServerData* データ ソースに上限と下限を追加します。  
  
幸いなことに、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] には、整数データを分類別の要因データに非常に効率的に変換できるように最適化された関数が含まれています。  
  
1.  まず、仮の変数をいくつか設定します。  
  
    ```R  
    sumDF <- sumOut$sDataFrame   
    var <- sumDF$Name    
    ```  
  
2.  先に作成した変数 *ccColInfo* を利用し、データ ソースに列を定義します。  
  
    また、列コレクションに新しく計算された列をいくつか追加します (*numTrans*、*numIntlTrans*、*creditLine*)。  
  
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
  
3.  列コレクションを更新しているので、次のステートメントを適用し、先に定義した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースの更新版を作成できます。  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        table = sqlFraudTable,   
        colInfo = ccColInfo,        
        rowsPerRead = sqlRowsPerRead)   
    ```  
  
    これで、*sqlFraudDS* データ ソースに、*ccColInfo* に追加された新しい列が含まれます。  
  
以上の変更は R のデータ ソース オブジェクトにのみ影響を与えます。新しいデータはデータベース テーブルにまだ書き込まれていません。 ただし、*sumOut* 変数でキャプチャされたデータを使用し、視覚化と概要を作成できます。 次の手順では、これを行い、同時にコンピューティング コンテキストを切り替える方法について説明します。 

> [!TIP]
> 使用しているコンピューティング コンテキストがわからなくなった場合は、`rxGetComputeContext()` を使用してください。  戻り値が `RxLocalSeq Compute Context` の場合、ローカルのコンピューティング コンテキストを使用しています。
  
## 次の手順  
[R を使用して SQL Server データを視覚化する (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/visualize-sql-server-data-using-r-data-science-deep-dive.md)  
  
## 前の手順  
[計算コンテキストの定義と使用 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/define-and-use-compute-contexts-data-science-deep-dive.md)  
  
  
  
