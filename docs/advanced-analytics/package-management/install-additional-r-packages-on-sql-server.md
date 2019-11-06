---
title: Sqlmlutils を使用して新しい R パッケージをインストールする
description: Sqlmlutils を使用して、SQL Server Machine Learning Services または SQL Server R Services のインスタンスに新しい R パッケージをインストールする方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f8ce5c7bcf12a2431c2de779912d2e309c628cb1
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542145"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>Sqlmlutils を使用して新しい R パッケージをインストールする

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、 [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils)パッケージの関数を使用して、SQL Server Machine Learning Services または SQL Server R Services のインスタンスに新しい R パッケージをインストールする方法について説明します。 インストールするパッケージは、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) t-sql ステートメントを使用して、データベース内で実行されている R スクリプトで使用できます。

> [!NOTE]
> SQL Server に R パッケージを追加する場合は、標準の R `install.packages` コマンドを使用しないことをお勧めします。 代わりに、この記事で説明されているように**sqlmlutils**を使用します。

## <a name="prerequisites"></a>[前提条件]

- SQL Server に接続するために使用するクライアントコンピューターに、 [R](https://www.r-project.org)と[rstudio Desktop](https://www.rstudio.com/products/rstudio/download/)をインストールします。 スクリプトの実行には任意の R IDE を使用できますが、この記事では RStudio を前提としています。

- SQL Server への接続に使用するクライアントコンピューターに、 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is)または[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) をインストールします。 他のデータベース管理ツールまたはクエリツールを使用することもできますが、この記事では Azure Data Studio または SSMS を前提としています。

### <a name="other-considerations"></a>その他の考慮事項

- SQL Server で実行されている R スクリプトでは、既定のインスタンスライブラリにインストールされているパッケージのみを使用できます。 SQL Server、そのライブラリが同じコンピューター上にある場合でも、外部ライブラリからパッケージを読み込むことはできません。 これには、他の Microsoft 製品と共にインストールされる R ライブラリも含まれます。

- セキュリティが強化された SQL Server 環境では、次のことを避けることをお勧めします。
  - ネットワークアクセスを必要とするパッケージ
  - 管理者特権でのファイルシステムアクセスが必要なパッケージ
  - SQL Server 内部で実行しても効果のない web 開発などのタスクに使用されるパッケージ

## <a name="install-sqlmlutils-on-the-client-computer"></a>クライアントコンピューターに sqlmlutils をインストールする

**Sqlmlutils**を使用するには、まず、SQL Server への接続に使用するクライアントコンピューターにインストールする必要があります。

**Sqlmlutils**パッケージは**Rodbcext**パッケージに依存し、 **rodbcext**は他の多くのパッケージに依存します。 次の手順では、これらのパッケージをすべて正しい順序でインストールします。

### <a name="install-sqlmlutils-online"></a>Sqlmlutils をオンラインでインストールする

クライアントコンピューターがインターネットにアクセスできる場合は、 **sqlmlutils**とその依存パッケージをオンラインでダウンロードしてインストールすることができます。

1. 最新の**sqlmlutils** zip ファイルを https://github.com/Microsoft/sqlmlutils/tree/master/R/dist からクライアントコンピューターにダウンロードします。 ファイルを解凍しないでください。

1. **コマンドプロンプト**を開き、次のコマンドを実行して、 **Sqlmlutils**と**rodbcext**パッケージをインストールします。 ダウンロードした**sqlmlutils** zip ファイルの完全なパスに置き換えます (この例では、ファイルがドキュメントフォルダーにあることを前提としています)。 **Rodbcext**パッケージはオンラインであり、インストールされています。

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>Sqlmlutils をオフラインでインストールする

クライアントコンピューターがインターネットに接続されていない場合は、インターネットにアクセスできるコンピューターを使用して、 **sqlmlutils**と**Rodbcext**パッケージを事前にダウンロードする必要があります。 その後、クライアントコンピューターのフォルダーにファイルをコピーして、パッケージをオフラインでインストールできます。

