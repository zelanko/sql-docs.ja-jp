---
title: "SQL Server の R パッケージの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
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
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: cebafeabd73260f166244e963754a2bd740bfe0f
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="r-package-management-for-sql-server"></a>SQL Server の R パッケージの管理

この記事では、SQL Server 2017 および SQL Server 2016 での R パッケージを管理するための機能について説明します。

+ R パッケージを管理するための推奨事項 
+ SQL Server 2016 と 2017 年 1 の間でのパッケージ管理の変更

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="recommended-methods-for-package-management"></a>パッケージの管理に推奨される方法

SQL Server 2016 および SQL Server 2017 年 1 の場合は、コンピューターの管理者は、機械学習が有効になっている各インスタンス用のパッケージをインストールできます。 

パッケージは、インスタンス ライブラリを使用して、ファイル システムにインストールされ、インスタンス間で共有することはできません。 これは、現在、SQL Server 2016 および SQL Server 2017 の両方の推奨される方法です。

+ [SQL Server に追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
+ [SQL Server にインストールされているパッケージの確認](determine-which-packages-are-installed-on-sql-server.md)

さらがあれば**dbo**ロールのメンバーシップ、機械学習が有効になっている SQL Server のインスタンスにパッケージをインストールできます R リモート クライアントから RevoScaleR を新しい関数を使用しています。

+ [パッケージのインストール用の新しい R 関数](#bkmk_remoteInstall)

### <a name="installation-on-servers-with-no-internet-access"></a>インターネットにアクセスできないサーバーへのインストール

使用することが必要な R パッケージのバージョンを調べるし、すべての依存関係のパッケージの提供を容易にできるように、 [miniCRAN](https://mran.microsoft.com/package/miniCRAN)です。 この R パッケージは、対象パッケージの一覧を取得し、すべての依存関係と共に、zip 形式で対象のパッケージを含むローカル リポジトリを作成します。 サーバーにコピーする、オフライン、または、複数のインスタンス間でリポジトリを共有できます。

詳細については、次を参照してください。 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成する](create-a-local-package-repository-using-minicran.md)です。

### <a name="python-packages"></a>Python パッケージ

新しい Python パッケージのインストールでは、同じガイドラインに従います。 

+ 現在の Python のバージョンとの互換性を確認するのには、事前に Python パッケージを確認します。
+ セキュリティを強化した SQL Server 環境を Python パッケージの適合性を評価します。
+ Python tools を使用して、管理者としてパッケージをインストールするには
+ インスタンス ライブラリでのみ SQL Server のコンテキストで実行する必要があるパッケージをインストールします。 
+ テストに複数の環境を使用する場合、実稼働環境であれば、確認インスタンス ライブラリで、同じバージョンの Python パッケージがインストールされていることします。

インストール手順については、次を参照してください[SQL Server に新しい Python パッケージをインストール。](../python/install-additional-python-packages-on-sql-server.md)

## <a name="features-for-package-management-in-sql-server-2016-and-sql-server-2017"></a>SQL Server 2016 および SQL Server 2017 でパッケージの管理の機能

SQL Server 2017 は、データベース管理者によって R (および Python) のパッケージを簡単に管理をサポートするために一部の新機能を追加します。 これらの新機能は、次のとおりです。

+ インストールまたは T-SQL を使用してパッケージ ライブラリの管理機能
+ データベース ロールを介して、データベース レベルでのユーザー アクセス権を管理します。 

今後のリリースでは、データベース管理者によってパッケージの管理の主な方法を提供し、必要なライブラリをインストールするデータ サイエンティスト向けより容易にこれらの機能が必要です。

について同時に、Microsoft R Server と Machine Learning サーバー追加される新しい R 関数をインストールして、SQL Server のコンピューティング コンテキストでパッケージを共有しやすくします。 これらの関数は、T-SQL に基づいて SQL Server の機能に関係なく動作し、R クライアントをリモートから実行する対象としています。

このセクションでは、これらの機能の概要を示します。

### <a name="bkmk_remoteInstall"></a>パッケージのインストール用の新しい RevoScaleR 関数 

R Server または Machine Learning のサーバーの最新バージョンを持つユーザーで新しい関数にも使用できます[ **RevoScaleR** ](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)パッケージを SQL Server のコンピューティング コンテキストとして指定されたインスタンスにインストールします。

+ データ サイエンティストは、SQL Server コンピューターに直接アクセスしなくても、SQL Server に必要な R パッケージをインストールできます。 ただし、ユーザーがデータベース所有者のメンバーをする必要があります (**dbo**) の役割です。

+ ユーザーは、共有スコープを持つパッケージをインストールすることによって、他のユーザーとパッケージを共有できます。 同じ SQL Server データベースの権限のある他のユーザーは、パッケージにアクセスできます。

+ ユーザーは、プライベート sandbox R パッケージを作成、他のユーザーに表示されていないプライベート パッケージをインストールできます。

+ パッケージの同期により、パッケージの簡単なバックアップと復元

#### <a name="package-installation-functions"></a>パッケージのインストール機能

次のパッケージ管理機能は、指定された計算コンテキストでパッケージのインストールと削除のための RevoScaleR で提供されます。

-   [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages): 指定された計算コンテキストでインストールされているパッケージに関する情報を確認します。

-   [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages): パッケージの zip 形式を指定したリポジトリから、またはローカルに保存されたを読み取ることにより、コンピューティング コンテキストにパッケージをインストールします。

-   [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages): インストール済みパッケージのコンピューティング コンテキストから削除します。

-   [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage): 指定された計算コンテキストで 1 つまたは複数のパッケージのパスを取得します。

-   [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages): 指定された計算のコンテキストで、ファイル システムおよびデータベース間でパッケージのライブラリにコピーします。

-   [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths): SQL Server 内で実行中にパッケージのライブラリ ツリーの検索パスを取得します。

これらの関数を使用するには、必要なアクセス許可のある、SQL Server のコンピューティング コンテキストを使用して SQL Server のインスタンスに接続します。 

> [!IMPORTANT]
> 接続に使用する資格情報は、サーバーで、操作を完了できるかどうかを決定します。

これらのパッケージのインストール機能の依存関係を確認してローカル コンピューティング コンテキストで R パッケージのインストールと同じように、SQL Server に関連するすべてのパッケージをインストールすることができます。 パッケージをアンインストールする関数では、依存関係を計算し、SQL Server の他のパッケージで使用されなくなったパッケージが削除されていることを確認し、リソースを解放します。

SQL Server 2017 にインストールされている RevoScaleR のバージョンでは、これらの新しい関数が含まれています。 これらの関数を取得することもできます。 [SQL Server インスタンスをアップグレードする](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)の最新のバージョンを使用する[Microsoft R Server または Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server)です。 使用するバージョン 9.0.1 またはそれ以降。

#### <a name="package-synchronization-functions"></a>パッケージの同期関数

パッケージの同期は、R パッケージのみの新しい機能です。 データベース エンジンは、パッケージは、特定の所有者と、グループによって使用され、必要な場合、それらのパッケージをファイル システムに記述できますを追跡します。 通常これらのシナリオでは、パッケージの同期を使用します。

+ SQL Server のインスタンス間で R パッケージを移動するには。
+ 特定のユーザー用のパッケージを再インストールするか、データベースを復元した後にグループ化する必要があります。

有効にして、この機能を使用する方法の詳細については、次を参照してください。 [for SQL Server の R パッケージ同期](package-install-uninstall-and-sync.md)です。

### <a name="package-management-using-t-sql"></a>T-SQL を使用してパッケージの管理

SQL Server 2017 は、DBA は、データベース レベルでの R パッケージより詳細に制御を提供する新しい T-SQL ステートメントを追加します。 DBA は、Python tools または R を使用する方法を学習する必要はありませんをする必要があり、他のユーザーと共有するパッケージをインストールする機能を R または Python のユーザーに付与できません。 代わりにする必要があります。

この機能は、マルチ ユーザー環境でのコラボレーションとバージョンの管理が容易にします。 例。

+ 他のユーザーと、チームで開発したパッケージを共有するには。
+ 複数のアナリストは、同じデータベースで作業しているおよび同じパッケージの異なるバージョンを使用する必要があります。
+ 同時にバックアップを実行して、操作を復元する場合に、データベース、または移動するパッケージとそのアクセス許可を移動するには。

SQL Server 2017 でパッケージの管理は、これらの新しいデータベース オブジェクトと機能に依存します。

+ [新しいデータベース ロール](#bkmk_roles)、管理するためのアクセスをパッケージ化および使用
+ [外部ライブラリの作成](#bkmk_createExternalLibrary)ステートメントでは、サーバーをライブラリのパッケージをアップロードします。

これらの機能の使用には、インスタンスおよびデータベース レベルでいくつか追加の準備が必要です。 

+  明示的にデータベース管理者は、パッケージ管理機能を有効に、必要なデータベース オブジェクトを作成するスクリプトを実行して必要があります。 詳細については、次を参照してください。 [R パッケージの管理を有効にする方法](r-package-how-to-enable-or-disable.md)です。

+ ユーザーは、データベース レベルで、ロールに割り当てる必要があります。 これらのロールは、共有またはプライベートのパッケージをインストールする機能をユーザーに提供します。

+ パッケージのライブラリをインストールするには、外部ライブラリの作成、新しい T-SQL ステートメントを使用します。 ただし、すべてのパッケージの依存関係を事前に準備ができているし、1 つの zip ファイルの一部としてインストールする必要があります。

> [!NOTE]
> ここで説明する機能は、現時点で完全に機能は、今後のリリースには、パッケージのライブラリを準備して依存関係の管理を容易にできるように追加の機能強化が含まれています。 R パッケージのインストールに慣れている場合は、今のところ、R ツールを使用するように続行することをお勧めします。

#### <a name="bkmk_createExternalLibrary"></a> CREATE EXTERNAL LIBRARY 

[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)データベース管理者がユーザーの R ツールをしなくてもパッケージを操作に役立つ SQL Server 2017 に導入された新しい T-SQL ステートメントです。 

使用する、**外部ライブラリの作成**zip 形式のファイル形式でインスタンス外部のライブラリにアップロードするステートメント。 承認されたユーザー、ライブラリにアクセスし、自分で使用するためをインストールします。

たとえば、R プロジェクトごとに異なるバージョンの複数のコピーを作成できます。 別個のライブラリとしてアップロードするには、いくつかのバージョンをプライベートに保持し、いくつかのバージョンを他のユーザーと共有することができます。

"Library"は、基本的に、1 つの名前のユーザーを使用できるようにする外部のパッケージのコレクションです。 たとえば、外部ライブラリとして SQL Server に、次のいずれかを公開する可能性があります。

+ 依存関係のないと、作成した 1 つの R パッケージ
+ をインストールするパッケージとインストールに必要な依存関係
+ 特定のタスクまたはその依存関係と、プロジェクトに関連する R パッケージのコレクション

ライブラリの名前は、パッケージまたは SQL Server でパッケージのコレクションを管理するためと、インストールされているパッケージから独立していることができます。 ただし、ライブラリ名は、インスタンス間で一意である必要があります。

このステートメントを使用するには、パッケージ管理機能をインスタンスで有効にする必要があります。 詳細については、次を参照してください。[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。

> [!NOTE]
> 現在このステートメントを使用して、r です。 サポートが将来的に Python パッケージと、Linux などの他のプラットフォームで実行されるパッケージで計画的なだけの Windows ベースのライブラリを作成することができます。

外部のライブラリは、サーバーにアップロードされている、インスタンスに関連付けられた R パッケージのライブラリをインストールする必要があります。 これにはこれを行ういくつかの方法があります。

+ 標準的な R コマンドを実行`install.packages`sp_execute_external_script 内です。 パッケージをインストールするアクセス許可を持つアカウントを使用して接続をしてください。

+ リモート R クライアントから SQL Server に接続し、実行[rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) SQL Server のコンピューティング コンテキストでします。 もう一度、アクセス許可が必要パッケージのインストールにこれを行うプライベートまたは共有のスコープのいずれか。

すべてのパッケージの依存関係が提供されるように、使用をお勧め[miniCRAN](create-a-local-package-repository-using-minicran.md)ローカル リポジトリを作成します。 その zip ファイルを使用して、対象のパッケージとその依存関係をインストールすることができますし、します。

#### <a name="bkmk_roles"></a>パッケージの管理用のデータベース ロール 

パッケージの管理の SQL Server で提供される新しいロールは既定では、機械学習をインストールして有効になっている場所のインスタンスであっても含まれていません。 スクリプトを実行しての説明に従ってここで、ロールを追加する必要があります:[を有効にするか、パッケージの管理を無効にする](r-package-how-to-enable-or-disable.md)です。

このスクリプトを実行した後は、次の新しいデータベース ロールが表示されます。

+ `rpkgs-users`: このロールのメンバー パッケージを使用して、共有別にインストールされた`rpkgs-shared`ロールのメンバーです。

+ `rpkgs-private`: このロールのメンバーのメンバーと同じ権限での共有パッケージへのアクセスがある、`rpkgs-users`ロール。 このロールのメンバーことができますもインストール、削除、およびスコープを持つ個別のパッケージを使用します。

+ `rpkgs-shared`: このロールのメンバーのメンバーと同じアクセス許可がある、`rpkgs-private`ロール。 さらに、このロールのメンバーは、インストールまたは共有のパッケージを削除します。

+ `db_owner`: このロールのメンバーのメンバーと同じアクセス許可がある、`rpkgs-shared`ロール。 さらに、このロールのメンバーが**付与**他のユーザーが、インストール、または両方を削除する権利を共有およびプライベート パッケージです。

DBA は、データベースごとのロールにユーザーを追加できます。



## <a name="next-steps"></a>次の手順

[SQL Server の Machine Learning のパッケージの管理](r-package-management-for-sql-server-r-services.md)
