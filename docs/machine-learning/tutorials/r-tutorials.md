---
title: R のチュートリアル
titleSuffix: SQL machine learning
description: この記事では、SQL 機械学習用の R のチュートリアルについて説明します。 スクリプトを実行して機械学習モデルを構築する方法をご確認ください。
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/04/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 63c271c4e1d59c9446495607b42b0b5ad13ea246
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606924"
---
# <a name="r-tutorials-for-sql-machine-learning"></a>SQL 機械学習用の R チュートリアル

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
この記事では、[SQL Server 上の Machine Learning Services](../sql-server-machine-learning-services.md) および [ビッグ データ クラスター](../../big-data-cluster/machine-learning-services.md)用の R のチュートリアルおよびクイックスタートについて説明します。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
この記事では、[SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) 用の R のチュートリアルおよびクイックスタートについて説明します。
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
この記事では、[SQL Server 2016 R サービス](../r/sql-server-r-services.md)用の R のチュートリアルおよびクイックスタートについて説明します。
::: moniker-end

<a name="bkmk_sqltutorials"></a>

## <a name="r-tutorials"></a>R のチュートリアル

| チュートリアル | 説明 |
|------|-------------|
| [デシジョン ツリーでスキー レンタルを予測する](r-predictive-model-introduction.md) | R とデシジョン ツリー モデルを使用して、将来のスキー レンタルの数を予測します。 Azure Data Studio のノートブックを使用してデータの準備とモデルのトレーニングを行い、T-SQL を使用してモデルを展開します。 |
| [K-Means クラスタリングを使用した顧客の分類](r-clustering-model-introduction.md) | R を使用して、顧客を分類するための K-Means クラスタリング モデルを開発および展開します。 Azure Data Studio のノートブックを使用してデータの準備とモデルのトレーニングを行い、T-SQL を使用してモデルを展開します。 |
| [データ サイエンティスト向けのデータベース内 R 分析](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | SQL Server を初めて使用する R 開発者向けに、このチュートリアルでは SQL Server で一般的なデータ サイエンス タスクを実行する方法について説明します。 データを読み込んで視覚化し、モデルをトレーニングして SQL Server に保存し、予測分析にモデルを使用します。 |
| [SQL 開発者向けのデータベース内 R 分析](../tutorials/sqldev-in-database-r-for-sql-developers.md) | [!INCLUDE[tsql](../../includes/tsql-md.md)] ツールのみを使用して、完全な R ソリューションを構築し、展開します。 ソリューションを運用環境に移行することに重点を置いています。 ストアド プロシージャに R コードをラップし、R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存し、パラメーター化された呼び出しを R モデルに行い、予測を実行する方法について学習します。 |

## <a name="r-quickstarts"></a>R のクイックスタート

SQL 機械学習を初めて使用する場合は、R のクイックスタートを試すこともできます。

| クイック スタート | 説明 |
|-|-|
| [単純な R スクリプトを実行する](quickstart-r-create-script.md) | [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して T-SQL で R を呼び出す方法の基本を説明します。 |
| [R を使用したデータ構造とオブジェクト](quickstart-r-data-types-and-objects.md) | SQL で R を使用してデータ構造を処理する方法について説明します。 |
| [R での予測モデルの作成とスコア付け](quickstart-r-data-types-and-objects.md) | R モデルを作成、トレーニング、および使用して新しいデータから予測を行う方法について説明します。 |

## <a name="next-steps"></a>次のステップ

SQL Server での R の技術的な詳細については、「[SQL Server の R 言語拡張機能](../concepts/extension-r.md)」を参照してください。
