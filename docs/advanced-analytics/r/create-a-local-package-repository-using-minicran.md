---
title: MiniCRAN - SQL Server Machine Learning Services を使用してローカルの R パッケージ リポジトリを作成します。
description: MiniCran を使用して、検出、アセンブル、および 1 つの統合パッケージ R パッケージの依存関係をインストールします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: d9154bc1c01bdf9bd7bdfd7a4032b4ed173464d6
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510219"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>MiniCRAN を使用してローカルの R パッケージ リポジトリを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html)によって作成されたパッケージ[Andre de Vries](https://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)、識別し、パッケージと R パッケージのオフライン インストールの他のコンピューターにコピーすることを 1 つのフォルダーに依存関係をダウンロードします。

入力として 1 つまたは複数のパッケージを指定します。 **miniCRAN**再帰的には、これらのパッケージの依存関係ツリーを読み取り、CRAN またはのようなリポジトリからのみ表示されているパッケージとその依存関係をダウンロードします。

を出力として**miniCRAN** 、選択したパッケージと必要なすべての依存関係から成る内部に矛盾のリポジトリを作成します。 このローカル リポジトリをサーバーに移動し、インターネットに接続せず、パッケージのインストールに進むことができます。

> [!NOTE]
> R の経験豊富なユーザーは、多くの場合、ダウンロードしたパッケージの DESCRIPTION ファイル内の依存パッケージの一覧を探します。 ただし、パッケージに記載**Imports**第 2 レベルの依存関係があります。 このため、お勧め**miniCRAN**必要なパッケージの完全なコレクションを構築します。

## <a name="why-create-a-local-repository"></a>ローカル リポジトリを作成する理由

ローカル パッケージ リポジトリを作成する目的は、サーバー管理者または組織内の他のユーザーは、特に 1 つのインターネット アクセスがないサーバーに新しい R パッケージをインストールに使用できる 1 つの場所を提供します。 リポジトリを作成した後に、新しいパッケージを追加または既存のパッケージのバージョンのアップグレードによって変更できます。

パッケージ リポジトリには、これらのシナリオがあります。

- **セキュリティ**:ダウンロードと CRAN またはいずれかのミラー サイトからは、新しい R パッケージをインストールするのには、多くの R ユーザーが慣れています。 ただし、セキュリティ上の理由から、実行している運用サーバーの[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]通常、インターネット接続はありません。

- **オフライン インストールを容易に**:オフラインのサーバーにパッケージをインストールするには、ことも、すべてのパッケージの依存関係をダウンロードする、Using miniCRAN を使用すると、正しい形式ですべての依存関係を取得しやすくが必要です。

    MiniCRAN を使用するをインストールするパッケージを準備するときに、パッケージの依存関係のエラーを回避できます、 [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)ステートメント。

- **強化されたバージョン管理**:マルチ ユーザー環境では、サーバー上の複数のパッケージ バージョンの無制限のインストールを回避するために、それなりの理由があります。 ローカル リポジトリを使用して、アナリストによって使用される一貫性のある一連のパッケージを提供します。 

