---
title: Revoscalepy で Python を使用してモデルを作成する |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d549b06b9fe371dc2b1966c62776ec4e88c45726
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740831"
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Revoscalepy で Python を使用してモデルを作成するには
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンでは、SQL Server で、線形回帰モデルを作成する、リモート開発クライアントから Python コードを実行する方法を学習します。 

## <a name="prerequisites"></a>前提条件

+ このレッスンでは、前のレッスンとは異なるデータを使用します。 最初に前のレッスンを完了する必要はありません。 ただし、前のレッスンを完了し、Python を実行するよう既に構成サーバーが存在する場合は、そのサーバーとデータベースとして使用コンピューティング コンテキスト。
+ 計算として SQL Server を使用する Python コードを実行するには、コンテキストには、SQL Server 2017 以降が必要です。 さらに、明示的にインストールし、機能を有効にする必要があります**Machine Learning サービス**、Python 言語オプションを選択します。

    SQL Server 2017 のプレリリース版をインストールした場合に更新するには、少なくとも RTM バージョン。 以降のサービス リリースを展開し、Python の機能を向上させるきました。 このチュートリアルの一部の機能は、以前のプレリリース バージョン動かないことがあります。

+ この例は、定義済みの Python 環境という名前を使用して`PYTEST_SQL_SERVER`です。 格納する環境が構成されて**revoscalepy**と他の必要なライブラリです。 

    場合は、環境を Python を実行するように構成することはありません、行う必要がありますとは別にします。 Python 環境を変更または作成する方法の詳細については、このチュートリアルの対象外です。 正しいライブラリが含まれている Python クライアントを設定する方法の詳細については、次を参照してください。 [Python のインストール クライアント](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)と[ツールへのリンクの Python](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)です。

## <a name="remote-compute-contexts-and-revoscalepy"></a>リモート計算コンテキストと revoscalepy

このサンプルでは、リモートで Python モデルの作成のプロセス_計算コンテキスト_をクライアントから作業は、SQL Server、Spark、Machine Learning サーバーなどのリモート環境を選択することができますを操作が実際に実行されます。 計算コンテキストを使用すると、1 回のコードの記述をすべてサポートされている環境に配置してやすくなります。

SQL Server での Python コードを実行する必要があります、 **revoscalepy**パッケージです。 これと同様に、Microsoft によって提供される特殊な Python パッケージ、 **RevoScaleR** R 言語用のパッケージです。 **Revoscalepy**パッケージ計算コンテキストの作成をサポートし、ローカルのワークステーションとリモート サーバーの間でデータとモデルを渡すためのインフラストラクチャを提供します。 **Revoscalepy**関数は、データベース内でコードが実行をサポートする[RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver)です。

このレッスンではデータを使用する SQL Server に基づく線形モデルをトレーニングする[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)、内の関数**revoscalepy**ほど大きなデータセットでも回帰をサポートします。 

このレッスンを設定して、使用する方法の基本についても示します、 **SQL Server の計算コンテキスト**Python でします。 方法についての計算コンテキストを他のプラットフォームでは、使用はサポートされている計算コンテキストを参照してください[Machine Learning のサーバーでスクリプトの実行の計算コンテキスト](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)

## <a name="prepare-the-database-and-sample-data"></a>データベースおよびサンプル データを準備します。

1. このレッスンは、データベースを使用して`sqlpy`です。 前のレッスンのいずれかを行わなかった場合は、次のコードを実行してデータベースを作成できます。

    ```sql
    CREATE DATABASE sqlpy;
    GO
    USE sqlpy;
    GO
    ```

    > [!IMPORTANT]
    > 別のデータベースを使用する場合は、サンプル コードを編集し、接続文字列でデータベース名を変更することを確認します。

