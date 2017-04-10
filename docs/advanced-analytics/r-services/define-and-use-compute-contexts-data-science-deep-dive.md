---
title: "計算コンテキストの定義と使用 (データ サイエンスの詳細情報) | Microsoft Docs"
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
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# 計算コンテキストの定義と使用 (データ サイエンスの詳細情報)
複雑な計算の一部をローカル コンピューターではなくサーバー上で実行することに決めました。 その決断を実行するには、サーバー上で R コードを実行するための計算コンテキストを作成する必要があります。  
  
[RxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxinsqlserver) 関数は、[RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) パッケージに入っている拡張 R 関数の 1 つです。 この関数は、ローカル コンピューターとリモート実行コンテキストとの間にデータベース接続を作成してオブジェクトを渡すタスクを処理します。  
  
この手順では、*RxInSqlServer* 関数を使用して R コードで計算コンテキストを定義する方法について説明します。  


  
## 計算コンテキストを作成して設定する  
計算コンテキストを作成するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する次の基本的な情報が必要です。  
  
-   インスタンスの接続文字列  
-   出力の処理方法に関する仕様  
-   トレース有効化または共有ディレクトリ指定のための省略可能な引数


 それでは始めましょう。

1.  計算が行われるインスタンスの接続文字列を指定します。  これは、計算コンテキストを作成するときに *RxInSqlServer* 関数に渡す複数の変数のうちのほんの 1 つです。 

    **SQL ログインを使用する**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>" 
      ```

    **統合 Windows 認証を使用する**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"" 
      ```
2.  出力の処理方法を指定します。 次のコードでは、R ジョブの結果を常に待機するが、リモート計算からのコンソール出力は返さないように、ワークステーション上の R セッションの動作を指定します。  
  
    ```R  
    sqlWait <- TRUE   
    sqlConsoleOutput <- FALSE   
    ```  
  
    *RxInSqlServer* に渡す *wait* 引数は、次のオプションをサポートします。  
  
    -   **TRUE**。 ジョブは、完了するか失敗するまでブロックされ、その制御は戻りません。  ブロック ジョブと非ブロック ジョブの詳細については、次を参照してください。 
  
    -   **FALSE**。 ジョブのブロックが直ちに解除され制御が戻ります。これにより、ユーザーは引き続き他の R コードを実行できるようになります。 ただし、非ブロック モードであっても、ジョブの実行中は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とのクライアント接続を維持する必要があります。  

3. 必要に応じて、ローカルの R セッションと、リモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターおよびそのアカウントによる、共有使用のためのローカル ディレクトリの場所を指定できます。
    
    ```R  
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")   
    
    ## Add this line to create directory if it does not exist
    dir.create(sqlShareDir, recursive = TRUE) 
    ```  
    この引数には、フォルダーを明示的に指定するのではなく、既定値を使用することをお勧めします。 詳細については、[ScaleR のリファレンス](https://msdn.microsoft.com/microsoft-r/scaler/rxinsqlserver)を参照してください。
    
    使用されているフォルダーを確認するだけの場合は、`rxGetComputeContext` を実行して現在の計算コンテキストについての詳細を表示できます。 
  

4.  すべての変数の準備が整ったら、それらの変数を引数として `RxInSqlServer` コンストラクターに指定することで、計算コンテキスト オブジェクトを定義します。  
  
    ```R  
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,        
         #shareDir = sqlShareDir,       
         wait = sqlWait,   
         consoleOutput = sqlConsoleOutput)  
    ```  
  
    *RxInSqlServer* の構文は、前にデータ ソースの定義に使用した *RxSqlServerData* 関数とほとんど同じです。 しかし、次に示すいくつかの重要な相違点があります。  
  
    -   *RxSqlServerData* 関数を使用して定義するデータ ソース オブジェクトは、データの保存場所を指定します。  
  
    -   これに対し、計算コンテキスト (*RxInSqlServer* 関数を使用して定義される) は、集計やその他の計算が実行される場所を示します。  
  
    計算コンテキストを定義しても、ワークステーションで実行されるその他の一般的な R 計算に影響なく、データのソースは変わりません。 たとえば、データ ソースとしてローカル テキスト ファイルを定義できますが、計算コンテキストを SQL Server に変更し、すべての読み取りと集計を SQL Server コンピューター上のデータに対して行うことができます。 
  
## 計算コンテキストに対するトレースを有効にする  
特定のリモート計算コンテキストで実行すると、ローカル コンテキストで動作する操作で問題が発生することがあります。 問題を分析したりパフォーマンスを監視したりする場合は、計算コンテキストでトレースを有効にして、実行時のトラブルシューティングをサポートできます。  
  
1. 同じ接続文字列を使用する新しい計算コンテキストを作成しますが、引数 *traceEnabled* と *traceLevel* を *RxInSqlServer* コンストラクターに追加します。  
  
    ```R  
    sqlComputeTrace <- RxInSqlServer(   
        connectionString = sqlConnString,        
        #shareDir = sqlShareDir,  
        wait = sqlWait,   
        consoleOutput = sqlConsoleOutput,       
        traceEnabled = TRUE,
        traceLevel = 7)  
    ```  
  
    この例では、*traceLevel* プロパティを 7 に設定してあります。これは、"すべてのトレース情報を表示する" ことを意味します。  

2. この計算コンテキストに切り替えるには、*rxSetComputeContext* 関数を使用して、名前でコンテキストを指定します。

    ```R  
    rxSetComputeContext( sqlComputeTrace)
    ```

    このチュートリアルでは、トレースを有効にしていない計算コンテキストを使用します。 トレースを有効にしたときのパフォーマンスはすべての操作ではテストされておらず、ネットワーク接続によってエクスペリエンスが異なる場合があります。  
  
リモート計算コンテキストを作成したので、次に R コードをサーバーまたはローカルで実行するように計算コンテキストを変更する方法を学習します。  
  
## 次の手順  
[レッスン 2: R スクリプトの作成と実行 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## 前の手順  
[SQL Server データに対するクエリおよび変更 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/query-and-modify-the-sql-server-data-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
