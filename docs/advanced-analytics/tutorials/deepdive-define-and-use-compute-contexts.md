---
title: 定義し、RevoScaleR コンピューティング コンテキストで SQL Server Machine Learning の使用
description: SQL Server で R 言語を使用して計算コンテキストを定義する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: f020fffd28223fe37699c38f55bedb2f9e5e65d8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511020"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>定義し、計算コンテキスト (SQL Server と RevoScaleR チュートリアル) を使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

前のレッスンでは使用して**RevoScaleR**データ オブジェクトを検査する関数。 このレッスンで、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数で、リモートの SQL Server のコンピューティング コンテキストを定義することができます。 リモート計算コンテキストを持つサーバーでリモート セッションにローカルのセッションから R の実行を移すことができます。 

> [!div class="checklist"]
> * コンピューティング コンテキストをリモート SQL サーバーの構成要素について説明します。
> * 計算コンテキストのオブジェクトのトレースを有効にします。

**RevoScaleR**複数のコンピューティング コンテキストをサポートします。Hadoop、Spark、HDFS と SQL Server データベース内。 SQL サーバーの場合、 **RxInSqlServer**関数は、サーバーの接続と、ローカル コンピューターとリモート実行コンテキストの間のオブジェクトの引き渡しに使用します。

## <a name="create-and-set-a-compute-context"></a>作成し、コンピューティング コンテキストの設定

**RxInSqlServer** SQL Server 計算コンテキストを作成する関数は、次の情報を使用します。

+ 接続文字列、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス
+ 出力の処理方法の指定
+ 共有データ ディレクトリの省略可能な指定
+ トレースを有効にするか、トレース レベルを指定する省略可能な引数

このセクションでは、各部分について説明します。

1. 計算を実行するインスタンスの接続文字列を指定します。 先ほど作成した接続文字列を再利用することができます。

    **SQL ログインを使用する**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Windows 認証を使用する**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. 出力の処理方法を指定します。 次のスクリプトでは、次の操作を処理する前に、サーバー上で R ジョブの結果を待機するローカルの R セッションを指示します。 また、ローカル セッションに表示されないリモート計算からの出力を抑制します。
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    *RxInSqlServer* に渡す **wait** 引数は、次のオプションをサポートします。
  
    -   **TRUE**。 ジョブは、ブロッキングとして構成されているが失敗したかが完了するまでは返されません。  詳細については、[分散し、Machine Learning Server での並列コンピューティング](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing)を参照してください。
  
    -   **FALSE**。 ジョブは、ブロック不可として構成されているし、その他の R コードの実行を継続することができますを即座に戻ります。 ただし、非ブロック モードであっても、ジョブの実行中は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とのクライアント接続を維持する必要があります。

3. 必要に応じて、ローカルの R セッションと、リモート共有使用のためのローカル ディレクトリの場所を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューターおよびそのアカウント。

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   共有の特定のディレクトリを手動で作成する場合は、次のような行を追加できます。

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. 引数を渡す、 **RxInSqlServer**を作成するコンストラクター、*計算コンテキスト オブジェクト*します。

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

5. リモート計算コンテキストを有効にします。

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. そのプロパティを含む、コンピューティング コンテキストに関する情報を返します。

    ```R
    rxGetComputeContext()
    ```

7. (次のレッスンは、リモート コンピューティング コンテキストを使用する方法を示します)、"local"キーワードを指定することで、ローカル コンピューターに計算コンテキストをリセットします。

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> この関数でサポートされているその他のキーワードの一覧が必要な場合、R コマンド ラインに「 `help("rxSetComputeContext")` 」と入力してください。

## <a name="enable-tracing"></a>トレースを有効にします。

リモート計算コンテキストで実行すると、ローカル コンテキストで動作する操作で問題が発生することがあります。 問題を分析またはパフォーマンスを監視する場合は、実行時のトラブルシューティングをサポートするために、計算コンテキストでトレースを有効にすることができます。

1. 同じ接続文字列を使用する新しい計算コンテキストの作成が、引数を追加*traceEnabled*と*traceLevel*を**RxInSqlServer**コンストラクター。

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

2. 使用して、 [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext)関数を名前でトレースが有効なコンピューティング コンテキストを指定します。

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>次のステップ

サーバー上の R コードを実行するか、ローカル コンピューティング コンテキストを切り替える方法について説明します。

> [!div class="nextstepaction"]
> [コンピューティングの概要統計情報では、ローカルとリモート計算コンテキスト](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)