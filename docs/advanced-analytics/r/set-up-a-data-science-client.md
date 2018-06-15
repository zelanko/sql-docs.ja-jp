---
title: SQL Server での R 開発用のデータ サイエンス クライアントのセットアップ |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dd0b420630846382b9d7cf456352bb606a4f0040
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31204564"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>SQL Server での R 開発用のデータ サイエンス クライアントのセットアップします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

インスタンスを構成した後[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]機械学習をサポートするためには、リモート実行および配置用サーバーに接続できる開発環境を設定する必要があります。

この記事では、SQL Server で R コードを実行する無料の Visual Studio Community エディションの構成を含む、いくつかの一般的なクライアント シナリオについて説明します。

## <a name="install-r-libraries-on-the-client"></a>クライアントでの R ライブラリをインストールします。

クライアント環境には、Microsoft R Open に加えて、SQL Server 上での R の分散的実行をサポートする RevoScaleR パッケージを含める必要があります。 R の標準のディストリビューションの R タスクの並列実行やリモート計算コンテキストをサポートするパッケージではありません。

これらのライブラリを取得するには、次のいずれかをインストールします。
  
+ [Microsoft R Client](http://aka.ms/rclient/download)

+ Microsoft R Server (for SQL Server 2016)

    - SQL Server のセットアップからインストールするを参照してください[インストール SQL Server 2016 R Server (スタンドアロン)。](../install/sql-r-standalone-windows-install.md)

    - 別の Windows ベースのインストーラーを使用するのを参照してください[Machine Learning Server for Windows のインストール。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ 機械学習の (SQL Server 2017) 用サーバー

    - SQL Server のセットアップからインストールするを参照してください[SQL Server サーバーをインストール 2017 Machine Learning (スタンドアロン)。](../install/sql-machine-learning-standalone-windows-install.md)

    - 別の Windows ベースのインストーラーを使用するのを参照してください[Windows 用の R Server 9.1 のインストール。](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="r-tools"></a>R のツール

いずれかでインストールされているのと同じ R ツールを取得する SQL Server で R をインストールするときに**基本**RGui、Rterm などの R のインストール。 このため実際があるすべてのツールを開発し、R コードをテストする必要があります。

次の標準的な R ツールが含まれている、*基本インストール*R のし、そのため、既定でインストールされます。

+ **RTerm**: R スクリプトを実行するためのコマンド ライン ターミナル

+ **RGui.exe**:  R のための単純な対話型エディター。コマンドライン引数は RGui.exe と RTerm で同じです。

+ **RScript**: R スクリプトをバッチ モードで実行するためのコマンドライン ツール。

これらのツールを検索するには、SQL Server または機能を学習するスタンドアロンのマシンを設定するときにインストールされた R ライブラリを決定します。 たとえば、既定のインストールでは、R ツールはこれらのフォルダーにあります。

+ SQL Server 2016 R Services: `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server のスタンドアロン: `~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 マシン サービスを学習します。 `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ 機械学習のサーバー (スタンドアロン)。 `~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

R ツールのヘルプを必要がある場合は、開く**RGui**をクリックして**ヘルプ**オプションのいずれかを選択

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R クライアントは、開発用に、RevoScaleR パッケージに対するアクセスを提供する無料でダウンロードします。 R のクライアントをインストールするには、SQL Server データベース内の分析、および Hadoop、Spark、または Machine Learning のサーバーを使用して Linux 上の分散 R コンピューティングを含む、すべてのサポートされているコンピューティング コンテキストで実行できる R ソリューションを作成できます。

別の R 開発環境が既にインストールされている場合 RStudio などは、ライブラリおよび Microsoft R クライアントによって提供される実行可能ファイルを使用する環境を再構成します。 により、RevoScaleR パッケージのすべての機能を使用することができますが、パフォーマンスが制限されます。

詳細については、次を参照してください。 [Microsoft R クライアントは何ですか。](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="install-a-development-environment"></a>開発環境をインストールします。

優先の R 開発環境がない場合、次のいずれかのお勧めします。

+ R Tools for Visual Studio

    Visual Studio 2015 で動作します。

    セットアップについては、次を参照してください。 [R Tools for Visual Studio のインストール方法](https://docs.microsoft.com/visualstudio/rtvs/installation)です。
 
    Microsoft R クライアント ライブラリを使用する RTVS を構成するのを参照してください[Microsoft R Client について。](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

    無料の Community Edition でもには、R、Python、および f# のプロジェクト テンプレートがインストールされるデータ サイエンス ワークロードが含まれています。

    Visual Studio からのダウンロード[このサイト](https://www.visualstudio.com/vs/)です。 

+ RStudio

    RStudio を使用する場合は、RevoScaleR ライブラリを使用するために追加の手順が必要です。

    - 必要なパッケージとライブラリを取得する Microsoft R クライアントをインストールします。
    - Microsoft R ランタイムを使用する R パスを更新します。

    詳細については、次を参照してください。 [R クライアントの構成、IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide)です。

## <a name="configure-your-ide"></a>IDE を構成します。

+ R Tools for Visual Studio

    参照してください[このサイト](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)ビルドし、R をデバッグする方法の例をいくつかのプロジェクト R Tools for Visual Studio を使用します。 

+ Visual Studio 2017

    Microsoft R クライアントまたは R サーバーをインストールする場合**する前に**Visual Studio をインストールして、R サーバー ライブラリを自動的に検出され、ライブラリ パスに使用します。 RevoScaleR ライブラリをインストールしていないかどうか、 **R ツール**メニューの  **R クライアントのインストール**です。

## <a name="run-r-in-sql-server"></a>SQL Server で R を実行します。

この例では、インストールされている、データ サイエンスのワークロードで Visual Studio の 2017 Community Edition を使用します。

1. **ファイル**メニューの **新規**し、**プロジェクト**です。

2. 手の形は、ウィンドウには、プレインストールされたテンプレートの一覧が含まれています。 をクリックして**R**を選択して**R プロジェクト**です。 **名前**ボックスに、入力`dbtest` をクリック**OK**です。

3. Visual Studio は、フォルダーの新しいプロジェクトと既定のスクリプト ファイルが作成されます。`Script.R`です。 

4. 型`.libPaths()`スクリプトの最初の行にファイルを開き、ctrl キーを押しながら ENTER キーを押します。

5. 現在の R ライブラリ パスを表示するか、 **R 対話型**ウィンドウです。 

6. をクリックして、 **R ツール**メニュー **Windows**ワークスペースに表示できる他の R に固有のウィンドウの一覧を表示します。
 
    + 現在のライブラリ内のパッケージにヘルプを表示するには、CTRL + 3 です。
    + R の変数を参照してください、**変数エクスプ ローラー**CTRL + 8 です。

7. SQL Server のインスタンスへの接続文字列を作成し、RxInSqlServer コンス トラクターで接続文字列を使用して、SQL Server データ ソース オブジェクトを作成します。 

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
    > バッチを実行するを実行し、ctrl キーを押しながら ENTER キーを押してする行を選択します。

8. サーバーに、計算コンテキストを設定し、データの単純な R コードを実行します。

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    結果が返される、 **R 対話型**ウィンドウです。
    
    自分でコードが SQL Server インスタンスで実行されていることを保証する場合は、Profiler を使用してトレースを作成することができます。