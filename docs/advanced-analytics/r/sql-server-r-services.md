---
title: SQL Server 2016 の SQL Server Machine Learning サービスでの R Services
description: データ サイエンスと統計モデリング、予測分析、データの視覚化をなどのリレーショナル データに対する統合された R タスク用の SQL Server で R です。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: bc506d245878d459a3c4639ff4e5a6c2f2a9f8f6
ms.sourcegitcommit: f7ad034f748ebc3e5691a5e4c3eb7490e5cf3ccf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2019
ms.locfileid: "67469113"
---
# <a name="r-services-in-sql-server-2016"></a>SQL server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R Services は、SQL Server で R コードと関数を実行するために使用される、SQL Server 2016 データベース エンジン インスタンスへのアドオンです。 コア エンジンのプロセスから分離が完全にストアド プロシージャ、T-SQL スクリプトが R のステートメントを含むまたは T-SQL を含む R コードとしてのリレーショナル データに使用可能な機能拡張フレームワークでコードが実行されます。 

R Services には、R、読み込みと複数コアで大量のデータを処理して 1 つの統合の出力に結果を集計できるように、Microsoft からの企業の R パッケージを使用したオーバーレイの基本ディストリビューションが含まれています。 Microsoft の R 関数とアルゴリズムがスケールとユーティリティの両方のエンジニア リング: 予測分析、統計モデリング、データの視覚化、および最先端の機械学習、商用のサーバー製品のエンジニア リングでアルゴリズムを提供し、Microsoft によってサポートされています。 

R ライブラリを含める[ **RevoScaleR**](ref-r-revoscaler.md)、 [ **MicrosoftML (R)** ](ref-r-microsoftml.md)、およびその他。 R Services がデータベース エンジンと統合されているため、データの近くで分析し、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除できます。

> [!Note]
> R Services が SQL Server 2017 で名前が変更された以降に[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)Python の加算を反映します。

## <a name="components"></a>コンポーネント

SQL Server 2016 には R のみです。 次の表では、SQL Server 2016 の機能について説明します。

| コンポーネント | 説明 |
|-----------|-------------|
| SQL Server スタート パッド サービス | 外部の R ランタイムと、SQL Server インスタンス間の通信を管理するサービス。 |
| R パッケージ | [**RevoScaleR** ](ref-r-revoscaler.md)はこのライブラリでスケーラブルな R. 関数が最も広く使用されている間は、プライマリ ライブラリ。 データ変換と操作、統計の概要作成、視覚化、およびモデリングと分析の多くの形式は、これらのライブラリで表示されます。 さらに、これらのライブラリ内の関数は、並列処理、調整され、計算エンジンによって管理されるデータのチャンク上で動作する機能の使用可能なコア間でワークロードを自動的に配布します。  <br/>[**MicrosoftML (R)** ](ref-r-microsoftml.md)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 <br/>[**sqlRUtils** ](ref-r-sqlrutils.md) T-SQL ストアド プロシージャに R スクリプトを配置すること、データベースでストアド プロシージャを登録すると、R 開発環境からストアド プロシージャを実行しているヘルパー関数を提供します。<br/>[**olapR** ](ref-r-olapr.md)は R で MDX クエリを指定するため|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open)は r です Microsoft のオープン ソース ディストリビューションには。パッケージおよびインタープリターが含まれます。 常にセットアップによってインストールされている MRO のバージョンを使用します。 |
| R ツール | R コンソール ウィンドウとコマンド プロンプトは、R のディストリビューションで標準的なツールです。  |
| R のサンプルとスクリプト |  オープン ソースの R と RevoScaleR パッケージが作成して事前インストールされているデータを使用してスクリプトを実行できるように、組み込みのデータ セットを含める |
| R で事前トレーニング済みモデル | 事前トレーニング済みモデルは特定のユース ケース用に作成し、microsoft データ サイエンスのエンジニア リング チームによって管理されます。 事前トレーニング済みモデルとして使用することができます-正、負のセンチメントをスコア付けで、テキストまたはイメージを提供する新しいデータの入力を使用して機能を検出します。 モデルでは、R services での実行が、SQL Server セットアップでインストールすることはできません。 詳細については、次を参照してください。[インストール事前トレーニング済みの機械学習では、SQL Server のモデル](../install/sql-pretrained-models-install.md)します。 |

## <a name="using-r-services"></a>R Services を使用します。

開発者およびアナリスト多くの場合、ローカルの SQL Server インスタンス上で実行されるコードがあります。 Machine Learning サービスを追加し、外部スクリプトの実行を有効にして、SQL Server のモダリティで R コードを実行することができます。 ストアド プロシージャにスクリプトをラップする、SQL Server テーブルでは、モデルを格納する、またはクエリの T-SQL と R 関数を組み合わせることです。

データベース内分析の最も一般的なアプローチは、使用する[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、R スクリプトを入力パラメーターとして渡します。

従来のクライアント サーバーのやり取りは別の方法です。 IDE のある任意のクライアント ワークステーションからインストールできます[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)、実行をプッシュするコードを記述 (と呼ばれる、*リモート計算コンテキスト*) データとリモートの SQL を操作するサーバー。 

最後に、使用する場合、[スタンドアロン サーバー](r-server-standalone.md)と Developer edition では、同じライブラリとインタープリターを使用して、クライアント ワークステーションでソリューションを構築して SQL Server Machine Learning で運用環境のコードを配置することができます、Services (In-database)。 

## <a name="how-to-get-started"></a>開始する方法

セットアップを開始、バイナリを使い慣れた開発ツールにアタッチし、最初のスクリプトを記述します。

**手順 1:** インストールし、ソフトウェアを構成します。 

+ [SQL Server 2016 R Services (In-database) をインストールします。](../install/sql-r-services-windows-install.md)

**手順 2:** これらのチュートリアルのいずれかを使用して実際に体験が得られます。

+ [チュートリアル: R を使用してデータベース内分析について説明します](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [チュートリアル: R を使用したエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**手順 3:** お気に入りの R パッケージを追加し、Microsoft によって提供されるパッケージと共に使用

+ [SQL Server の R パッケージ管理](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>関連項目

 [SQL Server 2016 R Services をインストールします。](../install/sql-r-services-windows-install.md)
