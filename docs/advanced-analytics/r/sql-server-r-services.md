---
title: SQL server 2016 R Services |Microsoft Docs
description: データベース内分析のために SQL Server サービスの概要概要については、R のサポートします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/27/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9be6cf7b38482673db0308b4680500dede313e09
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118340"
---
# <a name="r-services-in-sql-server-2016"></a>SQL server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2016 R Services は、データベース エンジン インスタンス、SQL Server で R コードを実行するためのアドオンです。 コア エンジンのプロセスから分離が完全にストアド プロシージャ、T-SQL スクリプトが R のステートメントを含むまたは T-SQL を含む R コードとしてのリレーショナル データに使用可能な機能拡張フレームワークでコードが実行されます。 

R Services には、R、読み込みと複数コアで大量のデータを処理して 1 つの統合の出力に結果を集計できるように、Microsoft からの企業の R パッケージを使用したオーバーレイの基本ディストリビューションが含まれています。 Microsoft の R 関数とアルゴリズムがスケールとユーティリティの両方のエンジニア リング: 予測分析、統計モデリング、データの視覚化、および最先端の機械学習、商用のサーバー製品のエンジニア リングでアルゴリズムを提供し、Microsoft によってサポートされています。 

R ライブラリには、RevoScaleR、MicrosoftML、およびその他のユーザーが含まれます。 R Services がデータベース エンジンと統合されているため、データの近くで分析し、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除できます。

## <a name="components"></a>Components

SQL Server 2016 には R のみです。 次の表では、SQL Server 2016 の機能について説明します。

| コンポーネント | 説明 |
|-----------|-------------|
| SQL Server スタート パッド サービス | 外部の R ランタイムと、SQL Server インスタンス間の通信を管理するサービス。 |
| R パッケージ | [**RevoScaleR** ](revoscaler-overview.md)はこのライブラリでスケーラブルな R. 関数が最も広く使用されている間は、プライマリ ライブラリ。 データ変換と操作、統計の概要作成、視覚化、およびモデリングと分析の多くの形式は、これらのライブラリで表示されます。 さらに、これらのライブラリ内の関数は、並列処理、調整され、計算エンジンによって管理されるデータのチャンク上で動作する機能の使用可能なコア間でワークロードを自動的に配布します。  <br/>[**MicrosoftML (R)** ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 <br/>[**sqlRUtils** ](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) T-SQL ストアド プロシージャに R スクリプトを配置すること、データベースでストアド プロシージャを登録すると、R 開発環境からストアド プロシージャを実行しているヘルパー関数を提供します。<br/>[**olapR** ](how-to-create-mdx-queries-using-olapr.md)は R で MDX クエリを指定するため|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open)は r です Microsoft のオープン ソース ディストリビューションには。パッケージおよびインタープリターが含まれます。 常にセットアップによってインストールされている MRO のバージョンを使用します。 |
| R ツール | R コンソール ウィンドウとコマンド プロンプトは、R のディストリビューションで標準的なツールです。  |
| R のサンプルとスクリプト |  オープン ソースの R と RevoScaleR パッケージが作成して事前インストールされているデータを使用してスクリプトを実行できるように、組み込みのデータ セットを含める |
| R で事前トレーニング済みモデル | 事前トレーニング済みモデルは特定のユース ケース用に作成し、microsoft データ サイエンスのエンジニア リング チームによって管理されます。 事前トレーニング済みモデルとして使用することができます-正、負のセンチメントをスコア付けで、テキストまたはイメージを提供する新しいデータの入力を使用して機能を検出します。 モデルでは、R services での実行が、SQL Server セットアップでインストールすることはできません。 詳細については、次を参照してください。[インストール事前トレーニング済みの機械学習では、SQL Server のモデル](../install/sql-pretrained-models-install.md)します。 |

## <a name="how-to-get-started"></a>開始する方法

セットアップを開始、バイナリを使い慣れた開発ツールにアタッチし、最初のスクリプトを記述します。

**手順 1:** をインストールし、ソフトウェアを構成します。 

+ [SQL Server 2016 R Services (In-database) をインストールします。](../install/sql-r-services-windows-install.md)

**手順 2:** これらのチュートリアルのいずれかを使用して実践的な経験を積みます。

+ [チュートリアル: R を使用した in-database 分析を説明します。](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [チュートリアル: エンド ツー エンドのチュートリアルでは、R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**手順 3:** お気に入りの R パッケージを追加し、Microsoft によって提供されるパッケージと共に使用

+ [SQL Server の R パッケージ管理](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>関連項目

 [SQL Server 2016 R Services をインストールします。](../install/sql-r-services-windows-install.md)
