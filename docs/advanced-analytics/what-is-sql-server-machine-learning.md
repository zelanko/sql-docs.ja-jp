---
title: SQL Server Machine Learning Services とは (Python と R)
titleSuffix: ''
description: Machine Learning Services は、リレーショナル データを使用して Python および R スクリプトを実行できるようになる SQL Server の機能です。 オープンソースのパッケージとフレームワーク、および予測分析と機械学習用の Microsoft Python および R パッケージを使用できます。 スクリプトは、SQL Server の外部またはネットワーク経由でデータを移動することなく、データベース内で実行されます。 この記事では、SQL Server Machine Learning Services の基本について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/06/2020
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a94a3aea418a4c404b568fe6df7af701bc46de34
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285906"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>SQL Server Machine Learning Services とは (Python と R)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services は、リレーショナル データを使用して Python および R スクリプトを実行できるようになる SQL Server の機能です。 オープンソースのパッケージとフレームワーク、および予測分析と機械学習用の [Microsoft Python および R パッケージ](#packages)を使用できます。 スクリプトは、SQL Server の外部またはネットワーク経由でデータを移動することなく、データベース内で実行されます。 この記事では、SQL Server Machine Learning Services の基本について説明します。

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> SQL Server で Java を実行する方法については、[言語拡張のドキュメント](../language-extensions/language-extensions-overview.md)を参照してください。
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Machine Learning Services とは

SQL Server Machine Learning Services では、データベース内で Python および R スクリプトを実行できます。 この機能を使用して、データの準備とクリーンアップ、特徴エンジニアリング、およびデータベース内での機械学習モデルのトレーニング、評価、およびデプロイを行うことができます。 この機能により、データが存在する場所でスクリプトが実行され、ネットワークを介して別のサーバーにデータが転送されなくなります。

Python と R のベース ディストリビューションは Machine Learning Services に含まれています。 Python 用の Microsoft パッケージ [revoscalepy](python/ref-py-revoscalepy.md) および [microsoftml](python/ref-py-microsoftml.md) と、R 用の [RevoScaleR](r/ref-r-revoscaler.md)、[MicrosoftML](r/ref-r-microsoftml.md)、[olapR](r/ref-r-olapr.md)、および [sqlrutils](r/ref-r-sqlrutils.md) に加え、PyTorch、TensorFlow、scikit-learn などのオープンソースのパッケージとフレームワークをインストールおよび使用できます。

Machine Learning Services では、SQL Server での Python および R スクリプトの実行に拡張フレーム ワークを使用します。 このしくみについては以下を参照してください。

