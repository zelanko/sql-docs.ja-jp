---
title: SQL Server Machine Learning Services (Python と R) とは何ですか?
titleSuffix: ''
description: Machine Learning Services は SQL Server の機能であり、リレーショナルデータを使用して Python および R スクリプトを実行する機能を提供します。 オープンソースのパッケージとフレームワーク、および予測分析と機械学習のための Microsoft Python および R パッケージを使用できます。 スクリプトは、SQL Server の外部またはネットワーク経由でデータを移動することなく、データベース内で実行されます。 この記事では、SQL Server Machine Learning Services の基本について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/07/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4a1a9a3b0f712458466051ce2c67c0a725ef0a76
ms.sourcegitcommit: 12b7e3447ca2154ec2782fddcf207b903f82c2c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957438"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>SQL Server Machine Learning Services (Python と R) とは何ですか?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services は SQL Server の機能であり、リレーショナルデータを使用して Python および R スクリプトを実行する機能を提供します。 オープンソースのパッケージとフレームワーク、および予測分析と機械学習のための[Microsoft Python および R パッケージ](#packages)を使用できます。 スクリプトは、SQL Server の外部またはネットワーク経由でデータを移動することなく、データベース内で実行されます。 この記事では、SQL Server Machine Learning Services の基本について説明します。

Azure SQL Database では、 [Machine Learning Services](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview)は現在パブリックプレビューの段階にあります。

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> SQL Server で Java を実行する方法については、[言語拡張のドキュメント](../language-extensions/language-extensions-overview.md)を参照してください。
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Machine Learning Services とは

SQL Server Machine Learning Services では、データベース内で Python および R スクリプトを実行できます。 この機能を使用して、データの準備とクリーンアップ、特徴エンジニアリング、およびデータベース内での機械学習モデルのトレーニング、評価、およびデプロイを行うことができます。 この機能により、データが存在するスクリプトが実行され、ネットワーク経由で別のサーバーにデータが転送されることがなくなります。

Python と R のベースディストリビューションは Machine Learning Services に含まれています。 PyTorch、、scikit-learn などのオープンソースのパッケージとフレームワークを使用できます。また、Python 用の Microsoft パッケージ [revoscalepy](python/ref-py-revoscalepy.md) と [microsoftml](python/ref-py-microsoftml.md)、および[RevoScaleR](r/ref-r-revoscaler.md)、[microsoft ml](r/ref-r-microsoftml.md)、[olapr](r/ref-r-olapr.md) などを使用できます。、R の場合は [sqlrutils](r/ref-r-sqlrutils.md)。

Machine Learning Services は、拡張フレームワークを使用して SQL Server で Python および R スクリプトを実行します。 詳細については、次を参照してください。

