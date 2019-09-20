---
title: 高度な R 関数の作成
titleSuffix: SQL Server Machine Learning Services
description: このクイックスタートでは、SQL Server Machine Learning Services を使用した高度な統計計算用の R 関数を記述する方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cebd4ea6a356af6802a0e26f778667b2acc4b80c
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71149906"
---
# <a name="quickstart-write-advanced-r-functions-with-sql-server-machine-learning-services"></a>クイック スタート: SQL Server Machine Learning Services を使用した高度な R 関数の作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、SQL Server Machine Learning Services を使用して SQL ストアドプロシージャに R の数学関数とユーティリティ関数を埋め込む方法について説明します。 T-sql で実装するのが複雑な高度な統計関数は、1行のコードだけを使用して R で実行できます。

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、R 言語がインストールされている[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)で SQL Server のインスタンスにアクセスする必要があります。

  SQL Server インスタンスは、Azure 仮想マシンまたはオンプレミスに配置できます。 外部スクリプト機能が既定で無効になっているため、[外部スクリプトを有効](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)にし、開始する前に**SQL Server Launchpad サービス**が実行されていることを確認する必要がある場合があることに注意してください。

- また、R スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-sql クエリまたはストアドプロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリツールを使用して実行できます。 このクイックスタートでは、 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)を使用します。

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>乱数を生成するストアド プロシージャを作成する

わかりやすくするために、r `stats`パッケージを使用して、既定でインストールされていて、r がインストールされた SQL Server Machine Learning Services に読み込まれています。 パッケージには、一般的な統計タスク用の数百の関数が含まれますが、その中の `rnorm` 関数は、指定された標準偏差と平均に対し、正規分布を使用して、指定された個数の乱数を生成します。

たとえば、次の R コードでは、標準偏差が3の場合、50の平均で100の数値が返されます。

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

T-sql からこの r の行を呼び出すには、次のように、の`sp_execute_external_script`r スクリプトパラメーターに r 関数を追加します。

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

別の乱数のセットをもっと簡単に生成するにはどうすればよいでしょうか。

これは、SQL Server と組み合わせると簡単です。 ユーザーから引数を取得し、これらの引数を変数として R スクリプトに渡すストアドプロシージャを定義します。

```sql
CREATE PROCEDURE MyRNorm (
    @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXEC sp_execute_external_script @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- 最初の行では、ストアド プロシージャが実行されるときに必要な各 SQL 入力パラメーターを定義します。

- `@params` で始まる行は、R コードで使用されるすべての変数と、対応する SQL データ型を定義します。

- それに続く行は、SQL パラメーター名を対応する R 変数名にマップします。

ストアド プロシージャで R 関数をラップしたので、次のように関数を簡単に呼び出し、別の値を渡すことができます。

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>トラブルシューティングのための R ユーティリティ関数の使用

既定でインストールされるユーティリティパッケージには、現在の R 環境を調査するためのさまざまなユーティリティ関数が用意**されて**います。 これらの関数は、SQL Server と外部環境での R コードの実行方法が矛盾している場合に役立ちます。

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

> [!TIP]
> `system.time` や`proc.time`などのシステムタイミング関数を使用して、r プロセスによって使用される時間をキャプチャし、パフォーマンスの問題を分析する多くのユーザー。

例については、次のチュートリアルを参照してください。[データ機能を作成](../tutorials/walkthrough-create-data-features.md)します。 このチュートリアルでは、r のタイミング関数をソリューションに埋め込んで、R 関数とのパフォーマンスを比較します。データから機能を作成するための t-sql 関数。

## <a name="next-steps"></a>次の手順

SQL Server Machine Learning Services の詳細については、以下を参照してください。

- [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
