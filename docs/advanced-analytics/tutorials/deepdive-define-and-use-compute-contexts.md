---
title: 定義し、計算コンテキスト (SQL と R deep dive) を使用して |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cb559b0acfc77ddb7e48cc0b3cacf76d421481ac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202344"
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>定義し、計算コンテキスト (SQL と R deep dive) を使用します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このレッスンでは、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数で、SQL Server のコンピューティング コンテキストを定義し、ローカル コンピューターではなく、サーバー上の複雑な計算を実行することができます。 

RevoScaleR は、Hadoop、Spark、またはデータベース内での R コードを実行できるように、複数のコンピューティング コンテキストをサポートしています。 SQL Server のサーバーを定義して、関数は、データベース、ローカル コンピューターとリモートの実行コンテキストの間の接続を渡してオブジェクトを作成するタスクを処理します。

SQL Server を作成する関数は、コンテキストは、次の情報を計算します。

- 接続文字列、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス
- 出力を処理する方法の指定
- トレースを有効にするか、トレース レベルを指定する省略可能な引数
- 共有データ ディレクトリの省略可能な指定

## <a name="create-and-set-a-compute-context"></a>作成し、コンピューティング コンテキストを設定

1. 計算を実行するインスタンスの接続文字列を指定します。  先ほど作成した接続文字列を再利用することができます。 別のサーバーに、計算を移動するかをいくつかのタスクを実行する別のログインを使用する場合は、別の接続文字列を作成できます。

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
  
    *RxInSqlServer* に渡す **wait** 引数は、次のオプションをサポートします。
  
    -   **TRUE**。 ジョブは、ブロッキングとして構成されて、これが完了するかが失敗したまで返されません。  詳細については、次を参照してください。[分散し、マシン学習サーバーで並列コンピューティング](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing)です。
  
    -   **FALSE**。 ジョブは、非ブロッキングとして構成されているし、他の R コードの実行を継続することができますが、すぐに戻る。 ただし、非ブロック モードであっても、ジョブの実行中は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とのクライアント接続を維持する必要があります。

3. 必要に応じて、リモートとローカルの R セッションで共有するローカル ディレクトリの場所を指定することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター、およびそのアカウント。

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. 共有の特定のディレクトリを手動で作成する場合は、次のような行を追加できます。

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    共有の現在使用されているフォルダーを特定するのには、実行`rxGetComputeContext()`、詳細については、現在の計算コンテキストが返されます。 詳細については、 [ScaleR のリファレンス](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/)を参照してください。

4. 引数としてを指定するすべての変数の場合は、準備ができていること、 **RxInSqlServer**コンス トラクターを作成する、*コンテキスト オブジェクトをコンピューティング*です。

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    構文**RxInSqlServer**場合とほぼ同様の検索、 **RxSqlServerData**以前に使用したデータ ソースを定義する関数。 しかし、次に示すいくつかの重要な相違点があります。
      
    - [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)関数を使用して定義するデータ ソース オブジェクトは、データの保存場所を指定します。
    
    - これに対し、コンピューティング コンテキストを関数を使用して定義されている[RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)を示します、集計およびその他の計算を実行します。
    
    計算コンテキストを定義しても、ワークステーションで実行されるその他の一般的な R 計算に影響なく、データのソースは変わりません。 たとえば、データ ソースとしてローカル テキスト ファイルを定義できますが、計算コンテキストを SQL Server に変更し、すべての読み取りと集計を SQL Server コンピューター上のデータに対して行うことができます。

## <a name="enable-tracing-on-the-compute-context"></a>コンピューティング コンテキストでトレースを有効にします。

リモート計算コンテキストで実行すると、ローカル コンテキストで動作する操作で問題が発生することがあります。 問題を分析したりパフォーマンスを監視したりする場合は、計算コンテキストでトレースを有効にして、実行時のトラブルシューティングをサポートできます。

1. 同じ接続文字列を使用する新しいコンピューティング コンテキストを作成するが、引数を追加*traceEnabled*と*traceLevel*を**RxInSqlServer**コンス トラクターです。

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

2. 計算コンテキストを変更するには、[rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) 関数を使用して、名前でコンテキストを指定します。

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > このチュートリアルでは、トレースを有効になっていないコンピューティング コンテキストを使用します。 
    > 
    > ただし、トレースを使用する場合は、注意してください、エクスペリエンスが、ネットワーク接続によって影響を 可能性があります。 注意するすべての操作のトレースが有効なオプションのパフォーマンスがテストされていないためです。

使用する方法を説明する次の手順で、サーバーに対して R コードを実行する、またはローカルでのコンテキストを計算します。

## <a name="next-step"></a>次の手順

[R スクリプトの作成と実行](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>前の手順

[SQL Server データに対するクエリおよび変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
