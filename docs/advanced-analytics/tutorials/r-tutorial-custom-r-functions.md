---
title: RevoScaleR rxExec - SQL Server Machine Learning を使用して SQL Server でカスタム R 関数を実行します。
description: RevoScaleR 関数を使用して SQL Server でカスタム R スクリプトを実行する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5773641f442fe844657e6aabd6b9dcea24f4475b
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509909"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec"></a>RxExec を使用して SQL Server でカスタム R 関数を実行します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server のコンテキストでカスタム R 関数を実行するには、関数を使用して渡すことによって[rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec)ライブラリ、スクリプトが必要ですが、サーバーにインストールされても、これらのライブラリは、ベースと互換性があることを前提と配布は r です。 

**RxExec**関数**RevoScaleR**が必要な任意の R スクリプトを実行するためのメカニズムを提供します。 さらに、 **rxExec**スケールをそれ以外の場合、ネイティブの R エンジンのリソースの制約に制限されるスクリプトに追加する 1 台のサーバーで複数のコア間で作業を明示的に配布することができます。

このチュートリアルでは、リモート サーバーで実行されるカスタム R 関数の実行を示すためにシミュレートされたデータを使用します。

## <a name="prerequisites"></a>前提条件

+ [SQL Server 2017 の Machine Learning サービス (R) を使用した](../install/sql-machine-learning-services-windows-install.md)または[SQL Server 2016 R Services (In-database)](../install/sql-r-services-windows-install.md)
  
+ [データベース権限](../security/user-permission.md)と SQL Server データベースのユーザー ログイン

+ [RevoScaleR ライブラリを使用して開発ワークステーション](../r/set-up-a-data-science-client.md)

クライアント ワークステーションで R のディストリビューションは、組み込み**Rgui**このチュートリアルでは R スクリプトの実行に使用できるツールです。 For Visual Studio、RStudio や R ツールなど、IDE を使用することもできます。

## <a name="create-the-remote-compute-context"></a>リモート計算コンテキストを作成します。

クライアント ワークステーションで次の R コマンドを実行します。 たとえば、使用している**Rgui**、この場所から起動します。C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64\.

1. 計算を実行する SQL Server インスタンスの接続文字列を指定します。 サーバーは、R 統合を構成する必要があります。 データベース名は、この演習では使用されませんが、接続文字列では、1 つが必要です。 テストやサンプル データベースがある場合は、を使用できます。

    **SQL ログインを使用する**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>; Database=<database-name>;Uid=<SQL-user-name>;Pwd=<password>"
    ```

    **Windows 認証を使用する**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>;Database=<database-name>;Trusted_Connection=True"
    ```

2. 接続文字列で参照されている SQL Server インスタンスにリモート コンピューティング コンテキストを作成します。

    ```R
    sqlCompute <- RxInSqlServer(connectionString = sqlConnString)
    ```

3. コンピューティング コンテキストをアクティブ化し、確認の手順として、オブジェクト定義を返します。 計算コンテキスト オブジェクトのプロパティを表示する必要があります。

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>カスタム関数を作成します。

この演習では、組のサイコロのロールで構成される一般的なカジノをシミュレートするカスタム R 関数を作成します。 ゲームのルールは、win または損失の結果を確認します。

+ 7 か 11 を最初に転がしたでロールアウト、あなたの勝ちです。
+ 2 をロールバック、紛失した 3 つ、または 12 です。
+ 4 のロール、その番号になります、ポイントでは、5、6、8、9、または 10、およびするまでロールが失われる (この場合あなたの勝ち) もう一度ポイントまたはロールの場合は、これで、7 かロールバックします。

このゲームは R で簡単にシミュレートできます。カスタム関数を作成し、それを何度も実行します。

1.  次の R コードを使用して、カスタム関数を作成します。
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result <- "Loss" }
                else if (count > 1 && roll == 7 )
                { result <- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  関数を実行して、1 つのサイコロ ゲームをシミュレートします。
  
    ```R
    rollDice()
    ```
  
    あなたの勝ちでしたか。それとも負けでしたか。
  
これで、運用上のスクリプトがある場合を見てみましょうを使用する方法**rxExec**勝率の決定に役立つシミュレーションの作成を複数回を関数を実行します。

## <a name="pass-rolldice-in-rxexec"></a>RxExec rollDice() を渡す

リモート SQL Server のコンテキストで任意の関数を実行するには、呼び出し、 **rxExec**関数。

1. 引数としてカスタム関数を呼び出す**rxExec**をシミュレーションを変更するその他のパラメーターを使用します。
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + *timesToRun* 引数を使用すれば、関数を実行する回数を指示できます。  この場合、20 回サイコロを振ります。
  
    + *RNGseed* 引数と *RNGkind* 引数を利用し、乱数の生成を制御できます。 *RNGseed* が **auto**に設定されると、各ワーカーで並行乱数ストリームが初期化されます。
  
2. **rxExec** 関数は実行のたびに 1 つの要素で一覧を作成します。ただし、一覧が完了するまで内容はわかりません。 ときにすべての反復処理が完了するで始まる行**長さ**が値を返します。
  
    次の手順に進むと、勝敗記録のまとめを取得できます。
  
3. R の **unlist** 関数を使用して、返された一覧をベクトルに変換し、 **table** 関数を使用して結果をまとめます。
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    結果は次のようになります。
  
     *負け勝ち* *12 8*

## <a name="conclusion"></a>まとめ

この演習は、単純化され、SQL Server で実行されている R スクリプト内の任意の R 関数を統合するための重要なメカニズムを示しています。 この手法を可能にする重要な点をまとめています。

+ SQL Server は、machine learning と R 統合用に構成する必要があります。[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) R 機能を使用または[SQL Server 2016 R Services (In-database)](../install/sql-r-services-windows-install.md)します。

+ 関数で、すべての依存関係を含む使用されるオープン ソースまたはサードパーティ製のライブラリは、SQL Server にインストールする必要があります。 詳細については、[新しい R パッケージをインストール](../r/install-additional-r-packages-on-sql-server.md)を参照してください。

+ スクリプトを開発環境から運用環境のセキュリティを強化した環境に移行と、ファイアウォールとネットワークの制限が生じる場合があります。 スクリプトが期待どおりに実行できるかどうかを確認するには、慎重にテストします。

## <a name="next-steps"></a>次のステップ

使用するより複雑な例については**rxExec**、この記事を参照してください。[Foreach と rxExec 粒度が粗い並列処理](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)