> [!TIP]
> Azure Machine Learning で使用するためのパッケージを準備するのに miniCRAN を使用することもできます。 詳細については、このブログを参照してください。[Michele Usuelli での Azure ML で miniCRAN を使用します。](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>MiniCRAN をインストールします。

**MiniCRAN**パッケージ自体は他の 18 の CRAN パッケージに依存である間、 **RCurl**システム依存関係を持つ、パッケージで、 **curl devel**パッケージ。 同様に、パッケージ**XML**に依存している**libxml2 devel**します。 依存関係を解決するには、ローカル リポジトリ フル インターネットにアクセスできるコンピューターで、最初にビルドすることをお勧めします。 

基本の R を使用しているコンピューターで、次のコマンドを実行する R ツール、およびインターネットに接続します。 これがあると見なされます*いない*SQL Server コンピューター。 次のコマンドをインストール、 **miniCRAN**パッケージと、必要な**igraph**パッケージ。 パッケージが既にインストールされているかどうか、この例を確認しますが、if をバイパスするステートメントと、パッケージを直接インストールします。

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>CRAN ミラーと MRAN スナップショットを設定します。

パッケージの取得中に使用するミラー サイトを指定します。 たとえば、お住まいの地域に必要なパッケージを含む MRAN サイト、またはその他のサイトを使用する可能性があります。 ダウンロードに失敗した場合は、別のミラー サイトをお試しください。

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>ローカル フォルダーを作成します。

ローカルのフォルダーを作成します。`C:\mylocalrepo`収集パッケージを保存します。 多くの場合、この反復する場合、おそらく"miniCRANZooPackages"または"miniCRANMyRPackagev2"などのわかりやすい名前を使用する必要があります。

ローカル リポジトリとフォルダーを指定します。 R 構文ではスラッシュのパス名は、これは逆の Windows の規則。

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>ローカル リポジトリにパッケージを追加します。

後**miniCRAN**がインストールされ、読み込まれると、ダウンロードするその他のパッケージを指定するリストを作成します。

**いない**依存関係をこの最初のリストに追加します。 **Igraph**によって使用されるパッケージ**miniCRAN**の依存関係の一覧が生成されます。 生成された依存関係グラフを使用する方法の詳細については、次を参照してください。 [miniCRAN を使用して、パッケージの依存関係を識別する](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html)します。

1. ターゲット パッケージ、"zoo"と「予測」変数に追加します。

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. 必要に応じて、依存関係グラフのプロットが有益ことができます。
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. ローカル リポジトリを作成します。 SQL Server インスタンスにインストールされているバージョンに必要な場合、R のバージョンを変更してください。 3.2.2 のバージョンが SQL Server 2016 では、バージョン 3.3 が SQL Server 2017 にします。 コンポーネントのアップグレードを実行した場合、バージョンが新しい場合があります。 詳細については、次を参照してください。[パッケージ情報の取得の R と Python](determine-which-packages-are-installed-on-sql-server.md)します。

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   MiniCRAN パッケージからこの情報は、パッケージをコピーする必要のあるフォルダー構造の作成、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]以降。

この時点で、パッケージを含むフォルダーがある必要があり、他のパッケージが必要です。 この例のようなパスがあります。C:\mylocalrepo\bin\windows\contrib\3.3 とそれには、zip 形式のパッケージのコレクションを含める必要があります。 パッケージを解凍したり、すべてのファイルの名前を変更しないでください。

必要に応じて、ローカル miniCRAN リポジトリに含まれるパッケージを一覧表示するには、次のコードを実行します。

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>インスタンスのライブラリにパッケージを追加します。

必要なパッケージをローカル リポジトリを作成したら、パッケージ リポジトリを SQL Server コンピューターに移動します。 次の手順では、R ツールを使用してパッケージをインストールする方法について説明します。

1. パッケージをインストールするサーバーをそのまま、miniCRAN リポジトリを含むフォルダーをコピーします。 このフォルダは、この構造体を通常が: miniCRAN ルート > bin > windows > contrib > バージョン > すべてのパッケージ。 次の例では、ルート ドライブ、フォルダーと仮定します。 

2. インスタンスに関連付けられている、R ツールを開きます (たとえば、Rgui.exe を使用できます)。 右クリックして**管理者として実行**システムを更新するツールを許可します。

    - SQL Server 2017 の場合、RGUI のファイルの場所は`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`します。

    - SQL Server 2016、RGUI の彼のファイルの場所は`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`します。

3. インスタンスのライブラリのパスを取得し、ライブラリ パスの一覧に追加します。 SQL Server 2017 では、パスは、次の例に似ています。

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. コピーしたサーバー上の新しい場所を指定、 **miniCRAN**リポジトリとして`server_repo`します。

    この例で、サーバー上の一時フォルダーにリポジトリをコピーしたと想定されます。

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. サーバー上の新しい R ワークスペースを使用しているために、インストールするパッケージの一覧も提供する必要があります。

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. MiniCRAN リポジトリのローカル コピーへのパスを提供する、パッケージをインストールします。

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. インスタンスのライブラリでは、次のようなコマンドを使用してインストールされているパッケージを表示できます。

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>関連項目

+ [パッケージ情報の取得](determine-which-packages-are-installed-on-sql-server.md)
+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)
+ [操作方法ガイド](sql-server-machine-learning-tasks.md)


