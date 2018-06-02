---
title: SQL Server の R パッケージの同期 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5aa19e54917a421567c5ede2013e019de609d8b6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585228"
---
# <a name="r-package-synchronization-for-sql-server"></a>SQL Server の R パッケージの同期
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 に含まれる RevoScaleR のバージョンには、ファイル システムと、インスタンスとデータベース間のパッケージが使用されている R パッケージのコレクションを同期する機能が含まれています。

この機能は、SQL Server データベースに関連付けられた R パッケージのコレクションをバックアップするが簡単に提供されました。 この機能を使用して、そのデータベースで作業してデータ研究員によって使用されたすべての R パッケージは、データベースだけでなく、管理者は復元できます。

この記事は、パッケージの同期機能と使用方法について説明します、 [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages)次のタスクを実行する関数。

+ SQL Server データベース全体をパッケージの一覧を同期させる

+ パッケージが、個別のユーザーやユーザーのグループによって使用の同期します。

+ R. によって必要に応じて、新しいサーバー上のファイル システムにインストールされる、ユーザーのパッケージは、ユーザーは、別の SQL Server に移動した場合と、ユーザーの作業用のデータベースのバックアップを実行して、新しいサーバーに復元できます。

たとえば、これらのシナリオでパッケージの同期を使用する場合があります。

+ DBA は新しいマシンに SQL Server のインスタンスを復元し、R クライアントから接続し、実行をユーザーに要求する`rxSyncPackages`を更新し、そのパッケージを復元します。

+ 実行するために、ファイル システム上の R パッケージが破損するいると思われる`rxSyncPackages`SQL Server にします。

## <a name="requirements"></a>要件

パッケージの同期を使用することができます、前に、適切なバージョンの Microsoft R または Machine Learning のサーバーが必要です。 Microsoft R バージョン 9.1.0 またはそれ以降は、この機能が用意されています。 

有効にする必要がありますも、[パッケージ管理機能は](r-package-how-to-enable-or-disable.md)サーバーにします。

### <a name="determine-whether-your-server-supports-package-management"></a>サーバーがパッケージの管理をサポートするかどうかを確認します。

この機能は、SQL Server 2017 CTP 2 で使用できる以降です。

Microsoft r です。 最新バージョンを使用するインスタンスをアップグレードする SQL Server 2016 のインスタンスにこの機能を追加することができます。詳細については、次を参照してください。 [SQL Server R Services のアップグレードに使用する SqlBindR.exe](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

### <a name="enable-the-package-management-feature"></a>パッケージの管理機能を有効にします。

パッケージの同期を使用するには、個々 のデータベースと SQL Server インスタンスで、新しいパッケージ管理機能を有効にする必要があります。 詳細については、次を参照してください。[有効にするにまたは SQL Server 用のパッケージの管理を無効にする](r-package-how-to-enable-or-disable.md)です。

1. サーバーの管理者は、SQL Server インスタンスの機能を有効します。
2. 各データベースについて、管理者は、個々 のユーザー、権限付与をインストールしたり、R パッケージを共有するデータベース ロールの使用されます。

これを行うときに、RevoScaleR 関数をなど、使用できる[rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages)をデータベースにパッケージをインストールします。  ユーザーと使用可能なパッケージに関する情報は、SQL Server インスタンスに格納されます。 

パッケージの管理機能を使用して新しいパッケージを追加するたびに SQL Server およびファイル システムで、両方のレコードが更新されます。 この情報は、データベース全体の情報をパッケージ復元に使用できます。

### <a name="permissions"></a>アクセス許可

+ パッケージの同期関数を実行したユーザーは、SQL Server インスタンスと、パッケージであるデータベース プリンシパルのセキュリティをする必要があります。

+ 関数の呼び出し元は、これらのパッケージの管理ロールのいずれかのメンバーである必要があります: **rpkgs 共有**または**rpkgs プライベート**です。

+ としてマークされているパッケージを同期するために**共有**、関数が実行されている人のメンバである必要があります、 **rpkgs 共有**ロール、およびパッケージを移動している必要がありますがインストールされている共有するスコープのライブラリです。

+ としてマークされているパッケージを同期するために**プライベート**、パッケージまたは管理者の所有者は、関数を実行する必要がありますいずれかと、パッケージをプライベートにする必要があります。

+ 他のユーザーに代わってパッケージを同期するために、所有者必要があります bhe のメンバー、 **db_owner**データベース ロール。

## <a name="how-package-synchronization-works"></a>パッケージの同期のしくみ

パッケージの同期を使用するのには、呼び出す[rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages)の新機能である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)です。 

呼び出しごとに`rxSyncPackages`、SQL Server インスタンスとデータベースを指定する必要があります。 その後、またはいずれか、同期するためにパッケージを一覧表示パッケージ スコープを指定します。

1. 使用して SQL Server のコンピューティング コンテキストを作成、`RxInSqlServer`関数。 コンピューティング コンテキストを指定しない場合は、現在のコンピューティング コンテキストが使用されます。

2. 指定された計算コンテキストのインスタンスでデータベースの名前を指定します。 パッケージは、データベースごとに同期されます。

3. スコープ引数を使用して同期するためにパッケージを指定します。

    使用する場合**プライベート**スコープ、指定された所有者が所有するパッケージのみが同期されます。 指定した場合**共有**スコープ、データベース内のすべての非プライベート パッケージが同期されます。 
    
    いずれかを指定せず、関数を実行する場合**プライベート**または**共有**スコープ、すべてのパッケージが同期されます。

4. コマンドが成功した場合は、ファイル システム内の既存のパッケージが指定されたスコープの所有者と、データベースに追加されます。

    ファイル システムが破損している場合、データベースで保守管理の一覧に基づいて、パッケージが復元されます。

    パッケージの管理機能がターゲット データベースで使用可能でない場合、エラーが発生します"パッケージ管理機能するか、無効になって、SQL server またはバージョンが古すぎる"。

### <a name="example-1-synchronize-all-package-by-database"></a>例 1. データベースでのすべてのパッケージを同期します。

この例では、ローカル ファイル システムから、新しいパッケージを取得し、データベース [TestDB] で、パッケージをインストールします。 特定の所有者がないため、一覧には、プライベートと共有のスコープにインストールされているすべてのパッケージが含まれています。

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

次の例では、特定のユーザーにインストールされたパッケージのみを同期する方法を示します。 この例では、ユーザーが SQL ログイン名で識別される*user1*です。

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="related-resources"></a>関連リソース

[SQL Server の R パッケージの管理](install-additional-r-packages-on-sql-server.md)
