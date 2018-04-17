---
title: MiniCRAN (SQL Server の Machine Learning) を使用してローカルの R パッケージ リポジトリを作成 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4ce6479c0e7087e63271811abb47a2174747638e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>MiniCRAN を使用してローカルの R パッケージ リポジトリを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) Andre de Vries これらの一般的なシナリオをサポートするために、パッケージが作成されました。 

+ パッケージの依存関係の 1 つのパッケージまたはパッケージのセットを分析します。
+ インターネットにアクセスせず、サーバーにインストールするための一連の R パッケージを準備しています。

ユーザーが、必要なパッケージのセットを指定し、miniCRAN を再帰的にはこれらのパッケージの依存関係ツリー読み込みます CRAN または類似のリポジトリからのみ表示されているパッケージとその依存関係をダウンロードします。

出力として miniCRAN は、選択したパッケージと必要なすべての依存関係で構成される内部に矛盾のリポジトリを作成します。 このローカル リポジトリをサーバーに移動し、インターネットを使用せず、パッケージのインストールを続行できます。

経験豊富な R ユーザーは、多くの場合、ダウンロードしたパッケージの DESCRIPTION ファイル内の依存パッケージの一覧を探します。 ただし、パッケージに記載**Imports**第 2 レベルの依存関係のある可能性があります。 このため、ことをお勧めの使用、 **miniCRAN**メソッドです。

## <a name="what-is-a-package-repository"></a>パッケージ リポジトリとは

ローカル パッケージ リポジトリを作成する目的は、インターネット アクセスが許可されていないサーバーに新しい R パッケージをインストールするサーバーの管理者または組織内の他のユーザーが使用できる 1 つの場所を提供します。 リポジトリを作成した後に、新しいパッケージを追加または既存のパッケージのバージョンのアップグレードによって変更できます。

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html)によって R が書き込まれた用パッケージ[Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)は一貫性のある、作成を容易にできるように、組織用の R パッケージのセットを管理します。 

パッケージのリポジトリには、これらのシナリオがあります。

- **セキュリティ**: からダウンロードおよびインストールでは、R パッケージを新しい CRAN またはそのミラー サイトのいずれかに慣れている多くの R ユーザー。 ただし、セキュリティの理由により、実稼働サーバーが実行されている[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]通常、インターネット接続はありません。

- **オフライン インストールを簡単に**: パッケージをインストールするサーバーがオフラインにする必要がありますダウンロードすることもすべてのパッケージの依存関係を使用する miniCRAN 簡単に正しい形式ですべての依存関係を取得します。

    MiniCRAN を使用するをインストールするパッケージを準備する際に、パッケージの依存関係のエラーを回避できます、[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)ステートメントです。

- **バージョン管理の改善**: マルチ ユーザー環境では、サーバー上の複数のパッケージ バージョンの無制限のインストールを回避する理由。 ローカル リポジトリを使用すると、アナリストが使用するパッケージの一貫性のあるセットを提供できます。 

> [!TIP]
> また、Azure Machine Learning で使用するためのパッケージを準備するのに miniCRAN を使用することができます。 詳細については、このブログを参照してください: [Michele Usuelli での Azure ML で miniCRAN の使用](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>MiniCRAN を使用してパッケージを準備します。

**MiniCRAN**パッケージ自体が他の 18 の CRAN パッケージを依存である間、 **RCurl**システムの依存関係のあるパッケージで、 **curl devel**パッケージです。 同様に、パッケージ**XML**に依存している**libxml2 devel**です。 

これらすべての依存関係を簡単に満たすことができるように、これらの理由から、ローカル リポジトリ フル インターネットにアクセスできる、コンピューターで、最初にビルドを勧めします。 

リポジトリが作成された後は、別の場所にリポジトリを行うことができます。

### <a name="step-1-install-the-minicran-package"></a>手順 1. MiniCRAN パッケージをインストールします。

作成することで開始する、 **miniCRAN**をソースとして使用するリポジトリです。 インターネットにアクセスできるコンピューターでこのリポジトリを作成する必要があります。

1. インストール、 **miniCRAN**パッケージと、必要な**igraph**パッケージです。 パッケージが既にインストールされているかどうか、この例が確認されますが、if をバイパスできますステートメントと、パッケージを直接インストールします。

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") 
    if(!require("igraph")) install.packages("igraph") 
    library("miniCRAN")
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>手順 2. パッケージ ソースの定義: CRAN ミラー、または MRAN スナップショット

1. パッケージの取得中に使用するミラー サイトを指定します。 たとえば、お住まいの地域を必要なパッケージを含む MRAN サイト、またはその他のサイトを使用する可能性があります。 ダウンロードに失敗した場合は、別のミラー サイトを再試行してください。

    ```R
    CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
    CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
    ```

2. 収集されたパッケージを格納するローカル フォルダーの名前を入力します。 

    事前にフォルダーを作成することを確認します。 場合、エラーが発生、`local_repo`フォルダーでは、後で、R コードを実行するときに存在しません。

    フォルダーには、わかりやすい名前が必要です。 ここで"miniCRAN"を使用しましたが、"miniCRANZooPackages"または"miniCRANMyRPackagev2"などのわかりやすい名前を使用する場合は、この手順を繰り返します多くの場合、おそらく必要があります。

    ```R
    local_repo <- "~/miniCRAN"
    ```

    ティルダ拡張演算子を返しますと同じ結果を含む環境変数、`Sys.getenv("R_USER")`です。

### <a name="step-3-add-packages-to-the-repository"></a>手順 3. パッケージをリポジトリに追加します。

1. 後に**miniCRAN**はその他のパッケージをダウンロードするを指定するリストを作成する、インストールされています。

    **いない**この最初のリストに依存関係を追加します。 **Igraph**によって使用されるパッケージ**miniCRAN**依存関係の一覧が生成されます。 生成された依存関係グラフを使用する方法の詳細については、次を参照してください。 [miniCRAN を使用して、パッケージの依存関係を識別する](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html)です。

    次の R スクリプトでは、"zoo"と「予測」変数には、ターゲットのパッケージを追加します。

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. にないために必要な依存関係グラフにプロットすることがわかりやすくことができます。
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. ローカル リポジトリを作成します。 必要に応じて、R バージョンを変更してください。

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

    この情報から miniCRAN パッケージにパッケージをコピーする必要のあるフォルダー構造を作成、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]以降。