+ [機能拡張フレームワーク](concepts/extensibility-framework.md)
+ [Python の拡張機能](concepts/extension-python.md)
+ [R の拡張機能](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Machine Learning Services でできること

Machine Learning Services を使用して、SQL Server 内で機械学習モデルとディープ ラーニング モデルを構築およびトレーニングできます。 また、既存のモデルを Machine Learning Services にデプロイし、予測にリレーショナル データを使用することもできます。

SQL Server Machine Learning Services を使用できる予測の種類の例としては、次のものがあります。

|||
|-|-|
|分類/カテゴリ|顧客からのフィードバックを肯定的なカテゴリと否定的なカテゴリに自動的に分割します|
|回帰/予測の連続値|サイズと場所に基づいて家の価格を予測します|
|異常検出|不正な銀行取引を検出します |
|Recommendations|以前の購入に基づいて、オンラインの顧客が購入する商品を提案します|

### <a name="how-to-execute-python-and-r-scripts"></a>Python および R スクリプトを実行する方法

Machine Learning Services で Python および R スクリプトを実行するには、次の 2 つの方法があります。

+ 最も一般的な方法は、T-SQL ストアド プロシージャ [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) を使用することです。

+ また、任意の Python または R クライアントを使用して、実行をリモートの SQL Server にプッシュするスクリプト (*リモート計算コンテキスト*と呼ばれます) を書くこともできます。 詳細については、[Python 開発](python/setup-python-client-tools-sql.md)と [R 開発](r/set-up-a-data-science-client.md)のためにデータ サイエンス クライアントを設定する方法に関する記事を参照してください。

<a name="versions"></a>

## <a name="python-and-r-versions"></a>Python および R のバージョン

Machine Learning Services に含まれる Python および R のバージョンは、使用する SQL Server のバージョンによって異なります。 

| SQL Server のバージョン | Python バージョン | R バージョン |
|-|-|-|
| SQL Server 2017 | 3.5.2 | 3.3.3 |
| SQL Server 2019 | 3.7.3 | 3.5.2 |

SQL Server 2016 の R バージョンについては、[「R Services とは」の「R バージョン」セクション](r/sql-server-r-services.md#version)を参照してください。

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Python および R パッケージ

Microsoft のエンタープライズ パッケージに加えて、オープンソース パッケージとフレームワークを使用できます。 最も一般的なオープンソースの Python および R パッケージは、Machine Learning Services にプレインストールされています。 Microsoft の次の Python および R パッケージも含まれています。

| Language | Package | 説明 |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | スケーラブルな Python 用のプライマリ パッケージ。 データの変換と操作、統計の概要、視覚化、および多くの形式のモデリング。 さらに、このパッケージの関数により、並列処理に使用できるコア全体にワークロードが自動的に分散されます。 |
| Python | [microsoftml](python/ref-py-microsoftml.md) | テキスト分析、画像分析、感情分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | スケーラブルな R の主要パッケージ。データの変換と操作、統計の概要、視覚化、多くの形式のモデリング。 さらに、このパッケージの関数により、並列処理に使用できるコア全体にワークロードが自動的に分散されます。 |
| R | [MicrosoftML (R)](r/ref-r-microsoftml.md) | テキスト分析、画像分析、感情分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 |
| R | [olapR](r/ref-r-olapr.md) | SQL Server Analysis Services OLAP キューブに対する MDX クエリに使用される R 関数。 |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | T-SQL ストアド プロシージャで R スクリプトを使用し、そのストアド プロシージャをデータベースに登録し、[R 開発環境](r/set-up-a-data-science-client.md)からストアド プロシージャを実行するメカニズム。 |
| R | [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) は、Microsoft の R の拡張ディストリビューションです。 これは、統計分析とデータ サイエンスの機能が一式そろったオープンソース プラットフォームです。 R に基づき、100% の互換性があり、パフォーマンスと再現性を向上させる追加機能が含まれています。 |

Machine Learning Services と共にインストールされるパッケージと、他のパッケージをインストールする方法の詳細については、以下を参照してください。

+ [Python パッケージ情報の取得](package-management/python-package-information.md)
+ [sqlmlutils を使用した Python パッケージのインストール](package-management/install-additional-python-packages-on-sql-server.md)
+ [R パッケージ情報の取得](package-management/r-package-information.md)
+ [sqlmlutils を使用した新しい R パッケージのインストール](package-management/install-additional-r-packages-on-sql-server.md)

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Machine Learning Services の基本的な使用方法

1. [SQL Server Machine Learning Services のインストール](install/sql-machine-learning-services-windows-install.md)

1. 開発ツールを構成します。 使用できるもの:

    + T-SQL およびストアド プロシージャ [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) を使用して Python または R スクリプトを実行する [Azure Data Studio](../azure-data-studio/what-is.md) または [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)。
    + スクリプトを実行する開発用のノート PC またはワークステーション上の Python または R。 [revoscalepy](python/ref-py-revoscalepy.md) と [RevoScaleR](r/ref-r-revoscaler.md) を使用してデータをローカルにプルすることや、リモートから SQL Server に実行をプッシュすることができます。 詳細については、[Python 開発](python/setup-python-client-tools-sql.md)と [R 開発](r/set-up-a-data-science-client.md)のためにデータ サイエンス クライアントを設定する方法に関する記事を参照してください。

1. 初めての Python または R スクリプトを作成する

    + クイック スタート:[単純な Python スクリプトを実行する](tutorials/quickstart-python-create-script.md)
    + クイック スタート:[単純な R スクリプトを実行する](tutorials/quickstart-r-create-script.md)
    + チュートリアル:[T-SQL で Python を使用する](tutorials/sqldev-in-database-python-for-sql-developers.md):データの探索、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (5 部構成シリーズ)
    + チュートリアル:[T-SQL で R を使用する](tutorials/sqldev-in-database-r-for-sql-developers.md):データの探索、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (5 部構成シリーズ)

## <a name="next-steps"></a>次のステップ

+ [SQL Server Machine Learning Services のインストール](install/sql-machine-learning-services-windows-install.md)
+ [Python 開発](python/setup-python-client-tools-sql.md)と [R 開発](r/set-up-a-data-science-client.md)のためにデータ サイエンス クライアントを設定する
