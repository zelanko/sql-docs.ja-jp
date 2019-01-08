---
title: R の開発 - SQL Server Machine Learning Services のデータ サイエンス クライアントのセットアップします。
description: SQL Server へのリモート接続用の開発ワークステーションにローカルの R ライブラリとツールをインストールします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/17/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 86b2ba305263b4699a3fe85328e854ba3105e4ab
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645515"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>SQL Server での R 開発用データ サイエンス クライアントのセットアップします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R 統合、SQL Server 2016 で使用可能な R 言語のオプションに含めるときに後で、 [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)または[SQL Server 2017 の Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)インストールします。 

開発、SQL Server の R ソリューションをデプロイし、インストール[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)を取得する開発ワークステーションに[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)およびその他の R ライブラリ。 リモートの SQL Server インスタンスにも必要な RevoScaleR ライブラリは、両方のシステム間のコンピューティングの要求を調整します。 

この記事では、machine learning と R 統合を有効になっているリモート SQL Server と対話できるように、R クライアント開発ワークステーションを構成する方法について説明します。 この記事の手順を完了すると、SQL Server のものと同じ R ライブラリがあります。 SQL Server のリモート R セッションにローカルの R セッションからの計算をプッシュする方法もわかります。

![クライアントとサーバー コンポーネント](media/sqlmls-r-client-revo.png "ローカルとリモートの R セッションとライブラリ")

