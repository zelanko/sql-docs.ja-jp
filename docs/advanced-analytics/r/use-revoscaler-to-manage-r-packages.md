---
title: "SQL Server にパッケージ化 RevoScaleR 関数を使用して、見つからないか、R をインストールする方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: b600d7d118ad5bcc24c201683246f3e037da3fba
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>RevoScaleR 関数を使用して、見つからないか、SQL Server で R パッケージをインストールする方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Microsoft R Server リリース 9.0.1 には、操作のサポートに、SQL Server のコンピューティング コンテキストでパッケージがインストールされている新しい RevoScaleR 関数が導入されました。 これらの新しい関数やすく、データ サイエンティストを R コードを実行し、サーバーに直接アクセスすることがなく、SQL Server にパッケージをインストールします。

## <a name="how-does-it-work"></a>動作方法

R Server 9.0.1 が場合や、使用することができます、 [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) SQL Server のコンピューティング コンテキストでパッケージをインストールするリモート R クライアントからの関数。 このオプションを使用するには、サーバーおよびデータベースにパッケージの管理を有効にする必要があります。 この機能では、R Services の Machine Learning のサービスを対応するバージョンがサーバーにインストールすることも必要です。

RevoScaleR の新しいバージョンには、これらの関数も含まれます。 

+ [RxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage)関数は、指定された計算コンテキストで 1 つまたは複数のパッケージのパスを取得します。

    ユーザーとスコープの組み合わせを使用して、パッケージを検索または特定のデータベースにパッケージを追加することができます。

+ [RxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages)関数は、指定された計算コンテキストでインストールされているパッケージの一覧を取得します。

+ [RxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages)関数は、コンピューティング コンテキストにパッケージをインストール、パッケージを圧縮またはローカルに保存されたを読み取ることによって指定されたリポジトリからいずれか。

    この関数は、依存関係をチェックし、によってローカル コンピューティング コンテキストで R パッケージのインストールと同じように、SQL Server に関連するすべてのパッケージをインストールすることができます。

+ [RxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages)関数は、指定された計算コンテキストからパッケージを削除します。

    また、依存関係を計算し、SQL Server 上の他のパッケージで使用される不要になったパッケージを削除すること、リソースを解放することを確認します。

+ 使用して、 [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages)ファイル システムとデータベースの場合は、指定された計算コンテキストの間でパッケージ ライブラリに関する情報をコピーする関数。

+ 使用して、 [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)関数 SQL Server インスタンス ライブラリのパスを決定する計算コンテキスト。

**適用されます:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]です。   サポートされても[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] R Server 9.0 以降にアップグレードします。   その他の制限が適用されます。

## <a name="requirements"></a>必要条件

+ これらの関数を実行するには、サーバーおよびデータベースに接続して、R コマンドを実行するアクセス許可が必要です。

+ リモート R クライアントからこれらの関数を使用する場合必要があります最初に作成する計算コンテキストのオブジェクトを使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数。 その後、各パッケージの管理機能を使用するには、引数としてコンピューティング コンテキストを渡します。

+ 指定しないと、ユーザー名とパスワード、計算コンテキストを作成するときに、R コードを実行しているユーザーの id が使用されます。

+ 内のパッケージ管理機能を実行することも`sp_execute_external_script`します。 これを行うと、ストアド プロシージャの呼び出し元のセキュリティ コンテキストを使用して、関数が実行されます。

+ パッケージの**共有範囲**に属しているユーザーによってインストールされていることができます、`rpkgs-shared`指定データベース内のロール。 このロールのすべてのユーザーには、共有のパッケージをアンインストールできます。

+ パッケージの**プライベート スコープ**に属するすべてのユーザーがインストールされていることができます、`rpkgs-private`データベース内のロール。 ただし、ユーザーが表示したり、独自のパッケージのみをアンインストールします。

+ データベース所有者は、共有またはプライベートのパッケージを操作できます。

## <a name="package-installation-from-machine-learning-server-or-remote-r-client"></a>Machine Learning のサーバーまたはリモートの R クライアントからのパッケージのインストール

開始する前に、これらの条件を満たしていることを確認します。

+ クライアントに RevoScale 9.0.1 またはそれ以降。
+ RevoScaleR の同等のバージョンが SQL Server インスタンスにインストールされました。
+ [パッケージ管理機能は](..\r\r-package-how-to-enable-or-disable.md)がインスタンスで有効になっています。
+ 指定したインスタンスおよびデータベースにパッケージをインストールすることができますをデータベース ロールのメンバーであります。 将来的にロールをサポートするか、インストールを実行するパッケージ共有またはプライベートの場所。 ここでは、データベース所有者である場合、パッケージをインストールすることができます。

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

## <a name="examples"></a>使用例

このセクションでは、SQL Server インスタンスまたは計算コンテキストとしてデータベースに接続するときに、リモート クライアントからこれらの関数を使用する方法の例を示します。

すべての例については、接続文字列、または接続文字列を必要とする計算コンテキストのいずれかを指定する必要があります。 この例では、SQL Server のコンピューティング コンテキストを作成する 1 つの方法を提供します。

```R
instance_name <- "Machine name/Instance name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

サーバーが置かれていると、セキュリティ モデル、に応じて接続文字列内のドメインとサブネットの仕様を指定するか、SQL ログインを使用する必要があります。 例:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"


### Get package path on a remote SQL Server compute context

This example gets the path for the **RevoScaleR** package on the compute context, `sqlcc`.

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