**Rodbcext**パッケージには多数の依存パッケージがあり、パッケージのすべての依存関係を識別することは複雑です。 [**MiniCRAN**](https://andrie.github.io/miniCRAN/)を使用して、すべての依存パッケージを含むパッケージのローカルリポジトリフォルダーを作成することをお勧めします。
詳細については、「 [miniCRAN を使用してローカル R パッケージリポジトリを作成する](create-a-local-package-repository-using-minicran.md)」を参照してください。

**Sqlmlutils**パッケージは、クライアントコンピューターにコピーしてインストールできる1つの zip ファイルで構成されています。

インターネットにアクセスできるコンピューターの場合:

1. **MiniCRAN**をインストールします。 詳細については、「 [Install miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran) 」を参照してください。

1. RStudio で、次の R スクリプトを実行して、 **Rodbcext**パッケージのローカルリポジトリを作成します。 この例では、`c:\downloads\rodbcext` フォルダーにリポジトリを作成します。

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end

   @No__t_0 値には、SQL Server にインストールされている R のバージョンを使用します。 インストールされているバージョンを確認するには、次の T-sql コマンドを使用します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. 最新の**sqlmlutils** zip ファイルを https://github.com/Microsoft/sqlmlutils/tree/master/R/dist からダウンロードします (ファイルを解凍しないでください)。 たとえば、`c:\downloads\sqlmlutils_0.7.1.zip` にファイルをダウンロードします。

1. **Rodbcext**リポジトリフォルダー全体 (`c:\downloads\rodbcext`) と**sqlmlutils** zip ファイル (`c:\downloads\sqlmlutils_0.7.1.zip`) をクライアントコンピューターにコピーします。 たとえば、クライアントコンピューターのフォルダー `c:\temp\packages` にコピーします。

SQL Server に接続するために使用するクライアントコンピューターで、コマンドプロンプトを開き、次のコマンドを実行して**Rodbcext**と**sqlmlutils**をインストールします。

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>SQL Server に R パッケージを追加する

次の例では、SQL Server に[**グルー**](https://cran.r-project.org/web/packages/glue/)パッケージを追加します。

### <a name="add-the-package-online"></a>パッケージをオンラインで追加する

SQL Server への接続に使用するクライアントコンピューターがインターネットにアクセスできる場合は、 **sqlmlutils**を使用して、インターネット経由で**グルー**パッケージと依存関係を検索し、そのパッケージを SQL Server インスタンスにリモートでインストールすることができます。

1. クライアントコンピューターで RStudio を開き、新しい**R スクリプト**ファイルを作成します。

1. **Sqlmlutils**を使用して**グルー**パッケージをインストールするには、次の R スクリプトを使用します。 独自の SQL Server データベース接続情報を置き換えます (Windows 認証を使用しない場合は、`uid` パラメーターと `pwd` パラメーターを追加します)。

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > **スコープ**には、**パブリック**または**プライベート**のいずれかを指定できます。 パブリックスコープは、すべてのユーザーが使用できるパッケージをデータベース管理者がインストールする場合に便利です。 プライベートスコープを使用すると、パッケージをインストールするユーザーのみがパッケージを使用できるようになります。 スコープを指定しない場合、既定のスコープは**プライベート**になります。

### <a name="add-the-package-offline"></a>パッケージをオフラインで追加する

クライアントコンピューターがインターネットに接続されていない場合は、 **miniCRAN**を使用して、インターネットにアクセスできるコンピューターを使用して、**グルー**パッケージをダウンロードできます。 次に、パッケージをクライアントコンピューターにコピーして、パッケージをオフラインでインストールできるようにします。
**MiniCRAN**のインストールについては、「 [Install miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran) 」を参照してください。

インターネットにアクセスできるコンピューターの場合:

1. 次の R スクリプトを実行して、**グルー**のローカルリポジトリを作成します。 この例では、`c:\downloads\glue` にリポジトリフォルダーを作成します。

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end


   @No__t_0 値には、SQL Server にインストールされている R のバージョンを使用します。 インストールされているバージョンを確認するには、次の T-sql コマンドを使用します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. **グルー**リポジトリフォルダー全体 (`c:\downloads\glue`) をクライアントコンピューターにコピーします。 たとえば、`c:\temp\packages\glue` フォルダーにコピーします。

クライアントコンピューターで、次のようにします。

1. RStudio を開き、新しい**R スクリプト**ファイルを作成します。

1. **Sqlmlutils**を使用して**グルー**パッケージをインストールするには、次の R スクリプトを使用します。 独自の SQL Server データベース接続情報を置き換えます (Windows 認証を使用しない場合は、`uid` パラメーターと `pwd` パラメーターを追加します)。

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > **スコープ**には、**パブリック**または**プライベート**のいずれかを指定できます。 パブリックスコープは、すべてのユーザーが使用できるパッケージをデータベース管理者がインストールする場合に便利です。 プライベートスコープを使用すると、パッケージをインストールするユーザーのみがパッケージを使用できるようになります。 スコープを指定しない場合、既定のスコープは**プライベート**になります。

## <a name="use-the-package"></a>パッケージを使用する

**グルー**パッケージがインストールされたら、t-sql **sp_execute_external_script**コマンドを使用して SQL Server の R スクリプトで使用できます。

1. Azure Data Studio または SSMS を開き、SQL Server データベースに接続します。

1. 次のコマンドを実行します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
       , @script = N'
   library(glue)

   name <- "Fred"
   birthday <- as.Date("2020-06-14")
   text <- glue(''My name is {name} '',
   ''and my birthday is {format(birthday, "%A, %B %d, %Y")}.'')

   print(text)
         ';
   ```

    **[結果]**

    ```text
    My name is Fred and my birthday is Sunday, June 14, 2020.
    ```

## <a name="remove-the-package"></a>パッケージを削除する

**グルー**パッケージを削除する場合は、次の R スクリプトを実行します。 前に定義したのと同じ**接続**変数を使用します。

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>次のステップ

- インストールされている R パッケージの詳細については、「 [Get r package information](r-package-information.md) 」を参照してください。
- R パッケージの操作の詳細については、「 [r パッケージの使用に関するヒント](tips-for-using-r-packages.md)」を参照してください。
- Python パッケージのインストールの詳細については、「 [pip を使用した python パッケージのインストール](install-additional-python-packages-on-sql-server.md)」を参照してください。
- SQL Server Machine Learning Services の詳細については、「 [SQL Server Machine Learning Services (Python および R) とは](../what-is-sql-server-machine-learning.md)」を参照してください。
