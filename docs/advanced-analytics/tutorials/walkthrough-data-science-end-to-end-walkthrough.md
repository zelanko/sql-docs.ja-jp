---
title: R 言語を使用したデータ科学者向けのチュートリアル
description: データベース内分析用のエンドツーエンドの R ソリューションを作成する方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/11/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ad7f5a500f740e4a302f814ec9523dfb33ecc68b
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278278"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>チュートリアル:R データ科学者向け SQL 開発
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

データ科学者向けのこのチュートリアルでは、SQL Server 2016 または SQL Server 2017 の R 機能のサポートに基づいて、予測モデリングのためのエンドツーエンドソリューションを構築する方法について説明します。 このチュートリアルでは SQL Server で[NYCTaxi_sample](demo-data-nyctaxi-in-sql.md)データベースを使用します。 

R コード、@no__t 0 のデータ、およびカスタム SQL 関数の組み合わせを使用して、ドライバーが特定のタクシー旅行に関するヒントを得られる可能性を示す分類モデルを作成します。 また、R モデルを @no__t 0 に配置し、サーバーデータを使用してモデルに基づいてスコアを生成します。

この例は、販売キャンペーンに対する顧客の反応の予測やイベントでの支出や参加の予測など、あらゆる種類の実際の問題に拡張できます。 モデルはストアドプロシージャから呼び出すことができるので、アプリケーションに簡単に埋め込むことができます。

このチュートリアルでは、R 開発者が [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] になるように設計されているため、可能な限り R を使用します。 ただし、これは、各タスクで必ずしも R が最適なツールであるという意味ではありません。 多くの場合、特にデータ集計と機能エンジニアリングについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の方が優れたパフォーマンスを示す可能性があります。  このようなタスクでは、特に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新機能 (メモリ最適化列ストア インデックスなど) のメリットが得られます。 考えられる最適化について説明します。

## <a name="prerequisites"></a>前提条件

+ R 統合または[SQL Server 2016 r Services](../install/sql-r-services-windows-install.md) [での Machine Learning Services の SQL Server](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [データベース権限](../security/user-permission.md)と SQL Server データベースユーザーログイン

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [NYC タクシーデモデータベース](demo-data-nyctaxi-in-sql.md)

+ R に付属する RStudio や組み込みの RSTUDIO ツールなどの R IDE

クライアントワークステーションでこのチュートリアルを実行することをお勧めします。 同じネットワーク上で SQL Server と R 言語が有効になっている @no__t 0 のコンピューターに接続できる必要があります。 ワークステーション構成の手順については、「 [R 開発用のデータサイエンスクライアントのセットアップ](../r/set-up-a-data-science-client.md)」を参照してください。

または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R 開発環境の両方を備えたコンピューターでこのチュートリアルを実行できますが、運用環境ではこの構成をお勧めしません。 クライアントとサーバーを同じコンピューターに配置する必要がある場合は、"リモート" クライアントから R スクリプトを送信するために、2つ目の Microsoft R ライブラリのセットを必ずインストールしてください。 SQL Server インスタンスのプログラムファイルにインストールされている R ライブラリは使用しないでください。 具体的には、1台のコンピューターを使用している場合は、クライアントとサーバーの操作をサポートするために、両方の場所に RevoScaleR ライブラリが必要です。

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

> [!NOTE]
> R クライアントではなく[Machine Learning Server](https://docs.microsoft.com/machine-learning-server/)または[Data Science Virtual Machine](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/)を使用している場合、RevoScaleR へのパスは C:\Program Files\Microsoft\ML Server\R_SERVER\library\RevoScaleR になります。

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>追加の R パッケージ

このチュートリアルでは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の一部として既定でインストールされない R ライブラリがいくつか必要です。 パッケージは、ソリューションを開発するクライアントと、ソリューションを配置する @no__t 0 のコンピューターの両方にインストールする必要があります。

### <a name="on-a-client-workstation"></a>クライアントワークステーション上

R 環境で、次の行をコピーし、コンソールウィンドウ (Rgui または IDE) でコードを実行します。 一部のパッケージでは、必要なパッケージもインストールします。 つまり、32のパッケージがインストールされます。 この手順を完了するには、インターネットに接続している必要があります。
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>サーバー上

SQL Server にパッケージをインストールするには、いくつかのオプションがあります。 たとえば、SQL Server には、データベース管理者がパッケージリポジトリを作成し、独自のパッケージをインストールする権限をユーザーに割り当てることができる[R パッケージ管理](../r/install-additional-r-packages-on-sql-server.md)機能が用意されています。 ただし、コンピューターの管理者である場合は、R を使用して新しいパッケージをインストールできます (正しいライブラリにインストールする場合)。

> [!NOTE]
> サーバーでは、メッセージが表示**さ**れた場合でも、ユーザーライブラリにはインストールしないでください。 をユーザーライブラリにインストールすると、SQL Server インスタンスはパッケージを見つけられず、実行できなくなります。 詳細については、「 [SQL Server での新しい R パッケージのインストール](../r/install-additional-r-packages-on-sql-server.md)」を参照してください。

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで、**管理者権限で** RGui.exe を開きます。  既定値を使用して SQL Server R Services をインストールした場合、Rgui は C:\Program Server\MSSQL13. にあります。MSSQLSERVER\R_SERVICES\bin\x64).

2. R プロンプトで、次の R コマンドを実行します。
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  この例では、R grep 関数を使用して、使用可能なパスのベクトルを検索し、"Program Files" を含むパスを検索します。 詳細については、「 [https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep)」を参照してください。

  パッケージが既にインストールされていると思われる場合は、`installed.packages()` を実行して、インストールされているパッケージの一覧を確認します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [データの探索と集計](walkthrough-view-and-summarize-data-using-r.md)
