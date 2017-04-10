---
title: "SQL Server と XDF ファイル間のデータの移動 (データ サイエンスの詳細) | Microsoft Docs"
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
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# SQL Server と XDF ファイル間のデータの移動 (データ サイエンスの詳細)
ローカル コンピューティング コンテキストで作業している場合、ローカル データ ファイルと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (*RxSqlServerData* データ ソースとして定義されている) の両方にアクセスできます。  
  
ここでは、データの変換を実行できるように、データを取得し、ローカル コンピューター上のファイルにそれを保存する方法を学習します。 完了したら、*rxDataStep* を使用して、ファイル内のデータで新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを作成します。  
  
## XDF ファイルから SQL Server テーブルを作成する  

*rxImport* 関数を使用して、サポートされているデータ ソースからローカル XDF ファイルにデータをインポートできます。 ローカル ファイルを使用することは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納されているデータに対して多くのさまざまな分析を実行し、同じクエリを何度も実行したくない場合に便利なことがあります。  
  
この練習では、クレジット カードの不正使用データを再度使用します。 このシナリオでは、カリフォルニア、オレゴン、ワシントンの各州のユーザーに対して追加の分析を実行するように求められています。 効率向上のため、これらの州のデータだけをローカル コンピューターに格納し、性別、カード会員、州、および残高の変数を操作します。  
  
1.  以前に作成した *stateAbb* ベクトルを再利用して、含めるレベルを特定し、新しい変数 *statesToKeep* をコンソールに出力します。  
  
    ```  
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)   
  
    statesToKeep  
  
    ```  
 **[結果]**
CA |  または  | WA 
-- | -- | --
 5 |  38  | 48 
  
2.  次に、[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用し、SQL Server から引き渡すデータを定義します。  後で、この変数は *rxImport* の *inData* 引数として使用します。  
  
    ```R  
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")  
  
    ```  
  
    クエリにライン フィードやタブなどの隠し文字がないことを確認します。  
  
3.  次に、R でデータを操作するときに使用する列を定義します  
  たとえば、データ セットが小さいとき、クエリは 3 つの州のデータのみを返すため、3 つの因子水準のみを必要とします。  *statesToKeep* 変数を再利用して、含める正しい水準を特定できます。  
  
    ```R  
    importColInfo <- list(   
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),       
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),     
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))   
            )  
  
    ```  
  
4.  ローカル コンピューターですべてのデータが使用できる必要があるため、コンピューティング コンテキストを**ローカル**に設定します。  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
5.  *RxSqlServerData* の引数として定義したすべての変数を渡し、データ ソース オブジェクトを作成します。  
  
    ```R  
    sqlServerImportDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        sqlQuery = importQuery,   
        colInfo = importColInfo)  
  
    ```  
  
6.  次に、*rxImport* を呼び出して、現在の作業ディレクトリの `ccFraudSub.xdf` というファイルにデータを保存します。  
  
    ```R  
    localDS <- rxImport(inData = sqlServerImportDS,   
        outFile = "ccFraudSub.xdf",    
        overwrite = TRUE)  
  
    ```  
  
    *rxImport* 関数から返される *localDs* オブジェクトは、ディスクにローカルに保存された ccFraud.xdf データ ファイルを表す軽量の *RxXdfData* データ ソース オブジェクトです。  
  
7.  XDF ファイルで *rxGetVarInfo* を呼び出し、データ スキーマが同じであることを確認します。  
  
    ```R  
    rxGetVarInfo(data = localDS)   
    ```  
    **[結果]**
    
    *rxGetVarInfo(data = localDS)*    
    *Var 1: gender, Type: factor, no factor levels available*    
    *Var 2: cardholder, Type: factor, no factor levels available*    
    *Var 3: balance, Type: integer, Low/High: (0, 22463)*    
    *Var 4: state, Type: factor, no factor levels available*
  
8.  これでさまざまな R 関数を呼び出して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上のソース データの場合と同じように、*localDs* オブジェクトを分析できます。 例:  
  
    ```R  
    rxSummary(~gender + cardholder + balance + state, data = localDS)    
    ```  
  
コンピューティング コンテキストの使用と各種データ ソースの操作を習得したので、何かおもしろいことを試してみましょう。  
  
次の最後のレッスンでは、カスタム R 関数を使用して、それをリモート サーバーで実行し、簡単なシミュレーションを作成します。  
  
## 次の手順  
[レッスン 5: 簡単なシミュレーションの作成 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  
  
## 前の手順  
[レッスン 4: ローカル計算コンテキストでのデータの分析 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
