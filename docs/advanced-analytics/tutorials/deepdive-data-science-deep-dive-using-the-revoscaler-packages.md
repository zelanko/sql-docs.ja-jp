---
title: RevoScaleR 関数に関する詳しいチュートリアル-SQL Server Machine Learning
description: このチュートリアルでは、SQL Server Machine Learning の R 統合を使用して、RevoScaleR 関数を呼び出す方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4ce2eea1638c301f85741dc22f7541af0cf7e5d6
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596623"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>チュートリアル:SQL Server データで RevoScaleR R 関数を使用します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)並列データ サイエンスと機械学習のワークロードの処理および Microsoft R パッケージの分散を提供します。 SQL Server での R 開発用**RevoScaleR**コアのいずれかの組み込みパッケージ、パッケージの管理、コンピューティング コンテキストの設定、データ ソース オブジェクトを作成するための関数は、そして最も重要: データ エンド ツー エンドでの操作視覚エフェクトと分析にインポートします。 SQL Server で機械学習アルゴリズム依存している**RevoScaleR**データ ソース。 重要である**RevoScaleR**場面で、その関数を呼び出す方法は、不可欠なスキルです。 

このマルチパート チュートリアルでは、範囲に導入された**RevoScaleR**データ サイエンスに関連付けられているタスクの関数。 プロセスで、ローカルおよびリモート計算コンテキストの間でデータを移動、リモート コンピューティング コンテキストを作成する方法を学習およびリモートの SQL Server で R コードを実行します。 作成してモデルをデプロイする方法と分析して、ローカルとリモートのサーバーの両方にデータをプロットする方法も学習します。

## <a name="prerequisites"></a>前提条件

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) R 機能を使用または[SQL Server 2016 R Services (In-database)](../install/sql-r-services-windows-install.md)
  
+ [データベース権限](../security/user-permission.md)と SQL Server データベースのユーザー ログイン

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ RStudio や R に付属する組み込み RGUI ツールなど、IDE

ローカルおよびリモート計算コンテキストの間で交互に切り替えるには、2 つのシステム必要があります。 ローカルは、通常、データ サイエンスのワークロード用の十分な能力の開発ワークステーションです。 リモートここでは、SQL Server 2017 または SQL Server 2016 R 機能を有効にします。 

コンピューティング コンテキストの切り替えが、同じバージョンに基づいて**RevoScaleR**ローカルとリモートの両方のシステムでします。 ローカルのワークステーションで取得できます、 **RevoScaleR**パッケージおよび Microsoft R Client をインストールすることによって、関連するプロバイダー。

同じコンピューターにクライアントとサーバーを配置する必要がある場合は、「リモート」のクライアントから R スクリプトを送信するための Microsoft R ライブラリの 2 番目のセットをインストールすることを確認します。 SQL Server インスタンスのプログラム ファイルにインストールされている R ライブラリを使用しません。 具体的には、1 台のコンピューターを使用している場合、 **RevoScaleR**クライアントとサーバーの操作をサポートするためにこれらの場所の両方でのライブラリです。

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\R_SERVICES\library\RevoScaleR

クライアントの構成については、次を参照してください。 [R 開発用のデータ サイエンス クライアント セットアップ](../r/set-up-a-data-science-client.md)します。


## <a name="r-development-tools"></a>R 開発ツール

R 開発者は、通常記述および R コードをデバッグするための Ide を使用します。 推奨事項をいくつか以下に示します。

- **R Tools for Visual Studio** (RTVS) は、無料プラグインを Intellisense、デバッグを提供し、Microsoft R 向けサポートR Server と SQL Server Machine Learning サービスの両方で使用できます。 ダウンロードするには、「 [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)」を参照してください。

- **RStudio** は R 開発用の最も一般的な環境の 1 つです。 詳細については、次を参照してください。 [ https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)します。

- 基本 R ツール (R.exe、RTerm.exe、RScripts.exe) は、SQL Server または R Client に R をインストールするときにも既定でインストールされます。 IDE をインストールしたくない場合は、このチュートリアルでは、コードを実行する組み込みの R ツールを使用できます。

いることを思い出してください**RevoScaleR**ローカルとリモートの両方のコンピューターが必要です。 RStudio または他の Microsoft R ライブラリが不足している環境の一般的なインストールを使用して、このチュートリアルを完了できません。 詳しくは、「 [データ サイエンス クライアントのセットアップ](../r/set-up-a-data-science-client.md)」を参照してください。

## <a name="summary-of-tasks"></a>タスクの概要

+ 最初に、CSV ファイルまたは XDF ファイルからデータを取得します。 データをインポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で関数を使用して、 **RevoScaleR**パッケージ。
+ モデルのトレーニングとスコア付けを使用して、実行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューティング コンテキスト。 
+ 使用**RevoScaleR**新しいを作成する関数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スコア付けの結果を保存するテーブル。
+ サーバーの両方のプロットを作成し、ローカル コンピューティング コンテキスト。
+ 内のデータに対してモデルのトレーニング[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で R を実行して、データベース、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。
+ データのサブセットを抽出し、分析に再利用できる、ローカル ワークステーション上の XDF ファイルとして保存します。
+ スコアリングには、ODBC 接続を開くことで新しいデータの取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 スコア付けは、ローカル ワークステーションで行われます。
+ カスタム R 関数を作成し、コンピューティング コンテキストをシミュレーションを実行するサーバーで実行します。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [レッスン 1:データベースとアクセス許可を作成します。](deepdive-work-with-sql-server-data-using-r.md)