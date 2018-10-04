---
title: PowerShell (チュートリアル) を使用してデータを準備する |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cc47b7a8ba7090064983063ab579bd8ac8a1ccbb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142092"
---
# <a name="prepare-the-data-using-powershell-walkthrough"></a>PowerShell (チュートリアル) を使用してデータを準備します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この時点には、インストールされている次のいずれかが必要です。

+ SQL Server 2016 R Services
+ SQL Server 2017 Machine Learning Services を有効になっている R 言語により

このレッスンでは、データ、R パッケージ、および Github リポジトリから、このチュートリアルで使用される R スクリプトをダウンロードします。 利便性のための PowerShell スクリプトを使用してすべてのものをダウンロードすることができます。

また、サーバーと R ワークステーションの両方に、いくつか追加の R パッケージをインストールする必要があります。 手順を説明します。

次に、2 番目の PowerShell スクリプト RunSQL_R_Walkthrough.ps1 を使用して、モデリング、スコア付けに使用されるデータベースを構成します。 スクリプトがデータベースにデータの一括読み込みを実行することを指定して、一部の SQL 関数とデータ サイエンス タスクを簡略化するストアド プロシージャを作成します。

それでは、始めましょう!

## <a name="1-download-the-data-and-scripts"></a>1.データとスクリプトをダウンロードします。

必要なすべてのコードは、GitHub リポジトリに用意されています。 PowerShell スクリプトを使用して、ファイルのローカル コピーを作成できます。

1.  データ サイエンス クライアント コンピューターで、管理者権限で Windows PowerShell コマンド プロンプトを開きます。

2.  ダウンロード スクリプトをエラーなく実行できるようにするために、次のコマンドを実行します。 これにより、システムの既定値を変更することなく、スクリプトを一時的に実行できるようになります。

    ```
    Set-ExecutionPolicy Unrestricted -Scope Process -Force
    ```
      
