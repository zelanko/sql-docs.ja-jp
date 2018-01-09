---
title: "MiniCRAN を使用して、ローカルのパッケージ リポジトリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 066e09747684ede5837d93736f32792736b8985d
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-local-package-repository-using-minicran"></a>MiniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。

R パッケージを準備するにはインターネットにアクセスできないサーバーへのインストールの 2 つの方法はあります。

-   [1 つのローカル リポジトリを作成する miniCRAN パッケージを使用します。](#bkmk_miniCRAN)

    [MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) CRAN のようなリポジトリから選択したパッケージから成る内部に矛盾のリポジトリを作成します。 ユーザーが、必要なパッケージのセットを指定し、miniCRAN を再帰的にはこれらのパッケージの依存関係ツリー読み込みますのみリストされているパッケージとその依存関係をダウンロードします。

    このローカル リポジトリをサーバーに移動し、インターネットを使用せず、パッケージのインストールを続行できます。

-   [手動でダウンロードして、1 つずつのパッケージをコピー](#bkmk_manual)

    ダウンロードしたパッケージの DESCRIPTION ファイル内の依存パッケージの一覧が表示されます。 
    
    ただし、パッケージに記載**Imports**第 2 レベルの依存関係のある可能性があります。 このため、ことをお勧めの使用、 **miniCRAN**メソッドです。

> [!TIP]
> Azure Machine Learning で使用するためのパッケージを準備する miniCRAN を使用することができますをご存知でしたか。 詳細については、このブログを参照してください: [Michele Usuelli での Azure ML で miniCRAN の使用](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>MiniCRAN を使用してパッケージを準備します。

ローカル パッケージ リポジトリを作成する目的は、インターネット アクセスが許可されていないサーバーに新しい R パッケージをインストールするサーバーの管理者または組織内の他のユーザーが使用できる 1 つの場所を提供します。

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html)によって R が書き込まれた用パッケージ[Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)は一貫性のある、作成を容易にできるように、組織用の R パッケージのセットを管理します。 

MiniCRAN を使用してリポジトリを作成する多くの利点があります。

-   **セキュリティ**: からダウンロードおよびインストールでは、R パッケージを新しい CRAN またはそのミラー サイトのいずれかに慣れている多くの R ユーザー。 ただし、セキュリティの理由により、実稼働サーバーが実行されている[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]通常、インターネット接続はありません。

-   **オフライン インストールを簡単に**: パッケージをインストールするサーバーがオフラインにする必要がありますダウンロードすることもすべてのパッケージの依存関係を使用する miniCRAN 簡単に正しい形式ですべての依存関係を取得します。

-   **バージョン管理の改善**: マルチ ユーザー環境では、サーバー上の複数のパッケージ バージョンの無制限のインストールを回避する理由。

リポジトリを作成した後に、新しいパッケージを追加または既存のパッケージのバージョンのアップグレードによって変更できます。

> [!NOTE]
> MiniCRAN パッケージ自体は、これは、curl devel パッケージでシステムの依存関係のある RCurl パッケージ、その他の 18 の CRAN パッケージに依存します。 同様に、パッケージ XML libxml2 devel に依存しています。 、そのため、ビルドすることお勧めするローカル リポジトリ最初にインターネットを完全にアクセスするには、コンピューターでこれらすべての依存関係を簡単に満たすことができるようにします。 作成した後は、別の場所にリポジトリを行うことができます。

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

2.  収集されたパッケージを格納するローカル フォルダーの名前を入力します。 

    事前にフォルダーを作成することを確認します。 場合、エラーが発生、`local_repo`フォルダーでは、後で、R コードを実行するときに存在しません。

    フォルダーには、わかりやすい名前が必要です。 たとえば、"miniCRAN"は使用しないでくださいし、代わりに何か"GeneticsPackages"または"TeamRPackages1.0.2"のように入力します。

    ```R
    local_repo <- "~/miniCRAN"
    ```

    ティルダ拡張演算子を返しますと同じ結果を含む環境変数、`Sys.getenv("R_USER")`です。

### <a name="step-3-add-packages-to-the-repository"></a>手順 3. パッケージをリポジトリに追加します。

1.  MiniCRAN をインストールした後は、その他のパッケージをダウンロードするを指定するリストを作成します。

    この初期の一覧には依存関係を追加しないでください。**igraph** miniCRAN によって使用されるパッケージの依存関係の一覧が生成されます。 生成された依存関係グラフを使用する方法の詳細については、次を参照してください。 [miniCRAN を使用して、パッケージの依存関係を識別する](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html)です。

    次の R スクリプトでは、対象パッケージ、"zoo"および「予測」を取得する方法を示します。

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. にないために必要な依存関係グラフにプロットすることがわかりやすくことができます。
    
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

- MiniCRAN リポジトリと R ツールを使用して、インスタンスのライブラリをインストールします。

- SQL Server データベースにパッケージをアップロードし、外部ライブラリの作成ステートメントを使用してインストールします。 このオプションには、SQL Server 2017 が必要です。 参照してください[SQL Server に追加の R パッケージをインストール](install-additional-r-packages-on-sql-server.md)です。

次の手順では、R ツールを使用してパッケージをインストールする方法について説明します。

1. パッケージをインストールするサーバーをそのままで、miniCRAN リポジトリを含むフォルダーにコピーします。

2. インスタンスに関連付けられた R ツールを使用して、R コマンド プロンプトを開きます。

    - SQL Server 2017、既定のフォルダーは`C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`します。

    - SQL Server 2016 では、既定のフォルダーは `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library` です。

    - 名前付きインスタンスの場合は、既定のパスはなどになります:`<instance_path>.RTEST/R_SERVICES/library`です。

    -  SQL Server を別のドライブにインストールしていたり、インストール パスにその他の変更を加えたりしている場合は、それらの変更もパスに反映するようにします。

3.  インスタンス ライブラリのパスを取得し、ライブラリ パスの一覧に追加します。

    ```R
    .libPaths()[1]  
    lib \<- .libPaths()[1]
    ```

    このコマンドで SQL Server などのインスタンスに関連付けられているライブラリのパスを返す必要があります:"c:/program ファイルまたは Microsoft SQL Server/MSSQL14 です。MSSQLSERVER/R_SERVICES/ライブラリ"

4.  MininCRAN のリポジトリのコピー先サーバー上の場所を指定`server_repo`です。

    この例では、リポジトリは、サーバーで、[ユーザー] フォルダーにコピーした想定しています。

    ```R
    R server_repo <- "C:\\Users\\MyUserName\\miniCRAN"
    ```

5.  サーバー上の新しい R ワークスペースを使用しているためにをインストールするパッケージの一覧も提供する必要があります。

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6.  MiniCRAN リポジトリのローカル コピーへのパスを提供する、パッケージをインストールします。

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath(server_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE)
    ```

7.  インスタンス ライブラリからは、次のようなコマンドを使用してインストールされているパッケージを表示できます。

    ```R
    installed.packages()
    ```

> [!NOTE] 
> SQL Server のサーバー管理者は、必要がありますパッケージをインストール miniCRAN リポジトリからのインスタンスによって使用される既定のライブラリにします。 

## <a name="manually-download-single-packages"></a>手動で単一のパッケージをダウンロードします。

MiniCRAN を使用しないようにする場合、必要なパッケージとその依存関係を手動でダウンロードできます。 これを行うには、管理者またはサーバーの唯一の所有者をしている必要があります。

パッケージをダウンロードした後は、zip 形式のファイルの場所から R パッケージをインストールします。

1. パッケージの zip ファイルをダウンロードしてローカル フォルダーに保存

2. そのフォルダーにコピー、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]コンピューター。

3. SQL Server インスタンスのライブラリに、パッケージをインストールします。

> [!NOTE]
> R ツールを使用してパッケージをインストールするときに、全体として、インスタンスにインストールされます。 
> 
> データベースにパッケージをインストールし、パッケージをデータベース ロールを使用しているユーザーと共有する場合は、外部ライブラリの作成ステートメントを使用して、ライブラリをアップロードする必要があります。 参照してください[SQL サーバーに追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
