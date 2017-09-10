---
title: "計算コンテキストの定義と使用 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: 
ms.date: 05/22/2017
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
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: 17
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 511738cfce795600bcfa06a95de4cdf3d6b503bb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="define-and-use-compute-contexts"></a>計算コンテキストの定義と使用


複雑な計算の一部をローカル コンピューターではなくサーバー上で実行するとします。 これを行うには、サーバー上で R コードを実行できる計算コンテキストを作成します。

**RxInSqlServer** 関数は、 [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) パッケージに入っている拡張 R 関数の 1 つです。 この関数は、ローカル コンピューターとリモート実行コンテキストとの間にデータベース接続を作成してオブジェクトを渡すタスクを処理します。

この手順では、 **RxInSqlServer** 関数を使用して R コードで計算コンテキストを定義する方法について説明します。

計算コンテキストを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する次の基本的な情報が必要です。

- インスタンスの接続文字列
- 出力の処理方法に関する仕様
- トレース有効化または共有ディレクトリ指定のための省略可能な引数

## <a name="create-and-set-a-compute-context"></a>計算コンテキストを作成して設定する

1. 計算が行われるインスタンスの接続文字列を指定します。  これは、計算コンテキストを作成するときに *RxInSqlServer* 関数に渡す複数の変数のうちのほんの 1 つです。 先に作成した接続文字列を再利用できます。また、別のサーバーに計算を移動したり、別の ID を使用する場合は、別の接続文字列を作成することもできます。

    **SQL ログインを使用する**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>"
      ```

    **Windows 認証を使用する**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
      ```
2. 出力の処理方法を指定します。 次のコードでは、R ジョブの結果を常に待機するが、リモート計算からのコンソール出力は返さないように、ワークステーション上の R セッションの動作を指定します。
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    *RxInSqlServer* に渡す *wait* 引数は、次のオプションをサポートします。
  
    -   **TRUE**。 ジョブは、完了するか失敗するまでブロックされ、その制御は戻りません。  詳細については、次を参照してください。[分散し、Microsoft R での並列コンピューティング](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing)です。
  
    -   **FALSE**。 ジョブのブロックが直ちに解除され制御が戻ります。これにより、ユーザーは引き続き他の R コードを実行できるようになります。 ただし、非ブロック モードであっても、ジョブの実行中は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とのクライアント接続を維持する必要があります。

3. 必要に応じて、ローカルの R セッションと、リモートの  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターおよびそのアカウントによる、共有使用のためのローカル ディレクトリの場所を指定できます。

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. 共有の特定のディレクトリを手動で作成する場合は、次のような行を追加できます。 共有の現在使用されているフォルダーを特定するのには、実行`rxGetComputeContext`、詳細については、現在の計算コンテキストが返されます。 詳細については、 [ScaleR のリファレンス](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinsqlserver)を参照してください。

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. 作成する RxInSqlServer コンス トラクターに引数としてを指定するすべての変数の場合は、準備ができていること、*コンテキスト オブジェクトをコンピューティング*です。

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    RxInSqlServer * の構文はデータ ソースの定義を使用した RxSqlServerData 関数のものとほぼ同じことを確認する可能性があります。 しかし、次に示すいくつかの重要な相違点があります。
      
    - RxSqlServerData、関数を使用して定義されているデータ ソース オブジェクトは、データの格納場所を指定します。
    
    - これに対し、(RxInSqlServer 関数を使用して定義されている) のコンピューティング コンテキストを示します、集計およびその他の計算を行います。
    
    計算コンテキストを定義しても、ワークステーションで実行されるその他の一般的な R 計算に影響なく、データのソースは変わりません。 たとえば、データ ソースとしてローカル テキスト ファイルを定義できますが、計算コンテキストを SQL Server に変更し、すべての読み取りと集計を SQL Server コンピューター上のデータに対して行うことができます。

## <a name="enable-tracing-on-the-compute-context"></a>計算コンテキストに対するトレースを有効にする

リモート計算コンテキストで実行すると、ローカル コンテキストで動作する操作で問題が発生することがあります。 問題を分析したりパフォーマンスを監視したりする場合は、計算コンテキストでトレースを有効にして、実行時のトラブルシューティングをサポートできます。

1. 同じ接続文字列を使用する新しいコンピューティング コンテキストを作成するが、引数を追加*traceEnabled*と*traceLevel*を*RxInSqlServer*コンス トラクターです。

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

2. コンピューティング コンテキストを変更するには、rxSetComputeContext 関数を使用し、名前でコンテキストを指定します。

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > このチュートリアルでは、トレースを有効にしていない計算コンテキストを使用します。 すべての操作のトレースが有効なオプションのパフォーマンスがテストされていないためにです。
    > 
    > ただし、トレースを使用する場合は、注意してください、エクスペリエンスが、ネットワーク接続によって影響を 可能性があります。

リモート計算コンテキストを作成したので、次に R コードをサーバーまたはローカルで実行するように計算コンテキストを変更する方法を学習します。

## <a name="next-step"></a>次の手順

[作成し、R スクリプトを実行します。](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)


## <a name="previous-step"></a>前の手順

[クエリおよび SQL Server データの変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)



