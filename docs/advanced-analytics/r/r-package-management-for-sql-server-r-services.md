---
title: "SQL Server の R パッケージの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f19982251b629d12215595685c0633b4c6b61c98
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="r-package-management-for-sql-server"></a>SQL Server の R パッケージの管理

このトピックでは、SQL Server のインスタンスで実行されている R パッケージの管理に使用できるパッケージの管理機能について説明します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="package-management-using-t-sql"></a>T-SQL を使用してパッケージの管理

Machine learning のジョブのサーバーを使用する場合は、これらの特権がある場合、コンピューターの管理者として R パッケージをインストールする続行することができます。

ただし、パッケージを他のユーザーと共有する必要がある場合、または複数の人が、サーバーで machine learning のジョブを実行する必要がある場合、パッケージの共有ライブラリを設定するより効率的です。 SQL Server では、データベース ロールを介して、これをサポートします。

データベース管理者は、ロールの設定、およびロールにユーザーを追加することを担当します。 ロールを介したデータベース管理者は追加または SQL Server 環境から R パッケージを削除するアクセス許可を持つユーザー、およびパッケージのインストールを監査することができますを制御できます。

### <a name="database-roles-for-package-management"></a>パッケージ管理のデータベース ロール

次の新しいデータベース ロールは、SQL Server のセキュリティで保護されたインストールし、R パッケージの管理をサポートします。

- `rpkgs-users`: すべてのメンバーによってインストールされた共有のパッケージを使用するユーザーをできるように、`rpkgs-shared`ロール。

- `rpkgs-private`: と同じ権限で共有のパッケージへのアクセスを提供する、`rpkgs-users`ロール。 このロールのメンバーは、プライベート スコープのパッケージをインストール、削除および使用することもできます。

-  `rpkgs-shared`: 同じアクセス許可を提供する、`rpkgs-private`ロール。 このロールのメンバーであるユーザーは、共有パッケージをインストールまたは削除することもできます。

- `db_owner`: 同じアクセス許可を持つ、`rpkgs-shared`ロール。 また、共有パッケージとプライベート パッケージの両方をインストールまたは削除する権利をユーザーに付与することもできます。

### <a name="creating-an-external-package-library-using-t-sql"></a>T-SQL を使用して外部パッケージ ライブラリを作成します。

さらに、T-SQL ステートメントをサポートしている SQL Server 2017**外部ライブラリの作成**、外部ライブラリのデータベース管理者による管理をサポートします。 現在このステートメントを使用して、Python パッケージや、Linux など、他のプラットフォームで実行用に作成されたパッケージの将来のサポートを計画し、r です。 追加の Windows ベースのライブラリを作成することができます。

