---
title: "SQL Server の R パッケージの同期 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: ed7dbf99b0f492b5ca8879bb67a7256fdfae3306
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---

# <a name="r-package-synchronization-for-sql-server"></a>SQL Server の R パッケージの同期

SQL Server 2017 には、ファイル システムと、インスタンスとデータベース間のパッケージが使用されている R パッケージのコレクションを同期する機能が含まれています。
この機能は、SQL Server データベースに関連付けられた R パッケージのコレクションをバックアップするが簡単に提供されました。 この機能を使用して、そのデータベースで作業してデータ研究員によって使用されたすべての R パッケージは、データベースだけでなく、管理者は復元できます。

このトピックは、パッケージの同期機能と使用方法について説明します、 [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages)次のタスクを実行する関数。

+ SQL Server データベース全体をパッケージの一覧を同期させる

+ パッケージが、個別のユーザーやユーザーのグループによって使用の同期します。

+ R. によって必要に応じて、新しいサーバー上のファイル システムにインストールされる、ユーザーのパッケージは、ユーザーは、別の SQL Server に移動した場合と、ユーザーの作業用のデータベースのバックアップを実行して、新しいサーバーに復元できます。

たとえば、これらのシナリオでパッケージの同期を使用する場合があります。

+ DBA は新しいマシンに SQL Server のインスタンスを復元し、R クライアントから接続し、実行をユーザーに要求する`rxSyncPackages`を更新し、そのパッケージを復元します。

+ 実行するために、ファイル システム上の R パッケージが破損するいると思われる`rxSyncPackages`SQL Server にします。

## <a name="requirements"></a>必要条件

パッケージの同期を使用することができます、前に、Microsoft R の適切なバージョンが必要し、関連するデータベース機能を有効にします。

### <a name="determine-whether-your-server-supports-package-management"></a>サーバーがパッケージの管理をサポートするかどうかを確認します。

この機能は、SQL Server 2017 CTP 2 で使用できる以降です。

この機能は、Microsoft R バージョン 9.1.0 で R 関数を使用するため機能を追加できますこの SQL Server 2016 のインスタンスには Microsoft r です。 最新バージョンを使用するインスタンスをアップグレードすることで詳細については、次を参照してください。 [SQL Server R Services のアップグレードに使用する SqlBindR.exe](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

### <a name="enable-the-package-management-feature"></a>パッケージの管理機能を有効にします。

パッケージの同期を使用するには、R のタスクの実行に使用される個々 のデータベースと SQL Server インスタンスで、新しいパッケージ管理機能を有効にする必要があります。

1. サーバーの管理者は、SQL Server インスタンスの機能を有効します。
2. 各データベースについて、管理者によって、インストールしたり、R パッケージを共有する機能がユーザーに許可されます。

これを行うときに、ユーザーと、インストールされているパッケージに関する情報は、SQL Server インスタンスに格納されます。 この情報は、ファイル システムでの R パッケージの更新を適用できます。

パッケージの管理機能を使用して新しいパッケージを追加するたびに SQL Server およびファイル システムで、両方のレコードが更新されます。

> [!NOTE]
> インストールする場合がされた R パッケージ、従来の方法では、R ツールを使用して、ファイル システムに直接パッケージをインストールするパッケージの同期を使用することはできません。
### <a name="permissions"></a>Permissions

+ パッケージの同期関数を実行したユーザーは、SQL Server インスタンスと、パッケージであるデータベース プリンシパルのセキュリティをする必要があります。

+ 関数の呼び出し元は、これらのパッケージの管理ロールのいずれかのメンバーである必要があります: **rpkgs 共有**または**rpkgs プライベート**です。

+ としてマークされているパッケージを同期するために**共有**、関数が実行されている人のメンバである必要があります、 **rpkgs 共有**ロール、およびパッケージを移動している必要がありますがインストールされている共有するスコープのライブラリです。

+ としてマークされているパッケージを同期するために**プライベート**、パッケージまたは管理者の所有者は、関数を実行する必要がありますいずれかと、パッケージをプライベートにする必要があります。

+ 所有者を他のユーザーに代わってパッケージを同期するのメンバーである必要があります、 **db_owner**データベース ロール。

## <a name="how-package-synchronization-works"></a>パッケージの同期のしくみ

パッケージの同期を使用するのには、呼び出す[rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages)の新機能である[RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)です。 Sp_execute_external_script を使用して SQL Server からこの関数を呼び出すことができます、または R クライアントをリモートから実行し、SQL Server のコンピューティング コンテキストを指定することができます。 

パッケージは呼び出しごとに、データベース レベルで管理されるため`rxSyncPackages`、SQL Server インスタンスおよびデータベース、およびパッケージの一覧を指定するか、パッケージ スコープを指定する必要があります。

1. 使用して SQL Server のコンピューティング コンテキストを作成、`RxInSqlServer`関数。 コンピューティング コンテキストを指定しない場合は、現在のコンピューティング コンテキストが使用されます。

2. 指定された計算コンテキストのインスタンスでデータベースの名前を指定します。 パッケージは、データベースごとに管理されます。

3. 同期するためにパッケージを一覧表示します。

4.  必要に応じて、使用して、*スコープ*パッケージ 1 人のユーザーまたはユーザーのグループを同期するかどうかを示すために渡す引数。 いずれかを指定せず、関数を実行する場合**プライベート**または**共有**スコープのすべてのスコープの使用可能なパッケージのセット全体、ユーザーがコピーされます。

コマンドが正常に実行された場合、ファイル システム内の既存のパッケージは、指定されたスコープの所有者と、データベースに追加されます。 ファイル システムが破損している場合、データベースで保守管理の一覧に基づいて、パッケージが復元されます。

### <a name="example-1-synchronize-all-package-by-database"></a>例 1. データベースでのすべてのパッケージを同期します。

この例では、データベース [TestDB] でインストールされているすべてのパッケージを取得します。 特定の所有者がないため、一覧には、プライベートと共有のスコープにインストールされているすべてのパッケージが含まれています。

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="example-2-restrict-synchronized-packages-by-scope"></a>例 2。 スコープによって同期されているパッケージを制限します。

次の例では、指定されたスコープ内のパッケージのみを同期します。

```R
#Shared scope
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)

#Private scope
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>例 3 です。 所有者によって同期されているパッケージを制限します。

次の例では、特定のユーザーにインストールされたパッケージのみを取得する方法を示します。 この例では、ユーザーが SQL ログイン名で識別される*user1*です。

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

### <a name="example-4-restrict-synchronized-packages-by-owner"></a>例 4 です。 所有者によって同期されているパッケージを制限します。

次の例では、データベースで管理されているパッケージの一覧で、ファイル システムにインストールされているパッケージを同期します。 いずれかのパッケージが見つからない場合、ファイル システムにインストールされます。

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

## <a name="related-resources"></a>関連リソース

[SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)

