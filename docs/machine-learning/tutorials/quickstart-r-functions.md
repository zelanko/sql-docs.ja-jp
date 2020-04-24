---
title: クイック スタート:R 関数
description: このクイックスタートでは、SQL Server Machine Learning Services で R の数学関数とユーティリティ関数を使用する方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fd3c3326fe0b186ade24cbcf95f587abba1cb6bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487286"
---
# <a name="quickstart-r-functions-with-sql-server-machine-learning-services"></a>クイック スタート:SQL Server Machine Learning Services での R 関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、SQL Server Machine Learning Services で R の数学関数とユーティリティ関数を使用する方法について説明します。 多くの場合、統計関数は T-SQL での実装が複雑ですが、R では、わずか数行のコードで行うことができます。

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、R 言語がインストールされた [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) をもつ SQL Server のインスタンスへのアクセスが必要となります。

  あなたの SQL Server インスタンスは、Azure 仮想マシンまたはオンプレミスに配置できます。 外部スクリプト機能が既定で無効になっていることに注意してください。そのため、開始する前に、[外部スクリプトを有効にし](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)、**SQL Server Launchpad サービス**が実行されていることを確認する必要があります。

- また、R スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-SQL クエリまたはストアド プロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリ ツールを使用して実行できます。 このクイック スタートでは、[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) を使用します。

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>乱数を生成するストアド プロシージャを作成する

わかりやすくするために、R `stats` パッケージを使用します。このパッケージは、R がインストールされた SQL Server Machine Learning Services が既定でインストールおよびロードされていてます。 パッケージには、一般的な統計タスク用の数百の関数が含まれますが、その中の `rnorm` 関数は、指定された標準偏差と平均に対し、正規分布を使用して、指定された個数の乱数を生成します。

たとえば、次の R コードは、指定された 3 の標準偏差で、平均値が 50 の 100 個の数値を返します。

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

この R の行を T-SQL から呼び出すには、次のように、`sp_execute_external_script` の R スクリプト パラメーターに R 関数を追加します。

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

さまざまな乱数のセットを簡単に生成するにはどうすればよいでしょうか。

これは、SQL Server と組み合わせると簡単です。 ユーザーから引数を取得し、これらの引数を変数として R スクリプトに渡すストアド プロシージャを定義します。

```sql
CREATE PROCEDURE MyRNorm (
    @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- 最初の行は、ストアド プロシージャを実行するときに必要になる SQL 入力パラメーターそれぞれを定義します。

- `@params` で始まる行は、R コードで使用されるすべての変数と対応する SQL データ型を定義します。

- すぐ後に続く行では、SQL パラメーター名と対応する R 変数名をマップします。

これでストアド プロシージャに R 関数がラップされたため、次のように関数を簡単に呼び出してさまざまな値を渡すことができます。

```sql
EXECUTE MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>トラブルシューティングのために R ユーティリティ関数を使用する

既定では、**utils** パッケージが含まれます。このパッケージは、現在の R 環境を調査するためのさまざまなユーティリティ関数を提供します。 これらの関数は、SQL Server と外部環境で R コードが実行する方法に不一致が見つかった場合に役立つ可能性があります。

たとえば、R `memory.limit()` 関数を使用すると、現在の R 環境のメモリを取得できます。 `utils` パッケージはインストールされますが、既定では読み込まれないため、最初に `library()` 関数を使用して読み込む必要があります。

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

> [!TIP]
> R プロセスによって使用される時間をキャプチャし、パフォーマンスの問題を分析するのに、多くのユーザーが `system.time` や `proc.time` など、R のシステム タイミング関数を使用しています。 例については、「[データ機能の作成](../tutorials/walkthrough-create-data-features.md)」チュートリアルを参照してください。R タイミング関数がソリューションに埋め込まれています。

## <a name="next-steps"></a>次のステップ

SQL Server で R を使用して機械学習モデルを作成するには、次のクイック スタートに従ってください。

> [!div class="nextstepaction"]
> [SQL Server Machine Learning Services を使用して R で予測モデルを作成してスコア付けする](quickstart-r-train-score-model.md)

SQL Server Machine Learning Services の詳細については、次を参照してください。

- [SQL Server Machine Learning Services (Python と R) とは](../sql-server-machine-learning-services.md)