詳細については、次を参照してください。[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。

## <a name="package-management-using-r"></a>R を使用するパッケージの管理

**RevoScaleR**パッケージには、関数簡単のインストールと R パッケージの管理をサポートするにはようになりましたが含まれています。 パッケージの管理用のデータベース ロールと組み合わせて、これらの新しい関数には、これらのシナリオがサポートされています。

- データ サイエンティストは、SQL Server コンピューターに管理アクセスしなくても、SQL Server に必要な R パッケージをインストールできます。
- データベース単位ごとに、パッケージがインストールされているし、データベースが移動されると、パッケージが一緒に移動します。
- パッケージを他のユーザーと共有すると簡単です。 ローカル パッケージ リポジトリを設定する場合、各データ サイエンティストは、自分のデータベースにパッケージをインストールするリポジトリを使用できます。
- データベース管理者は、R コマンドを実行する方法を学習する必要はありませんし、複雑なパッケージの依存関係を追跡する必要はありません。
- DBA は、インストール、アンインストール、またはパッケージを使用する SQL Server ユーザーが許可されているコントロールの使い慣れたデータベース ロールを使用できます。

### <a name="r-package-management-functions"></a>R パッケージの管理機能

次のパッケージ管理機能は、指定された計算コンテキストでパッケージのインストールと削除のための RevoScaleR で提供されます。

+ [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): 指定された計算コンテキストでインストールされているパッケージに関する情報を確認します。

+ [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): パッケージの zip 形式を指定したリポジトリから、またはローカルに保存されたを読み取ることにより、コンピューティング コンテキストにパッケージをインストールします。

+ [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): インストール済みパッケージのコンピューティング コンテキストから削除します。

+ [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): 指定された計算コンテキストで 1 つまたは複数のパッケージのパスを取得します。

+ [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): 指定された計算のコンテキストで、ファイル システムおよびデータベース間でパッケージのライブラリにコピーします。

+ [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): SQL Server 内で実行中にパッケージのライブラリ ツリーの検索パスを取得します。

これらのパッケージは、既定では、SQL Server 2017 も含まれます。 以上を使用するインスタンスをアップグレードする場合は、SQL Server 2016 のインスタンスにパッケージを追加することができます Microsoft R 9.0.1 です。 詳細については、次を参照してください。 [R をアップグレードするのを使用して SqlBindR.exe](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

これらの関数については、RevoScaleR 関数のリファレンス ページを参照してください: (https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

## <a name="how-package-management-works"></a>パッケージ管理のしくみ

パッケージをインストールするアクセス許可を持っている場合、R コードのパッケージ管理関数のいずれかを実行し、パッケージを追加または削除する計算コンテキストを指定します。 計算コンテキストは、ローカル コンピューターまたは SQL Server インスタンス上のデータベースの場合があります。 パッケージをインストールする呼び出しが SQL Server で実行されると、資格情報でサーバー上の操作が完了したかどうかが判断されます。 パッケージのインストール関数では、依存関係を確認し、ローカル計算コンテキストでの R パッケージのインストールなど、関連するパッケージを SQL Server にインストールできることを確認します。 パッケージをアンインストールする関数では、依存関係を計算し、SQL Server の他のパッケージで使用されなくなったパッケージが削除されていることを確認し、リソースを解放します。

各データ サイエンティストは、プライベート sandbox R パッケージを作成、他のユーザーに表示されていないプライベート パッケージをインストールできます。 パッケージをデータベースにスコープすることができます、各ユーザー データベースごとに分離されたパッケージのサンド ボックスを取得するため、別のバージョンの同じ R パッケージをインストールする簡単です。

新しいサーバーに、作業用のデータベースを移行する場合、すべてのパッケージの一覧を読み取るし、新しいサーバー上のデータベースにインストールを行うパッケージ同期関数を使用できます。

> [!NOTE]
> 
> パッケージの管理の R 関数は、Microsoft R Server 9.0.1 で始まる提供されます。 RevoScaleR の関数は、できない場合は、おそらく最新バージョンにアップグレードする必要があります。

### <a name="bkmk_scope"></a>ロールによるパッケージのスコープの設定

新しいパッケージ管理関数には、SQL Server の特定のデータベース上でのパッケージのインストールと使用のために 2 つのスコープが用意されています。

- **共有スコープ**

  *共有範囲*意味共有スコープのロールの権限が与えられているユーザー (`rpkgs-shared`) インストールして、指定したデータベースへのパッケージをアンインストールします。 共有スコープ ライブラリにインストールされたパッケージは、インストールされた R パッケージの使用を許可されたユーザーであれば、SQL Server 上のデータベースの他のユーザーが使用できます。

- **プライベート スコープ**

  *プライベート スコープ*意味プライベート スコープのロールのメンバーシップが与えられたユーザー (`rpkgs-private`) インストールしたり、ユーザーごとに定義されたプライベートなライブラリの場所にパッケージをアンインストールします。 そのため、プライベート スコープにインストールされているすべてのパッケージは、そのパッケージをインストールしたユーザーのみが使用できます。 言い換えると、SQL Server 上のユーザーは、他のユーザーがインストールしたプライベート パッケージを使用できません。

SQL Server 上のパッケージの展開と管理のために、 *共有* スコープと *プライベート* スコープのモデルを組み合わせてカスタムのセキュア システムを開発できます。

たとえば、共有スコープを使用して、データ サイエンティストのグループのリーダーやマネージャーにパッケージをインストールするアクセス許可を付与し、同じ SQL Server インスタンスの他のすべてのユーザーまたはデータ サイエンティストがそれらのパッケージを使用することができます。

また、ユーザー間をさらに厳格に分離するシナリオや、複数のバージョンのパッケージを使用するシナリオがあります。 この場合、プライベート スコープを使用して、個別のアクセス許可をデータ サイエンティストに付与し、必要なパッケージについてのみインストールと使用を許可することができます。 パッケージはユーザーごとにインストールされるため、1 人のユーザーがインストールしたパッケージは、同じ SQL Server データベースを使用する他のユーザーの作業に影響はありません。

### <a name="synchronizing-r-package-libraries"></a>同期の R パッケージ ライブラリ

SQL Server 2017 (および Microsoft R Server の 2017 年 4 月リリース) の CTP 2.0 リリースでは、新しい R 関数の*パッケージを同期する*です。

パッケージの同期では、データベース エンジンがパッケージを特定の所有者と、グループによって使用され、必要な場合、それらのパッケージをファイル システムに記述できますを追跡することを意味します。 これらのシナリオでは、パッケージの同期を使用できます。

+ SQL Server のインスタンス間で R パッケージを移動します。
+ 特定のユーザー用のパッケージを再インストールするか、データベースを復元した後にグループ化する必要があります。

詳細については、次を参照してください。 [rxSyncPackages](../r/package-install-uninstall-and-sync.md)です。

## <a name="examples"></a>使用例

これらの例では、パッケージの管理機能の基本的な使用法を示しています。 これらのコマンドを実行するには、インスタンスで R コマンドを実行する権限があることが必要です。

+ ターミナル リモート R から実行すると、SQL Server インスタンスを指定するコンピューティング コンテキスト オブジェクトを作成し、引数としてコンピューティング コンテキストを渡すこと、関数を実行します。

+ ストアド プロシージャからのパッケージ管理機能を実行する必要がありますをラップするそれらの呼び出しで`sp_execute_external_script`です。

### <a name="package-scoping"></a>パッケージのスコープ

この例は、インスタンスにインストールされているパッケージを確認`myServer`、データベースに`TestDB`です。 パッケージの管理は、特定のデータベースとユーザーに制限されます。 ユーザーが指定されていない場合は、コンピューティング コンテキスト コールを実行するユーザーが使用されます。 詳細については、次を参照してください。[ロールによってパッケージの Scoping](#bkmk_scope)です。

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-location-on-a-remote-sql-server-compute-context"></a>リモート SQL Server のコンピューティング コンテキストでパッケージの場所を取得します。

この例では、計算コンテキスト **sqlServer** の *RevoScaleR*パッケージのパスを取得します。

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>複数のパッケージの場所を取得する

次の例では、計算コンテキスト **sqlServer** の **RevoScaleR** および *lattice*パッケージのパスを取得します。 複数のパッケージに関する情報を取得するには、パッケージ名を含む文字列のベクトルを渡します。

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```

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

### <a name="get-package-versions-on-a-remote-compute-context"></a>リモートのコンピューティング コンテキストでパッケージのバージョンを取得します。

コンピューティング コンテキストでインストールされているパッケージのビルド番号とバージョン番号を取得する、R コンソールからこのコマンドを実行*sqlServer*です。

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>SQL Server にパッケージをインストールする

この例では、 **ggplot2** パッケージとその依存関係を計算コンテキスト *sqlServer*にインストールします。

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

### <a name="package-synchronization"></a>パッケージの同期

次の例では、データベースで管理されているパッケージの一覧で、ファイル システムにインストールされているパッケージを同期します。 一部のパッケージが存在しない場合は、ファイル システムにインストールされます。

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

## <a name="next-steps"></a>次の手順

[有効にするにまたは R パッケージの管理を無効にする方法](../r/r-package-how-to-enable-or-disable.md)

