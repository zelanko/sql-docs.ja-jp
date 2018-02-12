---
title: "SQL Server に追加の R パッケージをインストール |Microsoft ドキュメント"
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 530745918dfd4808694b401be55e40bac00f3cce
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="install-additional-r-packages-on-sql-server"></a>SQL Server に追加の R パッケージをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。

**適用対象:** 
+ [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]  [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]
+ [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="prerequisites"></a>前提条件

+ Windows のバージョンのパッケージがあるかどうかを判断します[適切なパッケージのバージョンと形式を取得する。](#packageVersion)

+ サーバーがインターネットにアクセスできる、Windows バイナリを事前にダウンロードする必要があります: [zip ファイルのダウンロード](#bkmk_zipPreparation)

+ パッケージの依存関係を識別します。 

    - 依存関係について心配する必要はありません、サーバーにインターネットへのアクセスがある場合は、すべての必要なパッケージを自動的にインストールすることができます。

    - 場合、サーバーは**いない**インターネットへのアクセス、すべての依存関係を特定し、zip 形式で、事前に必要なパッケージをダウンロードする必要があります。 これを行う簡単な方法は使用する[miniCRAN](create-a-local-package-repository-using-minicran.md)をすべての依存関係パッケージのコレクションを準備します。 このリポジトリは、サーバー コンピューターにコピーできます。

+ パッケージの互換性を確認します。 パッケージは、SQL Server で実行されている R のバージョンと互換性があります。

    また、パッケージ (または必要なすべてのパッケージ) が SQL Server やポリシーによってブロックされる機能に含まれるかどうかを確認してください。 たとえば、特定のパッケージは、セキュリティを強化した SQL Server 環境で不適切な適合です。 こうしたパッケージには、Java、または通常は SQL Server 環境の場合、または管理者特権でのファイル システム アクセスが必要なパッケージで使用されるその他のフレームワークを使用して、ネットワークにアクセスするパッケージが含まれる可能性があります。

+ 権限

    SQL Server を実行しているコンピューターへの管理アクセスが必要です。

    さらに、SQL Server で実行するには、パッケージを現在のインスタンスに関連付けられている既定のライブラリでインストールする必要があります。 既定のライブラリを検索する方法については、次を参照してください。 [SQL Server と共にインストールされている R パッケージ](installing-and-managing-r-packages.md)です。
    
    経験の R ユーザーの場合は、特別なアクセス許可がないか、ダウンロードしておかなくても事前に、コマンドラインからパッケージをインストールすることに慣れてする必要があります。 ただし、このメソッドは、SQL Server では機能しません。 多くの場合の SQL Server コンピューターにインターネット接続はありません。 サーバーのファイルへのアクセスをさらに、または外部の記憶域が制限されている可能性があります。 SQL Server での R ジョブ runnign によってユーザー ライブラリにインストールされているパッケージにアクセスできません。 

    SQL Server コンピュータに管理アクセス権を持っていない場合は、データベース管理者は、パッケージのインストールに関するヘルプを検索します。

+ パッケージを使用する必要がある各インスタンスに対して個別にインストールを実行します。

     パッケージは、インスタンス間で共有することはできません。 個別のインスタンス、パッケージのインストールに同じ zip 形式のファイル ソースを使用できますが、パッケージの個別のコピーが各インスタンスのライブラリに追加します。

## <a name="install-packages"></a>パッケージをインストールします。

このセクションでは、次のシナリオでパッケージのインストール手順を示します。

+ [インターネットにアクセスできるサーバーに新しいパッケージをインストールします。](#bkmk_rInstall)
+ [サーバーでパッケージのオフライン インストールの実行**ありません**インターネットへのアクセス](#bkmk_offlineInstall)
+ [RevoScaleR を使用した SQL Server のコンピューティング コンテキストにパッケージをインストールします。](#bkmk_rAddPackage)
+ [外部ライブラリの作成ステートメントを使用してパッケージをインストールする](#bkmk_createlibrary)(SQL Server 2017 のみですその他の制限を適用)。

### <a name="bkmk_rInstall"></a>R ツールを使用してオンラインのインストール

標準の R ツールを使用すると、SQL Server 2016 または SQL Server 2017 のインスタンスに新しいパッケージをインストールします。 ただし、これを行う管理者をする必要があります。

1.  インスタンスは、R ライブラリがインストールされているサーバー上のフォルダーに移動します。

    > [!IMPORTANT] 
    > 現在のインスタンスに関連付けられている既定のライブラリにパッケージをインストールすることを確認します。 ユーザーのディレクトリにパッケージをインストールことはありません。

    必要なアクセス許可がない、データベース管理者に連絡し、必要なパッケージの一覧を指定します。

2.  R コマンド プロンプトを管理者として開きます。

    たとえば、Windows のコマンド プロンプトを使用している場合は、RTerm.Exe または RGui.exe が配置されているディレクトリに移動します。 

    **[既定のインスタンス]**

    SQL Server 2017: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **[名前付きインスタンス]**

    SQL Server 2017: `C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

    機械学習のコンポーネントをアップグレードするバインディングを使用している場合、パスを変更した可能性があります。 常に新しいパッケージをインストールする前に、インスタンス パスを確認します。 

3.  R コマンドを実行`install.packages`パッケージをインストールします。 たとえば、次のステートメントは、人気のある e1071 パッケージをインストールします。 

    ```R
    install.packages("e1071", lib = lib.SQL)
    ```

    二重引用符は、パッケージ名の必要があります。

4. ミラー サイトを求められたら、現在の場所は便利では任意のサイトを選択します。

5. ターゲットのパッケージは、その他のパッケージに依存している場合、R インストーラーは自動的に依存関係をダウンロードして、インストールします。

> [!IMPORTANT]
> パッケージを使用する必要がある各インスタンスに対して個別にインストールを実行します。 パッケージは、インスタンス間で共有することはできません。

### <a name = "bkmk_offlineInstall"></a>R ツールを使用してオフラインのインストール 

インストールするパッケージが準備の依存関係を持つかどうか**すべて**前もってパッケージが必要です。  参照してください、[インストール ヒント](#bkmk_tips)セクション パッケージの準備に関するヘルプを参照します。

> [!IMPORTANT]
>  事前に完全な依存関係を分析し、必要なすべてのパッケージをダウンロードすることを確認することが重要でしていないインターネットにアクセスできるサーバーにパッケージをインストールするたびに**する前に**インストールを開始します。 お勧め[miniCRAN](https://mran.microsoft.com/package/miniCRAN)このプロセスにします。 この R パッケージ リストを受け取り、パッケージをインストールしてなどの依存関係を分析するすべての zip ファイルを取得します。 miniCRAN は、サーバー コンピューターにコピーできる 1 つのリポジトリを作成します。
> 
> 詳細については、「 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。](create-a-local-package-repository-using-minicran.md)

1. Zip 形式のパッケージまたはリポジトリをローカルの共有、またはその他のサーバーにアクセスできる場所にコピーします。

2.  インスタンスは、R ライブラリがインストールされているサーバー上のフォルダーに移動します。

    たとえば、Windows のコマンド プロンプトを使用している場合は、RTerm.Exe または RGui.exe が配置されているディレクトリに移動します。

    **[既定のインスタンス]**

    SQL Server 2017: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **[名前付きインスタンス]**

    SQL Server 2017: `C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

3. R コマンド プロンプトを管理者として開きます。

4.  R コマンドを実行`install.packages`パッケージまたはリポジトリの名前とその zip ファイルの場所を指定します。

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    このコマンドは、R パッケージを抽出`mynewpackage`ディレクトリにコピーを保存すると仮定した場合、ローカル zip ファイルから`C:\Temp\Downloaded packages`、し、ローカル コンピューターにパッケージをインストールします。 パッケージがすべての依存関係を持つ、インストーラーは、ライブラリ内の既存のパッケージを確認します。 依存関係を含むリポジトリを作成した場合、インストーラー パッケージをインストールします requireed もします。

    場合は、必要なパッケージは、インスタンス ライブラリに存在しない、その zip ファイルに見つかりません対象パッケージのインストールは失敗します。

### <a name="bkmk_rAddPackage"></a>リモート R クライアントからサーバー上の R パッケージをインストールします。

最近のバージョンの[R サーバーまたは Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server)RevoScaleR には、SQL Server のコンピューティング コンテキストへ新しい R パッケージのインストールをサポートする関数が含まれています。 

1. 開始する前に、これらの条件を満たしていることを確認します。

    + クライアントに RevoScale 9.0.1 またはそれ以降。
    + RevoScaleR の同等のバージョンが SQL Server インスタンスにインストールされました。
    + [パッケージ管理機能は](..\r\r-package-how-to-enable-or-disable.md)がインスタンスで有効になっています。
    + 指定したインスタンスおよびによって、共有内のパッケージまたは prvate コンテキストをインストールすることができますをデータベース ロールのメンバーであります。

2. R コマンドラインからインスタンスと、データベースに接続文字列を定義し、接続文字列を使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)コンス トラクターを SQL Server のコンピューティング コンテキストを作成します。

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. インストールし、文字列変数のリストを保存するパッケージの一覧を作成します。

    ```R
    packageList <- c("e1071", "mice")
    ```

4. 呼び出す[rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages)コンピューティング コンテキストおよびパッケージ名を含む文字列変数を渡します。

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    依存パッケージが必要な場合は、インストールされている、インターネット接続があると仮定するとします。
    
    この例では、所有者およびスコープが指定されていないためパッケージがインストールされて、そのユーザーの既定のスコープで、接続を行うユーザーの資格情報を使用します。

### <a name="bkmk_createlibrary"></a>MiniCRAN リポジトリと外部ライブラリの作成を使用してパッケージをインストールするには 

SQL Server 2017 は、インストールして、T-SQL を使用して R パッケージを管理するための新機能を提供します。 ただし、このプロセスでは、ローカル インターネットからダウンロードするのではなく、ファイルを zip 形式と、パッケージが使用可能にする必要があります。 すべてのパッケージが事前に準備されていませんが、ステートメントは失敗します。

外部ライブラリの作成は、これらの条件下でサポートされます。

+ 依存関係のないを持つ 1 つのパッケージをインストールします。
+ 依存関係を持つ複数のパッケージ、またはパッケージをインストールして、すべてのパッケージを事前に準備しました。 

**手順**

1.  Zip 形式の形式でパッケージを準備するか、パッケージとその依存関係を含む miniCRAN リポジトリを作成します。  

2. Zip 形式のファイルまたはリポジトリをサーバー上のローカル フォルダーにコピーします。

     > [!IMPORTANT]
     > ソースは、対象パッケージだけでなく、関連の必要なパッケージに含まれている必要があります、指定したファイルです。

3. 管理者は、T-SQL ステートメントを実行`CREATE EXTERNAL LIBRARY`zip 形式のパッケージのコレクションをデータベースにアップロードします。

    たとえば、次のステートメントは、randomForest パッケージとその依存関係を含む miniCRAN リポジトリを参照します。 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Downloads\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    CREATE ステートメントで、任意の名前を使用することはできません外部ライブラリ名の読み込みまたはパッケージを呼び出すときに使用するものと同じ名前が必要です。

4. ストアド プロシージャ内のコードを実行して、SQL server、または使用するための複数のパッケージをインストールします。
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # install randomForest and its dependencies
    library(randomForest)'
    ```

    成功した場合、**メッセージ**「'randomForest' が正常に開梱済みのパッケージおよび MD5 の合計値をチェック」と「完了には、実行がチェーンされた」などのウィンドウでメッセージを報告する必要があります。

    インストールが失敗した場合は、すべてのパッケージには、インストールが失敗して、後続のパッケージのインストールをインストールする場合がありますも失敗し、このメッセージ。 

    "エラー rxSqlPkgInstallPackages..詳細についてはログを確認してください - パッケージのインストールに失敗しました"

## <a name="package-installation-tips-and-frequently-asked-questions-faq"></a>パッケージのインストールのヒントとよく寄せられる質問 (FAQ)

このセクションでは、さまざまなヒントと SQL Server で R パッケージのインストールに関連する一般的な質問を示します。

###  <a name="packageVersion"></a>適切なパッケージのバージョンと形式を取得します。

R パッケージの供給元は複数あります。その中でもよく知られているのは CRAN と Bioconductor です。 R 言語の公式サイト (<https://www.r-project.org/>) には、これらのリソースが多数掲載されています。 多くのパッケージは、GitHub のソース コードを取得する場所に発行されます。 ただしが提供された社内の誰かによって開発された R パッケージです。

元に関係なくをインストールするパッケージが、Windows プラットフォームのバイナリ形式を持つことを確認する必要があります。 それ以外の場合、ダウンロードしたパッケージは、SQL Server 環境で実行できません。

### <a name="bkmk_zipPreparation"></a>Zip ファイルとしてパッケージをダウンロードします。

サーバーのインストールに、インターネットにアクセスせず、オフライン インストールの zip ファイルの形式でパッケージのコピーをダウンロードする必要があります。 パッケージを解凍できません。

たとえば、次の手順は、の正しいバージョンを取得するようになりましたについて説明します。、 [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html)パッケージを Bioconductor、コンピューターがインターネットにアクセスしていると仮定してからです。

1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。

2.  リンクを右クリックします。ZIP ファイル、および選択**として保存ターゲット**です。

3.  Zip 形式のパッケージが格納されているをクリックして、ローカル フォルダーに移動**保存**です。

    このプロセスにより、パッケージのローカル コピーが作成されます。 ダウンロード エラーが発生した場合は、さまざまなミラー サイトを再試行してください。

4. パッケージのアーカイブをダウンロードすると、パッケージをインストールまたは zip 形式のパッケージをインターネット アクセスが許可されていないサーバーにコピーできます。

> [!TIP]
> 場合は、誤ってバイナリをダウンロードする代わりに、パッケージをインストールすると、ダウンロードした zip ファイルのコピーがコンピューターにも保存されます。 ファイルの場所を決定するパッケージがインストールされているステータス メッセージをご覧ください。 インターネット アクセスが許可されていないサーバーには、その zip ファイルをコピーできます。
> このメソッドを使用してパッケージをダウンロードする場合は、パッケージの依存関係は含まれません。 

Zip ファイル形式と、R パッケージを作成する方法の詳細については、内容、ことをお勧めこのチュートリアルでは、R プロジェクト サイトから PDF 形式でダウンロードできます: [R パッケージを作成する](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf)です。

### <a name="bkmk_packageDependencies"></a>パッケージの依存関係を取得します。

R パッケージは、多くの場合、これらのいくつかできない可能性があります、インスタンスによって使用される既定の R ライブラリで、その他の複数のパッケージに依存します。 場合もありますパッケージには、既にインストールされている依存パッケージの別のバージョンが必要です。

使用することをお勧めを複数のパッケージをインストールまたは正しいパッケージの種類とバージョン、組織内のすべてのユーザーを取得することを確認する必要がある場合、 [miniCRAN](https://mran.microsoft.com/package/miniCRAN)パッケージを共有できるローカル リポジトリを作成するには複数のユーザーまたはコンピューター。 詳細については、次を参照してください。 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成する](create-a-local-package-repository-using-minicran.md)です。

### <a name="permissions"></a>権限

このセクションでは、さまざまなレベルの SQL Server 2016 および SQL Server 2017 でパッケージをインストールするために必要な権限について説明します。 インストールを行うことができますの R ツールまたは SQL Server を使用して、プロセスとアクセス許可が若干異なりますが、します。

-   SQL Server 2016

    このリリースでは、コンピューターの管理者のみが必要な場所にパッケージをインストールできます。 標準の R ツールを使用して、パッケージをインストールするが、管理者として実行して、インスタンスに関連付けられた R ツールを使用する必要があります。

-   SQL Server 2017

    管理アクセス権がある場合は場合、は、R ツールを使用して、インスタンス全体でパッケージをインストールできます。

    データベース所有者の場合は、接続を定義し、RxInSqlServer を使用して、インスタンスに接続する場合、リモート クライアントでは、R パッケージをインストールできます。
    
    このリリースには、今後のリリースでデータベース管理者によって R または Python のパッケージの管理をサポートするための新しい機能が含まれています。 この機能を使用して、、DBA は、によって最初インスタンスごとのパッケージの管理機能を有効にする必要があります。 この機能を有効にすると、個々 のユーザーは、データベース ロールによって、特定のデータベースにパッケージをインストールできます。 詳細については、次を参照してください。[を有効にするか、SQL Server の R パッケージの管理を無効にする](../r/r-package-how-to-enable-or-disable.md)です。

> [!IMPORTANT]
> 
> 経験豊富な R ユーザーはユーザー ライブラリで、パッケージをインストールして、ファイル パスを指定して R ソリューションの一部としてそのフォルダー内のパッケージを参照することに慣れてます。 ただし、この方法は、SQL Server ではサポートされません。 詳細と回避策については、次を参照してください。[ユーザー ライブラリでパッケージを使用する方法](packages-installed-in-user-libraries.md)です。

### <a name="establish-a-single-mirror-site-as-standard"></a>1 つのミラー サイトを標準として確立します。

新しいパッケージを追加するたびにミラー サイトを選択しなくても済むように、常に同じリポジトリが使用されるように R 開発環境を構成することができます。 これを行うには、グローバル R 設定ファイルを編集**です。Rprofile**、し、次の行を追加します。

`options(repos=structure(c(CRAN="<mirror site URL>")))`

示されている現在の CRAN ミラー[このサイト](https://cran.r-project.org/mirrors.html)です。

基本設定および R ランタイムの開始時に読み込まれるその他のファイルの詳細については、R コンソールからこのコマンドを実行します。`?Startup`

### <a name="know-which-library-you-are-using-for-installation"></a>インストールを使用しているライブラリを知る

何もインストールする前に以前、コンピューター上の R 環境を変更した場合の一時停止後、R の環境変数をことを確認して`.libPath`は 1 つのパスを使用します。

このパスは、インスタンスの R_SERVICES フォルダーを指す必要があります。 詳細については、次を参照してください。 [SQL Server と共にインストールされている R パッケージ](installing-and-managing-r-packages.md)です。

### <a name="side-by-side-installation-with-r-server"></a>R Server とサイド バイ サイド インストール

SQL Server マシン ラーニング サービスに加えて Microsoft マシン ラーニング Server (スタンドアロン) をインストールした場合、コンピューターがごとに、すべての R ツールとライブラリの重複を削除しない R の別のインストールに必要です。

> [!IMPORTANT]
> 
> R_SERVER ライブラリにインストールされているパッケージは、Microsoft R Server によってのみ使用され、SQL Server がアクセスできないされます。
> 
> 使用してください、`R_SERVICES`ライブラリ SQL Server で使用するパッケージをインストールするときにします。

### <a name="how-to-determine-which-packages-are-already-installed"></a>既にインストールされているパッケージを確認する方法ですか。

 参照してください[SQL Server と共にインストールされている R パッケージ](installing-and-managing-r-packages.md)