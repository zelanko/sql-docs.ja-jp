---
title: R と SQL Server のエンド ツー エンドのデータ サイエンスのチュートリアル |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d4f38fd424c881392d48b0a6a24feb7f7e27ee0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086504"
---
# <a name="end-to-end-data-science-walkthrough-for-r-and-sql-server"></a>R と SQL Server のエンド ツー エンドのデータ サイエンスのチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルでは、SQL Server 2016 または SQL Server 2017 のいずれかでサポートされる R 機能に基づく予測モデリングのエンド ツー エンド ソリューションを開発します。

このチュートリアルは、よく知られている公開データ セット、ニューヨーク市タクシー データセットに基づいています。 R コードの組み合わせを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ、およびドライバーが特定のタクシーの乗車でチップを取得する確率を示す分類モデルを構築するカスタム SQL 関数。 デプロイすることも、R モデルを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とサーバーのデータを使用して、モデルに基づいてスコアを生成します。

この例は、すべての種類の販売キャンペーンに対する顧客の反応を予測するか、支出やイベント参加者数を予測するなど、現実の問題に拡張できます。 ストアド プロシージャからモデルを呼び出すことが、ためには、アプリケーションで簡単に埋め込むことができます。

チュートリアルの目的は、R 開発者に紹介するため、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、可能な場合、R を使用します。 ただし、R は、各タスクに最適なツールでは必ずしもつまりされません。 多くの場合、特にデータ集計と機能エンジニアリングについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の方が優れたパフォーマンスを示す可能性があります。  このようなタスクでは、特に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新機能 (メモリ最適化列ストア インデックスなど) のメリットが得られます。 可能な最適化の過程で指摘ましょう。

## <a name="target-audience"></a>対象ユーザー

このチュートリアルは、R または SQL の開発者向けです。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を使用してエンタープライズ ワークフローに R を統合する方法の概要について説明します。  データベースとテーブルを作成、データをインポートするクエリの実行などのデータベース操作する必要があります。

+ すべての SQL と R スクリプトが含まれます。
+ 環境内で実行する、スクリプト内の文字列を変更する必要があります。 これを任意のコード エディターなど[Visual Studio Code](https://code.visualstudio.com/Download)します。

## <a name="prerequisites"></a>前提条件

ラップトップまたは他の Microsoft R ライブラリがインストールされているコンピューターでは、このチュートリアルを実行することをお勧めします。 を、同じネットワーク上に接続できる必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server と R 言語を有効になっているコンピューター。

両方を備えたコンピューターでチュートリアルを実行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と R 開発環境ですが運用環境のためには、この構成は推奨されません。

ラップトップなどのリモート コンピューターまたはその他のネットワークに接続されたコンピューターから R コマンドを実行する場合は、Microsoft R Open ライブラリをインストールする必要があります。 Microsoft R Client または Microsoft R Server をインストールすることができます。 リモート コンピューターに接続できる必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。

同じコンピューターにクライアントとサーバーを配置する必要がある場合は、「リモート」のクライアントから R スクリプトの送信に使用する Microsoft R ライブラリの別のセットをインストールすることを確認します。 使用するため R ライブラリがインストールされているは SQL Server インスタンスによってこの目的のため使用しないでください。

## <a name="add-r-to-sql-server"></a>SQL Server に R を追加します。

R がインストールされている対応の SQL Server のインスタンスへのアクセスが必要です。 このチュートリアルは当初 SQL ーバー 2016 用に開発されされるには、次の SQL Server のバージョンのいずれかを使用することが、2017 年でテストします。 (いくつか小さな違いが RevoScaleR 関数で、リリース間。)

+ [SQL Server 2017 Machine Learning Services をインストールします。](../install/sql-machine-learning-services-windows-install.md)
+ [SQL Server 2016 R Services のインストール](../install/sql-r-services-windows-install.md)します。

## <a name="install-an-r-development-environment"></a>R 開発環境をインストールします。

このチュートリアルでは、R 開発環境を使用することをお勧めします。 推奨事項を次に示します。

- **R Tools for Visual Studio** (RTVS) は、無料プラグインを Intellisense、デバッグを提供し、R Server と SQL Server Machine Learning サービスの両方で使用できる Microsoft R をサポートします。 ダウンロードするには、「 [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)」を参照してください。

- **Microsoft R Client**は RevoScaleR パッケージを使用して R の開発をサポートする軽量の開発ツールです。 これを取得する方法については、「 [Get Started with Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)」 (Microsoft R Client の概要) を参照してください。

- **RStudio** は R 開発用の最も一般的な環境の 1 つです。 詳細については、次を参照してください。 [ https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)します。

    RStudio または他の環境の一般的なインストールを使用して、このチュートリアルを完了することはできません。Microsoft R Open の接続ライブラリと R パッケージをインストールすることも必要があります。 詳しくは、「 [データ サイエンス クライアントのセットアップ](../r/set-up-a-data-science-client.md)」を参照してください。

- 基本 R ツール (R.exe、RTerm.exe、RScripts.exe) は、SQL Server または R Client に R をインストールするときにも既定でインストールされます。 IDE をインストールしたくない場合は、これらのツールを使用できます。

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>SQL Server インスタンスとデータベースのアクセス許可を取得します。

インスタンスに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にスクリプトを実行して、データをアップロードして、データベース サーバーで有効なログインを持って必要があります。  SQL ログインまたは統合 Windows 認証を使用できます。 R: を使用するデータベースで、アカウントの次のアクセス許可を構成するデータベース管理者に問い合わせてください。

- データベース、テーブル、関数、ストアド プロシージャの作成
- テーブルにデータを書き込む
- R スクリプトを実行する機能 (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

このチュートリアルでは、SQL ログインを使用しましたが**RTestUser**します。 私たちは一般に、Windows 統合認証を使用することが、デモのためにいくつかの単純な SQL ログインを使用してはお勧めします。

## <a name="next-steps"></a>次のステップ

[PowerShell を使用してデータを準備します。](walkthrough-prepare-the-data.md)
