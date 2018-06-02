---
title: MiniCRAN (SQL Server の Machine Learning) を使用してローカルの R パッケージ リポジトリを作成 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1f7ba3b4acde90d9e416eb092ac80cb0dfcbba8a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585644"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>MiniCRAN を使用してローカルの R パッケージ リポジトリを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html)によって作成されたパッケージ[Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)を識別、およびパッケージと R パッケージがインストールされたオフラインの他のコンピューターにコピーすることができます、1 つのフォルダーに依存関係をダウンロードします。

入力として 1 つまたは複数のパッケージを指定します。 **miniCRAN**再帰的には、これらのパッケージの依存関係ツリーを読み取り、CRAN または類似のリポジトリからのみ表示されているパッケージとその依存関係をダウンロードします。

出力として**miniCRAN**選択したパッケージと必要なすべての依存関係から成る内部に矛盾のリポジトリを作成します。 このローカル リポジトリをサーバーに移動し、インターネットに接続せず、パッケージのインストールに進むことができます。

> [!NOTE]
> 経験豊富な R ユーザーは、多くの場合、ダウンロードしたパッケージの DESCRIPTION ファイル内の依存パッケージの一覧を探します。 ただし、パッケージに記載**Imports**第 2 レベルの依存関係のある可能性があります。 このため、ことをお勧め**miniCRAN**必要なパッケージのコレクション全体を構築します。

## <a name="why-create-a-local-repository"></a>ローカル リポジトリを作成する理由

ローカル パッケージ リポジトリを作成する目的は、サーバー管理者または組織内の他のユーザーがサーバーでは、特にいずれかのインターネット アクセスが許可されていない新しい R パッケージをインストールに使用できる 1 つの場所を提供します。 リポジトリを作成した後に、新しいパッケージを追加または既存のパッケージのバージョンのアップグレードによって変更できます。

パッケージのリポジトリには、これらのシナリオがあります。

- **セキュリティ**: からダウンロードおよびインストールでは、R パッケージを新しい CRAN またはそのミラー サイトのいずれかに慣れている多くの R ユーザー。 ただし、セキュリティの理由により、実稼働サーバーが実行されている[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]通常、インターネット接続はありません。

- **オフライン インストールを簡単に**: パッケージをインストールするサーバーがオフラインにする必要がありますダウンロードすることもすべてのパッケージの依存関係を使用する miniCRAN 簡単に正しい形式ですべての依存関係を取得します。

    MiniCRAN を使用するをインストールするパッケージを準備する際に、パッケージの依存関係のエラーを回避できます、[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)ステートメントです。

- **バージョン管理の改善**: マルチ ユーザー環境では、サーバー上の複数のパッケージ バージョンの無制限のインストールを回避する理由。 ローカル リポジトリを使用すると、アナリストが使用するパッケージの一貫性のあるセットを提供できます。 

