---
title: R を示すクイック スタートは、SQL Server データ (SQL Server Machine Learning) と機能 |Microsoft Docs
description: このクイック スタートでは、SQL Server のデータを使用する R 関数を記述する方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/08/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 877c7ffd5cb67479eed0e2239cbe90d366934515
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878165"
---
# <a name="quickstart-using-r-functions-with-sql-server-data"></a>クイック スタート: SQL Server データと R 関数の使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

前のクイック スタートを完了すると場合の基本的な操作についてよく理解し、統計関数などのより複雑なものの準備ができました。 T-SQL で実装が複雑である高度な統計関数は、1 行のコードを R で実行できます。

このクイック スタートでは、R の数学を埋め込み、ストアド プロシージャを SQL Server のユーティリティ関数。

## <a name="prerequisites"></a>前提条件

前のクイック スタート[の Hello World R と SQL を](rtsql-using-r-code-in-transact-sql-quickstart.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>乱数を生成するストアド プロシージャを作成する

わかりやすくするため、R を使用してみましょう`stats`パッケージがインストールされ、SQL Server に R 機能のサポートをインストールすると、既定で読み込まれます。 パッケージには、一般的な統計タスク用の数百の関数が含まれますが、その中の `rnorm` 関数は、指定された標準偏差と平均に対し、正規分布を使用して、指定された個数の乱数を生成します。

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

SQL Server と組み合わせたときに簡単です。 ユーザーから引数を取得するストアド プロシージャを定義します。 次に、R スクリプトにそれらの引数を変数として渡します。

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

など、R でのシステム タイミング関数を使用するなどの多くのユーザー`system.time`と`proc.time`R プロセスによって使用される時間をキャプチャすると、パフォーマンスの問題を分析します。

例については、[データ機能の作成](../tutorials/walkthrough-create-data-features.md)に関するチュートリアルをご覧ください。 このチュートリアルでは、R タイミング関数はデータから機能を作成するための 2 つのメソッドのパフォーマンスを比較するソリューションに埋め込まれて: R 関数とします。T-SQL 関数します。

## <a name="next-steps"></a>次の手順

次に、SQL Server で R を使用して予測モデルを作成します。

> [!div class="nextstepaction"]
> [クイック スタート: 予測モデルを作成します。](rtsql-create-a-predictive-model-r.md)