インストールを検証するには、組み込みを使用することができます**RGUI**ツールのように、この記事で説明されているまたは[、ライブラリをリンク](#install-ide)RStudio に通常使用する別の IDE です。

> [!Tip]
> これらの演習ビデオ デモについては、次を参照してください。 [R の実行と Jupyter Notebook から SQL Server にリモートで Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/)します。

> [!Note]
> クライアント ライブラリをインストールする代わりを使用して、[スタンドアロン サーバー](../install/sql-machine-learning-standalone-windows-install.md)シナリオの詳細な作業を使用します。 一部のお客様のリッチ クライアントとして。 スタンドアロン サーバーは、SQL Server から切り離されます完全が同じ R ライブラリがあるため、使用できますがクライアントとしての SQL Server データベース内分析。 インポートおよびその他のデータ プラットフォームからのデータをモデル化する機能など、SQL に関連しない作業にも使用できます。 スタンドアロン サーバーをインストールする場合は、この場所に、R の実行可能ファイルを見つけることができます:`C:\Program Files\Microsoft SQL Server\140\R_SERVER`します。 インストールを検証する[R コンソール アプリを開く](#R-tools)R.exe をその場所で使用するコマンドを実行します。

## <a name="commonly-used-tools"></a>よく使用されるツール

To SQL では、新しい R 開発者向けまたは R および in-database 分析を新しい SQL 開発者であるかどうかが必要な R 開発ツールと T-SQL でのクエリ エディターの両方など[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)のすべてを実行するため、データベース内分析の機能です。

単純な R 開発シナリオには MRO および SQL Server ベースの R ディストリビューションにバンドルされている RGUI 実行可能ファイルで使用できます。 この記事では、ローカルとリモートの両方の R セッションの RGUI を使用する方法について説明します。 生産性の向上、使用してくださいフル装備の IDE など[RStudio または Visual Studio](#install-ide)します。

SSMS は、個別のダウンロード、作成して、R コードを格納しているものも含め、SQL Server のストアド プロシージャを実行している場合に便利です。 開発環境で記述するほぼすべての R コードは、ストアド プロシージャに埋め込むことができます。 その他のチュートリアルについては、ステップ[SSMS と埋め込まれた R](../tutorials/sqldev-in-database-r-for-sql-developers.md)します。

## <a name="1---install-r-packages"></a>1 - R パッケージをインストールします。

Microsoft の R パッケージで複数の製品およびサービス利用できます。 ローカルのワークステーションで Microsoft R Client のインストールをお勧めします。 R Client は、 [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)、 [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)、 [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)、およびその他の R パッケージ。

1. [Microsoft R Client のダウンロード](https://aka.ms/rclient/download)します。

2. インストール ウィザードで受け入れるか変更既定のインストール パス、そのまま使用またはコンポーネントの一覧を変更し、Microsoft R Client のライセンス条項に同意します。

  インストールが完了したら、[ようこそ] 画面は、製品やドキュメントを紹介します。

3. Intel 数値演算ライブラリ (MKL) 計算の出力を一貫性のあることを確認するには、MKL_CBWR システム環境変数を作成します。

  + コントロール パネルで、次のようにクリックします**システムとセキュリティ** > **システム** > **システムの詳細設定** >   **。環境変数**します。
  + という名前の新しいシステム変数を作成**MKL_CBWR**の値を設定して**自動**します。

## <a name="2---locate-executables"></a>2-実行可能ファイルを検索します。

検索し、R.exe、RGUI、およびその他のパッケージがインストールされていることを確認するインストール フォルダーの内容を一覧表示します。 

1. ファイル エクスプ ローラーで、R.exe の場所を確認する C:\Program Files\Microsoft\R Client\R_SERVER\bin フォルダーを開きます。

2. 確認には、オープン、x64 サブフォルダー **RGUI**します。 次の手順でこのツールを使用します。

3. RevoScaleR、MicrosoftML、およびその他のユーザーを含む、R Client にインストールされているパッケージの一覧を確認する C:\Program Files\Microsoft\R Client\R_SERVER\library を開きます。


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3 - RGUI を開始します。

SQL Server で R をインストールするときに、RGui や Rterm などの R の基本インストールに標準的な同じ R ツールを取得します。 これらのツールは、軽量でパッケージとライブラリの情報を確認するか、アドホック コマンドまたはスクリプトを実行するか、またはチュートリアルのステップ実行する場合に便利です。 これらのツールを使用して、R バージョン情報を取得し、接続を確認することができます。

1. C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 を開き、ダブルクリック**RGui** R コマンド プロンプトで R セッションを開始します。

  Microsoft のプログラム フォルダーから R セッションを起動すると、RevoScaleR の場合を含め、いくつかのパッケージが自動的に読み込みます。 

2. 入力`print(Revo.version)`コマンド プロンプトを返す RevoScaleR パッケージのバージョン情報。 RevoScaleR の 9.2.1 または 9.3.0 バージョンが必要です。

3. 入力**法による search()** インストールされているパッケージの一覧については、R プロンプトでします。

   ![R の読み込み時にバージョン情報](../install/media/rclient-rgui-r-prompt.png "R プロンプトを開く")


## <a name="4---get-sql-permissions"></a>4 - SQL アクセス許可を取得します。

R Client で R 処理は 2 つのスレッドとメモリ内のデータに制限されます。 複数のコアと大規模なデータ セットを使用して、スケーラブルな処理の実行を移すことができます (と呼ばれる*コンピューティング コンテキスト*) には、データ セットとリモートの SQL Server インスタンスの計算能力。 これは、クライアントとの統合に実稼働 SQL Server インスタンスでは、推奨されるアプローチと連携できるようにするには、アクセス許可と接続情報が必要です。

スクリプトを実行してデータをアップロードする SQL Server のインスタンスに接続するには、データベース サーバーで有効なログインが必要です。 SQL ログインまたは統合 Windows 認証を使用できます。 私たちは一般に、Windows 統合認証を使用する SQL ログインを使用する方が、スクリプトには、外部データへの接続文字列が含まれている場合に特に一部のシナリオでは、簡単ですがお勧めします。

少なくともコードを実行するために使用するアカウントを使用すると、特殊なアクセス許可が、外部スクリプトを実行、データベースから読み取る権限が必要です。 ほとんどの開発者はまた、ストアド プロシージャを作成して、トレーニング データを含むテーブルにデータを書き込むアクセス許可が必要か、データをスコア付けされました。 

データベース管理者に依頼[アカウントの次のアクセス許可を構成する](../security/user-permission.md)、r: を使用するデータベース

+ **EXECUTE ANY EXTERNAL SCRIPT**サーバー上の R スクリプトを実行します。
+ **db_datareader**モデルのトレーニングに使用するクエリを実行する特権。
+ **db_datawriter**トレーニング データまたはスコア付けされたデータを書き込む。
+ **db_owner**ストアド プロシージャなどのオブジェクトを作成するテーブル、関数。 
  必要もあります**db_owner** sample と test のデータベースを作成します。 

コードは、既定では、SQL Server がインストールされていないパッケージを必要とする場合は、インスタンスにインストールされているパッケージを作成するデータベース管理者に配置します。 SQL Server は、セキュリティで保護された環境とはパッケージをインストールできる場所に制限があります。 詳細については、次を参照してください。 [SQL Server に新しい R パッケージをインストール](install-additional-r-packages-on-sql-server.md)します。

## <a name="5---test-connections"></a>5 - 接続をテストします。

 検証手順として使用して**RGUI**と RevoScaleR をリモート サーバーへの接続を確認します。 SQL Server を有効にする必要があります[リモート接続](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server)などのユーザー ログインとデータベースに接続するためのアクセス許可が必要とします。 

以下の手順は、デモ データベース[NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)、および Windows 認証。

1. 開いている**RGUI**クライアント ワークステーションにします。 たとえばに移動`~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` をダブルクリックします**RGui.exe**を開始します。

2. RevoScaleR を自動的に読み込みます。 このコマンドを実行して、RevoScaleR が動作を確認します。 `print(Revo.version)`

3. リモート サーバー上で実行するデモ スクリプトを入力します。 リモート SQL Server インスタンスの有効な名前を含めるには、次のサンプル スクリプトを変更する必要があります。 ローカルのセッションとしてこのセッションが開始されますが、 **rxSummary**関数は、リモートの SQL Server インスタンスで実行します。

  ```R
  # Define a connection. Replace server with a valid server name.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  
  # Specify the input data in a SQL query.
  sampleQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
  
  # Define a remote compute context based on the remote server.
  cc <-RxInSqlServer(connectionString=connStr)

  # Execute the function using the remote compute context.
  rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr), computeContext=cc)
  ```

  **結果:**

  このスクリプトはリモート サーバー上のデータベースに接続、クエリを提供する、コンピューティング コンテキストを作成します`cc`、リモートでコードを実行するための命令が RevoScaleR 関数を提供し、 **rxSummary**統計を返すクエリ結果の概要です。

  ```R
    Call:
  rxSummary(formula = ~., data = RxSqlServerData(sqlQuery = sampleQuery, 
      connectionString = connStr), computeContext = cc)

  Summary Statistics Results for: ~.
  Data: RxSqlServerData(sqlQuery = sampleQuery, connectionString = connStr) (RxSqlServerData Data Source)
  Number of valid observations: 100 
  
  Name       Mean   StdDev   Min Max ValidObs MissingObs
  tip_amount 63.245 31.61087 36  180 100      0     
  ```

4. 取得し、コンピューティング コンテキストを設定します。 コンピューティング コンテキストを設定すると有効になります、セッションの実行中です。 わからない場合の計算がローカルかリモートかどうかを確認するには、次のコマンドを実行します。接続文字列を指定する結果は、リモート コンピューティング コンテキストを示します。

  ```R
  # Return the current compute context.
  rxGetComputeContext()

  # Revert to a local compute context.
  rxSetComputeContext("local")
  rxGetComputeContext()

  # Switch back to remote.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  cc <-RxInSqlServer(connectionString=connStr)
  rxSetComputeContext(cc)
  rxGetComputeContext()
  ```  

5. 名前と型を含む、データ ソースの変数に関する情報を返します。

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  結果には、23 の変数が含まれます。


6. 散布図を 2 つの変数間の依存関係があるかどうかを調べるを生成します。 

  ```R
  # Set the connection string. Substitute a valid server name for the placeholder.
  connStr <- "Driver=SQL Server;Server=<your database name>;Database=NYCTaxi_Sample;Trusted_Connection=true"

  # Specify a query on the nyctaxi_sample table.
  # For variables on each axis, remove nulls. Use a WHERE clause and <> to do this.
  sampleQuery <-"SELECT DISTINCT TOP 100 * from [dbo].[nyctaxi_sample] WHERE fare_amount <> '' AND  tip_amount <> ''"
  cc <-RxInSqlServer(connectionString=connStr)

  # Generate a scatter plot.
  rxLinePlot(fare_amount ~ tip_amount, data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr, computeContext=cc), type="p")
  ```

  次のスクリーン ショットでは、入力と散布図のプロットの出力を示します。

   ![散布図では、RGUI](media/rclient-setup-scatterplot.png "NYC タクシーのデモ データの散布図")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6 - R.exe リンク ツール

持続的なおよび重大な開発プロジェクトでは、統合開発環境 (IDE) をインストールする必要があります。 SQL Server のツールと組み込みの R ツールは、負荷の高い R 開発ツールが備わっていません。 作業中のコードをした後は、SQL Server で実行するためのストアド プロシージャとしてデプロイできます。

お使いの IDE をポイントして、ローカルの R ライブラリ: 基本の R、RevoScaleR の場合などです。 スクリプトがデータとそのサーバー上の操作にアクセスする SQL Server でリモート コンピューティング コンテキストを呼び出すと、スクリプトの実行中に発生リモート SQL サーバーでワークロードを実行します。

### <a name="rstudio"></a>RStudio

使用する場合[RStudio](https://www.rstudio.com/)、R ライブラリとリモートの SQL Server 上に対応する実行可能ファイルを使用する環境を構成することができます。

1. SQL Server にインストールされている R パッケージのバージョンを確認します。 詳細については、次を参照してください。[取得の R パッケージ情報](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)します。

1. Microsoft R Client または RevoScaleR と SQL Server インスタンスで使用される基本の R ディストリビューションを含め、その他の R パッケージを追加するスタンドアロン サーバー オプションのいずれかをインストールします。 レベル以下で、同じバージョンを選択します (パッケージは、旧バージョンと互換性のある) サーバー上と同じパッケージのバージョンを提供します。 バージョンについては、この記事ではマップのバージョンを参照してください。[R と Python のコンポーネントをアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

1. Rstudio に、 [R パスを更新](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R)RevoScaleR、Microsoft R Open、およびその他の Microsoft パッケージを提供する R 環境を指すようにします。 

  + R クライアント インストールでは、C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 を探します
  + スタンドアロン サーバーの場合は、C:\Program files \microsoft SQL Server\140\R_SERVER\Library または C:\Program files \microsoft SQL Server\130\R_SERVER\Library を探します

2. 閉じて RStudio を開きます。

RStudio を再度開くと、R R クライアント (またはスタンドアロン サーバー) から実行可能ファイルは、既定の R エンジンです。


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

## <a name="next-steps"></a>次の手順

異なる 2 つのチュートリアルには、リモートの SQL Server インスタンスからローカルのコンピューティング コンテキストの切り替えを行うように、演習が含まれます。

+ [チュートリアル:SQL Server データで RevoScaleR R 関数を使用します。](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)