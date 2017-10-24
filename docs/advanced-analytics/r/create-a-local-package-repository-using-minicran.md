---
title: "MiniCRAN を使用して、ローカルのパッケージ リポジトリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 1dd7e8f1a0054818849b3b9672a5df6286bdabce
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="create-a-local-package-repository-using-minicran"></a>MiniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。

R パッケージを準備するにはインターネットにアクセスできないサーバーへのインストールの 2 つの方法はあります。

-   [1 つのローカル リポジトリを作成する miniCRAN パッケージを使用します。](#bkmk_miniCRAN)

    [MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) CRAN のようなリポジトリから選択したパッケージから成る内部に矛盾のリポジトリを作成します。 ユーザーが、必要なパッケージのセットを指定し、miniCRAN を再帰的にはこれらのパッケージの依存関係ツリー読み込みますのみリストされているパッケージとその依存関係をダウンロードします。

    このローカル リポジトリをサーバーに移動し、インターネットを使用せず、パッケージのインストールを続行できます。

-   [手動でダウンロードして、1 つずつのパッケージをコピー](#bkmk_manual)

この記事は、両方の方法を使用して、R パッケージ リポジトリを作成する方法について説明し、使用をお勧め、 **miniCRAN**パッケージです。

## <a name="prepare-packages-using-minicran"></a>MiniCRAN を使用してパッケージを準備します。

ローカル パッケージ リポジトリを作成する目的は、インターネット アクセスが許可されていないサーバーに新しい R パッケージをインストールするサーバーの管理者または組織内の他のユーザーが使用できる 1 つの場所を提供します。

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html)によって R が書き込まれた用パッケージ[Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)は一貫性のある、作成を容易にできるように、組織用の R パッケージのセットを管理します。 

MiniCRAN を使用してリポジトリを作成する多くの利点があります。

-   **セキュリティ**: からダウンロードおよびインストールでは、R パッケージを新しい CRAN またはそのミラー サイトのいずれかに慣れている多くの R ユーザー。 ただし、セキュリティの理由により、実稼働サーバーが実行されている[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]通常、インターネット接続はありません。

-   **オフライン インストールを簡単に**: パッケージをインストールするサーバーがオフラインにする必要がありますダウンロードすることもすべてのパッケージの依存関係を使用する miniCRAN 簡単に正しい形式ですべての依存関係を取得します。

-   **バージョン管理の改善**: マルチ ユーザー環境では、サーバー上の複数のパッケージ バージョンの無制限のインストールを回避する理由。

リポジトリを作成した後に、新しいパッケージを追加または既存のパッケージのバージョンのアップグレードによって変更できます。

### <a name="step-1-install-the-minicran-package"></a>手順 1. MiniCRAN パッケージをインストールします。

まず、ソースとして使用する miniCRAN リポジトリを作成します。 インターネットにアクセスできるコンピューターでこのリポジトリを作成する必要があります。

1.  MiniCRAN パッケージと、必要なインストール**igraph**パッケージです。

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>手順 2. パッケージ ソースの定義: CRAN ミラー、または MRAN スナップショット

1. パッケージの取得中に使用するミラー サイトを指定します。

    ```R
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
    ```

2.  収集されたパッケージを格納するローカル フォルダーを指定します。 フォルダー miniCRAN; 名前を付ける必要はありません。"GeneticsPackages"または"ClientRPackages1.0.2"のようなわかりやすい名前がある可能性があります。

    フォルダーを事前に作成することを確認するだけです。 場合、エラーが発生、`local_repo`フォルダーでは、後で、R コードを実行するときに存在しません。

    ```R
    local_repo <- "~/miniCRAN"
    ```

    ティルダ拡張演算子を返しますと同じ結果を含む環境変数、`Sys.getenv("R_USER")`です。

### <a name="step-3-add-packages-to-the-repository"></a>手順 3. パッケージをリポジトリに追加します。

1.  MiniCRAN をインストールした後は、その他のパッケージをダウンロードするを指定するリストを作成します。

    この初期の一覧には依存関係を追加しないでください。**igraph** miniCRAN によって使用されるパッケージの依存関係の一覧が生成されます。 このグラフを使用する方法の詳細については、次を参照してください。 [miniCRAN を使用して、パッケージの依存関係を識別する](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html)です。

    次の R スクリプトでは、対象パッケージ、"zoo"および「予測」を取得する方法を示します。

    ```R
    pkgs_needed <- c("zoo", "forecast")

2. Optionally, plot the dependency graph, which can be informative and looks cool.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. ローカル リポジトリを作成します。 必要に応じて、R バージョンを変更してください。

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror)
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3")
    ```

    この情報から miniCRAN パッケージにパッケージをコピーする必要のあるフォルダー構造を作成、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]以降。