3.  次の Powershell コマンドを実行して、スクリプト ファイルをローカル ディレクトリにダウンロードします。 既定のフォルダーで別のディレクトリを指定しない場合`C:\tempR`が作成されるとすべてのファイルがそこに保存します。
  
    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_R_Walkthrough.ps1'  
    $ps1_dest = "$pwd\Download_Scripts_R_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_R_Walkthrough.ps1 –DestDir 'C:\tempR'
    ```
  
    別のディレクトリにファイル保存するには、パラメーター *DestDir* の値を編集し、コンピューターの別のフォルダーを指定します。 存在しないフォルダー名を入力する場合、フォルダーは、PowerShell スクリプトによって作成されます。
  
4.  ダウンロードには、しばらく時間がかかる場合があります。 完了すると、Windows PowerShell コマンド コンソールは次のようになります。
  
    ![PowerShell スクリプトの完了後](media/rsql-e2e-psscriptresults.PNG "PowerShell スクリプトの完了後")
  
5.  PowerShell コンソールで、コマンド `ls` を実行すると、 *DestDir*にダウンロードされたファイルの一覧が表示されます。  ファイルについては、次を参照してください。[内容](#whats-included-in-the-sample)します。

## <a name="2-install-required-r-packages"></a>2.必要な R パッケージをインストールします。

このチュートリアルでは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]の部分で既定ではインストールされない R ライブラリがいくつか必要です。 ソリューションを開発する場合と、パッケージをクライアントにインストールする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ソリューションをデプロイするコンピューター。

### <a name="install-required-packages-on-the-client"></a>必要なパッケージをクライアントにインストールする

ダウンロードした R スクリプトには、これらのパッケージをダウンロードおよびインストールするコマンドが含まれています。

1. R 環境で RSQL_R_Walkthrough.R というスクリプト ファイルを開きます。

2. 次の行を選択して実行します。
    
    ```
    # Install required R libraries, if they are not already installed.
    if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
    if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
    if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
    if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
    ```
    
    一部のパッケージでは、必要なパッケージもインストールします。 全部で、約 32 パッケージが必要です。

### <a name="install-required-packages-on-the-server"></a>必要なパッケージをサーバーにインストールする

SQL Server にパッケージをインストールできるように、多くのさまざまな方法はあります。 たとえば、SQL Server は[R パッケージ管理](../r/install-additional-r-packages-on-sql-server.md)により、データベース管理者はパッケージ リポジトリを作成し、ユーザーが自分のパッケージをインストールする権限を割り当てる機能。 ただし、コンピューターの管理者の場合は、適切なライブラリをインストールする場合に限り、R を使用して新しいパッケージをインストールできます。

> [!NOTE]
> サーバーで、**しない**場合でも、入力を求め、ユーザー ライブラリにインストールします。 ユーザー ライブラリにインストールする場合、SQL Server インスタンスが見つからないか、パッケージを実行します。 詳細については、「 [Installing New R Packages on SQL Server](../r/install-additional-r-packages-on-sql-server.md)」(SQL Server に新しい R パッケージをインストールする) を参照してください。

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで、**管理者権限で** RGui.exe を開きます。  既定値を使用して SQL Server R Services をインストールした場合、RGui.exe は C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64) にあります。

2.  R プロンプトで、次の R コマンドを実行します。
  
    ```
    install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    ```

    - この例では、R grep 関数を使用して、使用可能なパスのベクトルを検索し、"Program Files"を含むパスを見つけます。 詳細については、次を参照してください。 [ http://www.rdocumentation.org/packages/base/functions/grep](http://www.rdocumentation.org/packages/base/functions/grep)します。

    - パッケージが既にインストールされている場合を実行してインストールされているパッケージの一覧を確認してください。`installed.packages()`します。

## <a name="3-prepare-the-environment-using-runsqlrwalkthroughps1"></a>3.RunSQL_R_Walkthrough.ps1 を使用して環境を準備します。

ダウンロードにはと、データ ファイル、R スクリプト、および T-SQL スクリプトには、PowerShell スクリプトが含まれています`RunSQL_R_Walkthrough.ps1`します。 このスクリプトで、次のアクションが実行されます。

- SQL ネイティブ クライアントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用コマンドライン ユーティリティがインストールされているかどうかを確認します。 このコマンドライン ツールは、 [bcp ユーティリティ](../../tools/bcp-utility.md)を実行するために必要です。bcp ユーティリティは、データを SQL テーブルに高速一括読み込みする際に使用します。

- 指定したインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、データベースを構成し、モデルとデータのテーブルを作成する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをいくつか実行します。

- いくつかのストアド プロシージャを作成する SQL スクリプトを実行します。

- 以前にダウンロードしたデータを、`nyctaxi_sample` というテーブルに読み込みます。

- R スクリプト ファイルの引数を、指定したデータベース名を使用するように書き換えます。

ソリューションをビルドするコンピューターでこのスクリプトを実行します。 開発および R コードをテストする、ラップトップなど。 このコンピューター (これをデータ サイエンス クライアントと呼びます) は、名前付きパイプ プロトコルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに接続できる必要があります。

1. PowerShell コマンドラインを開いて**管理者として**します。
  
2.  スクリプトをダウンロードしたフォルダーに移動し、次のようにスクリプト名を入力します。 Enter キーを押します。

    ```
    .\RunSQL_R_Walkthrough.ps1
    ```
  
3.  次のパラメーターごとに求められます。
  
    **データベース サーバー名**: Machine learning Services または R Services がインストールされている SQL Server インスタンスの名前。

    ネットワークの要件によっては、インスタンス名に 1 つ以上のサブネット名を指定する必要があります。  たとえば、MYSERVER が動作しない場合は、myserver.subnet.mycompany.com を試してください。
    
    **作成するデータベースの名前**: たとえば、**Tutorial** や **Taxi** などと入力します

    **ユーザー名**: データベース アクセス権限を持つアカウントを指定します。 次の 2 つの選択肢があります。
    
    + CREATE DATABASE 特権を持つ SQL ログイン名を入力し、次のプロンプトで SQL パスワードを入力します。
    + 名前を入力せずに Enter キーを押して自分の Windows ID を使用し、セキュリティで保護されたプロンプトに、Windows パスワードを入力します。 PowerShell は、別の Windows ユーザー名の入力をサポートしていません。
    + 有効なユーザーを指定しなかった場合は、統合 Windows 認証を使用して、スクリプトが既定値です。
    
      > [!WARNING]
      > 資格情報を提供する PowerShell スクリプトで、プロンプトを使用すると、パスワードはプレーン テキストで更新されたスクリプト ファイルに書き込まれます。 必要な R オブジェクトの作成が完了したら、すぐにファイルを編集し、資格情報を削除してください。
      
    **CSV ファイルへのパス**: データ ファイルへの完全パスを指定します。 既定のパスとファイル名は、`C:\tempR\nyctaxi1pct.csv` です。
  
4.  Enter キーを押してスクリプトを実行します。

    スクリプトによってファイルがダウンロードされ、データがデータベースに自動的に読み込まれます。 これには、しばらく時間がかかる場合があります。 PowerShell ウィンドウ内のステータス メッセージを確認してください。
      
    一括インポートまたはその他のステップが失敗、」の説明に従って手動でデータを読み込むことができるかどうか、[トラブルシューティング](#bkmk_Troubleshooting)セクション。

**結果 (正常に完了した場合)**

```
Execution successful
Completed registering all stored procedures used in this walkthrough.
This step (registering all stored procedures) takes 0.39 seconds.
Plug in the database server name, database name, user name and password into the R script file
This step (plugging in database information) takes 0.48 seconds.
```

次のレッスンにジャンプするには、このリンクをクリックします[ビューと SQL を使用してデータを探索。](walkthrough-view-and-explore-the-data.md)

## <a name="bkmk_Troubleshooting"></a>トラブルシューティング

PowerShell スクリプトで問題があれば、行うことができます、手順のいずれかまたはすべて手動で例として、PowerShell スクリプトの行を使用しています。 このセクションでは、いくつかの一般的な問題と回避策を示します。

### <a name="powershell-script-didnt-download-the-data"></a>PowerShell スクリプトを実行してもデータをダウンロードできない

手動でデータをダウンロードするには、次のリンクを右クリックし、 **[対象をファイルに保存]** を選択します。

[http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv](http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv)

データを保存した場所のダウンロードしたデータ ファイルのパスとファイル名をメモします。 完全なパスを使用してテーブルにデータを読み込む必要がある**bcp**します。

### <a name="unable-to-download-the-data"></a>データをダウンロードできない

サイズが大きなデータ ファイルです。 インターネット接続が比較的良好なコンピューターを使用する必要があります。 またはダウンロードがタイムアウトになる可能性があります。

### <a name="could-not-connect-or-script-failed"></a>接続できない、またはスクリプトが失敗する

スクリプトの実行時には、次のエラーが返されることがあります:*SQL Server への接続の確立中に、ネットワーク関連のエラーまたはインスタンス固有のエラーが発生しました。*

+ インスタンス名のつづりが正しいことを確認します。
+ 接続文字列が正しいことを確認します。
+ ネットワークの要件によっては、インスタンス名に 1 つ以上のサブネット名を指定する必要があります。  たとえば、MYSERVER が動作しない場合は、myserver.subnet.mycompany.com を試してください。
+ Windows ファイアウォールで、SQL Server による接続が許可されているかどうかを確認してください。
+ サーバーを登録し、リモート接続できることを確認してください。
+ 名前付きインスタンスを使用している場合は、SQL Browser を有効にして接続を容易にしてください。

### <a name="network-error-or-protocol-not-found"></a>ネットワーク エラー、またはプロトコルが見つからない

+ インスタンスがリモート接続をサポートしていることを確認します。
+ 指定された SQL ユーザーがデータベースにリモートで接続できることを確認してください。
+ インスタンス上で名前付きパイプを有効にしてください。
+ アカウントのアクセス許可を確認します。 指定したアカウントに、新規データベース作成とデータ アップロードのアクセス許可がない可能性があります。

### <a name="bcp-did-not-run"></a>bcp が実行されなかった

+ コンピューターで [bcp ユーティリティ](../../tools/bcp-utility.md) を使用できることを確認します。 **bcp** は、PowerShell ウィンドウまたは Windows コマンド プロンプトから実行できます。
+ エラーが発生する場合、**bcp** ユーティリティの場所を PATH システム環境変数に追加して、やり直します。

### <a name="the-table-schema-was-created-but-the-table-has-no-data"></a>テーブル スキーマは作成されたがテーブルにデータがない

その他のスクリプトを問題なく実行できる場合、次のようにコマンド ラインから **bcp** を呼び出して手動でテーブルにデータをアップロードできます。

#### <a name="using-a-sql-login"></a>SQL ログインを使用する

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U <SQL login> -P <password>
~~~~

#### <a name="using-windows-authentication"></a>Windows 認証を使用する

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -T
~~~~

+ `in`キーワードは、データ移動の方向を指定します。
+ **-f** 引数には、フォーマット ファイルの完全パスを指定する必要があります。 **in** オプションを使用する場合、フォーマット ファイルが必要です。
+ SQL ログインで bcp を実行する場合、 **-U** 引数と **-P** 引数を使用します。
+ Windows 統合認証を使用している場合、 **-T** 引数を使用します。

スクリプトによってデータが読み込まれない場合は、構文をチェックし、サーバー名がネットワークに対して正しく指定されていることを確認してください。 たとえば、サブネットがあればそれらを含め、名前付きインスタンスに接続している場合は、コンピューター名も含めるようにしてください。 ログインに一括アップロードを実行する機能があることを確認します。

### <a name="i-want-to-run-the-script-without-prompts"></a>プロンプトなしでスクリプトを実行する必要がある

次のテンプレートを使用すると、環境固有の値を使用して、すべてのパラメーターを 1 つのコマンド ラインで指定できます。

```
.\RunSQL_R_Walkthrough.ps1 -server <server address> -dbname <new db name> -u <user name> -p <password> -csvfilepath <path to csv file>
```

次の例では、SQL ログインを使用してスクリプトを実行しています。

```
.\RunSQL_R_Walkthrough.ps1 -server MyServer.subnet.domain.com -dbname MyDB –u SqlUserName –p SqlUsersPassword -csvfilepath C:\temp\nyctaxi1pct.csv
```

-   *SqlUserName*の資格情報を使用して、指定したインスタンスとデータベースに接続します。
-   *C:\temp\nyctaxi1pct.csv*ファイルからデータを取得します。
-   *MyServer*という *インスタンスの* MyDB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで、 *dbo.nyctaxi_sample*テーブルにデータを読み込みます。

### <a name="the-data-loaded-but-it-contains-duplicates"></a>データは読み込まれるが重複がある

データベースに同じ名前と、同じスキーマの既存のテーブルが含まれている場合**bcp**既存のデータを上書きするのではなく、データの新しいコピーを挿入します。

データの重複を回避するには、スクリプトをもう一度実行する前に、既存のテーブルを切り捨てます。

## <a name="whats-included-in-the-sample"></a>このサンプルに含まれるもの

GitHub リポジトリからファイルをダウンロードするときは、次の要素が表示します。

+ CSV 形式でデータ参照してください[トレーニングとスコア付けデータ](#bkmk_data)詳細については
+ 環境を準備する PowerShell スクリプト
+ bcp を使用してデータを SQL Server にインポートする XML フォーマット ファイル
+ 複数の T-SQL スクリプト
+ このチュートリアルを実行するために必要なすべての R コード

### <a name="bkmk_data"></a>トレーニング セットとデータをスコア付け

このデータは、ニューヨーク市タクシー データ セットの代表的なサンプル データです。各乗車で支払われた乗車料金やチップなど、2013 年の 1 億 7,300 万件の乗車記録が含まれています。 データを使用しやすくするために、Microsoft データ サイエンス チームはダウンサンプリングを実行し、わずか 1% のデータを取得しました。  このデータは、Azure のパブリック BLOB ストレージ コンテナーに .CSV 形式で共有されています。 ソース データは、非圧縮ファイル、350 MB 未満です。

+ パブリック データセット: [NYC タクシーのデータセットとリムジン委員会](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)

+ [NYC タクシー データセットで Azure ML モデルを構築](https://blogs.technet.microsoft.com/machinelearning/2015/04/02/building-azure-ml-models-on-the-nyc-taxi-dataset/)します。

### <a name="powershell-and-r-script-files"></a>PowerShell と R のスクリプト ファイル

+ **RunSQL_R_Walkthrough.ps1**スクリプトを実行するこの最初に、PowerShell を使用します。 データをデータベースに読み込む SQL スクリプトを呼び出します。

+ **taxiimportfmt.xml** データをデータベースに読み込むときに、BCP ユーティリティに使用される書式定義ファイルです。

+ **RSQL_R_Walkthrough.R**データ分析とモデリングのレッスンの残りの部分で使用されるコア R スクリプトになります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データの調査、分類モデルの構築、プロットの作成に必要なすべての R コードが含まれています。

### <a name="t-sql-script-files"></a>T-SQL スクリプト ファイル

PowerShell スクリプトは、複数を実行します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] SQL Server インスタンス上のスクリプト。 次の表、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプトとその実行内容。

|SQL スクリプト ファイル名|説明|
|------------------------|----------------|
|create-db-tb-upload-data.sql|データベースと 2 つのテーブルを作成します。<br /><br /> *nyctaxi_sample*: トレーニング データ (ニューヨーク市のタクシーのデータ セットの 1% サンプル) を格納するテーブルです。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。<br /><br /> *nyc_taxi_models*: トレーニング済みモデルをバイナリ形式で格納するために使用されるテーブル。|
|PredictTipBatchMode.sql|トレーニングしたモデルを呼び出し、新しい監視のラベルを予測するストアド プロシージャを作成します。 入力パラメーターとしてクエリを指定できます。|
|PredictTipSingleMode.sql|トレーニングした分類モデルを呼び出し、新しい監視のラベルを予測するストアド プロシージャを作成します。 新しい監視の変数は、インライン パラメーターとして渡されます。|
|PersistModel.sql|データベースのテーブルに分類モデルのバイナリ表現を格納できるストアド プロシージャを作成します。|
|fnCalculateDistance.sql|乗車と降車の場所間の直線距離を計算する SQL スカラー値関数を作成します。|
|fnEngineerFeatures.sql|分類モデルをトレーニングするための機能を作成する SQL テーブル値関数を作成します。|

このチュートリアルで使用する T-SQL クエリを選択し、テスト済みとして実行することができます-R コードでは、します。 ただし、さらに実験を進める場合や、独自のソリューションを開発する場合は、専用の SQL 開発環境を使用してクエリのテストと調整を行ってから、R コードに追加することをお勧めします。

+ [Visual Studio Code](https://code.visualstudio.com/) の [mssql 拡張機能](https://code.visualstudio.com/docs/languages/tsql)は、無償で使用できる軽量な環境です。クエリの実行だけでなく、ほとんどのデータベース開発タスクもサポートしています。
+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) は無償ながらも強力なツールで、SQL Server データベースの開発や管理用に提供されています。

## <a name="next-lesson"></a>次のレッスン

[表示および R と SQL を使用してデータを調査できます。](walkthrough-view-and-explore-the-data.md)

## <a name="previous-lesson"></a>前のレッスン

[R と SQL Server のエンド ツー エンドのデータ サイエンスのチュートリアル](walkthrough-data-science-end-to-end-walkthrough.md)