+ [機能拡張フレームワーク](concepts/extensibility-framework.md)
+ [Python 拡張機能](concepts/extension-python.md)
+ [R 拡張機能](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Machine Learning Services でできること

Machine Learning Services を使用すると、SQL Server 内で機械学習とディープラーニングモデルを構築してトレーニングすることができます。 また、既存のモデルを Machine Learning Services に配置し、予測にリレーショナルデータを使用することもできます。

Machine Learning Services SQL Server 使用できる予測の種類の例としては、次のものがあります。

|||
|-|-|
|分類/分類|顧客からのフィードバックを自動的に正および負のカテゴリに分割する|
|回帰/予測の連続値|サイズと場所に基づいて、家の価格を予測する|
|異常検出|不正な銀行取引の検出 |
|推奨事項|以前の購入に基づいて、オンラインの買物客が購入する可能性のある製品を提案します|

### <a name="how-to-execute-python-and-r-scripts"></a>Python および R スクリプトを実行する方法

Machine Learning Services で Python および R スクリプトを実行するには、次の2つの方法があります。

+ 最も一般的な方法は、T-sql ストアドプロシージャ[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用することです。

+ また、任意の Python または R クライアントを使用し、リモート SQL Server に実行をプッシュするスクリプト (*リモートコンピューティングコンテキスト*と呼ばれます) を記述することもできます。 詳細については、「 [Python 開発](python/setup-python-client-tools-sql.md)および[R 開発](r/set-up-a-data-science-client.md)用のデータサイエンスクライアントを設定する方法」を参照してください。

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Python および R パッケージ

Microsoft のエンタープライズパッケージに加えて、オープンソースのパッケージとフレームワークを使用することもできます。 最も一般的なオープンソースの Python および R パッケージは、Machine Learning Services にプレインストールされています。 Microsoft の次の Python および R パッケージも含まれています。

| [言語] | [パッケージ] | 説明 |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | スケーラブルな Python 用のプライマリパッケージ。 データの変換と操作、統計の概要作成、視覚化、モデリングのさまざまな形式。 さらに、このパッケージの関数は、並列処理のために使用可能なコア間にワークロードを自動的に分散します。 |
| Python | [microsoftml](python/ref-py-microsoftml.md) | 機械学習アルゴリズムを追加して、テキスト分析、画像分析、およびセンチメント分析のためのカスタムモデルを作成します。 | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | スケーラブルな R のプライマリパッケージ。データの変換と操作、統計の概要作成、視覚化、およびさまざまな形式のモデリングを行うことができます。 さらに、このパッケージの関数は、並列処理のために使用可能なコア間にワークロードを自動的に分散します。 |
| R | [Microsoft Ml (R)](r/ref-r-microsoftml.md) | 機械学習アルゴリズムを追加して、テキスト分析、画像分析、およびセンチメント分析のためのカスタムモデルを作成します。 |
| R | [olapR](r/ref-r-olapr.md) | SQL Server Analysis Services OLAP キューブに対する MDX クエリに使用される R 関数。 |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | T-sql ストアドプロシージャで R スクリプトを使用し、そのストアドプロシージャをデータベースに登録し、 [r 開発環境](r/set-up-a-data-science-client.md)からストアドプロシージャを実行するためのメカニズム。 |
| R | [Microsoft R オープンプラン](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) は、Microsoft からの R の拡張ディストリビューションです。 これは、統計分析とデータサイエンスを行うための完全なオープンソースプラットフォームです。 これは、R と互換性があり、100% に準拠しており、パフォーマンスと再現性を向上させるための追加機能が含まれています。 |

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Machine Learning Services の使用を開始操作方法

1. [SQL Server Machine Learning Services のインストール](install/sql-machine-learning-services-windows-install.md)

1. 開発ツールを構成します。 次のものを使用できます。

    + [Azure Data Studio](../azure-data-studio/what-is.md)または[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)を使用して、t-sql とストアドプロシージャ[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して、Python または R スクリプトを実行します。
    + 独自の開発用ノート pc またはワークステーション上の Python または R を使用してスクリプトを実行できます。 データをローカルでプルするか、 [revoscalepy](python/ref-py-revoscalepy.md)と[RevoScaleR](r/ref-r-revoscaler.md)を使用して SQL Server にリモートで実行することができます。 詳細については、「 [Python 開発](python/setup-python-client-tools-sql.md)および[R 開発](r/set-up-a-data-science-client.md)用のデータサイエンスクライアントを設定する方法」を参照してください。

1. 初めての Python または R スクリプトを作成する

    + クイック スタート: [Python](tutorials/quickstart-python-run-using-t-sql.md)または[R](tutorials/quickstart-r-run-using-tsql.md)で "Hello world" スクリプトを実行する
    + クイック スタート: [Python](tutorials/quickstart-python-train-score-in-tsql.md)または[R](tutorials/quickstart-r-create-predictive-model.md)で予測モデルを作成する
    + チュートリアル:[T-sql で Python を使用する](tutorials/sqldev-in-database-python-for-sql-developers.md):データの探索、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (5 部構成シリーズ)
    + チュートリアル:[T-sql で R を使用する](tutorials/sqldev-in-database-r-for-sql-developers.md):データの探索、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (5 部構成シリーズ)
    + チュートリアル:[R ツールで Machine Learning Services を使用する](tutorials/walkthrough-data-science-end-to-end-walkthrough.md):データの探索、グラフとプロットの作成、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (6 部構成シリーズ)

## <a name="next-steps"></a>次の手順

+ [SQL Server Machine Learning Services のインストール](install/sql-machine-learning-services-windows-install.md)
+ [Python 開発](python/setup-python-client-tools-sql.md)および[R 開発](r/set-up-a-data-science-client.md)用のデータサイエンスクライアントをセットアップする
