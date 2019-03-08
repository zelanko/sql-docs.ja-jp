---
title: Python 開発 - SQL Server Machine Learning のデータ サイエンス クライアントのセットアップします。
description: Python を使用した SQL Server Machine Learning サービスへのリモート接続用の Python のローカル環境 (Jupyter Notebook または PyCharm) を設定します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c61275d1a52a3e248e2c1f551d30ece20c92b7fb
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579562"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services での Python 開発用のデータ サイエンス クライアントの設定します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python の統合での Python のオプションを追加するときに、SQL Server 2017 またはそれ以降の開始がある、 [Machine Learning サービス (In-database) インストール](../install/sql-machine-learning-services-windows-install.md)します。 

開発を SQL Server の Python のソリューションの配置は、インストールの Microsoft の[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)およびその他の Python ライブラリ、開発ワークステーション。 これはリモートの SQL Server インスタンス上でも、revoscalepy ライブラリは、両方のシステム間のコンピューティングの要求を調整します。 

この記事では、machine learning と Python の統合を有効になっているリモート SQL Server で操作できるようにする、Python 開発用ワークステーションを構成する方法について説明します。 この記事の手順を完了すると、SQL Server のものと同じ Python ライブラリがあります。 SQL Server での Python のリモート セッションにローカルの Python セッションからの計算をプッシュする方法もわかります。

![クライアントとサーバー コンポーネント](media/sqlmls-python-client-revo.png "ローカルとリモートの Python のセッションとライブラリ")

