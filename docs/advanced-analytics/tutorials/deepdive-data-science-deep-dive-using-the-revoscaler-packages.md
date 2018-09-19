---
title: SQL Server Machine Learning でのチュートリアルについては、RevoScaleR 関数 |Microsoft Docs
description: このチュートリアルでは、有効になっているサポートされている R を使用した SQL Server Machine Learning で RevoScaleR 関数を呼び出す方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4aa45d7ee690d55672c86be256e66d454860c2b6
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45563892"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>SQL Server のデータのチュートリアル: 使用 RevoScaleR の R 関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR とは、データ サイエンスと機械学習のワークロードを分散し並列処理を実現する Microsoft R パッケージです。 SQL Server での R 開発ツール、RevoScaleR は core の組み込みパッケージのコンピューティング コンテキストを設定するための関数の 1 つ、パッケージの管理と最も重要な: データ エンド ツー エンド、視覚化と分析へのインポートから操作します。 SQL Server で機械学習アルゴリズムでは、RevoScaleR のデータ ソースに依存関係があります。 RevoScaleR の重要度を指定するには、不可欠なスキルは場面とその関数を呼び出す方法です。 

このチュートリアルで、ローカルおよびリモート計算コンテキストの間でデータを移動、リモート コンピューティング コンテキストを作成する方法を学習し、リモート SQL Server で R コードを実行します。 作成してモデルをデプロイする方法と分析して、ローカルとリモートのサーバーの両方にデータをプロットする方法も学習します。

+ 最初に、CSV ファイルまたは XDF ファイルからデータを取得します。 データをインポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]RevoScaleR パッケージで、関数を使用します。
+ モデルのトレーニングとスコア付けを使用して、実行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューティング コンテキスト。 
+ RevoScaleR 関数を使用して、新規に作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スコア付けの結果を保存するテーブル。
+ サーバーの両方のプロットを作成し、ローカル コンピューティング コンテキスト。
+ 内のデータに対してモデルのトレーニング[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で R を実行して、データベース、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。
+ データのサブセットを抽出し、分析に再利用できる、ローカル ワークステーション上の XDF ファイルとして保存します。
+ スコアリングには、ODBC 接続を開くことで新しいデータの取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 スコア付けは、ローカル ワークステーションで行われます。
+ カスタム R 関数を作成し、コンピューティング コンテキストをシミュレーションを実行するサーバーで実行します。

## <a name="target-audience"></a>対象ユーザー

このチュートリアルの目的は、データ サイエンティスト向けまたは R、および概要とモデルの作成などのデータ サイエンス タスクをある程度理解している方のためです。 ただし、すべてのコードが提供される、ため場合でもを初めて使用する R コードを実行し、必要なサーバーとクライアント環境があると仮定すると、作業を進めるにします。

慣れておく必要があります[!INCLUDE[tsql](../../includes/tsql-md.md)]構文にアクセスする方法を理解して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]など、これらのツールを使用してデータベースします。

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Visual Studio でのデータベース ツール 
+ 無料[Visual Studio Code 用 mssql 拡張機能](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode)します。
  
> [!TIP]
> 中断した箇所からを容易に再開できるように、レッスンの合間に R ワークスペースを保存してください。

## <a name="prerequisites"></a>Prerequisites

- **SQL Server で R のサポート**
  
    インストール[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) R 機能、またはインストール[SQL Server 2016 R Services (In-database)](../install/sql-r-services-windows-install.md)します。

    外部スクリプトが有効になって、スタート パッド サービスを実行すると、およびサービスにアクセスする権限があることを確認してください。
  
-  **データベース権限**
  
    モデルのトレーニングで使用するクエリを実行するには、データが格納されているデータベースに対して **db_datareader** 権限が必要です。 R を実行するには、EXECUTE ANY EXTERNAL SCRIPT、アクセス許可が、ユーザーにあります。

-   **データ サイエンス開発用コンピューター**
  
    ローカルおよびリモート計算コンテキストの間で交互に切り替えるには、2 つのシステム必要があります。 ローカルは、通常、データ サイエンスのワークロード用の十分な能力の開発ワークステーションです。 リモートここでは、SQL Server 2017 または SQL Server 2016 R 機能を有効にします。 
    
    コンピューティング コンテキストの切り替えは、ローカルとリモートの両方のシステムで同じバージョンの RevoScaleR に実行されます。 ローカルのワークステーションで取得できます、RevoScaleR パッケージと関連するプロバイダーをインストールするか、次のいずれかを使用して: [Azure でのデータ サイエンス VM](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)、 [(無料) の Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)、または[Microsoft Machine Learning Server (スタンドアロン)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-install)します。 スタンドアロン サーバー オプションでは、Linux または Windows インストーラーを使用して、無料の developer edition をインストールします。 スタンドアロン サーバーをインストールするのに SQL Server セットアップを使用することもできます。
      
-   **追加の R パッケージ**
  
    このチュートリアルで、次のパッケージをインストールする: **dplyr**、 **ggplot2**、 **ggthemes**、 **reshape2**、および**e1071**. 手順は、チュートリアルの中で説明します。
  
    2 つの場所ですべてのパッケージをインストールする必要があります: R ソリューションの開発に使用されているワークステーションと R スクリプトが実行される SQL Server コンピューター。 サーバー コンピューターにパッケージをインストールするアクセス許可がない場合、は、管理者に問い合わせてください。 
    
    **ユーザー ライブラリにはパッケージをインストールしないでください。** SQL Server インスタンスで使用される R パッケージ ライブラリのパッケージをインストールする必要があります。

## <a name="r-development-tools"></a>R 開発ツール

R 開発者は、通常記述および R コードをデバッグするための Ide を使用します。 推奨事項をいくつか以下に示します。

- **R Tools for Visual Studio** (RTVS) は、無料プラグインを Intellisense、デバッグを提供し、Microsoft R 向けサポートR Server と SQL Server Machine Learning サービスの両方で使用できます。 ダウンロードするには、「 [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)」を参照してください。

- **RStudio** は R 開発用の最も一般的な環境の 1 つです。 詳細については、次を参照してください。 [ https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)します。

- 基本 R ツール (R.exe、RTerm.exe、RScripts.exe) は、SQL Server または R Client に R をインストールするときにも既定でインストールされます。 IDE をインストールしたくない場合は、このチュートリアルでは、コードを実行する組み込みの R ツールを使用できます。

RevoScaleR がローカルとリモートの両方のコンピューターに必要なことを思い出してください。 RStudio または他の Microsoft R ライブラリが不足している環境の一般的なインストールを使用して、このチュートリアルを完了できません。 詳しくは、「 [データ サイエンス クライアントのセットアップ](../r/set-up-a-data-science-client.md)」を参照してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [レッスン 1: データベースとアクセス許可を作成します。](deepdive-work-with-sql-server-data-using-r.md)

