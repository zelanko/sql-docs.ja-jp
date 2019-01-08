---
title: Revoscalepy で Python を使用して、SQL Server Machine Learning - モデルを作成
description: Revoscalepy 関数を使用して、SQL Server でリモートで実行されているデータ サイエンス モデルを作成する Python スクリプトを記述します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 18c5b801198946313e4f489902eb5f7c9ff0d7af
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596833"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Revoscalepy で Python を使用して、SQL Server でリモートで実行されているモデルの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) Microsoft から Python ライブラリでは、データの探索、視覚化、変換、および分析用データ サイエンスのアルゴリズムが用意されています。 このライブラリでは、SQL Server での Python の統合シナリオで戦略的な重要性があります。 マルチコア サーバーで**revoscalepy**関数を並列で実行できます。 中央のサーバーおよびクライアント ワークステーションを使用した分散アーキテクチャでは (すべてが同じ物理コンピューターを分離**revoscalepy**ライブラリ)、ローカルで開始されますが、シフトを実行する Python コードを記述することができます、リモート SQL Server インスタンスは、データが存在します。

見つかります**revoscalepy**で、次の Microsoft 製品とのディストリビューション。

+ [SQL Server Machine Learning Services (in-database)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (非 SQL、スタンドアロン サーバー)](https://docs.microsoft.com/machine-learning-server/index)
+ [クライアント側の Python ライブラリ (の開発ワークステーション)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

この演習に基づく線形回帰モデルを作成する方法を示します[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)、内のアルゴリズムのいずれかの**revoscalepy**の入力として計算コンテキストを受け取る。 この演習で実行するコード ローカルからで有効になっているリモートのコンピューティング環境にコードが実行を移動する**revoscalepy**関数により、リモート計算コンテキスト。

このチュートリアルを完了すると、学習する方法。

> [!div class="checklist"]
> * 使用**revoscalepy**線形モデルを作成するには
> * 操作をローカルからリモート コンピューティング コンテキストへシフトします。

## <a name="prerequisites"></a>前提条件

この演習で使用するサンプル データは、 [ **flightdata** ](demo-data-airlinedemo-in-sql.md)データベース。

IDE では、サンプル コードを実行する必要があると、IDE は、Python の実行可能ファイルにリンクする必要があります。

コンピューティング コンテキストのシフトを実践する必要があります、[ローカル ワークステーション](../python/setup-python-client-tools-sql.md)と、SQL Server データベース エンジンのインスタンスで[Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)と Python を有効にします。 

> [!Tip]
> 2 台のコンピューターを持っていない場合は、関連するアプリケーションをインストールすることによって 1 つの物理コンピューターでリモート コンピューティング コンテキストをシミュレートできます。 最初のインストール[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) 「リモート」のインスタンスとして動作します。 2 番目のインストール、 [Python クライアント ライブラリが動作する](../python/setup-python-client-tools-sql.md)クライアントとして。 同じ Python ディストリビューションと同じコンピューター上の Microsoft Python ライブラリの 2 つのコピーがあります。 ファイルのパスと、演習を正常に完了に使用して、Python.exe のコピーを追跡する必要があります。

## <a name="remote-compute-contexts-and-revoscalepy"></a>リモート計算コンテキストと revoscalepy

このサンプルでは、クライアントから、操作しますが、SQL Server、Spark、または操作が実際に実行される、Machine Learning Server などのリモート環境を選択することができます、リモート コンピューティング コンテキストでの Python モデルを作成するプロセスを示します。 リモート計算コンテキストでは、データが存在する計算を表示します。

SQL Server での Python コードを実行する必要があります、 **revoscalepy**パッケージ。 これと同様に、Microsoft によって提供される特殊な Python パッケージ、 **RevoScaleR** R 言語用のパッケージ。 **Revoscalepy**パッケージは、計算コンテキストの作成をサポートし、ローカルのワークステーションとリモート サーバー間でデータとモデルを渡すためのインフラストラクチャを提供します。 **Revoscalepy**関数は、データベース内でコードが実行をサポートする[RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver)します。

このレッスンでデータを使用する SQL Server に基づく線形モデルをトレーニングする[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)、内の関数**revoscalepy**非常に大規模なデータセットに対する回帰をサポートします。 

このレッスンでは、設定して、使用する方法の基本についても示します、 **SQL Server 計算コンテキスト**Python でします。 方法の詳細については、計算コンテキストを他のプラットフォームでは、使用し、はサポートされている計算コンテキストを参照してください[Machine Learning Server でのスクリプト実行のコンピューティング コンテキスト](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)します。


## <a name="run-the-sample-code"></a>サンプル コードを実行します。

データベースを準備している、テーブルに格納されているトレーニング データは Python の開発環境を開き、サンプル コードを実行します。

コードでは、次の手順を実行します。

1. 必要なライブラリと関数をインポートします。
2. SQL Server への接続を作成します。 作成**データソース**データを操作するためのオブジェクト。
3. 使用してデータを変更します。**変換**ロジスティック回帰アルゴリズムで使用できるようにします。
4. 呼び出し`rx_lin_mod`をモデルに適合するために使用する数式を定義します。
5. 元のデータに基づく予測のセットを生成します。
6. 予測された値に基づいて概要を作成します。

すべての操作を実行するには、SQL Server のインスタンスをコンピューティング コンテキストとして使用します。

> [!NOTE]
> コマンドラインから実行されているこのサンプルのデモについては、このビデオを参照してください。[SQL Server 2017 高度な分析の Python の使用](https://www.youtube.com/watch?v=FcoY795jTcc)

### <a name="sample-code"></a>サンプル コード

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=sqlpy;Trusted_Connection=True;'
    print("connectionString={0!s}".format(sql_connection_string))

    data_source = RxSqlServerData(
        sql_query = "select top 10 * from airlinedemosmall",
        connection_string = sql_connection_string,

        column_info = {
            "ArrDelay" : { "type" : "integer" },
            "DayOfWeek" : {
                "type" : "factor",
                "levels" : [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ]
            }
        })

    sql_compute_context = RxInSqlServer(
        connection_string = sql_connection_string,
        num_tasks = 4,
        auto_cleanup = False
        )

    #
    # Run linmod locally
    #
    linmod_local = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source)
    #
    # Run linmod remotely
    #
    linmod = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)

    # Predict results
    # 
    predict = rx_predict(linmod, data = rx_import(input_data = data_source))
    summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)
