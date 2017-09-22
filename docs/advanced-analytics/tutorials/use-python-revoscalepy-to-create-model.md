---
title: "Revoscalepy で Python を使用してモデルを作成する |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: c497ad3e302f2950a65cf41aaa41237f19171ab4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Revoscalepy で Python を使用してモデルを作成するには

この例では、線形回帰モデルのアルゴリズムを使用して、SQL Server で作成する方法、 **revoscalepy**パッケージです。

**Revoscalepy**用 Python を含むオブジェクト、変換、およびアルゴリズムと同様に指定されたパッケージ、 **RevoScaleR** R 言語用のパッケージです。 このライブラリには、コンピューティング コンテキストを作成する、計算コンテキスト、データを変換およびロジスティックと線形回帰、デシジョン ツリーなどのよく使用されるアルゴリズムを使用して予測モデルのトレーニングの間でデータを移動できます。

詳細については、次を参照してください[revoscalepy は何ですか?](../python/what-is-revoscalepy.md)と[Python 関数リファレンス。](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="prerequisites"></a>前提条件

> [!IMPORTANT]
> SQL Server での Python コードを実行する必要がありますがインストールした SQL Server 2017 CTP 2.0 以降、およびインストールし、機能を有効にする必要があります**Machine Learning サービス**Python のです。 その他のバージョンの SQL Server は、Python の統合をサポートしていません。

## <a name="run-the-sample-code"></a>サンプル コードを実行します。

このコードは、次の手順を実行します。

1. 必要なライブラリと関数をインポートします。
2. SQL Server への接続を作成し、データを操作するためのデータ ソース オブジェクトを作成します
3. ロジスティック回帰アルゴリズムで使用できるように、データを変更します。
4. 呼び出し`rx_lin_mod`モデルに適合するために使用する式を定義および
5. 元のデータ セットに基づく予測のセットを生成します。
6. 予測された値に基づいて概要を作成します。

すべての操作は、計算コンテキストとして SQL Server のインスタンスを使用して実行されます。

一般に、リモート計算コンテキストでの呼び出し元の Python のプロセスは、リモート計算コンテキストで R を使用する方法に似ています。 このリリースで提供された Python 統合コンポーネントを含む Python 開発環境を使用してまたはコマンド ラインからは、Python スクリプトとしては、サンプルを実行します。 コードでは、作成し、コンピューティング コンテキスト オブジェクトを使用して、特定の計算を実行する場所を指定します。

> [!NOTE]
> 必ず適切なデータベースと環境の名前を変更してください。
> 
> コマンドラインから実行しているこのサンプルのデモについては、このビデオを参照してください: [SQL Server 2017 Advanced Analytics Python の](https://www.youtube.com/watch?v=FcoY795jTcc)


### <a name="sample-code"></a>サンプル コード

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

from pandas import Categorical
import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=PyTestDb;Trusted_Connection=True;'
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

## <a name="discussion"></a>ディスカッション

コードを確認し、いくつかの主要手順を強調表示してみましょう。

### <a name="defining-a-data-source-and-compute-context"></a>ソースのデータの定義と計算コンテキスト

データ ソースは、計算コンテキストと異なります。 _データソース_コードで使用されるデータを定義します。 _計算コンテキスト_コードを実行する場所を定義します。

1. など、Python 変数の作成`sql_query`と`sql_connection_string`ソースとを使用するデータを定義します。 これらの変数を渡す、 [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata)コンス トラクターを実装する、**データ ソース オブジェクト**という`data_source`です。
2. 使用してコンピューティング コンテキスト オブジェクトを作成、 [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata)コンス トラクターです。 この例では、計算コンテキストとして使用する同じ SQL Server インスタンスにデータがあることを前提に以前に定義された同じ接続文字列を渡します。 ただし、データ ソースと計算コンテキストが別のサーバーになります。 生成される**コンテキスト オブジェクトをコンピューティング**という`sql_cc`です。
3. アクティブなコンピューティング コンテキストを選択します。 既定では、操作はつまり、異なるコンピューティング コンテキストを指定しない場合は、ローカルで実行されます、データ ソースからデータをフェッチする、およびモデルの調整は、現在の Python 環境で実行されます。

### <a name="changing-compute-contexts"></a>計算コンテキストを変更します。

この例では、個々 の引数を使用して、計算コンテキストを設定する**rx**関数。
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

呼び出しで同じことが当てはまります**rxsummary**コンピューティング コンテキストが再利用します。

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

関数を使用することもできます。 [rx_set_computecontext](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rx-set-compute-context)を既に定義されている計算コンテキストを切り替えます。

### <a name="setting-the-degree-of-parallelism"></a>並列処理の次数を設定

コンピューティング コンテキストを定義するときに設定することもパラメーター コンピューティング コンテキストでデータを処理する方法を制御します。 これらのパラメーターは、データ ソースの種類によって異なります。

SQL Server のコンピューティング コンテキストをバッチ サイズを設定したり、タスクの実行で使用する並列処理の次数についてのヒントを提供できます。

設定、サンプルが 4 つのプロセッサを搭載したコンピューターで実行された、 *num_tasks* 4 へのパラメーターです。 この値を 0 に設定した場合、SQL Server は、多くのタスクを並列に実行可能な限り、サーバーの現在の MAXDOP 設定では、既定値を使用します。ただし、多くのプロセッサを搭載したサーバーであっても割り当てられる可能性がありますのタスクの正確な数によって異なります、サーバーの設定など、他の多くの要因と他のジョブを実行しています。

## <a name="related-samples"></a>関連するサンプル

これらの Python のサンプルと高度なヒントと、エンド ツー エンドのデモ用のチュートリアルを参照してください。

+ [SQL 開発者のためのデータベースでの Python](sqldev-in-database-python-for-sql-developers.md)
+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [展開および Python モデルを使用します。](../python/publish-consume-python-code.md)