この記事で説明に従って、インストールを検証するには、組み込みの Jupyter Notebook を使用することができますまたは[、ライブラリをリンク](#install-ide)PyCharm に通常使用する別の IDE です。

> [!Tip]
> これらの演習ビデオ デモについては、次を参照してください。 [R の実行と Jupyter Notebook から SQL Server にリモートで Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/)します。

> [!Note]
> クライアント ライブラリをインストールする代わりを使用して、[スタンドアロン サーバー](../install/sql-machine-learning-standalone-windows-install.md)シナリオの詳細な作業を使用します。 一部のお客様のリッチ クライアントとして。 スタンドアロン サーバーは、SQL Server から切り離されます完全が同じ Python ライブラリがあるため、使用できますがクライアントとしての SQL Server データベース内分析。 インポートおよびその他のデータ プラットフォームからのデータをモデル化する機能など、SQL に関連しない作業にも使用できます。 スタンドアロン サーバーをインストールする場合は、この場所に、Python の実行可能ファイルを見つけることができます:`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`します。 インストールを検証する[Jupyter notebook を開いて](#python-tools)Python.exe をその場所で使用するコマンドを実行します。

## <a name="commonly-used-tools"></a>よく使用されるツール

To SQL では、新しい Python 開発者や、SQL 開発者を初めて使用する Python とデータベース内分析は、かどうかが必要、Python の開発ツールと T-SQL でのクエリ エディターの両方など[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)のすべてを実行するにはデータベース内分析の機能です。

Python 開発では、Jupyter Notebook は、SQL Server によってインストールされる Anaconda ディストリビューションにバンドルを使用できます。 この記事を実行できるように Python コードのローカルとリモートの SQL Server では、Jupyter Notebook を開始する方法について説明します。

SSMS は、個別のダウンロード、作成して、Python コードを格納しているものも含め、SQL Server のストアド プロシージャを実行している場合に便利です。 ストアド プロシージャで Jupyter Notebook で記述するほぼすべての Python コードを埋め込むことができます。 詳細については他のクイック スタート手順を実行できる[SSMS と埋め込まれた Python](../tutorials/quickstart-python-verify.md)します。

## <a name="1---install-python-packages"></a>1 - Python パッケージをインストールします。

ローカル ワークステーションには、Python 3.5.2 配布、および Microsoft 固有のパッケージと基本 Anaconda 4.2.0 をなど、SQL Server のものと同じ Python パッケージのバージョンが必要です。

インストール スクリプトでは、Python クライアントを 3 つの Microsoft 固有のライブラリを追加します。 スクリプトは、インストール[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)、データ ソース オブジェクトと、コンピューティング コンテキストを定義するために使用します。 インストール[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)機械学習アルゴリズムを提供します。 [Azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk)パッケージがインストールされても、スタンドアロン (インスタンスではない) の Machine Learning Server コンテキストに関連付けられた運用化タスクに適用し、データベース内分析の使用が制限される可能性があります。

1. インストール スクリプトをダウンロードします。

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) Microsoft Python パッケージのバージョン 9.2.1 をインストールします。 このバージョンは、既定の SQL Server 2017 インスタンスに対応します。 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) Microsoft Python パッケージのバージョンが 9.3 をインストールします。 リモート SQL Server 2017 インスタンスの場合、このバージョンは適して[Machine Learning Server 9.3 にバインドされている](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

2. 管理者特権での管理者権限で PowerShell ウィンドウを開き (右クリックして**管理者として実行**)。

3. インストーラーをダウンロードしたフォルダーに移動し、スクリプトを実行します。 追加、`-InstallFolder`ライブラリのフォルダーの場所を指定するコマンドライン引数。 例 : 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

インストール フォルダーを省略すると、既定で C:\Program Files\Microsoft\PyForMLS は。

インストールは完了に時間がかかります。 PowerShell ウィンドウで進行状況を監視することができます。 セットアップが完了したら、パッケージの完全なセットがあります。 

> [!Tip] 
> お勧め、 [Windows FAQ の Python](https://docs.python.org/3/faq/windows.html) Python プログラムを Windows で実行されている一般的な purppose について。

## <a name="2---locate-executables"></a>2-実行可能ファイルを検索します。

PowerShell でまだ Python.exe、スクリプト、およびその他のパッケージがインストールされていることを確認するインストール フォルダーの内容の一覧表示します。 

1. 入力`cd \`、ドライブのルートに移動し、指定したパスを入力する`-InstallFolder`前の手順でします。 インストール中にこのパラメーターを省略した場合、既定値は`cd C:\Program Files\Microsoft\PyForMLS`します。

2. 入力`dir *.exe`を実行可能ファイルを一覧表示します。 表示する必要があります**python.exe**、 **pythonw.exe**、および**アンインストール anaconda.exe**します。

  ![Python 実行可能ファイルの一覧](media/powershell-python-exe.png)
   
システムで Python の複数のバージョンをロードする場合は、この特定の Python.exe を使用する注意してください**revoscalepy**およびその他の Microsoft パッケージ。

> [!Note] 
> インストール スクリプトでは、新しい python インタープリターとモジュールをインストールしたが自動的にする必要があります、その他のツールを使用可能なしないことを意味する、コンピューターの PATH 環境変数は変更されません。 ツールに Python インタープリターとライブラリをリンクする方法の詳細については、次を参照してください。 [IDE をインストールする](#install-ide)します。

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3-Jupyter Notebook

Anaconda には、Jupyter Notebook が含まれています。 次の手順として、notebook を作成し、インストールしたライブラリを含むいくつかの Python コードを実行します。

1. Powershell プロンプトで、C:\Program Files\Microsoft\PyForMLS ディレクトリの中には、Scripts フォルダーから Jupyter Notebook を開きます。

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  既定のブラウザーで開く必要があります、notebook`https://localhost:8889/tree`します。

  起動する別の方法は、ダブルクリック**jupyter notebook.exe**します。 

2. クリックして**新規** をクリックし、 **Python 3**します。

  ![新しい Python 3 を選択した場合、jupyter notebook](media/jupyter-notebook-new-p3.png)

3. 入力`import revoscalepy`Microsoft 固有のライブラリのいずれかの読み込みを行うコマンドを実行します。

4. 入力し、実行`print(revoscalepy.__version__)`バージョン情報を返します。 9.2.1 または 9.3.0 を表示する必要があります。 これらのバージョンのいずれかを使用することができます[サーバーで revoscalepy](../r/determine-which-packages-are-installed-on-sql-server.md#get-package-vers)します。 

4. 複雑な一連のステートメントを入力します。 この例では、概要統計情報を使用して生成されます[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)ローカル データ セットに対して。 その他の関数は、サンプル データの場所を取得し、ローカルの .xdf ファイルのデータ ソース オブジェクトを作成します。

  ```python
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

データベース管理者に依頼[アカウントの次のアクセス許可を構成する](../security/user-permission.md)Python を使用するデータベースで。

+ **EXECUTE ANY EXTERNAL SCRIPT**サーバー上で Python を実行します。
+ **db_datareader**モデルのトレーニングに使用するクエリを実行する特権。
+ **db_datawriter**トレーニング データまたはスコア付けされたデータを書き込む。
+ **db_owner**ストアド プロシージャなどのオブジェクトを作成するテーブル、関数。 
  必要もあります**db_owner** sample と test のデータベースを作成します。 

コードは、既定では、SQL Server がインストールされていないパッケージを必要とする場合は、インスタンスにインストールされているパッケージを作成するデータベース管理者に配置します。 SQL Server は、セキュリティで保護された環境とはパッケージをインストールできる場所に制限があります。 パッケージのコードの一部としてアドホックのインストールは使用しないで、権限を持っている場合でもです。 また、server ライブラリの新しいパッケージをインストールする前に、セキュリティに影響を常に慎重に検討します。


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5 - テスト データを作成します。

リモート サーバー上のデータベースを作成する権限がある場合は、この記事の残りの手順に使用したあやめデモ データベースを作成する次のコードを実行することができます。

### <a name="1---create-the-irissql-database-remotely"></a>1 - irissql データベースをリモートで作成します。

```python
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

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3-Revoscalepy Api を使用してテーブルを作成およびあやめデータの読み込み

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6 - リモート接続をテストします。

この次の手順を試す前に、SQL Server インスタンスへの接続文字列での権限があることを確認します、 [Iris サンプル データベース](../tutorials/demo-data-iris-in-sql.md)します。 データベースが存在しないための十分なアクセス許可がある場合は、[これらインライン命令を使用してデータベースを作成](#create-iris-remotely)です。

接続文字列を有効な値に置き換えます。 サンプル コードを使用して`"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"`が、コードは、インスタンス名とデータベース ユーザー ログインにマップする資格情報オプションで、リモート サーバーを可能性があります指定する必要があります。

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

  ![jupyter notebook showing scatter plot output](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7 - ツールから Python を開始します。

開発者が頻繁に複数の Python のバージョンを扱うため、セットアップは、パスに Python を追加できません。 Python 実行可能ファイルとセットアップによってインストールされているライブラリを使用するリンク、IDE を**Python.exe**も提供するパスにある**revoscalepy**と**microsoftml**します。 

### <a name="command-line"></a>[パッケージ実行ユーティリティ]

実行すると**Python.exe** C:\Program Files\Microsoft\PyForMLS から (または、Python クライアント ライブラリのインストールに指定した位置にかかわらず)、完全な Anaconda ディストリビューションと Microsoft Python へのアクセスがあります。モジュール、 **revoscalepy**と**microsoftml**します。

1. C:\Program Files\Microsoft\PyForMLS に移動し、ダブルクリックして**Python.exe**します。
2. 対話型ヘルプを開きます。 `help()`
3. ヘルプのプロンプトで、モジュールの名前を入力:`help> revoscalepy`します。 ヘルプは、名前、パッケージのコンテンツ、バージョン、およびファイルの場所を返します。
4. バージョンとパッケージの情報を返す、**ヘルプ >** プロンプト:`revoscalepy`します。 Enter キーを数回にヘルプを終了します。
5. モジュールをインポートします。 `import revoscalepy`


### <a name="jupyter-notebooks"></a>Jupyter Notebook

この資料では、組み込みの Jupyter Notebook を使用して、関数の呼び出しを示す**revoscalepy**します。 このツールに慣れていない場合、次のスクリーン ショットは、パーツを組み合わせる方法と、すべて「動く」その理由を示します。 

親フォルダー C:\Program Files\Microsoft\PyForMLS には、Anaconda とマイクロソフトのパッケージが含まれます。 スクリプト フォルダーの下の Anaconda に Jupyter Notebook が含まれており、Python の実行可能ファイルは、Jupyter Notebook での自動登録します。 パッケージでは、サイト パッケージは、データ サイエンスと機械学習用に使用される 3 つの Microsoft パッケージを含む、ノートブックにインポートできます。

  ![実行可能ファイルとライブラリ](media/jupyter-notebook-python-registration.png)

別の IDE を使用している場合は、ツールに Python の実行可能ファイルと関数のライブラリをリンクする必要があります。 次のセクションでは、一般的に使用されるツールの手順を説明します。

### <a name="visual-studio"></a>Visual Studio

ある場合[Visual Studio での Python](https://code.visualstudio.com/docs/languages/python)Microsoft の Python パッケージを含む Python 環境を作成する次の構成オプションを使用します。

| 構成設定 | value |
|-----------------------|-------|
| **プレフィックスのパス** | C:\Program Files\Microsoft\PyForMLS |
| **インタープリターのパス** | C:\Program Files\Microsoft\PyForMLS\python.exe |
| **ウィンドウのインタープリター** | C:\Program Files\Microsoft\PyForMLS\pythonw.exe |

Python 環境の構成については、次を参照してください。 [Visual Studio での Python の管理環境](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)します。

### <a name="pycharm"></a>PyCharm

PyCharm、Machine Learning Server によってインストールされている実行可能ファイルの python インタープリターを設定します。

1. 新しいプロジェクト 設定で、クリックして**ローカル追加**します。

2. 入力`C:\Program Files\Microsoft\PyForMLS\`します。

これでインポートできます**revoscalepy**、 **microsoftml**、または**azureml**モジュール。 選択することもできます**ツール** > **Python コンソール**対話型ウィンドウを開きます。

## <a name="next-steps"></a>次のステップ

ツールと SQL Server への接続を稼働したら、Python のクイック スタートを使用してを実行して、スキルを展開[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)します。

> [!div class="nextstepaction"]
> [クイック スタート:Python は、SQL Server に存在することを確認します。](../tutorials/quickstart-python-verify.md)