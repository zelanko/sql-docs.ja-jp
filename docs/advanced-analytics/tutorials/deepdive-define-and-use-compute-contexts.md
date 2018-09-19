---
title: 定義し、計算コンテキスト (SQL と R の詳細情報) の使用 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a76e07cb2ecd03a59112f6c39e3fa2f7895e0a2
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975641"
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>定義し、計算コンテキスト (SQL と R の詳細情報) を使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、データ サイエンスの詳細情報を使用する方法のチュートリアルの一部[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

このレッスンで、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数で、SQL Server のコンピューティング コンテキストを定義し、ローカル コンピューターではなく、サーバーに複雑な計算を実行することができます。 

RevoScaleR は、Hadoop、Spark、またはデータベース内で R コードを実行できるように、複数のコンピューティング コンテキストをサポートしています。 For SQL Server をサーバーを定義して、関数は、データベースを作成するには、ローカル コンピューターとリモート実行コンテキストの間の接続を渡してオブジェクトのタスクを処理します。

SQL Server を作成する関数は、コンテキストは、次の情報を計算します。

- 接続文字列、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス
- 出力の処理方法の指定
- トレースを有効にするか、トレース レベルを指定する省略可能な引数
- 共有データ ディレクトリの省略可能な指定

## <a name="create-and-set-a-compute-context"></a>作成し、コンピューティング コンテキストの設定

1. 計算を実行するインスタンスの接続文字列を指定します。  先ほど作成した接続文字列を再利用することができます。 別のサーバーに、計算を移動したり、別のログインを使用して、いくつかのタスクを実行する場合は、別の接続文字列を作成できます。

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
  
    -   **TRUE**。 ジョブは、ブロッキングとして構成されているが失敗したかが完了するまでは返されません。  詳細については、次を参照してください。[分散し、Machine Learning Server での並列コンピューティング](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing)します。
  
    -   **FALSE**。 ジョブは、ブロック不可として構成されているし、その他の R コードの実行を継続することができますを即座に戻ります。 ただし、非ブロック モードであっても、ジョブの実行中は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とのクライアント接続を維持する必要があります。

3. 必要に応じて、ローカルの R セッションと、リモート共有使用のためのローカル ディレクトリの場所を指定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューターおよびそのアカウント。

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. 共有の特定のディレクトリを手動で作成する場合は、次のような行を追加できます。

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    共有の現在使用されているフォルダーを確認するのには、実行`rxGetComputeContext()`の詳細については、現在のコンピューティング コンテキストが返されます。 詳細については、 [ScaleR のリファレンス](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/)を参照してください。

4. 引数としてを提供するすべての変数を準備すること、 **RxInSqlServer**コンス トラクターを作成する、*計算コンテキスト オブジェクト*します。

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    構文は、 **RxInSqlServer**ほぼのと同じである、 **RxSqlServerData**データ ソースを定義する前に使用する関数。 しかし、次に示すいくつかの重要な相違点があります。
      
    - [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)関数を使用して定義するデータ ソース オブジェクトは、データの保存場所を指定します。
    
    - 関数を使用して、コンピューティング コンテキストを定義する一方、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)集計やその他の計算が実行される場所の場所を示します。
    
    計算コンテキストを定義しても、ワークステーションで実行されるその他の一般的な R 計算に影響なく、データのソースは変わりません。 たとえば、データ ソースとしてローカル テキスト ファイルを定義できますが、計算コンテキストを SQL Server に変更し、すべての読み取りと集計を SQL Server コンピューター上のデータに対して行うことができます。

## <a name="enable-tracing-on-the-compute-context"></a>コンピューティング コンテキストでトレースを有効にします。

リモート計算コンテキストで実行すると、ローカル コンテキストで動作する操作で問題が発生することがあります。 問題を分析またはパフォーマンスを監視する場合は、実行時のトラブルシューティングをサポートするために、計算コンテキストでトレースを有効にすることができます。

1. 同じ接続文字列を使用する新しい計算コンテキストの作成が、引数を追加*traceEnabled*と*traceLevel*を**RxInSqlServer**コンス トラクター。

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
    > このチュートリアルでは、トレースを有効にしていないコンピューティング コンテキストを使用します。 
    > 
    > ただし、トレースを使用する場合であるネットワーク接続によって、エクスペリエンスの影響を受ける可能性があることに注意してください。 注意するすべての操作のパフォーマンス トレースが有効なオプションがテストされていないためです。

使用する方法について説明します、次の手順で、サーバー上の R コードを実行するか、ローカル コンテキストを計算します。

## <a name="next-step"></a>次の手順

[R スクリプトの作成と実行](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>前の手順

[SQL Server データに対するクエリおよび変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
