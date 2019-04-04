---
title: R パッケージとファイル システム - SQL Server Machine Learning サービスからの同期
description: SQL Server での R ライブラリは、ファイル システムにインストールされている新しいバージョンに更新します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 57677e8d7573411be2e77baa7ffd8564ec9cbeb4
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511359"
---
# <a name="r-package-synchronization-for-sql-server"></a>SQL Server の R パッケージの同期
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 に含まれる RevoScaleR のバージョンには、ファイル システムと、インスタンスとデータベース間のパッケージが使用されている R パッケージのコレクションを同期する機能が含まれています。

この機能は、SQL Server データベースに関連付けられている R パッケージのコレクションをバックアップするが容易に提供されました。 この機能を使用して、そのデータベースでの作業データ サイエンティストによって使用されていたすべての R パッケージは、データベースだけでなく、管理者は復元できます。

この記事では、パッケージの同期機能と使用方法について説明します、 [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages)次のタスクを実行する関数。

+ SQL Server データベースの全体のパッケージの一覧を同期します。

+ ユーザーのグループまたは個々 のユーザーによって使用されるパッケージを同期します。

+ ユーザー用のパッケージは R で必要に応じて、新しいサーバー上のファイル システムにインストールする場合は、ユーザーが別の SQL Server、およびユーザーの作業用のデータベースのバックアップを作成し、新しいサーバーに復元

たとえば、これらのシナリオでパッケージとの同期を使用する可能性があります。

+ DBA は、新しいマシンに SQL Server のインスタンスを復元し、R クライアントから接続を実行するユーザーに要求する`rxSyncPackages`を更新し、そのパッケージを復元します。

+ 実行するため、ファイル システム上に R パッケージが破損するいると思われる`rxSyncPackages`SQL server。

## <a name="requirements"></a>必要条件

パッケージとの同期を使用する前に、適切なバージョンの Microsoft R または Machine Learning Server が必要です。 Microsoft R バージョン 9.1.0 またはそれ以降、この機能が提供されます。 

有効にする必要があります、[パッケージ管理機能](r-package-how-to-enable-or-disable.md)サーバー。

### <a name="determine-whether-your-server-supports-package-management"></a>サーバーがパッケージの管理をサポートするかどうかを確認します。

この機能は、SQL Server 2017 CTP 2 で使用できる、またはそれ以降です。

SQL Server 2016 のインスタンスには Microsoft r です。 最新バージョンを使用するインスタンスをアップグレードすることでこの機能を追加することができます。詳細については、[SQL Server R Services のアップグレードを使用して SqlBindR.exe](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)を参照してください。

### <a name="enable-the-package-management-feature"></a>パッケージの管理機能を有効にします。

パッケージとの同期を使用するには、個々 のデータベースと、SQL Server インスタンスで、新しいパッケージ管理機能を有効にする必要があります。 詳細については、[を有効にするか、SQL Server のパッケージ管理を無効にする](r-package-how-to-enable-or-disable.md)を参照してください。

1. サーバーの管理者では、SQL Server インスタンスの機能を有効します。
2. データベースごとに管理者は、個々 のユーザーする権限を付与 R のパッケージ共有のインストールまたはデータベース ロールを使用します。

これが完了したら、RevoScaleR 関数をなど、使用できる[rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages)をデータベースにパッケージをインストールします。  ユーザーおよび使用できるパッケージの詳細については、SQL Server インスタンスに格納されます。 

パッケージの管理機能を使用して新しいパッケージを追加するたびに、SQL Server とファイル システムで、両方のレコードが更新されます。 この情報は、データベース全体のパッケージ情報を復元できます。

### <a name="permissions"></a>アクセス許可

+ パッケージの同期機能を実行したユーザーは、SQL Server インスタンスとパッケージがあるデータベース プリンシパルのセキュリティである必要があります。

+ 関数の呼び出し元はこれらのパッケージの管理ロールのいずれかのメンバーである必要があります: **rpkgs 共有**または**rpkgs プライベート**します。

+ としてマークされているパッケージを同期する**共有**、関数を実行するユーザーのメンバである必要があります、 **rpkgs 共有**する必要がありますをインストールされているロール、および移動中のパッケージを共有するスコープのライブラリです。

+ としてマークされているパッケージを同期する**プライベート**、パッケージまたは管理者の所有者は、関数を実行する必要がありますいずれかと、パッケージはプライベートである必要があります。

+ 他のユーザーに代わってパッケージを同期する、所有者必要があります bhe のメンバー、 **db_owner**データベース ロール。

## <a name="how-package-synchronization-works"></a>パッケージの同期のしくみ

パッケージとの同期を使用するには、呼び出す[rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages)の新機能である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)します。 

呼び出しごとに`rxSyncPackages`、SQL Server インスタンスとデータベースを指定する必要があります。 次に、いずれかを同期するパッケージを一覧表示またはパッケージ スコープを指定します。

1. 使用して、SQL Server 計算コンテキストを作成、`RxInSqlServer`関数。 コンピューティング コンテキストを指定しない場合は、現在のコンピューティング コンテキストが使用されます。

2. 指定した計算コンテキストのインスタンスでデータベースの名前を提供します。 パッケージは、データベースごとに同期されます。

3. 同期スコープ引数を使用してパッケージを指定します。

    使用する場合**プライベート**スコープ、指定された所有者によって所有されているパッケージのみが同期されます。 指定した場合**共有**データベース内のすべての非プライベート パッケージのスコープを同期します。 
    
    いずれかを指定せず、関数を実行する場合**プライベート**または**共有**スコープ、すべてのパッケージが同期されます。

4. コマンドが成功した場合、ファイル システム内の既存のパッケージは、指定したスコープと所有者を持つ、データベースに追加されます。

    ファイル システムが壊れている場合は、データベースで管理一覧に基づいて、パッケージが復元されます。

    パッケージの管理機能が、ターゲット データベースで利用できない場合、エラーが発生します。「SQL Server のかは、パッケージの管理機能が無効またはバージョンが古すぎます」

### <a name="example-1-synchronize-all-package-by-database"></a>例 1. データベースでのすべてのパッケージを同期します。

この例では、ローカル ファイル システムから、新しいパッケージを取得し、[TestDB] データベースでパッケージをインストールします。 特定の所有者がないため、一覧には、プライベートと共有のスコープにインストールされているすべてのパッケージが含まれています。

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

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>例 3。 所有者によって同期されているパッケージを制限します。

次の例では、特定のユーザーに対してインストールされたパッケージのみを同期する方法を示します。 この例で、ユーザーは、SQL ログイン名によって識別*user1*します。

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="related-resources"></a>関連リソース

[SQL Server の R パッケージの管理](install-additional-r-packages-on-sql-server.md)
