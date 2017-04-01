---
title: "SQL Server R Services の R パッケージ管理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 7
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# SQL Server R Services の R パッケージ管理
SQL Server のインスタンスで実行されている R パッケージを管理しやすくするために、**RevoScaleR** パッケージには、R パッケージのインストールと管理をサポートする関数が追加されました。 

この新しい機能で、次のシナリオがサポートされます。

- データ サイエンティストは、SQL Server コンピューターに対する管理者のアクセス権を持っていなくても、必要な R パッケージを SQL Server にインストールできます。 パッケージはデータベースごとにインストールされます。
- パッケージを他のユーザーと共有する操作は簡単です。 ローカル パッケージ リポジトリを確立し、各データ サイエンティストがパッケージを各データベースにインストールするだけです。
- データベース管理者は R コマンドの実行方法や、パッケージの依存関係を把握する必要はありません。 DBA は、データベース ロールを使用して、パッケージのインストール、アンインストール、または使用を許可する SQL Server ユーザーを制御できます。
 
**機能**

* データベース管理者は、ロールの設定とユーザーのロールへの追加に責任を持ち、SQL Server 環境から R パッケージを追加または削除するアクセス許可を持つユーザーを制御できます。
* パッケージをインストールするアクセス許可を持っている場合、R コードのパッケージ管理関数のいずれかを実行し、パッケージを追加または削除する計算コンテキストを指定します。 計算コンテキストは、ローカル コンピューターまたは SQL Server インスタンス上のデータベースの場合があります。 
* パッケージをインストールする呼び出しが SQL Server で実行されると、資格情報でサーバー上の操作が完了したかどうかが判断されます。 
- パッケージのインストール関数では、依存関係を確認し、ローカル計算コンテキストでの R パッケージのインストールなど、関連するパッケージを SQL Server にインストールできることを確認します。
- パッケージをアンインストールする関数では、依存関係を計算し、SQL Server の他のパッケージで使用されなくなったパッケージが削除されていることを確認し、リソースを解放します。
- 各データ サイエンティストは、他のユーザーに表示されない非公開のパッケージをインストールし、独自の R パッケージを使用する隔離されたサンドボックスにすることができます。
-  複数のパッケージのスコープを 1 つのデータベースに設定して、各ユーザーが各データベースに隔離されたパッケージ サンドボックスを使用できるので、同じ R パッケージのさまざまなバージョンを簡単にインストールできます。 

