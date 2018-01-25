---
title: "SQL Server にパッケージ化 RevoScaleR 関数を使用して、見つからないか、R をインストールする方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: e10435c2a0cdc5ed181aeab9bdd0bbfefa9a7f25
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>RevoScaleR 関数を使用して、見つからないか、SQL Server で R パッケージをインストールする方法

Microsoft R Server リリース 9.0.1 には、操作のサポートに、SQL Server のコンピューティング コンテキストでパッケージがインストールされている新しい RevoScaleR 関数が導入されました。 これらの新しい関数容易にできるようにサーバーに直接アクセスすることがなく SQL Server で R コードを実行するデータ サイエンティストにします。

各データ サイエンティストは、他のユーザーに表示されていないプライベート パッケージをインストールできます。 パッケージをデータベースにスコープすることができます、各ユーザー データベースごとに分離されたパッケージのサンド ボックスを取得するため、別のバージョンの同じ R パッケージをインストールする簡単です。

作業データベースを新しいサーバーに移行する場合も、すべてのパッケージの一覧を読み取るし、新しいサーバー上のデータベースにインストールを行うパッケージ同期関数を使用することができます。

この記事では、これらの関数について説明し、関数の使用方法の例を示します。

## <a name="requirements"></a>必要条件

+ これらの関数を実行するには、インスタンスで R コマンドを実行するアクセス許可が必要です。

+ 指定しないと、ユーザー名とパスワード、計算コンテキストを作成するときに、R コードを実行しているユーザーの id が使用されます。

+ リモート R クライアントからこれらの関数を使用する場合必要があります最初に作成する計算コンテキストのオブジェクトを使用して、 [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver)関数。 その後、各パッケージの管理機能を使用するには、引数としてコンピューティング コンテキストを渡します。

+ 使用してパッケージの管理機能を実行することは`sp_execute_external_script`します。 これを行うと、ストアド プロシージャの呼び出し元のセキュリティ コンテキストを使用して、関数が実行されます。

## <a name="list-of-package-management-functions"></a>パッケージ管理機能の一覧

次のパッケージ管理機能は、指定された計算コンテキストでパッケージのインストールと削除のための RevoScaleR で提供されます。

+ [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages): 指定された計算コンテキストでインストールされているパッケージに関する情報を確認します。

+ [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages): パッケージの zip 形式を指定したリポジトリから、またはローカルに保存されたを読み取ることにより、コンピューティング コンテキストにパッケージをインストールします。

+ [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages): インストール済みパッケージのコンピューティング コンテキストから削除します。

+ [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage): 指定された計算コンテキストで 1 つまたは複数のパッケージのパスを取得します。

+ [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages): 指定された計算のコンテキストで、ファイル システムおよびデータベース間でパッケージのライブラリにコピーします。

+ [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths): SQL Server 内で実行中にパッケージのライブラリ ツリーの検索パスを取得します。

SQL Server 2017 で既定では、これらのパッケージが含まれています。 これらの関数については、RevoScaleR 関数のリファレンス ページを参照してください: (https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

> [!NOTE]
> パッケージの管理の R 関数とは、Microsoft R Server 9.0.1 から使用可能です。 RevoScaleR の関数は、できない場合は、おそらく最新バージョンにアップグレードする必要があります。 

## <a name="examples"></a>使用例

このセクションには、SQL Server インスタンスまたはデータベースでパッケージの管理機能を使用する方法の例が含まれています。 

+ パッケージのインストール関数では、依存関係を確認し、ローカル計算コンテキストでの R パッケージのインストールなど、関連するパッケージを SQL Server にインストールできることを確認します。

+ 関数を_アンインストール_パッケージはまた依存関係を計算し、SQL Server 上の他のパッケージで使用される不要になったパッケージを削除すること、リソースを解放することを確認します。

+ ユーザーとスコープの組み合わせを使用して、パッケージを検索または特定のデータベースにパッケージを追加することができます。

    + パッケージの**共有範囲**に属しているユーザーによってインストールされていることができます、`rpkgs-shared`指定データベース内のロール。 このロールのすべてのユーザーには、共有のパッケージをアンインストールできます。
    + パッケージの**プライベート スコープ**に属するすべてのユーザーがインストールされていることができます、`rpkgs-private`データベース内のロール。 ただし、ユーザーが表示したり、独自のパッケージのみをアンインストールします。
    + データベース所有者は、共有またはプライベートのパッケージを操作できます。

**R コード**

パッケージをインストールする権限がある場合、R クライアントから、パッケージのいずれかの管理機能を実行し、パッケージが追加または削除するのには、コンピューティング コンテキストを指定します。  計算コンテキストは、ローカル コンピューターまたは SQL Server インスタンス上のデータベースの場合があります。 資格情報は、サーバーで、操作を完了できるかどうかを決定します。

**TRANSACT-SQL から**

実行するにはパッケージの管理関数、ストアド プロシージャからへの呼び出しで囲む`sp_execute_external_script`です。

### <a name="get-list-of-packages-in-a-sql-server-compute-context"></a>SQL Server のコンピューティング コンテキストでパッケージの一覧を取得します。

この例は、インスタンスにインストールされているパッケージを確認`myServer`、データベースに`TestDB`です。 パッケージの管理は、特定のデータベースとユーザーに制限されます。 ユーザーが指定されていない場合は、コンピューティング コンテキスト コールを実行するユーザーが使用されます。 詳細については、次を参照してください。[ロールによってパッケージの Scoping](#bkmk_scope)です。

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>リモート SQL Server のコンピューティング コンテキストのパッケージ パスを取得します。

この例では、計算コンテキスト **sqlServer** の *RevoScaleR*パッケージのパスを取得します。

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>複数のパッケージの場所を取得する

次の例では、計算コンテキスト **sqlServer** の **RevoScaleR** および *lattice*パッケージのパスを取得します。 複数のパッケージに関する情報を取得するには、パッケージ名を含む文字列のベクトルを渡します。

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```


### <a name="get-package-versions-on-a-remote-compute-context"></a>リモートのコンピューティング コンテキストでパッケージのバージョンを取得します。

コンピューティング コンテキストでインストールされているパッケージのビルド番号とバージョン番号を取得する、R コンソールからこのコマンドを実行*sqlServer*です。

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>SQL Server にパッケージをインストールする

この例ではインストール、**予測**パッケージとその依存関係、計算コンテキストを*sqlServer*です。

  ```R
  pkgs <- c("ggplot2")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="remove-a-package-from-sql-server"></a>パッケージを SQL Server から削除する

この例では、 **ggplot2** パッケージとその依存関係を計算コンテキスト *sqlServer*から削除します。

  ```R
  pkgs <- c("ggplot2")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
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
