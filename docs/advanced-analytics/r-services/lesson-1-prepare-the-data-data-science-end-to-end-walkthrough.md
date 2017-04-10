---
title: "レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 65fd41d4-c94e-4929-a24a-20e792a86579
caps.latest.revision: 29
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 25
---
# レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル)
このチュートリアルの準備をするには、次の手順を実行する必要があります。

1. チュートリアルで使用するデータとすべての R スクリプトをダウンロードします。 GitHub からのダウンロードを簡易化する PowerShell スクリプトが用意されています。   

2. その他の R パッケージを、サーバーと R ワークステーションの両方にインストールします。  

3. モデリングとスコア付けに使用するデータベース、データなど、環境を準備します。
 
    この場合は、2 つ目の PowerShell スクリプト RunSQL_R_Walkthrough.ps1 を使用します。
    このスクリプトを実行すると、データベースが構成され、指定したテーブルにデータがアップロードされます。  また、データ サイエンス タスクを簡易化する SQL 関数とストアド プロシージャもいくつか作成されます。 
 

## <a name="1-download-the-data-and-scripts"></a>1.データとスクリプトをダウンロードする  
このチュートリアルの実行に必要なすべてのコードは、GitHub リポジトリに用意されています。 PowerShell スクリプトを使用して、ファイルのローカル コピーを作成できます。  
  
#### <a name="to-download-all-scripts-using-powershell"></a>PowerShell を使用してすべてのスクリプトをダウンロードするには  
  
1.  データ サイエンス クライアント コンピューターで、管理者権限で Windows PowerShell コマンド プロンプトを開きます。  
  
2.  このインスタンスでまだ PowerShell を実行したことがない場合、またはスクリプトを実行するアクセス許可がない場合は、エラーが発生する可能性があります。 その場合、スクリプトを実行する前にこのコマンドを実行して、システムの既定値を変更することなくスクリプトを一時的に許可することができます。  
  
    ```  
    Set-ExecutionPolicy Unrestricted -Scope Process -Force  
    ```  
  
3.  次のコマンドを実行して、スクリプト ファイルをローカル ディレクトリにダウンロードします。 別のディレクトリを指定しない場合、既定では C:\tempR というフォルダーが作成され、すべてのファイルがそこに保存されます。  
  
    ```  
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_R_Walkthrough.ps1'  
    $ps1_dest = "$pwd\Download_Scripts_R_Walkthrough.ps1"  
    $wc = New-Object System.Net.WebClient  
    $wc.DownloadFile($source, $ps1_dest)  
    .\Download_Scripts_R_Walkthrough.ps1 –DestDir 'C:\tempR'  
  
    ```  
  
    別のディレクトリにファイル保存するには、パラメーター *DestDir* の値を編集し、コンピューターの別のフォルダーを指定します。 存在しないフォルダー名を入力すると、PowerShell スクリプトの実行時に自動的にフォルダーが作成されます。  
  
4.  ダウンロードが完了すると、Windows PowerShell コマンド コンソールは次のようになります。  
  
    ![After completion of PowerShell script](../../advanced-analytics/r-services/media/rsql-e2e-psscriptresults.PNG "After completion of PowerShell script")  
  
5.  PowerShell コンソールで、コマンド `ls` を実行すると、*DestDir*にダウンロードされたファイルの一覧が表示されます。  ファイルの一覧と説明については、「[ダウンロードの内容](#What-the-Download-Includes)」を参照してください。
  
## <a name="2-install-required-packages"></a>2.必要なパッケージをインストールする  
このチュートリアルでは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の部分で既定ではインストールされない R ライブラリがいくつか必要です。 これらのパッケージは、ソリューションを開発するクライアントと、ソリューションを展開する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターの両方にインストールする必要があります。  
  
### <a name="install-required-packages-on-the-client"></a>必要なパッケージをクライアントにインストールする  
ダウンロードした R スクリプトには、これらのパッケージをダウンロードおよびインストールするコマンドが含まれています。  
  
1.  R 環境で RSQL_R_Walkthrough.R というスクリプト ファイルを開きます。  
  
2.  次の行を選択して実行します。  
  
    ```  
    # Install required R libraries for this walkthrough if they are not installed.   
  
    if (!('ggmap' %in% rownames(installed.packages()))){  
      install.packages('ggmap')  
    }  
    if (!('mapproj' %in% rownames(installed.packages()))){  
      install.packages('mapproj')  
    }  
    if (!('ROCR' %in% rownames(installed.packages()))){  
      install.packages('ROCR')  
    }  
    if (!('RODBC' %in% rownames(installed.packages()))){  
      install.packages('RODBC')  
    }  
    ```  
  
### <a name="install-required-packages-on-the-server"></a>必要なパッケージをサーバーにインストールする  

  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで、管理者権限で RGui.exe を開きます。  既定値を使用して SQL Server R Services をインストールした場合、RGui.exe は C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64) にあります。  
  
    または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに別の R 環境 (RStudio など) をインストールした場合、R コンソールを使用してコマンドを実行できます。  
  
