---
title: SQL Server データ (SQL のクイック スタートで R) で R 関数の使用 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 226712010118a54ac1c5350e128bf50cc261a128
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-r-functions-with-sql-server-data-r-in-sql-quickstart"></a>SQL Server データ (SQL のクイック スタートで R) で R 関数の使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

基本的な操作に慣れたら、次は R を楽しみましょう。たとえば、T-SQL を使用して多数の高度な統計関数を実装するのは複雑な場合がありますが、必要なのは 1 行の R コードのみです。  R Services では、ストアド プロシージャに R ユーティリティ スクリプトを簡単に埋め込むことができます。

これらの例では、SQL Server ストアド プロシージャに R の数学関数とユーティリティ関数を埋め込みます。

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>乱数を生成するストアド プロシージャを作成する

わかりやすくするため、R を使用してみましょう`stats`はインストールされ、R Services の既定で読み込まれたパッケージです。 パッケージには、一般的な統計タスク用の数百の関数が含まれますが、その中の `rnorm` 関数は、指定された標準偏差と平均に対し、正規分布を使用して、指定された個数の乱数を生成します。

たとえば、次の R コードは、指定された 3 の標準偏差で、平均 50 の 100 個の数値を返します。

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

この R の行を T-SQL から呼び出すには、次のように sp_execute_external_script を実行し、R スクリプト パラメーターで R 関数を追加します。

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

別の乱数のセットをもっと簡単に生成するにはどうすればよいでしょうか。

SQL Server と組み合わせた場合に簡単です。 ユーザーから引数を取得するストアド プロシージャを定義します。 次に、R スクリプトにそれらの引数を変数として渡します。

```sql
CREATE PROCEDURE MyRNorm (@param1 int, @param2 int, @param3 int)
AS
    EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
    WITH RESULT SETS (([Density] float NOT NULL));
```

+ 最初の行では、ストアド プロシージャが実行されるときに必要な各 SQL 入力パラメーターを定義します。

+ `@params` で始まる行は、R コードで使用されるすべての変数と、対応する SQL データ型を定義します。

+ それに続く行は、SQL パラメーター名を対応する R 変数名にマップします。

ストアド プロシージャで R 関数をラップしたので、次のように関数を簡単に呼び出し、別の値を渡すことができます。

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="related-resources"></a>関連リソース

+ その他の R パッケージをインストールするには、詳細を取得する高度な統計関数しますか。 参照してください[のインストールと R パッケージを管理する](../r/installing-and-managing-r-packages.md)です。

+ スタンドアロン R コードを簡単にパラメーター化できる SQL Server のストアド プロシージャを使用する形式に変換するために、Microsoft R チームが、新しい R パッケージを指定**sqlrutils**です。 詳細については、次を参照してください。 [sqlrutils を使用して、ストアド プロシージャを作成する方法](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)です。

## <a name="use-r-utility-functions-for-troubleshooting"></a>トラブルシューティングのための R ユーティリティ関数の使用

既定では、R のインストールが含まれます、`utils`パッケージで、現在の R 環境を調査するためのさまざまなユーティリティ関数を提供します。 これは、SQL Server と外部環境で R コードが実行する方法に不一致が見つかった場合に役立つ可能性があります。

たとえば、R `memory.limit()` 関数を使用して、現在の R 環境のメモリを取得できます。 `utils` パッケージはインストールされていますが既定で読み込まれていないため、最初に `library()` 関数を使用して読み込む必要があります。

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
        library(utils);
        mymemory <- memory.limit();
        OutputDataSet <- as.data.frame(mymemory);'
    , @input_data_1 = N' ;'
WITH RESULT SETS (([Col1] int not null));
```

など、R でシステム タイミング関数を使用するなどの多くのユーザー`system.time`と`proc.time`を R のプロセスによって使用された時間をキャプチャし、パフォーマンスの問題を分析します。

例については、[データ機能の作成](../tutorials/walkthrough-create-data-features.md)に関するチュートリアルをご覧ください。 このチュートリアルでタイミングの R 関数がデータから特徴を作成するための 2 つのメソッドのパフォーマンスを比較するソリューションに埋め込まれた: R 関数とします。T-SQL で機能します。

## <a name="next-lesson"></a>次のレッスン

次に、SQL Server で R を使用して予測モデルを作成します。

[予測モデルの作成](../tutorials/rtsql-create-a-predictive-model-r.md)
