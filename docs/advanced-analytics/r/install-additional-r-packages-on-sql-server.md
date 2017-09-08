---
title: "SQL Server に追加の R パッケージをインストールする | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: adc0e5fc229547632759c5702e98d87f4b71cbb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="install-additional-r-packages-on-sql-server"></a>SQL Server に追加の R パッケージをインストールする
このトピックでは、インターネットにアクセスできるコンピューターで、新しい R パッケージを [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] インスタンスにインストールする方法について説明します。

## <a name="1-locate-the-windows-binaries-in-zip-file-format"></a>1.ZIP ファイル形式の Windows バイナリを見つける

R パッケージは、多くのプラットフォームでサポートされます。 インストールするパッケージが Windows プラットフォーム向けのバイナリ形式であることを確認する必要があります。 それ以外の場合、ダウンロードしたパッケージは機能しません。

たとえば、 [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) パッケージを Bioconductor から取得する場合は次の手順に従います。  
  
1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。  
  
2.  ZIP ファイルへのリンクを右クリックし、  **[対象をファイルに保存]**を選択します。  
  
3.  ZIP 形式のパッケージを格納するローカル フォルダーに移動して、 **[保存]**をクリックします。  
  
 このプロセスにより、パッケージのローカル コピーが作成されます。 その後、パッケージをインストールするか、ZIP 形式のパッケージをインターネットにアクセスしないサーバーにコピーできます。  
  
  
## <a name="2-open-the-default-r-package-library-for-sql-server-r-services"></a>2.SQL Server R Services の既定の R パッケージ ライブラリを開く 

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] が関連付けられている R パッケージがインストールされているサーバー上のフォルダーに移動します。 パッケージは、現在のインスタンスに関連付けられている既定のライブラリにインストールすることが重要です。 

このライブラリを検索する方法については、「[Installing and Managing R Packages](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)」 (R パッケージのインストールと管理) を参照してください。

   パッケージを実行するインスタンスごとに、パッケージの別のコピーをインストールする必要があります。 現時点では、インスタンス間でパッケージを共有することはできません。
     
  
## <a name="3-open-an-administrative-command-prompt"></a>3.管理コマンド プロンプトを開く 

管理者として R を開きます。  これは、Windows のコマンド プロンプトを使用するか、いずれかの R ユーティリティを使用して行うことができます。
  
### <a name="using-the-windows-command-prompt"></a>Windows コマンド プロンプトを使用する 

1. 管理者として Windows コマンド プロンプトを開き、RTerm.Exe または RGui.exe ファイルが格納されているディレクトリに移動します。  
  
    既定のインストールでは、R **\bin** ディレクトリとなります。 たとえば、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、R ツールは次の場所に配置されます。 

    **既定のインスタンス**

     `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` 
 
     **名前付きインスタンス**
   
     `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
2. **R.Exe**を実行します。  
  
### <a name="using-the-r-command-line-utilities"></a>R コマンドライン ユーティリティを使用する 
  
1. Windows エクスプローラーを使用して、R ツールが格納されているディレクトリに移動します。  
  
2. **RGui.exe** または **R.exe** を右クリックし、**[管理者として実行]** をクリックします。  
## <a name="4-install-the-package"></a>4.パッケージをインストールする

パッケージをインストールするための R コマンドは、パッケージをインターネットから取得するか、ローカルの ZIP 形式のファイルから取得するかによって異なります。  
  
### <a name="install-package-from-internet"></a>インターネットからパッケージをインストールする  
  
1.  一般に、CRAN またはいずれかのミラー サイトから新しいパッケージをインストールするには、次のコマンドを使用します。  
  
    ```  
    install.packages("target_package_name")  
    ```
    
    パッケージ名は必ず二重引用符で囲む必要があります。

2.  パッケージがインストールされるライブラリを指定するために、次のようなコマンドを使用してライブラリの場所を設定します。
    
    ```  
    lib.SQL <- "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\R_SERVICES\\library"    
    ```

    [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、現在 1 つのパッケージ ライブラリのみを使用できることに注意してください。 ユーザー ライブラリにパッケージをインストールしないでください。これを行った場合、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] からパッケージを実行できなくなります。   
     
3.  ライブラリの場所が定義されていると、次のステートメントは、人気のある e1070 パッケージを、R Services で使用されるパッケージ ライブラリにインストールします。  
  
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
  
### <a name="manual-package-installation-or-installing-on-computer-with-no-internet-access"></a>パッケージの手動のインストール、またはインターネットにアクセスしないコンピューターへのインストール 

1. インストールするパッケージに依存関係がある場合は、必要なパッケージを前もって取得しておき、他のパッケージの ZIP 形式のファイルと一緒にフォルダーに追加します。

    > [!TIP]
    > 
    > R パッケージの頻繁なオフライン インストールをサポートする必要がある場合は、[miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) を使用してローカル リポジトリを設定することをお勧めします。  
  
2.  R コマンド プロンプトで、次のコマンドを入力し、インストールするパッケージのパスと名前を指定します。  
   
    ```  
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)  
    ``` 
     
    このコマンドはローカルの ZIP 形式のファイルから R パッケージを抽出し (ディレクトリ `C:\Temp\Downloaded packages`にコピーが保存されていると仮定した場合)、ローカル コンピューター上の R ライブラリにパッケージ (および依存関係にあるもの) をインストールします。  
  
3.  これまでにコンピューター上の R 環境を変更したことがある場合は、R 環境変数 `.libPath` が、1 つのパスだけを使用していることを確認する必要があります。それはインスタンスの R_SERVICES フォルダーを参照しています。  
  
> [!NOTE]
> SQL Server R Services に加え、Microsoft R Server (スタンドアロン) もインストールする場合、コンピューターには、すべての R ツールとライブラリが付属する R の別のインストールが用意されます。 R_SERVER ライブラリにインストールされるパッケージは、Microsoft R Server のみが使用し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はアクセスできません。  
> 
>  SQL Server で使用するパッケージをインストールするときは、常に R_SERVICES ライブラリを使用してください。

  
## <a name="see-also"></a>参照  
 [SQL Server R Services &#40;データベース内&#41; をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  

