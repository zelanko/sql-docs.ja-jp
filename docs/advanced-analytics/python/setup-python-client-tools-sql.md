---
title: SQL Server Machine Learning で使用するための Python クライアントの設定 |Microsoft Docs
description: Python を使用した SQL Server Machine Learning サービスへのリモート接続用の Python のローカル環境を設定します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 326676d1be684b90784351de316590ebdb1ff29f
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051154"
---
# <a name="set-up-a-python-client-for-use-with-sql-server-machine-learning"></a>SQL Server Machine Learning で使用するための Python クライアントの設定します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python の統合では、Machine Learning サービス (In-database) のインストールに Python のオプションを含めると、SQL Server 2017 またはそれ以降の開始使用できます。 詳細については、次を参照してください。 [SQL Server Machine Learning のサービスをインストール](../install/sql-machine-learning-services-windows-install.md)します。

この記事では、machine learning と Python の統合を有効になっているリモート SQL Server に接続できるように、クライアントの開発ワークステーションを構成する方法について説明します。 最後に、SQL Server 上のリモート セッションをローカル セッションからの機能に加えて SQL Server の機能と同じ Python ライブラリをプッシュ計算にがあります。

> [!Tip]
> ビデオ デモについては、次を参照してください。 [R を実行し、Jupyter Notebook から SQL Server にリモートで Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/)します。

