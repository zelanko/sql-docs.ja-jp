---
title: SQL Server Machine Learning で使用するための Python クライアント ツールのセットアップ |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6f6823870060992586756dffa93aac6937d27d65
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "40401302"
---
# <a name="set-up-python-client-tools-for-use-with-sql-server-machine-learning"></a>SQL Server Machine Learning で使用するためのクライアント ツールに Python を設定します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python の統合では、Machine Learning サービス (In-database) を Python のサポートを追加すると、SQL Server 2017 以降を起動使用できます。 詳細については、次を参照してください。 [SQL Server Machine Learning のサービスをインストール](../install/sql-machine-learning-services-windows-install.md)します。

この記事では、Python を有効になっているリモート SQL Server に接続できるように、開発ワークステーションを構成する方法を説明します。

### <a name="evaluation-and-independent-development"></a>評価と独立した開発
 
Developer edition および SQL Server に移動する Python スクリプトをローカルで作業する計画があれば、進んでに[IDE をインストールする](#install-ide)を SQL Server で使用されるローカルの Python ライブラリ、ツールをポイントします。

> [!Tip]
> デモとビデオ チュートリアルでは、次を参照してください。 [R を実行し、Jupyter Notebook または任意の IDE から SQL Server にリモートで Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/)またはこの[YouTube ビデオ](https://youtu.be/D5erljpJDjE)します。

## <a name="1---install-python-packages"></a>1 - Python パッケージをインストールします。

ローカルのワークステーションが SQL Server のものと同じ Python パッケージ バージョンをいる必要があります: revoscalepy microsftml とします。 追加の Python パッケージは利用で、Machine Learning Server スタンドアロン (インスタンスではない) のコンテキストでは、その他のシナリオでよく使用されます。 

1. インストール シェル スクリプトをダウンロード[ https://aka.ms/mls93-py ](https://aka.ms/mls93-py) (を使用して、または[ https://aka.ms/mls-py ](https://aka.ms/mls-py) 9.2 の。 リリース)。 スクリプトでは、前述のすべてのパッケージと共に Python 3.5.2 を含む Anaconda 4.2.0 をインストールします。

  を通じて提供されます。 Python コンポーネント[SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033)します。 別のバージョンが必要な場合は、次を参照してください[CAB のダウンロード。](../install/sql-ml-cab-downloads.md)

2. 管理者特権での管理者権限で PowerShell ウィンドウを開きます (を右クリックして**管理者として実行**)。

3. インストーラーをダウンロードしたフォルダーに移動し、スクリプトを実行します。 追加、`-InstallFolder`ライブラリのフォルダーの場所を指定するコマンドライン引数。 以下に例を示します。 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls")
   ```

   インストールは完了に時間がかかります。 PowerShell ウィンドウで進行状況を監視することができます。 セットアップが完了したら、パッケージの完全なセットがあります。 たとえば、指定した`C:\mspythonlibs`、フォルダー名としてでのパッケージを検索します`C:\mspythonlibs\Lib\site-packages`します。 既定のフォルダーは、それ以外の場合、`C:\Program Files\Microsoft\PyForMLS1`します。

インストール スクリプトでは、新しい python インタープリターとインストールしたモジュールは、ツールを自動的に使用可能なため、コンピューターの PATH 環境変数は変更されません。 ツールに Python インタープリターとライブラリをリンクする方法の詳細については、次を参照してください。 [5 - IDE をインストールする](#install-ide)します。

<a name="python-tool"></a>
 
## <a name="2---open-a-python-prompt"></a>2 - Python のプロンプトを開く

Microsoft での Python の統合には、組み込みのツールと revoscalepy や microsoftml のような製品固有のライブラリ以外のデータが含まれます。 セットアップが完了したら、次の項目はクライアントとサーバーの両方のインスタンスで使用できます。

+ Python のサンプル データ
+ 4.2 の anaconda ディストリビューション 
+ Python 実行可能ファイル python.exe と pythonw.exe

> [!Tip] 
> お勧め、 [Windows FAQ の Python](https://docs.python.org/3/faq/windows.html) Python プログラムを Windows で実行されている一般的な purppose について。

### <a name="on-client-workstations"></a>クライアント ワークステーション上で

セットアップ スクリプトでインストールされている Python 実行可能ファイルを使用します。

1. 移動して`C:\Program Files\Microsoft\PyForMLS\python.exe`またはのインストール パス用に選択した任意の場所。

2. 右クリック**Python.exe**選択**管理者として実行**を対話形式のコマンド ライン ウィンドウを開きます。

### <a name="on-sql-server"></a>SQL server

SQL Server セットアップでは、サーバー インスタンスに標準の Python ツールとリソースを追加します。 Developer edition を使用しているし、Python のバージョンを確認またはアドホックのコマンドを実行する: 場合

1. 移動して`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`します。

2. 右クリック**Python.exe**選択**管理者として実行**を対話形式のコマンド ライン ウィンドウを開きます。

> [!Note]
> 一般に、リソースの競合を回避することをお勧めする**しない**Python コードを実行して、SQL Server インスタンスをことができますと思われる場合は、サーバーで、インスタンスのライブラリから Python を実行します。 ただし、ツールを使用して、インスタンスのライブラリでは役に立つは、SQL Server で実行されている場合にのみ発生する問題をデバッグしより詳細なエラー メッセージを表示またはすべての必要なパッケージがインストールされていることを確認する場合あります。

## <a name="3---permissions"></a>3-アクセス許可

スクリプトを実行してデータをアップロードする SQL Server のインスタンスに接続するには、データベース サーバーで有効なログインが必要です。 SQL ログインまたは統合 Windows 認証を使用できます。 私たちは一般に、Windows 統合認証を使用するが、いくつかのシナリオが簡単では SQL ログインを使用することお勧めします。

少なくともコードを実行するために使用するアカウントを使用すると、特殊なアクセス許可が、外部スクリプトを実行、データベースから読み取る権限が必要です。 ほとんどの開発者も、スクリプトを含むストアド プロシージャの形式で新しいオブジェクトを作成するアクセス許可が必要しトレーニング データを含むテーブルにデータを書き込むまたはデータをスコア付けします。 

Python を使用するデータベースで、アカウントの次のアクセス許可を構成するデータベース管理者に依頼します。

+ **EXECUTE ANY EXTERNAL SCRIPT**サーバー上で Python を実行します。
+ **db_datareader**モデルのトレーニングに使用するクエリを実行する特権。
+ **db_datawriter**トレーニング データまたはスコア付けされたデータを書き込む。
+ **db_owner**ストアド プロシージャなどのオブジェクトを作成するテーブル、関数。 
  必要もあります**db_owner** sample と test のデータベースを作成します。 

コードは、既定では、SQL Server がインストールされていないパッケージを必要とする場合は、インスタンスにインストールされているパッケージを作成するデータベース管理者に配置します。 SQL Server は、セキュリティで保護された環境とはパッケージをインストールできる場所に制限があります。 パッケージのコードの一部としてアドホックのインストールは使用しないで、権限を持っている場合でもです。 また、server ライブラリの新しいパッケージをインストールする前に、セキュリティに影響を常に慎重に検討します。

## <a name="4---test-connections"></a>4 - 接続をテストします。

すべてのツールとライブラリをインストールした後をサーバーに接続し、計算コンテキストを作成できること、または Python は、SQL Server と通信できることを確認します。

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>その revoscalepy Python コマンドラインから動作を確認します

確認する、 **revoscalepy** Python 対話型コマンド プロンプトから次のサンプル コードを実行するモジュールを読み込むことができます。 コードは、Python のサンプル データを使用してデータの概要を生成し、 [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)します。 

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

Python のインスタンスが呼び出されているを確認できるように、サンプル データのパスが出力されます。

### <a name="verify-that-python-can-be-called-from-a-local-sql-server"></a>Python をローカルの SQL Server から呼び出せることを確認します。

ローカル開発環境に Python がローカルと通信していることを確認します[外部スクリプト用に構成された SQL Server インスタンス](../install/sql-machine-learning-services-windows-install.md)します。 SQL Server Management Studio を使用して、新しく開きます**クエリ**ストアド プロシージャのコンテキストで任意の単純な Python のコマンド ウィンドウと実行。

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

最初の Python ランタイムを起動するのにはしばらくかかるが、SQL Server スタート パッドが動作している、Python は、SQL Server から開始できますわかりますエラーがない場合。

確認する**revoscalepy**に基づいてスクリプトの実行、SQL Server インスタンス ライブラリにある[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)、若干の変更を SQL Server と互換性のある結果を生成するとします。 

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

Rx_summary 型のオブジェクトを返すため`class revoscalepy.functions.RxSummary.RxSummaryResults`、SQL Server で結果を処理するために、複数の要素が含まれています、表形式でデータ フレームだけを抽出することができます。

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>リモート計算コンテキストとして SQL Server の Python の実行を確認します

インストールした場合**revoscalepy**ローカルの Python 開発環境で Python が有効になっている、SQL Server 2017 のリモート インスタンスに接続できるし、としてサーバーを使用して同様のコード サンプルを実行する必要があります、コンテキストを計算します。 

このスクリプトを実行するには、有効なサーバー名と、既存のデータベースを指定します。 このスクリプトは、データベースを使用しないが、接続文字列では、これが必要です。

```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=<server-name>;Database=TestDB;Trusted_Connection=True"
sqlcc = RxInSqlServer(
    connection_string = sql_conn_string,
    num_tasks = 1,
    auto_cleanup = False,
    console_output = True,
    execution_timeout_seconds = 0,
    wait = True
    )
rx_set_compute_context(sqlcc)

# get sample data and path
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

# generate summary
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

このサンプルでは、概要オブジェクトは SQL Server への適切な形式で表形式データを返すのではなく、コンソールに返されます。 

また、ため[rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context)が呼び出されると、サンプル データが読み込まれると、ローカルの samples フォルダーではなく SQL Server コンピューターでは、samples フォルダーから。


<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5 - IDE をインストールします。

コマンドラインからスクリプトを単にデバッグしている場合は、標準の Python ツールで取得できます。 ただし、新しいソリューションを開発またはリモート クライアントから作業する場合の全機能装備の IDE を Python の使用を勧めします。 一般的なオプションがあります。

+ [Visual Studio 2017 Community エディション](https://www.visualstudio.com/vs/features/python/)の Python の使用
+ [AI tools for Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Visual Studio Code での Python](https://code.visualstudio.com/docs/languages/python)
+ PyCharm や Spyder、Eclipse などの人気のサード パーティ製ツール

Visual Studio は、データベース プロジェクトと machine learning プロジェクトをサポートしているためお勧めします。 Python 環境の構成については、次を参照してください。 [Visual Studio での Python の管理環境](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)します。

開発者が頻繁に複数の Python のバージョンを扱うため、セットアップは、パスに Python を追加できません。 Python 実行可能ファイルとセットアップによってインストールされているライブラリを使用するリンク、IDE を**Python.exe** revoscalepy と microsoftml も提供しているパスにします。 たとえば、Visual Studio で Python プロジェクトの場合、カスタム環境指定`C:\Program Files\Microsoft\PyForMLS`、`C:\Program Files\Microsoft\PyForMLS\python.exe`と`C:\Program Files\Microsoft\PyForMLS\pythonw.exe`の**プレフィックス パス**、**インタープリター パス**と**ウィンドウのインタープリター**、それぞれします。

追加のガイダンスについては、次を参照してください。[リンク Python ツールと Ide](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)します。 Python パスは異なりますが、さまざまなツールから Python ライブラリをリンクする方法を表示するための Microsoft Machine Learning Server、情報の記事が書き込まれます。

## <a name="next-steps"></a>次のステップ

ツールと SQL Server への接続を稼働したら、見て revoscalepy 関数と計算コンテキストの切り替えを取得する方法についてのチュートリアルの手順します。

> [!div class="nextstepaction"]
> [Revoscalepy とリモート コンピューティング コンテキストを使用して、モデルを作成します。](../tutorials/use-python-revoscalepy-to-create-model.md)