> [!TIP]
> また、Azure Machine Learning で使用するためのパッケージを準備するのに miniCRAN を使用することができます。 詳細については、このブログを参照してください: [Michele Usuelli での Azure ML で miniCRAN の使用](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>MiniCRAN をインストールします。

**MiniCRAN**パッケージ自体が他の 18 の CRAN パッケージを依存である間、 **RCurl**システムの依存関係のあるパッケージで、 **curl devel**パッケージです。 同様に、パッケージ**XML**に依存している**libxml2 devel**です。 依存関係を解決するには、ローカル リポジトリ フル インターネットにアクセスできるコンピューターで、最初にビルドすることをお勧めします。 

基本の R を使用しているコンピューターで次のコマンドを実行する R ツール、およびインターネットに接続します。 これがあると見なされます*いない*SQL Server コンピューター。 次のコマンドをインストール、 **miniCRAN**パッケージと、必要な**igraph**パッケージです。 パッケージが既にインストールされているかどうか、この例が確認されますが、if をバイパスできますステートメントと、パッケージを直接インストールします。

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>CRAN ミラーと MRAN スナップショットを設定します。

パッケージの取得中に使用するミラー サイトを指定します。 たとえば、お住まいの地域を必要なパッケージを含む MRAN サイト、またはその他のサイトを使用する可能性があります。 ダウンロードに失敗した場合は、別のミラー サイトを再試行してください。

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>ローカル フォルダーを作成します。

などのローカル フォルダーを作成する`C:\mylocalrepo`収集されたパッケージを格納します。 場合は、この手順を繰り返します多くの場合、おそらく"miniCRANZooPackages"または"miniCRANMyRPackagev2"などのわかりやすい名前を使用する必要があります。

ローカル リポジトリとしてフォルダーを指定します。 R 構文を使用してスラッシュ パス名の逆である Windows の規則からです。

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>パッケージをローカル リポジトリに追加します。

後に**miniCRAN**がインストールされているし、その他のパッケージをダウンロードするを指定するリストを作成読み込まれるとします。

**いない**この最初のリストに依存関係を追加します。 **Igraph**によって使用されるパッケージ**miniCRAN**依存関係の一覧が生成されます。 生成された依存関係グラフを使用する方法の詳細については、次を参照してください。 [miniCRAN を使用して、パッケージの依存関係を識別する](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html)です。

1. 対象のパッケージ、"zoo"と「予測」変数を追加します。

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. 必要に応じて、依存関係グラフのプロットがわかりやすくことができます。
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. ローカル リポジトリを作成します。 必ず、SQL Server インスタンスにインストールされているバージョンに必要な場合は、R のバージョンを変更してください。 3.2.2 のバージョンが SQL Server 2016 では、SQL Server 2017 でバージョン 3.3 がします。 コンポーネントのアップグレードを行った場合、バージョンが新しい可能性があります。 詳細については、次を参照してください。 [R の取得と Python パッケージ情報](determine-which-packages-are-installed-on-sql-server.md)です。

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   この情報から miniCRAN パッケージにパッケージをコピーする必要のあるフォルダー構造を作成、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]以降。

この時点で、パッケージを含むフォルダーがある必要があり、その他のパッケージが必要です。 パスは、この例のようにする必要があります: C:\mylocalrepo\bin\windows\contrib\3.3 とそれには、zip 形式のパッケージのコレクションを含める必要があります。 パッケージを解凍し、すべてのファイルの名前を変更したりしないでください。

必要に応じて、ローカル miniCRAN リポジトリに格納されているパッケージを一覧表示するには、次のコードを実行します。

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>インスタンスのライブラリにパッケージを追加します。

必要なパッケージを持つローカル リポジトリがある場合は後、は、SQL Server コンピューターにパッケージ リポジトリを移動します。 次の手順では、R ツールを使用してパッケージをインストールする方法について説明します。

1. パッケージをインストールするサーバーをそのままで、miniCRAN リポジトリを含むフォルダーにコピーします。 フォルダーがこの構造体を持つ通常: miniCRAN ルート > bin > windows > contrib > バージョン > すべてのパッケージです。 次の例については、ルート ドライブからフォルダーを想定しています。 

2. インスタンスに関連付けられた R ツールを開きます (たとえば、Rgui.exe を使用できます)。 右クリック**管理者として実行**ツール、システムの更新に使用できるようにします。

    - SQL Server の 2017 RGUI のファイルの場所は`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`します。

    - SQL Server 2016 RGUI の彼のファイルの場所は`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`します。

3. インスタンス ライブラリのパスを取得し、ライブラリ パスの一覧に追加します。 SQL Server の 2017 のパスは、次の例に似ています。

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. コピー先サーバーに新しい場所を指定、 **miniCRAN**リポジトリとして`server_repo`です。

    この例では、リポジトリは、サーバー上の一時フォルダーにコピーした想定しています。

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. サーバー上の新しい R ワークスペースを使用しているためにをインストールするパッケージの一覧も提供する必要があります。

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. MiniCRAN リポジトリのローカル コピーへのパスを提供する、パッケージをインストールします。

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. インスタンス ライブラリからは、次のようなコマンドを使用してインストールされているパッケージを表示できます。

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>参照

+ [パッケージ情報の取得](determine-which-packages-are-installed-on-sql-server.md)
+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)
+ [操作方法ガイド](sql-server-machine-learning-tasks.md)


