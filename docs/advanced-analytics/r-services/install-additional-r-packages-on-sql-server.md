---
title: "SQL Server に追加の R パッケージをインストールする | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 16
---
# SQL Server に追加の R パッケージをインストールする
このトピックのインスタンスに新しい R パッケージをインストールする方法について説明 [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] インターネットへのアクセス権を持つコンピューターにします。

## <a name="1-locate-the-windows-binaries-in-zip-file-format"></a>1.ZIP ファイルの形式で Windows バイナリを検索します。

多くのプラットフォームでサポートされる R パッケージです。 インストールするパッケージが Windows プラットフォーム向けのバイナリ形式を持つことを確認する必要があります。 それ以外の場合、ダウンロードしたパッケージは機能しません。

たとえば、 [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) パッケージを Bioconductor から取得する場合は次の手順に従います。  
  
1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。  
  
2.  ZIP ファイルへのリンクを右クリックし、  **[対象をファイルに保存]**を選択します。  
  
3.  ZIP 形式のパッケージを格納するローカル フォルダーに移動して、 **[保存]**をクリックします。  
  
 このプロセスでは、パッケージのローカル コピーを作成します。 パッケージをインストールしたり、圧縮したパッケージをインターネット アクセスがないサーバーにコピーできます。  
  
  
## <a name="2-open-the-default-r-package-library-for-sql-server-r-services"></a>2.SQL Server の R のサービスの既定 R パッケージのライブラリを開きます 

R パッケージが関連付けられているサーバー上のフォルダーに移動 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] がインストールされています。 現在のインスタンスに関連付けられている既定のライブラリには、パッケージをインストールすることが重要です。 

このライブラリを検索する方法については、次を参照してください。 [R パッケージの管理をインストールおよび](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)です。

   パッケージを実行するインスタンスごとに、パッケージの別のコピーをインストールする必要があります。 現在のインスタンスでパッケージを共有することはできません。
     
  
## <a name="3-open-an-administrative-command-prompt"></a>3.管理コマンド プロンプトを開く 

管理者として R を開きます。  これは、Windows のコマンド p ropt を使用するか、R ユーティリティの 1 つを使用して行うことができます。
  
### <a name="using-the-windows-command-prompt"></a>Windows コマンド プロンプトを使用する 

1. 管理者は、Windows コマンド プロンプトを開き、RTerm.Exe または RGui.exe ファイルが使用されているディレクトリに移動します。  
  
    既定のインストールでは、R **\bin** ディレクトリとなります。 たとえば、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], 、R のツールが表示されます。 

    **既定のインスタンス**

     `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` 
 
     **名前付きインスタンス**
   
     `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
2. **R.Exe**を実行します。  
  
### <a name="using-the-r-commandline-utilities"></a>R コマンドライン ユーティリティを使用する 
  
1. Windows エクスプ ローラーを使用して、R ツールが格納されているディレクトリに移動します。  
  
2. 右クリック **RGui.exe** または **RTerm.exe**, を選択して **管理者として実行**します。  
## <a name="4-install-the-package"></a>4.パッケージをインストールします。

パッケージをインストールする R コマンドは、インターネットやローカル zip ファイルからパッケージを取得するかどうかによって異なります。  
  
### <a name="install-package-from-internet"></a>インターネットからパッケージをインストールします。  
  
1.  一般に、次のコマンドを使用して、CRAN または 1 つのミラー サイトから新しいパッケージをインストールします。  
  
    ```  
    install.packages("target_package_name")  
    ```
    
    パッケージ名は必ず二重引用符で囲む必要があります。

2.  パッケージのインストールされているライブラリを指定するには、ライブラリの場所を設定するのに次のようなコマンドを使用します。
    
    ```  
    lib.SQL <- "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\R_SERVICES\\library"    
    ```

    注意してください [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、現在 1 つのパッケージのライブラリを使用します。 ユーザーのライブラリにパッケージをインストールしないまたはからパッケージを実行することができなく [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。   
     
3.  ライブラリの場所を定義したら、次のステートメントは、R のサービスで使用されるパッケージ ライブラリに人気のある e1070 パッケージをインストールします。  
  
    ```  
    install.packages("e1071", lib = lib.SQL)  
    ```  
  
4.  パッケージの取得元のミラー サイトを指定するよう求められます。 現在の場所から便利なミラー サイトを選択します。  
  
    現在の CRAN ミラー サイトの一覧については、 [こちら](https://cran.r-project.org/mirrors.html)を参照してください。  
  
    > [!TIP]  
    >  新しいパッケージを追加するたびにミラー サイトを選択しなくても済むように、常に同じリポジトリが使用されるように R 開発環境を構成することができます。  
    >   
    >  これを行うには、グローバル R 設定ファイル (.Rprofile) を編集して、次の行を追加します。  
    >   
    >  `options(repos=structure(c(CRAN="<mirror site URL>")))`  
    >   
    >  R ランタイムの開始時に読み込まれる基本設定およびその他のファイルの詳細については、R コンソールから次のコマンドを実行してください。  
    >   
    >  `?Startup`  
  
5.  目的のパッケージがその他のパッケージに依存している場合、R インストーラーは依存関係にあるパッケージを自動的にダウンロードしてインストールします。  
  
### <a name="manual-package-installation-or-installing-on-computer-with-no-internet-access"></a>手動のパッケージのインストール、またはインターネットにアクセスできないコンピューターにインストールします。 

1. インストールするパッケージに依存関係がある場合は、前もって必要なパッケージを取得し、他のパッケージの圧縮されたファイルとフォルダーに追加します。

    > [!TIP]
    > 
    > 使用して、ローカル リポジトリを設定することをお勧め [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) R パッケージの頻繁なオフライン インストールをサポートする必要がある場合。  
  
2.  R コマンド プロンプトで、次のコマンドを入力し、インストールするパッケージのパスと名前を指定します。  
   
    ```  
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)  
    ``` 
     
    このコマンドは、ディレクトリにコピーを保存すると仮定した場合、ローカル zip ファイルから、R パッケージを抽出 `C:\Temp\Downloaded packages`, とに、ローカル コンピューター上の R ライブラリ (その依存関係) のパッケージをインストールします。  
  
3.  以前のコンピューター上の R 環境を変更した場合はことを確認する R 環境変数 `.libPath` は、インスタンスの R_SERVICES フォルダーを参照する 1 つのパスを使用します。  
  
> [!NOTE]
> SQL Server の R のサービスだけでなく Microsoft R サーバー (スタンドアロン) をインストールしている場合、コンピューターはすべての R のツールとライブラリと R の別のインストールにがあります。 R_SERVER ライブラリにインストールされているパッケージは、Microsoft R サーバーでのみ使用されがアクセスできない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
> 
>  SQL Server で使用するパッケージをインストールするときに、R_SERVICES ライブラリを使用することを確認します。

  
## <a name="see-also"></a>参照  
 [SQL Server R Services #40; データベースに &#41; の設定します。](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  