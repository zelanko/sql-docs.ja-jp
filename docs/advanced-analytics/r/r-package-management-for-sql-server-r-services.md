---
title: "インストールして、SQL Server の machine learning のパッケージを管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/19/2018
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
ms.openlocfilehash: 0fd96240581203d9f948372dfbe98cac80a3b906
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="installing-and-managing-machine-learning-packages-in-sql-server"></a>インストールして、SQL Server の machine learning のパッケージを管理します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server 2016 および SQL Server 2017 で新しい R パッケージまたは Python パッケージをインストールする方法について説明します。 SQL Server にインストールできるパッケージに対しての制限についても説明します。

## <a name="overview-of-package-management-methods-and-requirements"></a>パッケージの管理方法と要件の概要

一般的な R または Python の開発とは異なりには、管理者レベルの制御下にあるフォルダーに SQL Server で使用されるパッケージをインストールする必要があります。 これには 1 つの場所にパッケージを維持するために多くの利点があります。

+ サーバーの管理者では、新しいファイルと、サーバー上のライブラリの追加を監視でき、パッケージのライブラリによって使用されるファイルの容量増加を制御することができます。 
+ パッケージは、ユーザーのライブラリで、同じパッケージの複数のコピーをインストールするのではなく、複数のデータベース ユーザーがより簡単に共有できます。
+ サーバーとその操作を保護する、セキュリティで保護された、承認されたパッケージのみをインストールできます。

ただし、これらの制限を使用すると、データ サイエンティストおよびアナリストの動作の変更によりを必ずしも。

+ 一般に、サーバーへの管理アクセスが必要です。 SQL Server の 2017 でデータベース管理者は、ロールを使用して、プライベート用にパッケージをインストールする機能を特定のユーザーに与えることができますが、管理者は、まだこの機能を有効にします。
+ 多くのサーバーには、インターネットへのアクセスはありません。 これらのコンピューターにパッケージをインストールするには、いくつか追加の準備が必要です。
+ パッケージは、インスタンス ライブラリにインストールされます。 パッケージは、インスタンス間で共有することはできません。
+ ユーザーは、ユーザーのライブラリがインストールされているパッケージを実行できません。

## <a name="package-installation-guides-for-r-or-python"></a>R、Python のパッケージのインストール ガイド

新しい R または Python パッケージをインストールする方法の詳細な手順については、次の記事を参照してください。 

### <a name="install-new-r-packages"></a>新しい R パッケージをインストールします。

+ [SQL Server に追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)

    管理者は、R ツールを使用して、SQL Server 2016 または 2017 に R パッケージをインストールできます。

    リモート R クライアントからの R パッケージをインストールすることもできます。 ここで R Server 9.0.2 以降がインストールされています。

    DDL ステートメントを使用して SQL Server 2017 で R パッケージをインストールすることもできます。

### <a name="install-new-python-packages"></a>新しい Python パッケージをインストールします。

+ [SQL Server に新しい Python パッケージをインストールする](../python/install-additional-python-packages-on-sql-server.md)

## <a name="prerequisites"></a>前提条件

ダウンロードや、新しいパッケージをインストールしようとすると、前に、要件を確認します。

+ Windows のバージョンのパッケージがあることを確認してください:[適切なパッケージのバージョンと形式を取得します。](#packageVersion)

+ すべてのパッケージの依存関係を特定し、SQL Server 環境との互換性を確認します。

+ R バージョンまたは Python のバージョンの互換性を確認します。 パッケージを R または SQL Server で実行されている Python のバージョンとの互換性にする必要があります。

+ アクセス許可です。 パッケージをインストールする権限があるかどうかを決定します。 インスタンスのライブラリをインストールするには、SQL Server を実行しているコンピューターへの管理アクセスが必要です。 SQL Server コンピュータに管理アクセス権を持っていない場合は、データベース管理者は、パッケージのインストールに関するヘルプを検索します。

    SQL Server の 2017 場合は、サーバーでパッケージの管理が有効化され、データベース所有者またはパッケージの管理ロールのメンバーであること、リモート クライアントから R パッケージをインストールできます。

+ リスクと、SQL Server 環境への特定のパッケージのインストールの利点を検討してください。 パッケージ (または必要なすべてのパッケージ) が SQL Server やポリシーによってブロックされる機能に含まれるかどうかを確認してください。 多くの R、Python パッケージとは、セキュリティを強化した SQL Server 環境で非常に悪い適合です。 問題が含まれます。

    - ネットワークにアクセスするパッケージ
    - Java、またはその他のフレームワークを SQL Server 環境で通常使用が必要なパッケージ
    - 管理者特権でのファイル システム アクセスが必要なパッケージ
    - パッケージは、web 開発または SQL Server 内で実行するパフォーマンスを改善しないその他のタスクに使用されます。

## <a name="installation-on-servers-with-no-internet-access"></a>インターネットにアクセスできないサーバーへのインストール

一般に、実稼働データベースをホストするサーバーでは、インターネットへの接続は許可されません。 などの環境に新しい R または Python のパッケージをインストールするには、すべてのパッケージとその依存関係を事前に準備して、インストールで使用するサーバー上のフォルダーにファイルをコピーする必要があります。

1. すべてのパッケージの依存関係を識別します。 
2. サーバーで、必要なパッケージが既にインストールされているかどうかを確認してください。 パッケージがインストールされている場合は、バージョンが正しいことを確認します。
3. パッケージとすべての依存関係を別のコンピューターにダウンロードします。
4. サーバーがアクセスできるフォルダーにファイルを移動します。
5. インスタンスのライブラリにパッケージをインストールするには、サポートされているインストール コマンドまたは DDL ステートメントを実行します。

すべての依存関係を識別すると、複雑なことができます。 使用することお勧めを r、 [miniCRAN](create-a-local-package-repository-using-minicran.md)オフライン パッケージ リポジトリを準備します。

For Python、同様にすべての依存関係を準備して、ローカルに保存する必要があります。 使用する Windows 互換のバイナリと WHL 形式を使用してください。
