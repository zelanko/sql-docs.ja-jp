---
title: SQL Server で使用する Python クライアント ツールのセットアップ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: python
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: c0054fd0dc9ecb3dbf9035ddff0f6828a85b471d
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="set-up-python-client-tools-for-use-with-sql-server"></a>SQL Server で使用するためのクライアント ツールの Python の設定します。 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server での Python コードの実行をサポートするために Windows コンピューターでの Python 環境を構成する方法について説明します。 これには、次のシナリオが含まれます。

+ リモートの Python ワークステーションでソリューションを開発テストし、SQL Server への SQL Server のコンピューティング コンテキストでの実行コードを送信します。 

    一般にする多機能な Python 開発環境をインストールします。 
    
    ローカル Python 環境は、SQL Server インスタンス上の Python 環境と互換性があるし、リモート計算コンテキストをサポートしているライブラリをインストールする必要があります。

+ 専用の Python tools を使用して、コードをテストの開発し、ストアド プロシージャで実行する SQL Server にコードを移行します。

    開発では、サーバーをフル機能の Python IDE を使用するとします。 ただし、コードをデプロイする前に、環境でテストする、SQL Server 環境をエミュレートします。

+ 主に SQL Server のストアド プロシージャでの Python コードを実行して、Python コードを開発しないでください。 コードがテストされ、ストアド プロシージャでラップする前にデバッグを期待します。 ただし、場合によってはならない場合があります、問題の原因を特定の SQL Server の外部のコードを実行します。

    サーバーで、任意の Python tools をインストールしたくないと、分布にインストールされている既定のツールのみを使用します。 ストアド プロシージャ外でコードが動作することを確認するインスタンス ライブラリを使用する Python 環境を構成する場合があります。

## <a name="requirements"></a>必要条件

使用して、Python コードを開発するツールに関係なくは、次の要件は、SQL Server での Python コードを実行するか SQL Server のデータを使用するたびに適用されます。