2. このサンプルは、航空券 dataset を使用して、R、Python の両方に用意されています。 Python サンプルについては、データベースを作成した後の手順に従ってここで説明されているデータを含むテーブルを設定します。 [RevoScaleR でデータのサンプル](https://docs.microsoft.com/machine-learning-server/r/sample-built-in-data)です。

3. クライアントで使用可能な環境を使用するには、この環境の名前を変更します。

## <a name="run-the-sample-code"></a>サンプル コードを実行します。

データベースの準備が完了しがあるテーブルに格納されたトレーニング データ Python 開発環境を開きコード サンプルを実行します。

コードでは、次の手順を実行します。

1. 必要なライブラリと関数をインポートします。
2. SQL Server への接続を作成します。 作成**データソース**データを操作するためのオブジェクト。
3. 使用してデータを変更**変換**ロジスティック回帰アルゴリズムで使用できるようにします。
4. 呼び出し`rx_lin_mod`し、モデルに適合するために使用する数式を定義します。
5. 元のデータに基づく予測のセットを生成します。
6. 予測された値に基づいて概要を作成します。

すべての操作は、計算コンテキストとして SQL Server のインスタンスを使用して実行されます。

> [!NOTE]
> コマンドラインから実行しているこのサンプルのデモについては、このビデオを参照してください: [SQL Server 2017 Advanced Analytics Python の](https://www.youtube.com/watch?v=FcoY795jTcc)

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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>コンピューティング コンテキストを定義すると、データ ソースを定義します。

データ ソースは、計算コンテキストと異なります。 _データソース_コードで使用されるデータを定義します。 _計算コンテキスト_コードを実行する場所を定義します。 ただし、同じ情報の一部を使用します。

+ Python 変数など`sql_query`と`sql_connection_string`データのソースを定義します。 

    これらの変数を渡す、 [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata)コンス トラクターを実装する、**データ ソース オブジェクト**という`data_source`です。

+ 作成する、**コンテキスト オブジェクトをコンピューティング**を使用して、 [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata)コンス トラクターです。 生成される**コンテキスト オブジェクトをコンピューティング**という`sql_cc`です。

    この例は、計算コンテキストとして使用する同じ SQL Server インスタンスにデータがあることを前提に、データ ソースで使用した同じ接続文字列を再利用されます。 
    
    ただし、データ ソースと計算コンテキストが別のサーバーになります。
 
### <a name="changing-compute-contexts"></a>計算コンテキストを変更します。

設定する必要がありますコンピューティング コンテキストを定義した後、**アクティブ コンピューティング コンテキスト**です。 

既定では、ほとんどの操作はつまり、異なるコンピューティング コンテキストを指定しない場合はローカルで実行されて、データ ソースからデータをフェッチする、およびコードは、現在の Python 環境で実行されます。

これにはアクティブなコンピューティング コンテキストを設定する 2 つの方法があります。
+ メソッドまたは関数の引数として
+ 呼び出して `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>メソッドまたは関数の引数としてコンピューティング コンテキストを設定します。

この例では、個々 の引数を使用して、計算コンテキストを設定する**rx**関数。
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

呼び出しでこのコンピューティング コンテキストを再利用[rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary): です。

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Rx_set_compute_context を使用して明示的にコンピューティング コンテキストを設定します。

関数は、 [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context)計算は既に定義されているコンテキストの間で切り替えることができます。

設定した後、アクティブなコンピューティング コンテキスト、変更するまでアクティブのままです。

### <a name="using-parallel-processing-and-streaming"></a>並列処理とストリーミングの使用

コンピューティング コンテキストを定義するときに設定することもパラメーター コンピューティング コンテキストでデータを処理する方法を制御します。 これらのパラメーターは、データ ソースの種類によって異なります。

SQL Server のコンピューティング コンテキストをバッチ サイズを設定したり、タスクの実行で使用する並列処理の次数についてのヒントを提供できます。

+ サンプルは、4 つのプロセッサを搭載したコンピューターで実行されたため、`num_tasks`パラメーターは、リソースの最大の使用を許可する 4 に設定されています。 
+ この値を 0 に設定した場合、SQL Server は、多くのタスクを並列に実行可能な限り、サーバーの現在の MAXDOP 設定では、既定値を使用します。 ただし、割り当てられる可能性がありますのタスクの正確な数は、サーバーの設定など、他の多くの要因とその他のジョブを実行しているに依存します。

## <a name="related-samples"></a>関連するサンプル

これらの追加の Python サンプルとチュートリアル リモート計算コンテキストの使用より複雑なデータ ソースを使用してエンド ツー エンド シナリオを示しています。

+ [SQL 開発者のためのデータベースでの Python](sqldev-in-database-python-for-sql-developers.md)
+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
