---
title: "SQL Server と R のデータ サイエンスのチュートリアルの前提条件 |Microsoft ドキュメント"
ms.date: 11/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: c3b8cd3873645606fa9e286c3afbfa953c0ae5a1
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="prerequisites-for-the-data-science-walkthrough-for-sql-server-and-r"></a>SQL Server と R のデータ サイエンスのチュートリアルの前提条件

ラップトップまたは Microsoft R ライブラリがインストールされているその他のコンピューターでは、このチュートリアルを実行することをお勧めします。 接続する場合、同じネットワーク上にする必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] machine learning のサービスと、R 言語を有効になっているコンピューターにします。

このチュートリアルを実行するには両方を持つコンピューターに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と R 開発環境が運用環境のためには、この構成はお勧めしません。

## <a name="install-machine-learning-for-sql-server"></a>SQL Server の機械学習をインストールします。

インストールされている R のサポートを持つ SQL Server のインスタンスへのアクセスが必要です。 このチュートリアルが当初 SQL erver 2016 用に開発され、次の SQL Server のバージョンのいずれかを使用することができますので、2017年でテストします。 (がいくつかの相違は小さい RevoScaleR 関数でリリース。)

+ SQL Server 2017 の機械学習の Services (In-database)
+ SQL Server 2016 R サービス

詳細については、次を参照してください。 [SQL Server R Services の設定 (データベース内](../r/set-up-sql-server-r-services-in-database.md)です。

> [!IMPORTANT]
> SQL Server のバージョン以前 2016年より統合をサポートしない R とただし、ODBC データ ソースとして、以前の SQL データベースを使用できます。

## <a name="install-an-r-development-environment"></a>R 開発環境をインストールします。

このチュートリアルでは、R 開発環境を使用することをお勧めします。 次にいくつかの提案を示します。

- **R Tools for Visual Studio** (RTVS) は、無料でプラグインを Intellisense、デバッグを提供し、Microsoft r です。 を使用できます R Server と SQL Server の Machine Learning のサービスの両方をサポートします。 ダウンロードするには、「 [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)」を参照してください。

- **Microsoft R クライアント**RevoScaleR パッケージを使用して R での開発をサポートする軽量の開発ツールです。 これを取得する方法については、「 [Get Started with Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)」 (Microsoft R Client の概要) を参照してください。

- **RStudio** は R 開発用の最も一般的な環境の 1 つです。 詳しくは、 [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)参照してください。

    RStudio またはその他の環境の一般的なインストールを使用してこのチュートリアルを完了することはできません。また、Microsoft R Open の R パッケージと接続ライブラリをインストールする必要があります。 詳しくは、「 [データ サイエンス クライアントのセットアップ](../r/set-up-a-data-science-client.md)」を参照してください。

- 基本的な R ツール (R.exe、RTerm.exe、RScripts.exe) は、SQL Server または R クライアントで R をインストールするときにも既定でインストールされます。 IDE をインストールしない場合は、これらのツールを使用できます。

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>SQL Server インスタンスとデータベースのアクセス許可を取得します。

インスタンスに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スクリプトを実行して、データのアップロードには、データベース サーバーで有効なログインを持っています。  SQL ログインまたは統合 Windows 認証を使用できます。 R: を使用するデータベースで、アカウントの次のアクセス許可を構成するデータベース管理者に問い合わせてください。

- データベース、テーブル、関数、ストアド プロシージャの作成
- テーブルにデータを書き込む
- R スクリプトを実行する機能 (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

このチュートリアルでは、SQL ログインを使用しています**RTestUser**です。 おは通常、Windows 統合認証を使用するが、SQL ログインを使用する方が簡単なデモの目的でことをお勧めします。

## <a name="change-list"></a>変更の一覧

+ このサンプルでは、SQL Server 2016 の R Services を使用してもともと開発されました。 ただし、重大な変更は、2016 SP1 用 Microsoft R コンポーネントで導入されました。 具体的には、 _varsToDrop_と_varsToKeep_パラメーターが不要になった SQL Server データ ソースのサポートされていました。 Therefre、SP1 より前のチュートリアルのバージョンをダウンロードしている場合にと連動しません SP1 ビルドします。

+ 現在のバージョンのサンプルは、SQL Server 2017 Machine Learning サービス (RC1 と RC2) の前のリリース ビルドを使用してテストされています。 一般に、ほとんどすべての手順を実行する必要があります変更せずに実行 2016 SP1 と 2017 年間です。

## <a name="next-lesson"></a>次のレッスン

[PowerShell を使用してデータを準備します。](/walkthrough-prepare-the-data.md)
