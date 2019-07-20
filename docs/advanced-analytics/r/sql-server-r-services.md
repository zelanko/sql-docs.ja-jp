---
title: SQL Server 2016 の R Services
description: データサイエンスと統計モデリング、予測分析、データビジュアライゼーションなどを含む、リレーショナルデータに対する統合 R タスクに対する SQL Server の r。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: e849140125ba39c7c1d8601c5ef32880a9d633ac
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344835"
---
# <a name="r-services-in-sql-server-2016"></a>SQL Server 2016 の R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R Services は、SQL Server で R コードと関数を実行するために使用される、SQL Server 2016 データベースエンジンインスタンスへのアドオンです。 コードは、コアエンジンプロセスから分離された機能拡張フレームワークで実行されますが、リレーショナルデータをストアドプロシージャとして完全に利用できます。また、R ステートメントを含む T-sql スクリプトとして、または T-sql を含む R コードとして使用することもできます。 

R Services には R の基本ディストリビューションが含まれており、Microsoft のエンタープライズ R パッケージと連携して、複数のコアで大量のデータを読み込んで処理し、結果を1つの統合された出力に集約することができます。 Microsoft の R 関数とアルゴリズムは、スケールとユーティリティの両方を対象として設計されています。予測分析、統計モデリング、データビジュアライゼーション、最先端の機械学習アルゴリズムを、エンジニアリングされた商用サーバー製品で提供します。Microsoft がサポートしています。 

R ライブラリには、 [**RevoScaleR**](ref-r-revoscaler.md)、 [**Microsoft ml (r)** ](ref-r-microsoftml.md)などが含まれます。 R Services はデータベースエンジンと統合されているため、分析をデータの近くに保持し、データ移動に伴うコストとセキュリティ上のリスクを排除できます。

> [!Note]
> R Services は、Python の追加を反映して、SQL Server 2017 以降で[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)に名前が変更されました。

## <a name="components"></a>コンポーネント

SQL Server 2016 は R のみです。 次の表では、SQL Server 2016 の機能について説明します。

| コンポーネント | 説明 |
|-----------|-------------|
| SQL Server Launchpad サービス | 外部 R ランタイムと SQL Server インスタンス間の通信を管理するサービス。 |
| R パッケージ | [**RevoScaleR**](ref-r-revoscaler.md)はスケーラブルな R のプライマリライブラリです。このライブラリの関数は、最も広く使用されています。 これらのライブラリには、データの変換と操作、統計の概要作成、視覚化、モデリングと分析のさまざまな形式があります。 また、これらのライブラリの関数は、並列処理のために使用可能なコア間にワークロードを自動的に分散します。また、計算エンジンによって調整および管理されるデータのチャンクを操作できます。  <br/>[**Microsoft ml (R)** ](ref-r-microsoftml.md)は、機械学習アルゴリズムを追加して、テキスト分析、画像分析、およびセンチメント分析のためのカスタムモデルを作成します。 <br/>[**sqlRUtils**](ref-r-sqlrutils.md)には、r スクリプトを t-sql ストアドプロシージャに配置し、ストアドプロシージャをデータベースに登録し、r 開発環境からストアドプロシージャを実行するためのヘルパー関数が用意されています。<br/>[**Olapr**](ref-r-olapr.md)は、R で MDX クエリを指定するためのものです。|
| Microsoft R Open (MRO) | [**Mro**](https://mran.microsoft.com/open)は、Microsoft の R のオープンソースディストリビューションです。パッケージとインタープリターが含まれています。 セットアップによってインストールされたバージョンの MRO を常に使用します。 |
| R ツール | R コンソールのウィンドウとコマンドプロンプトは、R ディストリビューションの標準ツールです。  |
| R のサンプルとスクリプト |  オープンソースの R パッケージと RevoScaleR パッケージには、事前にインストールされたデータを使用してスクリプトを作成して実行するための組み込みデータセットが含まれています。 |
| R の事前トレーニング済みのモデル | 事前トレーニング済みのモデルは、特定のユースケースに対して作成され、Microsoft のデータサイエンスエンジニアリングチームによって管理されます。 事前トレーニング済みのモデルを使用すると、指定した新しいデータ入力を使用して、テキスト内で肯定的なセンチメントをスコア付けしたり、画像の特徴を検出したりできます。 モデルは R Services で実行されますが、SQL Server セットアップを使用してインストールすることはできません。 詳細については、「 [SQL Server で事前トレーニング済みの機械学習モデルをインストール](../install/sql-pretrained-models-install.md)する」を参照してください。 |

## <a name="using-r-services"></a>R Services の使用

多くの場合、開発者とアナリストは、ローカル SQL Server インスタンス上でコードを実行しています。 Machine Learning Services を追加し、外部スクリプトの実行を有効にすることで、SQL Server 感覚様相: ストアドプロシージャでのスクリプトのラップ、SQL Server テーブルへのモデルの格納、クエリでの T-sql と R 関数の組み合わせによって R コードを実行できるようになります。

データベース内分析の最も一般的な方法は、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して、R スクリプトを入力パラメーターとして渡すことです。

従来のクライアントとサーバー間の対話は、もう1つの方法です。 IDE がインストールされている任意のクライアントワークステーションから[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)をインストールし、リモート SQL Server にデータおよび操作を実行するための (*リモートコンピューティングコンテキスト*と呼ばれる) 実行をプッシュするコードを記述できます。 

また、[スタンドアロンサーバー](r-server-standalone.md)と Developer edition を使用している場合は、同じライブラリおよびインタープリターを使用してクライアントワークステーションでソリューションをビルドし、SQL Server Machine Learning Services (データベース内) に運用コードをデプロイすることができます。 

## <a name="how-to-get-started"></a>開始する方法

セットアップを開始し、お気に入りの開発ツールにバイナリをアタッチして、最初のスクリプトを記述します。

**手順 1:** ソフトウェアをインストールして構成します。 

+ [SQL Server 2016 R Services (データベース内) のインストール](../install/sql-r-services-windows-install.md)

**手順 2:** 次のいずれかのチュートリアルを使用してハンズオン体験を得ます。

+ [チュートリアル: R を使用したデータベース内分析の学習](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [チュートリアル: R を使用したエンドツーエンドチュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**手順 3:** お気に入りの R パッケージを追加し、Microsoft が提供するパッケージと共に使用する

+ [SQL Server の R パッケージ管理](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>関連項目

 [SQL Server 2016 R Services のインストール](../install/sql-r-services-windows-install.md)