> [!Note]
> クライアント ライブラリだけをインストールする代わりには、スタンドアロン サーバーを使用しています。 スタンドアロンを使用して、リッチ クライアントとサーバーは、一部のお客様がエンド ツー エンドのシナリオの多くの作業を好むオプションです。 ある場合、[スタンドアロン サーバー](../install/sql-machine-learning-standalone-windows-install.md) SQL Server データベース エンジンのインスタンスから完全に分離された Python のサーバーがある SQL Server セットアップで提供されるため、します。 Standalon サーバーには、Anaconda と Microsoft 固有のライブラリのオープン ソース ベースのディストリビューションが含まれています。 この場所に、Python の実行可能ファイルを見つけることができます:`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`します。 リッチ クライアント インストールの検証、として開きます、 [Jupyter notebook](#python-tools) Python.exe を使用して、サーバーでコマンドを実行します。

## <a name="1---install-python-packages"></a>1 - Python パッケージをインストールします。

ベースの配布、および Microsoft 固有のパッケージを含む、SQL Server のものと同じ Python パッケージのバージョンがローカル ワークステーションにあります[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)と[microsftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)します。 [Azureml モデル-管理](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk)パッケージがインストールされても、スタンドアロン (インスタンスではない) の Machine Learning Server コンテキストに関連付けられた運用化タスクに適用されます。 SQL Server インスタンス上のデータベース内分析、運用化ではストアド プロシージャを使用します。

1. Python 3.5.2 を使用した Anaconda 4.2.0 以降をインストールするインストール スクリプトをダウンロードし、上記に示した Microsoft のパッケージを 3 つです。

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) SQL Server 2017 でない場合 (一般的なケース) をバインドします。 不明な場合は、このスクリプトを選択します。

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) リモートの SQL Server インスタンスの場合[Machine Learning Server 9.3 にバインドされている](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

2. 管理者特権での管理者権限で PowerShell ウィンドウを開き (右クリックして**管理者として実行**)。

3. インストーラーをダウンロードしたフォルダーに移動し、スクリプトを実行します。 追加、`-InstallFolder`ライブラリのフォルダーの場所を指定するコマンドライン引数。 以下に例を示します。 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

インストール フォルダーを省略すると、既定で C:\Program Files\Microsoft\PyForMLS は。

インストールは完了に時間がかかります。 PowerShell ウィンドウで進行状況を監視することができます。 セットアップが完了したら、パッケージの完全なセットがあります。 

> [!Tip] 
> お勧め、 [Windows FAQ の Python](https://docs.python.org/3/faq/windows.html) Python プログラムを Windows で実行されている一般的な purppose について。

## <a name="2---locate-executables"></a>2-実行可能ファイルを検索します。

PowerShell でも、Python.exe、スクリプト、およびその他のパッケージの場所を確認するインストール フォルダーに移動します。 

1. 入力`cd \`、ドライブのルートに移動し、指定したパスを入力する`-InstallFolder`前の手順でします。 インストール中にこのパラメーターを省略した場合、既定値は`cd C:\Program Files\Microsoft\PyForMLS`します。

2. 入力`dir *.exe`を実行可能ファイルを一覧表示します。 表示する必要があります**python.exe**、 **pythonw.exe**、および**アンインストール anaconda.exe**します。

  ![Python 実行可能ファイルの一覧](media/powershell-python-exe.png)
   
システムで Python の複数のバージョンをロードする場合は、この特定の Python.exe を使用する注意してください**revoscalepy**およびその他の Microsoft パッケージ。

> [!Note] 
> インストール スクリプトでは、新しい python インタープリターとモジュールをインストールしたが自動的にする必要があります、その他のツールを使用可能なしないことを意味する、コンピューターの PATH 環境変数は変更されません。 ツールに Python インタープリターとライブラリをリンクする方法の詳細については、次を参照してください。 [IDE をインストールする](#install-ide)します。

<a name="python-tool"></a>

## <a name="3---open-jupyter-notebooks"></a>3-Jupyter Notebook

Anaconda には、Jupyter Notebook が含まれています。 次の手順として、notebook を作成し、インストールしたライブラリを含むいくつかの Python コードを実行します。

1. Powershell プロンプトでは、Jupyter Notebook を開くスクリプト フォルダーに移動します。

   ```powershell
   .\Scripts\jupyter-notebook
   ```

  既定のブラウザーで開く必要があります、notebook`http://localhost:8889/tree`します。

2. クリックして**新規** をクリックし、 **Python 3**します。

  ![新しい Python 3 を選択した場合、jupyter notebook](media/jupyter-notebook-new-p3.png)

3. 入力`import revoscalepy`Microsoft 固有のライブラリのいずれかの読み込みを行うコマンドを実行します。

4. 複雑な一連のステートメントを入力します。 この例では、概要統計情報を使用して生成されます[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)ローカル データ セットに対して。 その他の関数は、サンプル データの場所を取得し、ローカルの .xdf ファイルのデータ ソース オブジェクトを作成します。

  ```Python
  import os
  from revoscalepy import rx_summary
  from revoscalepy import RxXdfData
  from revoscalepy import RxOptions
  sample_data_path = RxOptions.get_option("sampleDataDir")
  print(sample_data_path)
  ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
  summary = rx_summary("ArrDelay+DayOfWeek", ds)
  print(summary)
  ```

次のスクリーン ショットでは、入力と出力では、簡潔の一部を示します。

  ![jupyter notebook の revoscalepy 入力と出力の表示](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4 - SQL アクセス許可を取得します。

スクリプトを実行してデータをアップロードする SQL Server のインスタンスに接続するには、データベース サーバーで有効なログインが必要です。 SQL ログインまたは統合 Windows 認証を使用できます。 私たちは一般に、Windows 統合認証を使用する SQL ログインを使用する方が、スクリプトには、外部データへの接続文字列が含まれている場合に特に一部のシナリオでは、簡単ですがお勧めします。

少なくともコードを実行するために使用するアカウントを使用すると、特殊なアクセス許可が、外部スクリプトを実行、データベースから読み取る権限が必要です。 ほとんどの開発者はまた、ストアド プロシージャを作成して、トレーニング データを含むテーブルにデータを書き込むアクセス許可が必要か、データをスコア付けされました。 

Python を使用するデータベースで、アカウントの次のアクセス許可を構成するデータベース管理者に依頼します。

+ **EXECUTE ANY EXTERNAL SCRIPT**サーバー上で Python を実行します。
+ **db_datareader**モデルのトレーニングに使用するクエリを実行する特権。
+ **db_datawriter**トレーニング データまたはスコア付けされたデータを書き込む。
+ **db_owner**ストアド プロシージャなどのオブジェクトを作成するテーブル、関数。 
  必要もあります**db_owner** sample と test のデータベースを作成します。 

コードは、既定では、SQL Server がインストールされていないパッケージを必要とする場合は、インスタンスにインストールされているパッケージを作成するデータベース管理者に配置します。 SQL Server は、セキュリティで保護された環境とはパッケージをインストールできる場所に制限があります。 パッケージのコードの一部としてアドホックのインストールは使用しないで、権限を持っている場合でもです。 また、server ライブラリの新しいパッケージをインストールする前に、セキュリティに影響を常に慎重に検討します。

## <a name="5---test-remote-connection"></a>5 - リモート接続をテストします。

この次の手順を試す前に、SQL Server インスタンスへの接続文字列での権限があることを確認します、 [Iris サンプル データベース](../tutorials/demo-data-iris-in-sql.md)します。 データベースが存在しないための十分なアクセス許可がある場合は、[これらインライン命令を使用してデータベースを作成](#create-iris-remotely)です。

接続文字列を有効な値に置き換えます。 サンプル コードを使用して`"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"`が、コードはインスタンス名で、リモート サーバーを可能性があります指定する必要があります。

### <a name="define-a-function"></a>関数を定義します。

次のコードでは、後の手順で SQL Server に送信する関数を定義します。 実行すると、使用してデータとライブラリ (revoscalepy、pandas、matplotlib)、リモート サーバーであやめデータ セットの散布図のプロットを作成します。 ブラウザーで表示するために Jupyter Notebook に戻す、.png のバイト ストリームを返します。

```python
def send_this_func_to_sql():
    from revoscalepy import RxSqlServerData, rx_import
    from pandas.tools.plotting import scatter_matrix
    import matplotlib.pyplot as plt
    import io
    
    # remember the scope of the variables in this func are within our SQL Server Python Runtime
    connection_string = "Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"
    
    # specify a query and load into pandas dataframe df
    sql_query = RxSqlServerData(connection_string=connection_string, sql_query = "select * from iris_data")
    df = rx_import(sql_query)
    
    scatter_matrix(df)
    
    # return bytestream of image created by scatter_matrix
    buf = io.BytesIO()
    plt.savefig(buf, format="png")
    buf.seek(0)
    
    return buf.getvalue()
```

### <a name="send-the-function-to-sql-server"></a>関数を SQL Server に送信します。

この例で、リモート コンピューティング コンテキストを作成し、関数の実行を使用した SQL Server に送信[rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec)します。 **Rx_exec**関数は、引数としてコンピューティング コンテキストを受け入れるために役立ちます。 計算コンテキストの引数をリモートで実行する任意の関数が必要です。 などのいくつかの関数[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)この引数を直接サポートします。 そうでない操作で使用することができます**rx_exec**リモート コンピューティング コンテキストで、コードを提供します。

この例で生データがなかった SQL Server からの Jupyter Notebook に転送します。 あやめのデータベース内ですべての計算が発生して、イメージ ファイルのみがクライアントに返されます。

```python
from IPython import display
import matplotlib.pyplot as plt 
from revoscalepy import RxInSqlServer, rx_exec

# create a remote compute context with connection to SQL Server
sql_compute_context = RxInSqlServer(connection_string=connection_string.format(new_db_name))

# use rx_exec to send the function execution to SQL Server
image = rx_exec(send_this_func_to_sql, compute_context=sql_compute_context)[0]

# only an image was returned to my jupyter client. All data remained secure and was manipulated in my db.
display.Image(data=image)
```

次のスクリーン ショットでは、入力と散布図のプロットの出力を示します。

  ![jupyter notebook の散布図のプロットの出力を表示](media/jupyter-notebook-scatterplot.png)

## <a name="6---link-ide-to-pythonexe"></a>6 - IDE python.exe へのリンク

コマンドラインからスクリプトを単にデバッグしている場合は、標準の Python ツールで取得できます。 ただし、新しいソリューションを開発している場合は、フル機能の Python IDE を必要があります。 一般的なオプションがあります。

+ [Visual Studio 2017 Community エディション](https://www.visualstudio.com/vs/features/python/)の Python の使用
+ [AI tools for Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Visual Studio Code での Python](https://code.visualstudio.com/docs/languages/python)
+ PyCharm や Spyder、Eclipse などの人気のサード パーティ製ツール

Visual Studio は、データベース プロジェクトと machine learning プロジェクトをサポートしているためお勧めします。 Python 環境の構成については、次を参照してください。 [Visual Studio での Python の管理環境](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)します。

開発者が頻繁に複数の Python のバージョンを扱うため、セットアップは、パスに Python を追加できません。 Python 実行可能ファイルとセットアップによってインストールされているライブラリを使用するリンク、IDE を**Python.exe**も提供するパスにある**revoscalepy**と**microsoftml**します。 

Visual Studio で Python プロジェクトの場合、カスタム環境では、既定のインストールと仮定すると、次の値を指定します。

| 構成設定 | value |
|-----------------------|-------|
| **プレフィックスのパス** | C:\Program Files\Microsoft\PyForMLS |
| **インタープリターのパス** | C:\Program Files\Microsoft\PyForMLS\python.exe |
| **ウィンドウのインタープリター** | C:\Program Files\Microsoft\PyForMLS\pythonw.exe |

<a name="create-iris-remotely"></a>

## <a name="optional-create-the-iris-database-remotely"></a>リモートであやめのデータベースの作成オプション。

リモート サーバー上のデータベースを作成する権限があれば、この記事の例で使用される Iris デモ データベースを作成する次のコードを実行できます。

### <a name="1---create-the-irissql-database"></a>1 - irissql データベースを作成します。

```Python
import pyodbc

# creating a new db to load Iris sample in
new_db_name = "irissql"
connection_string = "Driver=SQL Server;Server=localhost;Database={0};Trusted_Connection=Yes;" 
                        # you can also swap Trusted_Connection for UID={your username};PWD={your password}
cnxn = pyodbc.connect(connection_string.format("master"), autocommit=True)
cnxn.cursor().execute("IF EXISTS(SELECT * FROM sys.databases WHERE [name] = '{0}') DROP DATABASE {0}".format(new_db_name))
cnxn.cursor().execute("CREATE DATABASE " + new_db_name)
cnxn.close()

print("Database created")
```

### <a name="2---import-iris-sample-from-sklearn"></a>2 - SkLearn から Iris サンプルをインポートします。

```Python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-recoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3-RecoscalePy Api を使用してテーブルを作成およびあやめデータの読み込み

```Python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

<a name="install-ide"></a>

## <a name="next-steps"></a>次の手順

ツールと SQL Server への接続を稼働したら、見て revoscalepy 関数と計算コンテキストの切り替えを取得する方法についてのチュートリアルの手順します。

> [!div class="nextstepaction"]
> [Revoscalepy とリモート コンピューティング コンテキストを使用して、モデルを作成します。](../tutorials/use-python-revoscalepy-to-create-model.md)