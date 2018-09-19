---
title: SQL Server での R 開発用データ サイエンス クライアントのセットアップ |Microsoft Docs
description: SQL Server へのリモート接続用の開発ワークステーションにローカルの R ライブラリとツールをインストールします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 309a78a2195f55a3ec39604b0c2bd385bb06a271
ms.sourcegitcommit: 9d0ff4f3e40db48fc01788684d34719065d159b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44724316"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>SQL Server での R 開発用のデータ サイエンス クライアントの設定します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

インスタンスを構成した後[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]機械学習をサポートするためには、リモート実行および配置のサーバーに接続できる R 開発環境を設定する必要があります。

### <a name="evaluation-and-independent-development"></a>評価と独立した開発
 
Developer edition および SQL Server に移動する場合、R スクリプトをローカルで作業する計画があれば、進んでに[IDE をインストールする](#install-ide)を SQL Server で使用されるローカルの R ライブラリ、ツールをポイントします。

> [!Tip]
> デモとビデオ チュートリアルでは、次を参照してください。 [R を実行し、Jupyter Notebook または任意の IDE から SQL Server にリモートで Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/)またはこの[YouTube ビデオ](https://youtu.be/D5erljpJDjE)します。

## <a name="1---install-r-packages"></a>1 - R パッケージをインストールします。

Microsoft 製品での R 機能は、多階層です。 Microsoft のオープン ソース基本 R ディストリビューションから始まりますがなど、製品固有のパッケージで拡張し、 [RevoScaleR](revoscaler-overview.md)、リモート計算コンテキストと R タスクの並列実行を有効にします。

クライアントとリモート サーバーの間の連携した操作には、両方のシステムと同じパッケージが必要です。 クライアント ワークステーション上のライブラリの完全な補完を取得するには、次の表にソフトウェア パッケージの 1 つをインストールします。 

| ライブラリのプロバイダー | 使用方法  |
|------------------|--------------------------------|
| [Microsoft R Client](http://aka.ms/rclient/download) |  この無料のダウンロードは、RevoScaleR、MicrosoftML、およびその他の R パッケージを提供しますは 2 つのスレッドとメモリ内のデータに制限されます。 ただし、ローカルで起動する R ソリューションを作成し、できます実行のシフト (と呼ばれる*コンピューティング コンテキスト*) データへのアクセスとリモートの SQL Server インスタンスの計算能力にします。 これは、実稼働 SQL Server インスタンスとクライアントの統合の推奨されるアプローチです。 このツールの詳細については、次を参照してください。 [Microsoft R Client は](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)します。|
| スタンドアロン サーバー | **共有機能**、SQL Server セットアップには、SQL Server 2016 R Services および SQL Server 2017 の machine learning 用のスタンドアロン サーバー インストール オプションが含まれています。 これらは、フル機能のサーバーに接続し、複数のデータ プラットフォームからデータを使用することができます、SQL Server から完全に分離します。 R と Python のタスクを実行している SQL Server データベース エンジン インスタンスにアクセスするクライアントの容量でソフトウェアを使用すること可能性がある可能性があります。 [SQL Server 2017 Machine Learning Server (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)が SQL Server 2017 machine learning のインスタンスとして同じライブラリです。 [SQL Server 2016 R Server (スタンドアロン)](../install/sql-r-standalone-windows-install.md)が SQL Server 2016 R Services と同じライブラリです。 |


<a name="r-tool"></a>
 
## <a name="2---open-an-r-prompt"></a>2 - R プロンプトを開きます

SQL Server で R をインストールするときに、RGui や Rterm などの R の基本インストールに標準的な同じ R ツールを取得します。 これらのツールは、軽量でパッケージとライブラリの情報を確認するか、アドホック コマンドまたはスクリプトを実行するか、またはチュートリアルのステップ実行する場合に便利です。 これらのツールを使用して、R バージョン情報を取得し、接続を確認することができます。

SQL Server または R Client にインストールされている R のバージョンを使用するには、SQL Server または R Client のプログラム フォルダーから、R のプロンプトを開きます。 次の手順は R クライアントおよび RGui.exe です。

1. R Client を参照してください`~\Program Files\Microsoft\R Client\R_SERVER\bin\x64`します。
2. ダブルクリック**RGui.exe** R コマンド プロンプトで R セッションを開始します。

Microsoft のプログラム フォルダーから R セッションを起動すると、RevoScaleR の場合を含め、いくつかのパッケージが自動的に読み込みます。 入力**法による search()** R プロンプトを確認します。

   ![R の読み込み時にバージョン情報](../install/media/rclient-rgui-r-prompt.png "R プロンプトを開く")

### <a name="tool-list-and-location"></a>ツールの一覧と場所

| ツール | 説明 | 
|------|-------------|
| **RTerm**: | R スクリプトを実行するためのコマンド ライン ターミナル | 
| **RGui.exe** | R 向けの単純な対話型エディターコマンドラインの引数は、RGui.exe と RTerm で同じです。 |
| **RScript** | バッチ モードでの R スクリプトを実行するためのコマンド ライン ツールです。 |

ツールがある**bin**としてインストールされている SQL Server の基本の R または R Client 用のフォルダー。 次のパスとは、インストールされている製品バージョンと機能によって、ツールの有効な場所です。

| Microsoft の製品 | R ツールの場所 |
|-------------------|-----------------|
| Microsoft R Client | `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64` |
| Microsoft Machine Learning (R) サーバー | `~\Program Files\Microsoft\R_SERVER\bin\x64`
| SQL Server 2016 R Services | `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2016 R スタンドアロン サーバー | `~\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64` 
| SQL Server 2017 の Machine Learning (R) のサービス | `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2017 Machine Learning (R) スタンドアロン サーバー | `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` |

## <a name="3---permissions"></a>3-アクセス許可

スクリプトを実行してデータをアップロードする SQL Server のインスタンスに接続するには、データベース サーバーで有効なログインが必要です。 SQL ログインまたは統合 Windows 認証を使用できます。 私たちは一般に、Windows 統合認証を使用するが、いくつかのシナリオが簡単では SQL ログインを使用することお勧めします。

少なくともコードを実行するために使用するアカウントを使用すると、特殊なアクセス許可が、外部スクリプトを実行、データベースから読み取る権限が必要です。 ほとんどの開発者も、スクリプトを含むストアド プロシージャの形式で新しいオブジェクトを作成するアクセス許可が必要しトレーニング データを含むテーブルにデータを書き込むまたはデータをスコア付けします。 

R: を使用するデータベースで、アカウントの次のアクセス許可を構成するデータベース管理者に問い合わせてください。

+ **EXECUTE ANY EXTERNAL SCRIPT**サーバー上で R を実行します。
+ **db_datareader**モデルのトレーニングに使用するクエリを実行する特権。
+ **db_datawriter**トレーニング データまたはスコア付けされたデータを書き込む。
+ **db_owner**ストアド プロシージャなどのオブジェクトを作成するテーブル、関数。 
  必要もあります**db_owner** sample と test のデータベースを作成します。 

コードは、既定では、SQL Server がインストールされていないパッケージを必要とする場合は、インスタンスにインストールされているパッケージを作成するデータベース管理者に配置します。 SQL Server は、セキュリティで保護された環境とはパッケージをインストールできる場所に制限があります。 パッケージのコードの一部としてアドホックのインストールは使用しないで、権限を持っている場合でもです。 また、server ライブラリの新しいパッケージをインストールする前に、セキュリティに影響を常に慎重に検討します。

> [!Tip]
> SQL Server とローカル開発環境での作業に慣れていない場合は、ログインとアクセス許可の設定の詳細については、このチュートリアルをステップすることができます: [RevoScaleR をさらに探究](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

## <a name="4---test-connections"></a>4 - 接続をテストします。

SQL Server を有効にする必要があります[リモート接続](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md)などのユーザー ログインとデータベースに接続するためのアクセス許可が必要とします。 以下の手順は、デモ データベース[NYCTaxi_Sample](../tutorials/sqldev-download-the-sample-data.md)と Windows 認証。

 検証手順として、組み込みのツールと RevoScaleR を使用して、リモート サーバーへの接続を確認します。

1. まず[、R ツールを開く](#r-tool)クライアント ワークステーションにします。 RevoScaleR を自動的に読み込みます。 たとえばに移動`~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` をダブルクリックします**RGui.exe**を開始します。

2. デモ データセットに関する統計情報の要約を返します。 このコマンドを実行して、RevoScaleR が動作を確認します。 SQL Server データベース エンジンのインスタンスの有効なサーバー名を指定することを確認します。

```r
connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
testQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
cc <-RxInSqlServer(connectionString=connStr)
rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=testQuery, connectionString=connStr), computeContext=cc)
```
このスクリプトはリモート サーバー上のデータベースに接続、クエリを提供する、コンピューティング コンテキストを作成します`cc`、リモートでコードを実行するための命令が RevoScaleR 関数を提供し、 **rxSummary**統計を返すクエリ結果の概要です。

<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5 - IDE をインストールします。

持続的なおよび重大な開発プロジェクトでは、統合開発環境 (IDE) をインストールする必要があります。 SQL Server のツールと組み込みの R ツールは、負荷の高い R 開発ツールが備わっていません。 作業中のコードをした後は、SQL Server で実行するためのストアド プロシージャとしてデプロイできます。

ローカルの R ライブラリをお使いの IDE をポイントする必要があります: R、RevoScaleR などの基本です。 スクリプトがデータとそのサーバー上の操作にアクセスする SQL Server でリモート コンピューティング コンテキストを呼び出すと、スクリプトの実行中に発生リモート SQL サーバーでワークロードを実行します。

### <a name="rstudio"></a>RStudio

使用する場合[RStudio](https://www.rstudio.com/)、R ライブラリとリモートの SQL Server 上に対応する実行可能ファイルを使用する環境を構成することができます。

1. SQL Server にインストールされている R パッケージのバージョンを確認します。 詳細については、次を参照してください。[取得の R パッケージ情報](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)します。

1. Microsoft R Client または RevoScaleR と SQL Server インスタンスで使用される基本の R ディストリビューションを含め、その他の R パッケージを追加するスタンドアロン サーバー オプションのいずれかをインストールします。 レベル以下で、同じバージョンを選択します (パッケージは、旧バージョンと互換性のある) サーバー上のものと同じパッケージ バージョンを提供します。 バージョンについては、この記事ではマップのバージョンを参照してください:[アップグレード R および Python コンポーネント](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

1. Rstudio に、 [R パスを更新](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R)RevoScaleR、Microsoft R Open、およびその他の Microsoft パッケージを提供する R 環境を指すようにします。 入手方法に応じて RevoScaleR とその他のライブラリでは、次のパスのいずれかがほとんどです。

  + C:\Program files \microsoft SQL Server\130\R_SERVER\Library
  + C:\Program files \microsoft SQL Server\140\R_SERVER\Library
  + C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64

### <a name="r-tools-for-visual-studio-rtvs"></a>R Tools for Visual Studio (RTVS)

推奨かどうかは、R の好きな IDE を既にがない、 **R Tools for Visual Studio**します。

+ [Visual Studio (RTVS) の R Tools をダウンロードします。](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [インストール手順](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio)RTVS は Visual Studio の複数のバージョンで使用できます。
+ [Visual Studio の R ツールを概要します。](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>RTVS から SQL Server に接続します。

この例では、データ サイエンスのワークロードがインストールされた Visual Studio 2017 Community Edition を使用します。

1. **ファイル**メニューの **新規**選び**プロジェクト**します。

2. 左側のウィンドウには、プレインストールされているテンプレートの一覧が含まれています。 クリックして**R**、選択および**R プロジェクト**します。 **名前**ボックスに「 `dbtest`  をクリック**OK**します。 

  Visual Studio では、新しいプロジェクト フォルダーと既定のスクリプト ファイルを作成します。`Script.R`します。 

3. 型`.libPaths()`スクリプトの最初の行にファイル、および ctrl キーを押しながら ENTER キーを押します。

  現在の R ライブラリ パスを表示するか、 **R インタラクティブ**ウィンドウ。 

4. をクリックして、 **R Tools**メニュー選択し、 **Windows**ワークスペースに表示できる他の R 固有ウィンドウの一覧を表示します。
 
    + 現在のライブラリ内のパッケージで ctrl キーを押しながら 3 を押してヘルプを表示します。
    + R の変数を参照してください、**変数エクスプ ローラー**CTRL + 8。

5. SQL Server インスタンスへの接続文字列を作成し、RxInSqlServer コンス トラクターで接続文字列を使用して、SQL Server データ ソース オブジェクトを作成します。 

    ```r
    connStr <- "Driver=SQL Server;Server=MyServer;Database=MyTestDB;Uid=;Pwd="
    sqlShareDir <- paste("C:\\AllShare\\", Sys.getenv("USERNAME"), sep = "")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    cc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    sampleDataQuery <- "SELECT TOP 100 * from [dbo].[MyTestTable]"
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, connectionString = connStr, rowsPerRead = 500)
    ```
    > [!TIP]
    > バッチを実行するを実行し、ctrl キーを押しながら ENTER キーを押してたい行を選択します。

6. サーバーに、コンピューティング コンテキストを設定し、データの単純な R コードを実行します。

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    結果が返されます、 **R インタラクティブ**ウィンドウ。
    
    SQL Server インスタンスで、コードが実行されていることを確認する場合は、Profiler を使用してトレースを作成することができます。

## <a name="next-steps"></a>次の手順

異なる 2 つのチュートリアルには、リモートの SQL Server インスタンスからローカルのコンピューティング コンテキストの切り替えを行うように、演習が含まれます。

+ [SQL Server のデータのチュートリアル: 使用 RevoScaleR の R 関数](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)