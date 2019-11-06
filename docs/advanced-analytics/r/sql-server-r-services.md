---
title: SQL Server 2016 R Services とは
titleSuffix: ''
description: R Services は、リレーショナルデータを使用して R スクリプトを実行する機能を提供する SQL Server 2016 の機能です。 オープンソースのパッケージとフレームワーク、および予測分析と機械学習のための Microsoft R パッケージを使用できます。 スクリプトは、SQL Server の外部またはネットワーク経由でデータを移動することなく、データベース内で実行されます。 この記事では、SQL Server R Services の基本について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/12/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 99aba9748e7ee6d53aabb18919324243740d996a
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71149926"
---
# <a name="what-is-sql-server-2016-r-services"></a>SQL Server 2016 R Services とは
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

R Services は、リレーショナルデータを使用して R スクリプトを実行する機能を提供する SQL Server 2016 の機能です。 オープンソースのパッケージとフレームワーク、および予測分析と機械学習のための[Microsoft R パッケージ](#packages)を使用できます。 スクリプトは、SQL Server の外部またはネットワーク経由でデータを移動することなく、データベース内で実行されます。 この記事では、SQL Server R Services の基本について説明します。

> [!Note]
> R Services は SQL Server 2017 以降の[Machine Learning Services](../what-is-sql-server-machine-learning.md)に名前が変更され、Python と r の両方をサポートしています。

## <a name="what-is-r-services"></a>R Services とは?

SQL Server R Services を使用すると、データベース内で R スクリプトを実行できます。 この機能を使用して、データの準備とクリーンアップ、特徴エンジニアリング、およびデータベース内での機械学習モデルのトレーニング、評価、およびデプロイを行うことができます。 この機能により、データが存在するスクリプトが実行され、ネットワーク経由で別のサーバーにデータが転送されることがなくなります。

R の基本ディストリビューションは R Services に含まれています。 Microsoft packages [RevoScaleR](../r/ref-r-revoscaler.md)、[MicrosoftML](../r/ref-r-microsoftml.md)、microsoft packages、[olapr]. に加えて、オープンソースのパッケージとフレームワークを使用することもできます。/r/ref-r-olapr.md)、および R の[sqlrutils](../r/ref-r-sqlrutils.md)。

R Services は、拡張フレームワークを使用して SQL Server で R スクリプトを実行します。 詳細については、次を参照してください。

+ [機能拡張フレームワーク](../concepts/extensibility-framework.md)
+ [R 拡張機能](../concepts/extension-r.md)

## <a name="what-can-i-do-with-r-services"></a>R Services でできること

R Services を使用して、SQL Server 内で機械学習とディープラーニングモデルを構築し、トレーニングすることができます。 また、既存のモデルを R Services に配置し、予測にリレーショナルデータを使用することもできます。

に SQL Server R Services 使用できる予測の種類の例として、次のものがあります。

|||
|-|-|
|分類/分類|顧客からのフィードバックを自動的に正および負のカテゴリに分割する|
|回帰/予測の連続値|サイズと場所に基づいて、家の価格を予測する|
|異常検出|不正な銀行取引の検出 |
|推奨事項|以前の購入に基づいて、オンラインの買物客が購入する可能性のある製品を提案します|

### <a name="how-to-execute-r-scripts"></a>R スクリプトを実行する方法

R Services で R スクリプトを実行するには、次の2つの方法があります。

+ 最も一般的な方法は、T-sql ストアドプロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用することです。

+ また、任意の R クライアントを使用して、(*リモートコンピューティングコンテキスト*と呼ばれる) 実行をリモート SQL Server にプッシュするスクリプトを記述することもできます。 詳細については[、「データサイエンスクライアントの R 開発を設定](../r/set-up-a-data-science-client.md)する方法」を参照してください。

<a name="packages"></a>

## <a name="r-packages"></a>R パッケージ

Microsoft のエンタープライズパッケージに加えて、オープンソースのパッケージとフレームワークを使用することもできます。 最も一般的なオープンソースの R パッケージは、R Services にプレインストールされています。 Microsoft の次の R パッケージも含まれています。

| [パッケージ] | 説明 |
|-|-|
| [RevoScaleR](../r/ref-r-revoscaler.md) | スケーラブルな R のプライマリパッケージ。データの変換と操作、統計の概要作成、視覚化、およびさまざまな形式のモデリングを行うことができます。 さらに、このパッケージの関数は、並列処理のために使用可能なコア間にワークロードを自動的に分散します。 |
| [Microsoft Ml (R)](../r/ref-r-microsoftml.md) | 機械学習アルゴリズムを追加して、テキスト分析、画像分析、およびセンチメント分析のためのカスタムモデルを作成します。 |
| [olapR](../r/ref-r-olapr.md) | SQL Server Analysis Services OLAP キューブに対する MDX クエリに使用される R 関数。 |
| [sqlrutils](../r/ref-r-sqlrutils.md) | T-sql ストアドプロシージャで R スクリプトを使用し、そのストアドプロシージャをデータベースに登録し、 [r 開発環境](../r/set-up-a-data-science-client.md)からストアドプロシージャを実行するためのメカニズム。 |
| [Microsoft R オープンプラン](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) は、Microsoft からの R の拡張ディストリビューションです。 これは、統計分析とデータサイエンスを行うための完全なオープンソースプラットフォームです。 これは、R と互換性があり、100% に準拠しており、パフォーマンスと再現性を向上させるための追加機能が含まれています。 |

## <a name="how-do-i-get-started-with-rservices"></a>RServices を使ってみる操作方法

1. [SQL Server 2016 R Services のインストール](../install/sql-r-services-windows-install.md)

1. 開発ツールを構成します。 次のものを使用できます。

    + [Azure Data Studio](../../azure-data-studio/what-is.md)または[SQL Server Management Studio (SSMS)](../../ssms/sql-server-management-studio-ssms.md)を使用して、t-sql とストアドプロシージャ[Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して R スクリプトを実行します。
    + スクリプトを実行するには、独自の開発用ノート pc またはワークステーションで R を使用します。 [RevoScaleR](../r/ref-r-revoscaler.md)を使用してデータをローカルにプルするか、リモートで実行を SQL Server にプッシュすることができます。 詳細については[、「データサイエンスクライアントの R 開発を設定](../r/set-up-a-data-science-client.md)する方法」を参照してください。

1. 最初の R スクリプトを作成する

    + クイック スタート: [SQL Server での単純な R スクリプトの作成と実行](../tutorials/quickstart-r-create-script.md)
    + クイック スタート: [R で予測モデルを作成してトレーニングする](../tutorials/quickstart-r-train-score-model.md)
    + チュートリアル:[T-sql で R を使用する](../tutorials/sqldev-in-database-r-for-sql-developers.md):データの探索、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (5 部構成シリーズ)
    + チュートリアル:R[ツールで r Services を使用する](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md):データの探索、グラフとプロットの作成、特徴エンジニアリングの実行、モデルのトレーニングとデプロイ、予測の作成 (6 部構成シリーズ)

## <a name="next-steps"></a>次の手順

+ [SQL Server 2016 R Services のインストール](../install/sql-r-services-windows-install.md)
+ [R 開発用のデータサイエンスクライアントをセットアップする](../r/set-up-a-data-science-client.md)