+ Python を使用するのには、SQL Server 2017 以降が必要です。 Machine Learning Services (In-database) をサポートする機能をインストールし、機能を明示的に有効にする必要があります。 詳細については、次を参照してください。 [SQL Server 2017 セットアップ](../r/set-up-sql-server-r-services-in-database.md)です。

    SQL Server 2017 の初期のリリースをインストールした場合にこのコマンド ライン ユーティリティから Python コマンドを実行しようとするとエラーが発生する可能性があります。 お勧めする[最新バージョンにアップグレード](#bkmk_update)可能な場合です。 

+ コードの実行に使用するアカウントがデータベースに接続し、Python コードを実行するアクセス許可を確認する必要があります。 特殊なアクセス許可`EXECUTE ANY EXTERNAL SCRIPT`の R または Python スクリプトを使用するすべてのアカウントが必要です。 

+ アカウントがデータを読み取るか、新しいオブジェクトを作成するために必要になる可能性があるデータベースの権限を確認する必要があります。 

+ コードは、既定では、SQL Server がインストールされていないパッケージを必要とする場合、データベース管理者に、インスタンスによって使用される、Python 環境にインストールされているパッケージを配置します。 SQL Server は、セキュリティで保護された環境とはパッケージのインストール場所の制限があります。 

    アドホック インストール パッケージのコードの一部としては使用しないで、権限を持っている場合でもです。 また、server ライブラリの新しいパッケージをインストールする前に、セキュリティに影響を常に慎重に検討します。

> [!NOTE]
> Machine Learning のサーバーで Python を使用する場合は、追加をサポートする Linux または Spark クラスターなどのコンテキストを計算の次の記事を参照してください。
> 
> + [Windows でカスタムの Python パッケージおよびインタープリターをローカルにインストールする方法](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)
> + [Python tools および Ide Machine Learning のサーバーにインストールされている Python インタープリターをリンクします。](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)

## <a name="default-tools-included-with-standard-install"></a>標準インストールに含まれている既定のツール

Machine Learning Services (in-database) および Python での SQL Server 2017 の既定のインストールは、次の標準的な Python ツールとリソースを追加します。

+ Python のサンプル データ
+ 4.2 anaconda ディストリビューション 
+ Python の実行可能ファイル python.exe と pythonw.exe

既定では、インストールはこのフォルダーには:`~\Program Files\Microsoft SQL Server\<instance_name>\PYTHON_SERVICES`です。 

## <a name="open-python-from-the-command-line"></a>Python をコマンドラインから開く 

インスタンスにインストールされている Python ランタイムを使用するのには、インストール パスから実行可能ファイルの Python を開始できます。 基本的な手順については、 [Windows に関する FAQ の Python](https://docs.python.org/3/faq/windows.html)です。

> [!IMPORTANT]
> 一般に、リソースの競合を避けるためには、ことをお勧めする**しない**Python インスタンス ライブラリから、サーバー上、実行可能であると思われる場合、SQL サーバー インスタンスで Python コードが実行されます。 ただし、インスタンス ライブラリ ツールを使用する場合がありますをより詳細なエラー メッセージを表示またはすべての必要なパッケージがインストールされていることを確認し SQL Server で実行されている場合にのみ発生する問題をデバッグしようとしている場合に役立ちます。

1. インスタンスのライブラリがインストールされているフォルダーに移動します。 たとえば、既定のインストールで、フォルダーは`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`します。

2. Python.exe を見つけます。 

3. 右クリックし **管理者として実行**を対話形式のコマンド ライン ウィンドウを開きます。

## <a name="bkmk_update"></a> Python のコンポーネントを更新します。

ここで説明されているスクリプトを使用してダウンロードしてより新しいバージョンをインストールするには、Python コンポーネントを更新することができます: [Windows 上のクライアントのインストールの Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter#install-on-windows)
> 
> スクリプトによってダウンロードされたインストーラーは[SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033)です。 別のバージョンを必要がある場合は、次を参照してください[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする。](http://bing.com)

## <a name="set-up-a-python-development-environment"></a>Python の開発環境を設定します。

単に、コマンドラインからのスクリプトをデバッグする場合は、Machine Learning サービスと共にインストールされる標準的な Python ツールでまたはテキスト エディターを使用できます。 ただし、新しいソリューションを開発またはリモート クライアントから作業する場合、多機能な Python IDE の使用を勧めします。 一般的なオプションは次のとおりです。

+ [Visual Studio 2017 Community エディション](https://www.visualstudio.com/vs/features/python/)Python の
+ [Visual Studio の AI ツール](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Visual Studio のコードでの Python](https://code.visualstudio.com/docs/languages/python)
+ PyCharm、Spyder、Eclipse などの一般的なサード パーティ製ツール

Visual Studio は、machine learning のプロジェクトだけでなく、データベース プロジェクトをサポートするためお勧めします。 Python 環境の構成については、次を参照してください[Visual Studio での管理 Python environments。](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

## <a name="install-revoscalepy"></a>Revoscalepy をインストールします。

読み込みしようとするときに、エラーが表示場合でも、Machine Learning のサービスが正常にインストールされて、 **revoscalepy** Python コマンドラインからの関数。 次の手順では、使用を有効にする更新プログラムをインストールする方法について説明する**revoscalepy**です。

1. インストールのシェル スクリプトをダウンロードhttps://aka.ms/mls93-py(を使用またはhttps://aka.ms/mls-py9.2 用です。 リリース)。 スクリプトは、前述のすべてのパッケージと共に 3.5.2、Python を含む Anaconda 4.2.0 をインストールします。

2. (管理者) として、管理者特権を持つ新しい PowerShell ウィンドウを開きます。

3. インストーラーをダウンロードしたフォルダーを開き、スクリプトを実行します。

```ps1
cd {{download-directory}}
.\Install-PyForMLS.ps1
```

実行することも、`-InstallFolder`コマンドライン引数とコマンドの一部として、新しいパスを指定します。 以下に例を示します。 

```ps1
.\Install-PyForMLS.ps1 -InstallFolder "<installation_path>")
```

エラーが発生した場合は、特定のファイルの実行ポリシー、セッションの期間を次のように中断する必要があります。 

```ps1
powershell -ExecutionPolicy Bypass -File "C:\<installation_path>\Install-PyForMLS.ps1"
```

セッションの実行中の実行ポリシーを中止することもできます。 このステートメントでは、実行ポリシーが に設定されている`Unrestricted`セッションの間およびは not 構成を変更または変更をディスクに書き込みます。

```ps1
Set-ExecutionPolicy Bypass -Scope Process
```

## <a name="verify-that-python-and-revoscalepy-are-working"></a>Python および revoscalepy が動作していることを確認します。

すべてのツールとライブラリをインストールした後に、サーバーに接続し、コンピューティング コンテキストを作成することや、Python は、SQL Server と通信できることを確認する必要があります。

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Python のコマンドラインからその revoscalepy の動作を確認します。

確認する、 **revoscalepy** Python 対話形式のコマンド プロンプトから次のサンプル コードを実行モジュールを読み込むことができます。 コードは、Python のサンプル データを使用してデータの概要を生成し、 [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)です。 

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

Python のどのインスタンスが呼び出されているを確認できるように、サンプル データのパスが印刷されます。

### <a name="verify-that-python-can-be-called-from-sql-server"></a>Python を SQL Server から呼び出せることを確認してください。

Python は、SQL Server と通信していることを確認するには、SQL Server Management Studio を開きます。 (など、別のようなツールを使用することができます[SQL 操作 Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is))。新しく開きます**クエリ**任意の単純な Python は、ストアド プロシージャのコンテキストでコマンド ウィンドウと実行。

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

最初に、Python ランタイムを起動するかかることができますが、場合はエラーが発生することを認識、SQL Server スタート パッドを使用すると、Python は、SQL Server から起動できます。

確認する**revoscalepy**に基づいてスクリプトを実行して、SQL Server インスタンス ライブラリにある[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)、若干の変更を SQL Server と互換性のある結果を生成するとします。 

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

Rx_summary が型のオブジェクトを返すため`class revoscalepy.functions.RxSummary.RxSummaryResults`、SQL Server で結果を処理する複数の要素が含まれています、表形式でデータ フレームだけを抽出することができます。

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>SQL Server のリモート計算コンテキストとしての Python の実行を確認します。

インストールした場合**revoscalepy**ローカルの Python 開発環境で Python が有効になっている、SQL Server 2017 のインスタンスに接続できるし、compute としてサーバーを使用するようなコード サンプルを実行する必要がありますコンテキスト。 


```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=;Database=TestDB;Trusted_Connection=True"
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

このサンプルでは SQL Server に表形式データを返す整形式ではなく、コンソールで、概要のオブジェクトが返されます。 

また、ため[rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context)が呼び出されると、サンプル データが読み込まれると、ローカルの samples フォルダーではなく、SQL Server コンピューターで、サンプル フォルダーからです。