4. この時点で、パッケージを含むフォルダーがある必要があり、その他のパッケージが必要です。

    MiniCRAN リポジトリに格納されているパッケージを一覧表示するには、次のコードを実行することができます。

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
    head(pdb);
    pdb$Package;
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>手順 4. リポジトリを使用してインスタンス ライブラリに R パッケージを追加するには

リポジトリを作成し、必要なパッケージを追加した後、サーバー コンピューターにパッケージ リポジトリを移動、R パッケージが SQL Server で使用するため、適切なライブラリでインストールされていることを確認してください。

次の手順では、R ツールを使用してパッケージをインストールする方法について説明します。

1. パッケージをインストールするサーバーをそのままで、miniCRAN リポジトリを含むフォルダーにコピーします。 フォルダーがこの構造体が通常: miniCRAN ルート > bin]->-> [windows contrib]-> [いいえバージョン]-> [すべてのパッケージ]-> [です。

2. インスタンスに関連付けられた R ツールを使用して、R コマンド プロンプトを開きます。

    - SQL Server 2017、既定のフォルダーは`C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`します。

    - SQL Server 2016 では、既定のフォルダーは `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library` です。

    - 名前付きインスタンスの場合は、既定のパスはなどになります:`<instance_path>.RTEST/R_SERVICES/library`です。

    -  SQL Server を別のドライブにインストールしていたり、インストール パスにその他の変更を加えたりしている場合は、それらの変更もパスに反映するようにします。

3. インスタンス ライブラリのパスを取得し、ライブラリ パスの一覧に追加します。

    ```R
    .libPaths()[1];
    lib <- .libPaths()[1]
    ```

    このコマンドで SQL Server などのインスタンスに関連付けられているライブラリのパスを返す必要があります:"c:/program ファイルまたは Microsoft SQL Server/MSSQL14 です。MSSQLSERVER/R_SERVICES/ライブラリ"

4. コピー先サーバーに新しい場所を指定、 **miniCRAN**リポジトリとして`server_repo`です。

    この例では、リポジトリは、サーバー上の一時フォルダーにコピーした想定しています。

    ```R
    source_repo <- "C:\\temp\\miniCRAN"
    ```

5. サーバー上の新しい R ワークスペースを使用しているためにをインストールするパッケージの一覧も提供する必要があります。

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6. MiniCRAN リポジトリのローカル コピーへのパスを提供する、パッケージをインストールします。

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath;(source_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE);
    ```

7. インスタンス ライブラリからは、次のようなコマンドを使用してインストールされているパッケージを表示できます。

    ```R
    installed.packages()
    ```

> [!NOTE] 
> パッケージを使用して、SQL Server で、インスタンスによって使用される既定のライブラリにパッケージをインストールする必要があります。 

## <a name="manually-install-a-single-package-from-a-zipped-file"></a>Zip ファイルから 1 つのパッケージを手動でインストールします。

依存関係を持たない 1 つのパッケージをインストールする場合または使用できない場合**miniCRAN**、する必要がありますパッケージを手動でダウンロードできます。 これを行うには、管理者またはサーバーの唯一の所有者をしている必要があります。

パッケージをダウンロードした後は、zip 形式のファイルの場所から R パッケージをインストールします。

1. Zip 形式のファイルとしてパッケージをダウンロードし、ローカル フォルダーに保存

2. そのフォルダーにコピー、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]コンピューター。

3. 従来の R コマンドを使用して、SQL Server インスタンスのライブラリに、パッケージをインストールします。 パッケージが既にインストールされていない依存関係を持つ、それらを含めていなかった場合は、インストールが失敗する可能性があります。 

使用して、SQL Server 2017 のインスタンスに個々 のパッケージをアップロードすることも、[外部ライブラリの作成ステートメント](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。 このプロセスでは、管理アクセス権も必要です。
