---
title: 高度な Python 関数を記述する
titleSuffix: SQL Server Machine Learning Services
description: このクイックスタートでは、SQL Server Machine Learning Services を使用した高度な統計計算用の Python 関数を記述する方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e369e83c99543cc31287932a25949c2ddec98e89
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72007722"
---
# <a name="quickstart-write-advanced-python-functions-with-sql-server-machine-learning-services"></a>クイック スタート: SQL Server Machine Learning Services を使用した高度な Python 関数の作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、SQL Server Machine Learning Services を使用して SQL ストアドプロシージャに Python の数学関数とユーティリティ関数を埋め込む方法について説明します。 T-sql で実装するのが複雑な高度な統計関数は、1行のコードだけで Python で実行できます。

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、Python 言語がインストールされている[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)で SQL Server のインスタンスにアクセスする必要があります。

  SQL Server インスタンスは、Azure 仮想マシンまたはオンプレミスに配置できます。 外部スクリプト機能が既定で無効になっているため、[外部スクリプトを有効](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)にし、開始する前に**SQL Server Launchpad サービス**が実行されていることを確認する必要がある場合があることに注意してください。

- また、Python スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-sql クエリまたはストアドプロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリツールを使用して実行できます。 このクイックスタートでは、 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)を使用します。

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>乱数を生成するストアド プロシージャを作成する

わかりやすくするために、python `numpy` パッケージを使用します。これは、Python がインストールされている SQL Server Machine Learning Services に既定でインストールされ、読み込まれます。 パッケージには、一般的な統計タスク用の数百の関数が含まれますが、その中の `random.normal` 関数は、指定された標準偏差と平均に対し、正規分布を使用して、指定された個数の乱数を生成します。

たとえば、次の Python コードは、標準偏差が3の場合、50の平均値100を返します。

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

T-sql からこの Python の行を呼び出すには、`sp_execute_external_script` の Python script パラメーターに Python 関数を追加します。 出力にはデータフレームが必要であるため、`pandas` を使用して変換します。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=100, loc=50, scale=3));
'
    , @input_data_1 = N'   ;'
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

別の乱数のセットをもっと簡単に生成するにはどうすればよいでしょうか。

これは、SQL Server と組み合わせると簡単です。 ユーザーから引数を取得し、これらの引数を変数として Python スクリプトに渡すストアドプロシージャを定義します。

```sql
CREATE PROCEDURE MyPyNorm (
      @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=mynumbers, loc=mymean, scale=mysd));
'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- 最初の行では、ストアド プロシージャが実行されるときに必要な各 SQL 入力パラメーターを定義します。

- `@params` で始まる行は、Python コードによって使用されるすべての変数と、対応する SQL データ型を定義します。

- 直後に続く行は、SQL パラメーター名を対応する Python 変数名にマップします。

ストアドプロシージャで Python 関数をラップしたので、次のように、関数を呼び出して別の値を渡すことができます。

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>トラブルシューティングに Python ユーティリティ関数を使用する

Python パッケージには、現在の Python 環境を調査するためのさまざまなユーティリティ関数が用意されています。 これらの関数は、SQL Server と外部環境での Python コードの実行方法が矛盾している場合に役立ちます。

たとえば、`time` のパッケージでシステムタイミング関数を使用して、Python プロセスによって使用される時間を計測し、パフォーマンスの問題を分析することができます。

```sql
EXECUTE sp_execute_external_script
      @language = N'Python'
    , @script = N'
import time
start_time = time.time()

# Run Python processes

elapsed_time = time.time() - start_time
'
    , @input_data_1 = N' ;';
```

## <a name="next-steps"></a>次の手順

SQL Server で Python を使用して機械学習モデルを作成するには、次のクイックスタートに従ってください。

> [!div class="nextstepaction"]
> [クイック スタート:SQL Server Machine Learning Services を使用して Python で予測モデルを作成およびスコア付けする

SQL Server Machine Learning Services の詳細については、以下を参照してください。

- [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