4. この時点で、パッケージを含むフォルダーがある必要があり、その他のパッケージが必要です。

    MiniCRAN リポジトリに格納されているパッケージを一覧表示するには、次のコードを実行することができます。

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE)
    head(pdb)
    pdb$Package
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>手順 4. リポジトリを使用してインスタンス ライブラリに R パッケージを追加するには

リポジトリを作成し、必要なパッケージを追加した後、サーバー コンピューターにパッケージ リポジトリを移動、R パッケージが SQL Server で使用するため、適切なライブラリでインストールされていることを確認してください。

SQL Server のバージョンによっては、SQL Server インスタンスに関連付けられた R ライブラリに新しいパッケージを追加するための 2 つのオプションがあります。

-   MiniCRAN リポジトリと R ツールを使用して、インスタンスのライブラリをインストールします。

-   SQL データベースにパッケージをアップロードし、外部ライブラリの作成ステートメントを使用して、データベースごとにパッケージをインストールします。 参照してください[SQL Server に追加の R パッケージをインストール](install-additional-r-packages-on-sql-server.md)です。

次の手順では、R ツールを使用してパッケージをインストールする方法について説明します。

1.  パッケージをインストールするサーバーにそのままで、miniCRAN リポジトリを含むフォルダーにコピーします。

2.  インスタンスに関連付けられた R ツールを使用して、R コマンド プロンプトを開きます。

    - SQL Server 2017、既定のフォルダーは`C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`します。

    - SQL Server 2016 では、既定のフォルダーは `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library` です。

    - 名前付きインスタンスの場合は、既定のパスはなどになります:`<instance_path>.RTEST/R_SERVICES/library`です。

    -  SQL Server を別のドライブにインストールしていたり、インストール パスにその他の変更を加えたりしている場合は、それらの変更もパスに反映するようにします。

3.  (の場合はユーザー ディレクトリにしている) インスタンス ライブラリのパスを取得し、ライブラリ パスの一覧に追加します。

    ```R
    .libPaths()[1]  
    lib \<- .libPaths()[1]
    ```

    これは、"c:/program ファイルまたは Microsoft SQL Server/MSSQL14 インスタンス パスを返します。MSSQLSERVER/R_SERVICES/ライブラリ"

2.  MininCRAN のリポジトリのコピー先サーバー上の場所を指定`server_repo`です。

    この例では、リポジトリは、サーバーで、[ユーザー] フォルダーにコピーした想定しています。

    ```R
    R server_repo <- "C:\\Users\\MyUserName\\miniCRAN"
    ```

3.  サーバー上の新しい R ワークスペースを使用しているためにをインストールするパッケージの一覧も提供する必要があります。

    ```R
    tspackages <- c("zoo", "forecast")
    ```

4.  MiniCRAN リポジトリのローカル コピーへのパスを使用して、パッケージをインストールします。

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath(server_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE)
    ```

5.  インストールされているパッケージを表示するようになりました。

    ```R
    installed.packages()
    ```

> [!NOTE] 
> 
> SQL Server の 2017 で、サーバー管理者がパッケージにアクセス許可を管理するのに役立つその他のデータベース ロールと T-SQL ステートメントが提供されます。 データベース管理者は、必要な場合は、R または T-SQL では、いずれかを使用して、パッケージをインストールするタスクを所有できます。 ただし、DBA は、独自のパッケージをインストールするのに機能をユーザーに提供するのにロールを使用することができますも。 詳細については、次を参照してください。 [for SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)です。
> 
> SQL Server 2016 でサーバー管理者は、する必要がありますパッケージをインストール miniCRAN リポジトリからのインスタンスによって使用される既定のライブラリにします。 これを行うには、ツールを使用して、R での説明に従って、[上記](#bkmk_Rtools)です。

## <a name="manually-download-single-packages"></a>手動で単一のパッケージをダウンロードします。

MiniCRAN を使用しないようにする場合、必要なパッケージとその依存関係を手動でダウンロードできます。 これを行うには、管理者またはサーバーの唯一の所有者をしている必要があります。

パッケージをダウンロードした後は、zip 形式のファイルの場所から R パッケージをインストールします。

1.  パッケージの zip ファイルをダウンロードしてローカル フォルダーに保存

2.  そのフォルダーにコピー、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]コンピューター。

3.  SQL Server インスタンスのライブラリに、パッケージをインストールします。

> [!NOTE]
> R ツールを使用してパッケージをインストールするときに、全体として、インスタンスにインストールされます。 
> 
> データベースにパッケージをインストールし、パッケージをデータベース ロールを使用しているユーザーと共有する場合は、外部ライブラリの作成ステートメントを使用して、ライブラリをアップロードする必要があります。 参照してください[SQL サーバーに追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)

