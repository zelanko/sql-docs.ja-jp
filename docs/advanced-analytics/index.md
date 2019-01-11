---
title: R と Python の機械学習とプログラミング拡張機能のドキュメント - SQL Server Machine Learning
description: SQL Server での R および Python と大規模なエンタープライズ データ分析用の組み込みのデータ サイエンス モデリングおよび機械学習アルゴリズム。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/09/2019
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7eb5083f17ab08f19b689b3550f979f88495f604
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206248"
---
# <a name="sql-server-machine-learning"></a>SQL Server Machine Learning

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"

## <a name="sql-server-machine-learning-and-programming-extensions-documentation"></a>SQL Server Machine Learning とプログラミング拡張機能のドキュメント

クイック スタート、チュートリアル、および操作方法に関する記事によって、常駐のリレーショナル データに対して R および Python 外部ライブラリおよび言語を使用する方法について説明します。 [SQL Server Machine Learning](what-is-sql-server-machine-learning.md) の R および Python ライブラリには、基本ディストリビューション、データ サイエンス モデル、機械学習アルゴリズム、およびネットワーク上でデータを転送する必要なく、大規模な高パフォーマンス分析を実行するための関数が含まれています。 

SQL Server 2019 では、Java コード実行で、R および Python と同じ拡張機能フレームワークが使われていますが、データ サイエンスと機械学習関数ライブラリは含まれていません。 新機能の詳細については、「[What's New in SQL Server Machine Learning Services](what-s-new-in-sql-server-machine-learning-services.md)」 (SQL Server Machine Learning Services の新機能) を参照してください。

|   |   | 
|---|---|-
| ![R ロゴ](./media/index/logo_r.png) | オープンソース R は、[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) で [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) と Microsoft AI アルゴリズムによって拡張されました。 これらのライブラリにより、予測および予測モデル、統計分析、視覚化、および大規模なデータ操作ができます。 <br/>R の統合は、[SQL Server 2016](./install/sql-r-services-windows-install.md) から始まり、[SQL Server 2017](./install/sql-machine-learning-services-windows-install.md) にも含まれています。 | 
| ![Python ロゴ](./media/index/logo_python.png) | Python 開発者は、大規模な予測分析と機械学習に Microsoft [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) と [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) ライブラリを使用できます。 Anaconda および Python 3.5 互換ライブラリは、ベースライン ディストリビューションです。 <br/>Python の統合は、[SQL Server 2017](./install/sql-machine-learning-services-windows-install.md) から開始されています。  | 
| ![Java のロゴ](./media/index/logo_java.png) | Java 開発者は、[Java 言語拡張](java/extension-java.md)を使用して、ストアド プロシージャまたは TRANSACT-SQL からアクセス可能なバイナリ形式でコードをラップできます。 <br/>Java の統合は、[SQL Server 2019 - プレビュー](./install/sql-machine-learning-services-ver15.md)から開始されています。 |
::: moniker-end

::: moniker range="=sql-server-2016||=sql-server-2017"

## <a name="sql-server-machine-learning-r-and-python-documentation"></a>SQL Server Machine Learning R および Python ドキュメント

クイック スタート、チュートリアル、および操作方法に関する記事によって、常駐のリレーショナル データに対して R および Python 外部ライブラリおよび言語を使用する方法について説明します。 [SQL Server Machine Learning](what-is-sql-server-machine-learning.md) の R および Python ライブラリには、基本ディストリビューション、データ サイエンス モデル、機械学習アルゴリズム、およびネットワーク上でデータを転送する必要なく、大規模な高パフォーマンス分析を実行するための関数が含まれています。 

|   |   | 
|---|---|-
| ![R ロゴ](./media/index/logo_r.png) | オープンソース R は、[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) で [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) と Microsoft AI アルゴリズムによって拡張されました。 これらのライブラリにより、予測および予測モデル、統計分析、視覚化、および大規模なデータ操作ができます。 <br/>R の統合は、[SQL Server 2016](./install/sql-r-services-windows-install.md) から始まり、[SQL Server 2017](./install/sql-machine-learning-services-windows-install.md) にも含まれています。 | 
| ![Python ロゴ](./media/index/logo_python.png) | Python 開発者は、大規模な予測分析と機械学習に Microsoft [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) と [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) ライブラリを使用できます。 Anaconda および Python 3.5 互換ライブラリは、ベースライン ディストリビューションです。 <br/>Python の統合は、[SQL Server 2017](./install/sql-machine-learning-services-windows-install.md) から開始されています。  | 
::: moniker-end

## <a name="5-minute-quickstarts"></a>5 分のクイックスタート

+ [R での予測モデルの作成](./tutorials/rtsql-create-a-predictive-model-r.md)

+ [R を使用したモデルからの予測とプロット](./tutorials/rtsql-predict-and-plot-from-model.md)


## <a name="step-by-step-tutorials"></a>ステップ バイ ステップ チュートリアル

+ [SQL Server に機械学習および拡張機能フレームワークを追加する方法](install/sql-machine-learning-services-windows-install.md)

+ [T-SQL およびストアド プロシージャから R を実行する方法](./tutorials/sqldev-in-database-r-for-sql-developers.md)

+ [Python で埋め込み分析を使用する方法](./tutorials/sqldev-in-database-python-for-sql-developers.md)


## <a name="video-introduction"></a>ビデオの概要

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>リファレンス

| [パッケージ] | [言語] | [説明] | 
|---------|----------|-------------|
| [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | R | R タスクの分散および並列処理: データ変換、探索、視覚化、統計および予測分析。 |
| [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | R に適合された Microsoft の AI アルゴリズムに基づいた関数。 |
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | R | OLAP キューブからのデータのインポート。 |
| [sqlRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | R | R と T-SQL のカプセル化のためのヘルパー関数。 |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Python タスクの分散および並列処理: データ変換、探索、視覚化、統計および予測分析。  | 
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Python に適合された Microsoft の AI アルゴリズムに基づいた関数。  |