2.  R プロンプトで、次の R コマンドを実行します。  
  
    ```  
    install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])  
    install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    ```  
  
**注**:  
  
-   この例では、R grep 関数を使用して、使用できるパスのベクトルを検索し、"Program Files" 内のパッケージを見つけます。 詳細については、 [http://www.rdocumentation.org/packages/base/functions/grep](http://www.rdocumentation.org/packages/base/functions/grep)を参照してください。   
  
-   パッケージが既にインストールされている場合は、R 関数 `installed.packages()` を使用してインストール済みパッケージの一覧を確認します。  
  
-   クライアントで、Program Files のメイン ライブラリに出力できない場合は、ユーザー ライブラリにインストールできます。 ただし、パッケージを SQL Server コンピューターにインストールする場合、SQL Server R Services に使用される既定のライブラリにインストールする必要があります。 ユーザー ライブラリは使用しないでください。 詳細については、「[Installing New R Packages on SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)」(SQL Server に新しい R パッケージをインストールする) を参照してください。
      

## <a name="3-run-powershell-script-runsqlrwalkthroughps1"></a>3.PowerShell スクリプト RunSQL_R_Walkthrough.ps1 を実行する  

この PowerShell スクリプトは、ソリューションを構築するコンピューター (たとえば、R コードを開発およびテストするコンピューター) で実行できます。 このコンピューターは、名前付きパイプ プロトコルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに接続できる必要があります。  
  
このスクリプトで、次のアクションが実行されます。  
  
-   SQL ネイティブ クライアントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用コマンドライン ユーティリティがインストールされているかどうかを確認します。 このコマンドライン ツールは、 [bcp ユーティリティ](../../tools/bcp-utility.md)を実行するために必要です。bcp ユーティリティは、データを SQL テーブルに高速一括読み込みする際に使用します。    
-   指定したインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、データベースを構成し、モデルとデータのテーブルを作成する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをいくつか実行します。    
-   いくつかのストアド プロシージャを作成する SQL スクリプトを実行します。    
-   以前にダウンロードしたデータを nyctaxi_sample テーブルに読み込みます。    
-   R スクリプト ファイルの引数を、指定したデータベース名を使用するように書き換えます。 

### <a name="to-run-the-script"></a>スクリプトを実行するには
  
1.  管理者として PowerShell コマンド ラインを開きます。    
  
2.  スクリプトをダウンロードしたフォルダーに移動し、次のようにスクリプト名を入力します。 Enter キーを押します。  
  
    ```  
    .\RunSQL_R_Walkthrough.ps1  
    ```  
  
3.  次の各パラメーターの指定が求められます。  
  
    - 作成するデータベースの名前。 
      たとえば、「**Tutorial**」、「**Taxi**」などと入力します。  
    - スクリプトを実行する資格情報。 次の 2 つの選択肢があります。
        + CREATE DATABASE 特権を持つ SQL ログイン名を入力し、次のプロンプトで SQL パスワードを入力します。
        + 名前を入力せずに Enter キーを押して自分の Windows ID を使用し、セキュリティで保護されたプロンプトに Windows パスワードを入力します。 PowerShell は、別の Windows ユーザー名の入力をサポートしていません。 

          有効なユーザーを指定できないと、スクリプトの既定で統合 Windows 認証が使用されます。  
  
    -   データベースにアップロードする csv ファイルの完全パス  
  
        このスクリプトで、ファイルがダウンロードされ、データがデータベースに自動的に読み込まれますが、その処理が失敗した場合は、常に手動でデータをアップロードできます。  
  
4.  Enter キーを押してスクリプトを実行します。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 
 問題が発生した場合は、この PowerShell スクリプトの行を例として使用して、すべての手順または任意の手順を実行します。 
 

### <a name="the-powershell-script-didnt-download-the-data"></a>PowerShell スクリプトを実行してもデータをダウンロードできない
  
手動でデータをダウンロードするには、次のリンクを右クリックし、**[対象をファイルに保存]** を選択します。  
  
[http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv](http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv)  
  
データを保存した場所のダウンロードしたデータ ファイルのパスとファイル名をメモします。 このパスは、 **bcp**を使用してテーブルにデータを読み込むときに必要になります。  
  
### <a name="i-was-unable-to-download-the-data"></a>データをダウンロードできない
サイズが大きなデータ ファイルです。 インターネット接続が比較的良好なコンピューターを使用してください。そうしないと、ダウンロードがタイムアウトする可能性があります。  

  
### <a name="could-not-connect-or-script-failed"></a>接続できない、またはスクリプトが失敗する  
  
+ インスタンス名のつづりが正しいことを確認します。 
+ 接続文字列が正しいことを確認します。    
+ ネットワークの要件によっては、インスタンス名に 1 つ以上のサブネット名を指定する必要があります。  たとえば、MYSERVER が動作しない場合は、myserver.subnet.mycompany.com を試してください。
  
### <a name="network-error-or-protocol-not-found"></a>ネットワーク エラー、またはプロトコルが見つからない  
  
+ インスタンスがリモート接続をサポートしていることを確認します。    
+ 指定した SQL ユーザーがリモートからデータベースに接続できること、インスタンスで名前付きパイプが有効であることを確認します。    
+ アカウントのアクセス許可を確認します。 指定したアカウントに、新規データベース作成とデータ アップロードのアクセス許可がない可能性があります。  

### <a name="bcp-did-not-run"></a>bcp が実行されなかった  

+ コンピューターで [bcp ユーティリティ](../../tools/bcp-utility.md)を使用できることを確認します。 PowerShell ウィンドウまたは Windows コマンド プロンプトから bcp を実行できます。
+ エラーが発生する場合、bcp ユーティリティの場所を PATH システム環境変数に追加して、やり直します。  

### <a name="the-table-schema-was-created-but-there-is-no-data-in-the-table"></a>テーブル スキーマは作成されるがテーブルにデータがない

その他のスクリプトを問題なく実行できる場合、次のようにコマンド ラインから **bcp** を呼び出して手動でテーブルにデータをアップロードできます。  


 
**SQL ログインを使用する**
    
~~~~ 
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U <SQL login> -P <password  
~~~~  
  
**Windows 認証を使用する**  

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -T 
~~~~ 
  
  
+ **in** キーワードで、データ移動の方向を指定します。  
+ **-f** 引数には、フォーマット ファイルの完全パスを指定する必要があります。 **in** オプションを使用する場合、フォーマット ファイルが必要です。
+ SQL ログインで bcp を実行する場合、**-U** 引数と **-P** 引数を使用します。
+ Windows 統合認証を使用している場合、**-T** 引数を使用します。 

  
### <a name="how-can-i-run-the-script-without-prompts"></a>プロンプトなしでスクリプトを実行するには  
  
環境に合う値を使用して、1 つのコマンド ラインですべてのパラメーターを指定できます。 
  
```  
.\RunSQL_R_Walkthrough.ps1 -server <server address> -dbname <new db name> -u <user name> -p <password> -csvfilepath <path to csv file>  
```  
  
たとえば、SQL ログインを使用してスクリプトを実行するには、次のように指定します。  
  
```  
.\RunSQL_R_Walkthrough.ps1 -server MyServer.subnet.domain.com -dbname MyDB –u SqlUserName –p SqlUsersPassword -csvfilepath C:\temp\nyctaxi1pct.csv  
```  
  
この例の内容は次のとおりです。  
  
-   *SqlUserName* の資格情報を使用して、指定したインスタンスとデータベースに接続します。  
-   *C:\temp\nyctaxi1pct.csv* ファイルからデータを取得します。  
-   *MyServer* という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの *MyDB* データベースで、*dbo.nyctaxi_sample* テーブルにデータを読み込みます。  

### <a name="the-data-loaded-but-it-contains-duplicates"></a>データは読み込まれるが重複がある

既存のテーブルがあり、スキーマが正しい場合、bcp の実行は継続されますが、既存のデータは上書きされず、データの新しいコピーが挿入されます。 その結果、データの重複が生じます。  スクリプトを実行する前に、既存のテーブルを切り詰めてください。

## <a name="what-the-download-includes"></a>ダウンロードの内容

GitHub リポジトリからファイルをダウンロードすると、内容は次のとおりです。
+ CSV 形式のデータ
+ 環境を準備する PowerShell スクリプト
+ bcp を使用してデータを SQL Server にインポートする XML フォーマット ファイル
+ 複数の T-SQL スクリプト
+ このチュートリアルを実行するために必要なすべての R コード

### <a name="training-and-scoring-data"></a>トレーニングとスコア付けのデータ  
このデータは、ニューヨーク市タクシー データ セットの代表的なサンプル データです。各乗車で支払われた乗車料金やチップなど、2013 年の 1 億 7,300 万件の乗車記録が含まれています。  このデータの元の収集方法と、完全なデータ セットの取得方法の詳細については、  
[http://chriswhong.com/open-data/foil_nyc_taxi/](http://chriswhong.com/open-data/foil_nyc_taxi/)を参照してください。  
  
データを使用しやすくするために、Microsoft データ サイエンス チームはダウンサンプリングを実行し、わずか 1% のデータを取得しました。  このデータは、Azure のパブリック BLOB ストレージ コンテナーに .CSV 形式で共有されています。 ソース データは圧縮されておらず、350 MB 未満です。  
 
### <a name="files"></a>[ファイル]

 
+ **RunSQL_R_Walkthrough.ps1** PowerShell を使用して、このスクリプトを最初に実行します。 データをデータベースに読み込む SQL スクリプトを呼び出します。  
    
+ **taxiimportfmt.xml** データをデータベースに読み込むときに、BCP ユーティリティに使用される書式定義ファイルです。
      
+ **RSQL_R_Walkthrough.R** 以降のレッスンでデータの分析とモデリングに使用されるコア R スクリプトです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データの調査、分類モデルの構築、プロットの作成に必要なすべての R コードが含まれています。   
  
### <a name="sql-scripts"></a>SQL スクリプト  
この PowerShell スクリプトでは、サーバーに対して複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトが実行されます。 次の表は、[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルの一覧です。  
  
|SQL スクリプト ファイル名|実行内容|  
|------------------------|----------------|  
|create-db-tb-upload-data.sql|データベースと 2 つのテーブルを作成します。<br /><br /> *nyctaxi_sample*: トレーニング データ (ニューヨーク市のタクシーのデータ セットの 1% サンプル) を格納するテーブルです。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。<br /><br /> *nyc_taxi_models*: トレーニングした分類モデルの保存に後で使用する空のテーブルです。|  
|PredictTipBatchMode.sql|トレーニングしたモデルを呼び出し、新しい監視のラベルを予測するストアド プロシージャを作成します。 入力パラメーターとしてクエリを指定できます。|  
|PredictTipSingleMode.sql|トレーニングした分類モデルを呼び出し、新しい監視のラベルを予測するストアド プロシージャを作成します。 新しい監視の変数は、インライン パラメーターとして渡されます。|  
|PersistModel.sql|データベースのテーブルに分類モデルのバイナリ表現を格納できるストアド プロシージャを作成します。|  
|fnCalculateDistance.sql|乗車と降車の場所間の直線距離を計算する SQL スカラー値関数を作成します。|  
|fnEngineerFeatures.sql|分類モデルをトレーニングするための機能を作成する SQL テーブル値関数を作成します。|  
  
このチュートリアルで使用されているすべての SQL クエリはテスト済みで、そのまま R コードで実行できます。 ただし、さらに実験を進める場合や、SQL クエリを使用して独自のソリューションを開発する場合は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] などの開発環境を使用してクエリのテストと調整を行ってから、R コードに追加することをお勧めします。  
  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2: データの表示と調査 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>前のレッスン  
[データ サイエンスのエンド ツー エンド チュートリアル](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
  
  
