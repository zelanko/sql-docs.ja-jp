---
title: SQL Server Machine Learning の R 言語を使用して、データ サイエンティスト向けのチュートリアル
description: In-database 分析をエンド ツー エンド R ソリューションを作成する方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 45d587b4d62c33e944b15c6b951fa1323620c50e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961703"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>チュートリアル:SQL R データ サイエンティスト向けの開発
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データ サイエンティスト向けのこのチュートリアルでは、SQL Server 2016 または SQL Server 2017 のいずれかでサポートされる R 機能に基づく予測モデリングのエンド ツー エンド ソリューションを構築する方法を説明します。 このチュートリアルでは、 [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) SQL Server データベース。 

R コードの組み合わせを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ、およびドライバーが特定のタクシーの乗車でチップを取得する確率を示す分類モデルを構築するカスタム SQL 関数。 デプロイすることも、R モデルを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とサーバーのデータを使用して、モデルに基づいてスコアを生成します。

この例は、すべての種類の販売キャンペーンに対する顧客の反応を予測するか、支出やイベント参加者数を予測するなど、現実の問題に拡張できます。 ストアド プロシージャからモデルを呼び出すことが、ためには、アプリケーションで簡単に埋め込むことができます。

チュートリアルの目的は、R 開発者に紹介するため、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、可能な場合、R を使用します。 ただし、R は、各タスクに最適なツールでは必ずしもつまりされません。 多くの場合、特にデータ集計と機能エンジニアリングについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の方が優れたパフォーマンスを示す可能性があります。  このようなタスクでは、特に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新機能 (メモリ最適化列ストア インデックスなど) のメリットが得られます。 可能な最適化の過程で指摘ましょう。

## <a name="prerequisites"></a>前提条件

+ [R 統合で SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md#verify-installation)または[SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

+ [データベース権限](../security/user-permission.md)と SQL Server データベースのユーザー ログイン

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [NYC タクシー デモ データベース](demo-data-nyctaxi-in-sql.md)

+ RStudio などの R IDE または R に付属する組み込み RGUI ツール

クライアント ワークステーションでは、このチュートリアルを実行することをお勧めします。 を、同じネットワーク上に接続できる必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server と R 言語を有効になっているコンピューター。 ワークステーションの構成については、次を参照してください。 [R 開発用のデータ サイエンス クライアント セットアップ](../r/set-up-a-data-science-client.md)します。

両方を備えたコンピューターでチュートリアルを実行する代わりに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と R 開発環境では、ですが運用環境のためには、この構成は推奨されません。 同じコンピューターにクライアントとサーバーを配置する必要がある場合は、「リモート」のクライアントから R スクリプトを送信するための Microsoft R ライブラリの 2 番目のセットをインストールすることを確認します。 SQL Server インスタンスのプログラム ファイルにインストールされている R ライブラリを使用しません。 具体的には、1 台のコンピューターを使用している場合は、クライアントとサーバーの操作をサポートするためにこれらの場所の両方で RevoScaleR ライブラリ必要があります。

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>追加の R パッケージ

このチュートリアルではいくつかの R ライブラリの一部として、既定でインストールされていない[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。 ソリューションを開発する場合と、パッケージをクライアントにインストールする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ソリューションをデプロイするコンピューター。

### <a name="on-a-client-workstation"></a>クライアント ワークステーションにインストール

R 環境では、次の行をコピーし、(Rgui または IDE) は、コンソール ウィンドウで、コードを実行します。 一部のパッケージでは、必要なパッケージもインストールします。 すべてでは、約 32 パッケージがインストールされます。 インターネットに接続すると、この手順を完了する必要があります。
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>サーバーで

SQL Server にパッケージをインストールするためのいくつかのオプションがあります。 たとえば、SQL Server は[R パッケージ管理](../r/install-additional-r-packages-on-sql-server.md)により、データベース管理者はパッケージ リポジトリを作成し、ユーザーが自分のパッケージをインストールする権限を割り当てる機能。 ただし、コンピューターの管理者の場合は、適切なライブラリをインストールする場合に限り、R を使用して新しいパッケージをインストールできます。

> [!NOTE]
> サーバーで、**しない**場合でも、入力を求め、ユーザー ライブラリにインストールします。 ユーザー ライブラリにインストールする場合、SQL Server インスタンスが見つからないか、パッケージを実行します。 詳細については、次を参照してください。 [SQL サーバーに新しい R パッケージをインストールする](../r/install-additional-r-packages-on-sql-server.md)します。

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで、**管理者権限で** RGui.exe を開きます。  既定値を使用して SQL Server R Services をインストールした場合、Rgui.exe は C:\Program files \microsoft SQL Server\MSSQL13 で見つかんだことができます。MSSQLSERVER\R_SERVICES\bin\x64)。

2. R プロンプトで、次の R コマンドを実行します。
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  この例では、R grep 関数を使用して、使用可能なパスのベクトルを検索し、"Program Files"を含むパスを見つけます。 詳細については、「[https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep)」を参照してください。

  パッケージが既にインストールされている場合を実行してインストールされているパッケージの一覧を確認してください。`installed.packages()`します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [確認し、データの集計](walkthrough-view-and-summarize-data-using-r.md)