---
title: RevoScaleR 関数を使用して、見つからないか、SQL Server Machine Learning Services の R パッケージをインストールする方法
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7eed38e54b0c4e77af8f7b3ede0af2d98b9c58b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642339"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>RevoScaleR 関数を使用して、検索、または SQL Server に R パッケージをインストールする方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

9.0.1 RevoScaleR と SQL Server のコンピューティング コンテキストの R パッケージ管理関数後を含まれています。 これらの関数は、サーバーへの直接アクセスせず、SQL Server にパッケージをインストールする管理者以外のリモートで使用できます。

SQL Server 2017 Machine Learning サービスには、RevoScaleR の新しいバージョンが既に含まれています。 SQL Server 2016 R Services のお客様が行う必要があります、[コンポーネントのアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)RevoScaleR パッケージの管理機能を取得します。 取得する方法については、バージョンとコンテンツ パッケージを参照してください[パッケージ情報を取得](determine-which-packages-are-installed-on-sql-server.md)します。

## <a name="revoscaler-functions-for-package-management"></a>パッケージの管理用の RevoScaleR 関数

次の表では、R パッケージのインストールと管理に使用される関数について説明します。

| 関数 | 説明 |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | リモートの SQL Server のインスタンスのライブラリのパスを決定します。 |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | リモートの SQL Server で 1 つまたは複数のパッケージのパスを取得します。 |
| [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | SQL Server のコンピューティング コンテキストでパッケージをインストールするリモート R クライアントからこの関数の呼び出しは、zip 形式のパッケージをローカルに保存された、指定したリポジトリからの読み取りまたは。 この関数は、依存関係をチェックし、によって、ローカル計算コンテキストで R パッケージのインストールと同じように、SQL Server に関連するパッケージをインストールすることができます。 このオプションを使用するには、サーバーとデータベース上のパッケージ管理を有効にする必要があります。 クライアントとサーバーの両方の環境には、同じバージョンの RevoScaleR 必要があります。 |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | 指定した計算コンテキストでインストールされているパッケージの一覧を取得します。 |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | については、ファイル システムと、指定した計算コンテキストのデータベース間でのパッケージ ライブラリをコピーします。 |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | 指定された計算コンテキストからパッケージを削除します。 また、依存関係を計算し、によりリソースを解放する、SQL Server 上の他のパッケージで使用するパッケージが削除します。 |

## <a name="prerequisites"></a>前提条件

+ [リモート SQL Server での R パッケージの管理を有効にします。](r-package-how-to-enable-or-disable.md)

+ RevoScaleR のバージョンは、クライアントとサーバーの両方の環境で同じである必要があります。 詳細については、次を参照してください。[パッケージ情報を取得](determine-which-packages-are-installed-on-sql-server.md)します。

+ R コマンドを実行して、サーバーおよびデータベースに接続するためのアクセス許可。 指定したインスタンスとデータベースにパッケージをインストールできるようにするデータベース ロールのメンバーがあります。

+ パッケージ**共有スコープ**に属しているユーザーがインストールされていることができます、`rpkgs-shared`で指定されたデータベース ロール。 このロールのすべてのユーザーには、共有パッケージをアンインストールできます。

+ パッケージ**プライベート スコープ**に属するすべてのユーザーがインストールされていることができます、`rpkgs-private`データベース内のロール。 ただし、ユーザーが表示して、独自のパッケージをアンインストールします。

+ データベースの所有者は、共有またはプライベートのパッケージを操作できます。

## <a name="client-connections"></a>クライアント接続

クライアント ワークステーションができる[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows)または[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (データ サイエンティストは多くの場合として、無料の developer edition を使用)、同じネットワーク上。

リモート R クライアントからパッケージ管理関数を呼び出すときに作成する必要があるコンピューティング コンテキストのオブジェクトを最初を使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数。 その後、使用する各パッケージの管理関数には、引数として、コンピューティング コンテキストを渡します。

ユーザー id は、通常、計算コンテキストを設定するときに指定します。 コンピューティング コンテキストを作成するときにユーザー名とパスワードを指定しないは、R コードを実行しているユーザーの id は使用されます。

1. R コマンドラインからは、インスタンスとデータベースに接続文字列を定義します。
2. 使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)コンス トラクターを接続文字列を使用して、SQL Server 計算コンテキストを定義します。

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. インストールし、一覧を文字列変数に保存するパッケージの一覧を作成します。

    ```R
    packageList <- c("e1071", "mice")
    ```

4. 呼び出す[rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages)計算コンテキストと、パッケージ名を含む文字列変数を渡します。

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    依存パッケージが必要な場合は、インストールされている、インターネット接続がクライアントで使用可能です。
    
    パッケージは、そのユーザーの既定のスコープで、接続を行っているユーザーの資格情報を使用してインストールされます。

## <a name="call-package-management-functions-in-stored-procedures"></a>ストアド プロシージャでパッケージ管理関数を呼び出す

内のパッケージ管理機能を実行する cam`sp_execute_external_script`します。 これを行うには、関数、ストアド プロシージャの呼び出し元のセキュリティ コンテキストを使用して実行されます。

## <a name="examples"></a>使用例

このセクションでは、SQL Server インスタンスまたは計算コンテキストとしてデータベースに接続するときに、リモート クライアントからこれらの関数を使用する方法の例を示します。

すべての例については、接続文字列、または接続文字列を必要とする計算コンテキストのいずれかを指定する必要があります。 この例では、SQL Server のコンピューティング コンテキストを作成する方法の 1 つを提供します。

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

サーバーがある場所とセキュリティ モデル、によっては、接続文字列でのドメインとサブネットの仕様を指定するか SQL ログインを使用する必要があります。 例 :

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>リモート SQL Server 計算コンテキストでパッケージのパスを取得します。

この例のパスを取得する、 **RevoScaleR**コンピューティング コンテキストでパッケージ`sqlcc`します。

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**結果**

"C:/プログラム ファイルまたは Microsoft SQL Server/MSSQL14 します。MSSQLSERVER/R_SERVICES/ライブラリ/RevoScaleR"

> [!TIP]
> SQL のコンソール出力を表示するオプションを有効にした場合は、前にある関数のステータス メッセージを取得可能性があります、`print`ステートメント。 コードのテストが完了したら後で設定`consoleOutput`メッセージを削除するコンピューティング コンテキストのコンス トラクターで FALSE にします。

### <a name="get-locations-for-multiple-packages"></a>複数のパッケージの場所を取得する

次の例のパスを取得する、 **RevoScaleR**と**格子**コンピューティング コンテキストでのパッケージ`sqlcc`します。 複数のパッケージに関する情報を取得するには、するには、パッケージ名を含む文字列ベクトルを渡します。

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>リモート コンピューティング コンテキストでパッケージ バージョンを取得します。

コンピューティング コンテキストでインストールされているパッケージのビルド番号とバージョン番号を取得する、R コンソールからこのコマンドを実行*sqlServer*します。

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**結果**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>SQL Server にパッケージをインストールする

この例ではインストール、**予測**パッケージとその依存関係を計算コンテキスト。

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>パッケージを SQL Server から削除する

この例は、**予測**パッケージとその依存関係を計算コンテキストから。

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>データベースとファイル システムの間でパッケージを同期します。

次の例では、データベースをチェックする**TestDB**、し、ファイル システムで、すべてのパッケージがインストールされているかどうかを決定します。 一部のパッケージが存在しない場合は、ファイル システムにインストールされています。

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

パッケージの同期のしくみ、データベースとユーザーごとのモデルごと。 詳細については、次を参照してください。 [for SQL Server の R パッケージの同期](../r/package-install-uninstall-and-sync.md)します。

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>SQL Server でパッケージを一覧表示、ストアド プロシージャを使用します。

Management Studio または現在のインスタンスにインストールされているパッケージの一覧を取得する、T-SQL をサポートする別のツールからこのコマンドの実行を使用して`rxInstalledPackages`ストアド プロシージャにします。

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

`rxSqlLibPaths`関数は、SQL Server Machine Learning サービスで使用されるアクティブなライブラリを使用できます。 このスクリプトでは、現在のサーバーのライブラリ パスのみを返すことができます。 

```sql
declare @instance_name nvarchar(100) = @@SERVERNAME, @database_name nvarchar(128) = db_name();
exec sp_execute_external_script 
  @language = N'R',
  @script = N'
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    .libPaths(rxSqlLibPaths(connStr));
    print(.libPaths());
  ', 
  @input_data_1 = N'', 
  @params = N'@instance_name nvarchar(100), @database_name nvarchar(128)',
  @instance_name = @instance_name, 
  @database_name = @database_name;
```

## <a name="see-also"></a>関連項目

+ [リモートの R パッケージ管理を有効にする](r-package-how-to-enable-or-disable.md)
+ [R パッケージの同期](package-install-uninstall-and-sync.md)
+ [R パッケージをインストールするためのヒント](packages-installed-in-user-libraries.md)
+ [既定のパッケージ](installing-and-managing-r-packages.md)