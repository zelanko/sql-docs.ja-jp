---
title: R と Python の machine learning のドキュメント - SQL Server Machine Learning サービス
description: SQL Server での R および Python と大規模なエンタープライズ データ分析用の組み込みのデータ サイエンス モデリングおよび機械学習アルゴリズム。
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: cbe617ea7732468732555bf6f0bba8ebaec2c17a
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141381"
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning サービス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

## <a name="sql-server-machine-learning-services-r-and-python-documentation"></a>SQL Server Machine Learning Services (R および Python) のドキュメント

クイック スタート、チュートリアル、および操作方法に関する記事によって、常駐のリレーショナル データに対して R および Python 外部ライブラリおよび言語を使用する方法について説明します。 R と Python ライブラリ[SQL Server Machine Learning Services](what-is-sql-server-machine-learning.md)基本ディストリビューション、データ サイエンス モデル、機械学習アルゴリズム、およびしなくても、大規模、高パフォーマンスの分析を実施するための関数を含めるネットワーク経由でデータを転送します。

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Java のドキュメントについては、次を参照してください。、 [SQL Server の言語拡張機能ドキュメント](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)します。
::: moniker-end

|   |   |
|---|:--|
| ![R ロゴ](media/index/logo_r.png) | オープンソース R は、[MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) で [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) と Microsoft AI アルゴリズムによって拡張されました。 これらのライブラリにより、予測および予測モデル、統計分析、視覚化、および大規模なデータ操作ができます。<br/>R の統合は、[SQL Server 2016](install/sql-r-services-windows-install.md) から始まり、[SQL Server 2017](install/sql-machine-learning-services-windows-install.md) にも含まれています。 |
| ![Python ロゴ](media/index/logo_python.png) | Python 開発者は、大規模な予測分析と機械学習に Microsoft [revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) と [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) ライブラリを使用できます。 Anaconda および Python 3.5 互換ライブラリは、ベースライン ディストリビューションです。<br/>Python の統合は、[SQL Server 2017](install/sql-machine-learning-services-windows-install.md) から開始されています。 |
| &nbsp; | &nbsp; |

## <a name="5-minute-quickstarts"></a>5 分のクイックスタート

- [R での予測モデルの作成](tutorials/rtsql-create-a-predictive-model-r.md)

- [R を使用したモデルからの予測とプロット](tutorials/rtsql-predict-and-plot-from-model.md)

## <a name="step-by-step-tutorials"></a>ステップ バイ ステップ チュートリアル

- [SQL Server への Machine Learning サービスをインストールする方法](install/sql-machine-learning-services-windows-install.md)

- [T-SQL およびストアド プロシージャから R を実行する方法](tutorials/sqldev-in-database-r-for-sql-developers.md)

- [Python で埋め込み分析を使用する方法](tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="video-introduction"></a>ビデオの概要

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>リファレンス

| [パッケージ] | [言語] | 説明 |
|:--------|:---------|:------------|
| [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) | R | R タスクの分散および並列処理: データ変換、探索、視覚化、統計および予測分析。 |
| [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | R に適合された Microsoft の AI アルゴリズムに基づいた関数。 |
| [olapR](/machine-learning-server/r-reference/olapr/olapr) | R | OLAP キューブからのデータのインポート。 |
| [sqlRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) | R | R と T-SQL のカプセル化のためのヘルパー関数。 |
[revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Python タスクの分散および並列処理: データ変換、探索、視覚化、統計および予測分析。 |
| [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Python に適合された Microsoft の AI アルゴリズムに基づいた関数。 |
| &nbsp; | &nbsp; | &nbsp; |