> [!NOTE]
> 現在、この機能は [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 専用としてリリースされています。 

## <a name="database-roles-and-database-scoping"></a>データベース ロールとデータベースのスコープ設定

新しいパッケージ管理関数には、SQL Server の特定のデータベース上でのパッケージのインストールと使用のために 2 つのスコープが用意されています。

- **共有スコープ**

  *共有スコープ*とは、共有スコープ ロール (**rpkgs-shared**) に対するアクセス許可が付与されたユーザーが、指定したデータベースでパッケージをインストールおよびアンインストールできることを意味します。 共有スコープ ライブラリにインストールされたパッケージは、インストールされた R パッケージの使用を許可されたユーザーであれば、SQL Server 上のデータベースの他のユーザーが使用できます。 

- **プライベート スコープ** 

  *プライベート スコープ*とは、プライベート スコープ ロール (**rpkgs-private**) のメンバーシップが与えられたユーザーが、ユーザーごとに定義されているプライベート ライブラリの場所でパッケージをインストールまたはアンインストールできることを意味します。 そのため、プライベート スコープにインストールされているすべてのパッケージは、そのパッケージをインストールしたユーザーのみが使用できます。 言い換えると、SQL Server 上のユーザーは、他のユーザーがインストールしたプライベート パッケージを使用できません。 

SQL Server 上のパッケージの展開と管理のために、*共有*スコープと*プライベート* スコープのモデルを組み合わせてカスタムのセキュア システムを開発できます。 

たとえば、共有スコープを使用して、データ サイエンティストのグループのリーダーやマネージャーにパッケージをインストールするアクセス許可を付与し、同じ SQL Server インスタンスの他のすべてのユーザーまたはデータ サイエンティストがそれらのパッケージを使用することができます。 

また、ユーザー間をさらに厳格に分離するシナリオや、複数のバージョンのパッケージを使用するシナリオがあります。 この場合、プライベート スコープを使用して、個別のアクセス許可をデータ サイエンティストに付与し、必要なパッケージについてのみインストールと使用を許可することができます。 パッケージはユーザーごとにインストールされるため、1 人のユーザーがインストールしたパッケージは、同じ SQL Server データベースを使用する他のユーザーの作業に影響はありません。 

### <a name="database-roles-for-package-management"></a>パッケージ管理のデータベース ロール

次の新しいデータベース ロールは、SQL R サービスの安全なインストールとパッケージをサポートしています。 

- **rpkgs-users** ユーザーは、**rpkgs-shared** ロールのメンバーによってインストールされた共有パッケージを使用することができます。

- **rpkgs-private** **rpkgs-users** ロールと同じアクセス許可で共有パッケージにアクセスできます。 このロールのメンバーは、プライベート スコープのパッケージをインストール、削除および使用することもできます。

-  **rpkgs-shared** **rpkgs-private** ロールと同じアクセス許可を付与します。 このロールのメンバーであるユーザーは、共有パッケージをインストールまたは削除することもできます。 
 
- **db_owner** - **rpkgs-shared** ロールと同じアクセス許可を持ちます。 また、共有パッケージとプライベート パッケージの両方をインストールまたは削除する権利をユーザーに付与することもできます。



## <a name="new-package-management-functions"></a>新しいパッケージ管理機能


+ `rxInstalledPackages`: 指定した計算コンテキストにインストールされているパッケージに関する情報を検索します。

+ `rxInstallPackages`: 指定したリポジトリから、またはローカルに保存されている zip 形式のパッケージを読み取ることで、計算コンテキストにパッケージをインストールします。

+ `rxRemovePackages`: インストール済みのパッケージを計算コンテキストから削除します。

+ `rxFindPackage`: 指定した計算コンテキストで 1 つ以上のパッケージのパスを取得します。

+ `rxSqlLibPaths`: パッケージのライブラリ ツリーの検索パスを SQL Server 内の実行中に取得します。

## <a name="examples"></a>使用例

### <a name="get-package-location-on-sql-server-compute-context"></a>SQL Server 計算コンテキストでパッケージの場所を取得する

この例では、計算コンテキスト *sqlServer* の **RevoScaleR** パッケージのパスを取得します。

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```
  
  ### <a name="get-locations-for-multiple-packages"></a>複数のパッケージの場所を取得する

次の例では、計算コンテキスト *sqlServer* の **RevoScaleR** および **lattice** パッケージのパスを取得します。 複数のパッケージに関する情報を検索するときに、パッケージ名を含む文字列ベクトルを渡します。

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```



### <a name="list-packages-in-specified-compute-context"></a>指定した計算コンテキストのパッケージを列挙する

この例では、計算コンテキスト *sqlServer* にインストールされているすべてのパッケージを列挙し、コンソールに表示します。

  ```R
  myPackages <- rxInstalledPackages(computeContext = sqlServer) 
  myPackages
  ```

### <a name="get-package-versions"></a>パッケージのバージョンを取得する

この例では、計算コンテキスト *sqlServer* にインストールされているパッケージのビルド番号とバージョン番号を取得します。

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer) 
```

### <a name="install-a-package-on-sql-server"></a>SQL Server にパッケージをインストールする

この例では、**ggplot2** パッケージとその依存関係を計算コンテキスト *sqlServer* にインストールします。

  ```R
  pkgs <- c("ggplot2")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="remove-a-package-from-sql-server"></a>パッケージを SQL Server から削除する

この例では、**ggplot2** パッケージとその依存関係を計算コンテキスト *sqlServer* から削除します。

  ```R
  pkgs <- c("ggplot2")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

## <a name="see-also"></a>参照

[R パッケージの管理を有効または無効にする方法](../../advanced-analytics/r-services/how-to-enable-or-disable-r-package-management.md)