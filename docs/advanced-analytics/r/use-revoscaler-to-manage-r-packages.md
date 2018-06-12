---
title: SQL Server にパッケージ化 RevoScaleR 関数を使用して、見つからないか、R をインストールする方法 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d92b3e993968ce48d7489b0c17d6bdba005809a3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707530"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>RevoScaleR 関数を使用して、見つからないか、SQL Server で R パッケージをインストールする方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR 9.0.1 し、SQL Server のコンピューティング コンテキストに R パッケージの管理の機能を後で含まれます。 これらの関数は、サーバーへの直接アクセスせず、SQL Server にパッケージをインストールする管理者以外のリモートで使用できます。

SQL Server 2017 Machine Learning サービスには、RevoScaleR の新しいバージョンが既に含まれています。 SQL Server 2016 の R Services のお客様が行う必要があります、[コンポーネントのアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)RevoScaleR パッケージ管理機能を取得します。 バージョンとコンテンツのパッケージを取得する方法についてを参照してください。[パッケージ情報を取得](determine-which-packages-are-installed-on-sql-server.md)です。

## <a name="revoscaler-functions-for-package-management"></a>パッケージの管理の RevoScaleR 関数

次の表では、R パッケージのインストールと管理に使用する関数について説明します。

| 関数 | 説明 |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | リモートの SQL Server のインスタンスのライブラリのパスを決定します。 |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | リモートの SQL Server で 1 つまたは複数のパッケージのパスを取得します。 |
| [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | SQL Server のコンピューティング コンテキストでパッケージをインストールするリモート R クライアントからこの関数を呼び出し、zip 形式のパッケージをローカルに保存されたか、指定されたリポジトリから読み取ることでします。 この関数は、依存関係をチェックし、によってローカル コンピューティング コンテキストで R パッケージのインストールと同じように、SQL Server に関連するすべてのパッケージをインストールすることができます。 このオプションを使用するには、サーバーおよびデータベースにパッケージの管理を有効にする必要があります。 クライアントとサーバーの両方の環境では、同じバージョンの RevoScaleR が必要です。 |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | 指定された計算コンテキストでインストールされているパッケージの一覧を取得します。 |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | ファイル システムとデータベースの場合は、指定された計算コンテキストの間でパッケージ ライブラリに関する情報をコピーします。 |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | 指定された計算コンテキストからパッケージを削除します。 また、依存関係を計算し、SQL Server 上の他のパッケージで使用される不要になったパッケージを削除すること、リソースを解放することを確認します。 |

## <a name="prerequisites"></a>前提条件

+ [リモート SQL Server 上の R パッケージの管理を有効にします。](r-package-how-to-enable-or-disable.md)

+ RevoScaleR バージョンは、クライアントとサーバーの両方の環境で同じである必要があります。 詳細については、次を参照してください。[パッケージ情報を取得](determine-which-packages-are-installed-on-sql-server.md)です。

+ R コマンドを実行して、サーバーと、データベースに接続する権限です。 指定したインスタンスおよびデータベースにパッケージをインストールすることができますをデータベース ロールのメンバーがあります。

+ パッケージの**共有範囲**に属しているユーザーによってインストールされていることができます、`rpkgs-shared`指定データベース内のロール。 このロールのすべてのユーザーには、共有のパッケージをアンインストールできます。

+ パッケージの**プライベート スコープ**に属するすべてのユーザーがインストールされていることができます、`rpkgs-private`データベース内のロール。 ただし、ユーザーが表示したり、独自のパッケージのみをアンインストールします。

+ データベース所有者は、共有またはプライベートのパッケージを操作できます。

## <a name="client-connections"></a>クライアント接続

クライアント ワークステーションは、 [Microsoft R クライアント](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows)または[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (このデータ サイエンティストは、多くの場合に無料の developer edition を使用するものです)、同じネットワーク上。

リモート R クライアントからパッケージの管理関数を呼び出すときにする必要があります最初に作成する計算コンテキストのオブジェクトを使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数。 その後、各パッケージの管理機能を使用するには、引数としてコンピューティング コンテキストを渡します。

ユーザー id は、通常、計算コンテキストを設定するときに指定します。 指定しないと、ユーザー名とパスワード、計算コンテキストを作成するときに、R コードを実行しているユーザーの id が使用されます。

1. R コマンドラインから、インスタンスとデータベースへの接続文字列を定義します。
2. 使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)コンス トラクターを接続文字列を使用して、SQL Server のコンピューティング コンテキストを定義します。

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

    依存パッケージが必要な場合は、インストールされている、インターネット接続が、クライアントで使用できると仮定します。
    
    パッケージをインストールするには、そのユーザーの既定のスコープで、接続を行うユーザーの資格情報が使用されます。

## <a name="call-package-management-functions-in-stored-procedures"></a>ストアド プロシージャ内でパッケージの管理関数を呼び出す

内のパッケージ管理機能を実行するカム`sp_execute_external_script`です。 これを行うと、ストアド プロシージャの呼び出し元のセキュリティ コンテキストを使用して、関数が実行されます。

## <a name="examples"></a>使用例

このセクションでは、SQL Server インスタンスまたは計算コンテキストとしてデータベースに接続するときに、リモート クライアントからこれらの関数を使用する方法の例を示します。

すべての例については、接続文字列、または接続文字列を必要とする計算コンテキストのいずれかを指定する必要があります。 この例では、SQL Server のコンピューティング コンテキストを作成する 1 つの方法を提供します。

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

サーバーが置かれていると、セキュリティ モデル、に応じて接続文字列内のドメインとサブネットの仕様を指定するか、SQL ログインを使用する必要があります。 以下に例を示します。

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>リモート SQL Server のコンピューティング コンテキストのパッケージ パスを取得します。

この例のパスを取得する、 **RevoScaleR**コンピューティング コンテキストでパッケージ`sqlcc`です。

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**結果**

"C:/program ファイルまたは Microsoft SQL Server/MSSQL14 です。MSSQLSERVER/R_SERVICES/ライブラリ/RevoScaleR"

> [!TIP]
> SQL コンソール出力を表示するオプションを有効にした場合の前に、関数からのステータス メッセージを取得する可能性があります、`print`ステートメントです。 コードのテストが完了したら、設定`consoleOutput`メッセージを削除するコンピューティング コンテキスト コンス トラクターで FALSE にします。

### <a name="get-locations-for-multiple-packages"></a>複数のパッケージの場所を取得する

次の例のパスを取得する、 **RevoScaleR**と**格子**コンピューティング コンテキストでのパッケージ`sqlcc`です。 複数のパッケージに関する情報を取得するには、パッケージ名を含む文字列のベクトルを渡します。

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>リモートのコンピューティング コンテキストでパッケージのバージョンを取得します。

コンピューティング コンテキストでインストールされているパッケージのビルド番号とバージョン番号を取得する、R コンソールからこのコマンドを実行*sqlServer*です。

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**結果**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>SQL Server にパッケージをインストールする

この例ではインストール、**予測**パッケージとその依存関係、計算コンテキストをします。

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>パッケージを SQL Server から削除する

この例は、**予測**パッケージとその依存関係、計算コンテキストからです。

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>データベースとファイル システムの間でパッケージを同期します。

次の例では、データベース**TestDB**、し、ファイル システム内のすべてのパッケージがインストールされているかどうかを決定します。 一部のパッケージが存在しない場合は、ファイル システムにインストールされます。

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

パッケージの同期のしくみ、データベースとユーザー単位ごとです。 詳細については、次を参照してください。 [for SQL Server の R パッケージ同期](../r/package-install-uninstall-and-sync.md)です。

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>SQL Server でパッケージを一覧表示、ストアド プロシージャを使用します。

Management Studio または現在のインスタンスにインストールされているパッケージの一覧を取得する、T-SQL をサポートしている別のツールからこのコマンドを実行を使用して`rxInstalledPackages`ストアド プロシージャでします。

```SQL
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

`rxSqlLibPaths`関数を使用して SQL Server マシン ラーニング サービスによって使用されるアクティブなライブラリを決定できます。 このスクリプトは、現在のサーバーのライブラリ パスのみを返すことができます。 

```SQL
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

## <a name="see-also"></a>参照

+ [リモートの R パッケージ管理を有効にする](r-package-how-to-enable-or-disable.md)
+ [R パッケージの同期](package-install-uninstall-and-sync.md)
+ [R パッケージをインストールするためのヒント](packages-installed-in-user-libraries.md)
+ [既定のパッケージ](installing-and-managing-r-packages.md)