```

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>コンピューティング コンテキストの定義とデータ ソースの定義

データ ソースは、計算コンテキストとは異なります。 *データソース*コードで使用するデータを定義します。 コンピューティング コンテキストでは、コードを実行する場所を定義します。 ただし、同じ情報の一部を使用します。

+ Python の変数など`sql_query`と`sql_connection_string`データのソースを定義します。 

    これらの変数を渡す、 [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata)コンス トラクターを実装する、**データ ソース オブジェクト**という`data_source`します。

+ 作成する、**計算コンテキスト オブジェクト**を使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver)コンス トラクター。 その結果、**計算コンテキスト オブジェクト**という`sql_cc`。

    この例では、計算コンテキストとして使用する同じ SQL Server インスタンスにデータがあるという前提で、データ ソースで同じ接続文字列を使用して、再使用します。 
    
    ただし、データ ソースと計算コンテキストは、別のサーバー上に可能性があります。
 
### <a name="changing-compute-contexts"></a>計算コンテキストを変更します。

設定する必要があります、コンピューティング コンテキストを定義した後、**アクティブなコンピューティング コンテキスト**します。 

既定では、ほとんどの操作です。 つまり、さまざまなコンピューティング コンテキストを指定しない場合、ローカルで実行され、データ ソースからデータをフェッチします。 コードは、現在の Python 環境で実行されます。

アクティブなコンピューティング コンテキストを設定する 2 つの方法はあります。
+ メソッドまたは関数の引数として
+ 呼び出して `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>メソッドまたは関数の引数としてコンピューティング コンテキストを設定します。

この例で、個々 の引数を使用して、コンピューティング コンテキストを設定する**rx**関数。
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

このコンピューティング コンテキストが呼び出しで再利用[rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Rx_set_compute_context を使用して明示的にコンピューティング コンテキストを設定します。

関数は、 [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context)計算既に定義されているコンテキストの間で切り替えることができます。

設定した後、アクティブなコンピューティング コンテキストを変更するまでアクティブのまま。

### <a name="using-parallel-processing-and-streaming"></a>並列処理とストリーミングを使用してください。

コンピューティング コンテキストを定義するときに設定することもパラメーター、コンピューティング コンテキストでデータを処理する方法を制御します。 これらのパラメーターは、データ ソースの種類によって異なります。

SQL Server 計算コンテキストでは、バッチ サイズを設定するか、タスクの実行で使用する並列処理の次数についてのヒントを提供します。

+ サンプルは、4 つのプロセッサを搭載したコンピューターで実行されたため、`num_tasks`パラメーターは、リソースの最大の使用を許可する 4 に設定されます。 
+ この値を 0 に設定する場合、SQL Server には、サーバーの現在の MAXDOP 設定で、できるだけ多くのタスクを並列で実行するには既定値が使用されます。 ただし、割り当てがタスクの正確な数は、サーバーの設定など、他の多くの要因とを実行している他のジョブに依存します。

## <a name="next-steps"></a>次の手順

これらの追加の Python のサンプルとチュートリアルは、リモート コンピューティング コンテキストの使用だけでなくより複雑なデータ ソース、使用するエンド ツー エンド シナリオを示します。

+ [SQL 開発者向けのデータベースでの Python](sqldev-in-database-python-for-sql-developers.md)
+ [Python と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
