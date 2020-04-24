---
title: Python のチュートリアル
description: この記事では、SQL Server Machine Learning Services 用の Python チュートリアルについて説明します。 SQL Server でスクリプトを実行して機械学習モデルを構築する方法をご確認ください。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e3733f12ed93d7c84a86259742b6996333c3900f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487353"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services 用の Python のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) 用の Python のチュートリアルおよびクイックスタートについて説明します。

+ Python スクリプトの実行方法について説明します。
+ Python モデルをビルドし、トレーニングして、SQL Server に展開します。
+ リモートおよびローカルの計算コンテキストについて説明します。
+ データ サイエンスと機械学習のための Microsoft Python パッケージについて説明します。

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Python のチュートリアル

| チュートリアル | 説明 |
|-|-|
| [線形回帰によるスキー レンタルの予測](python-ski-rental-linear-regression.md) | Python と線形回帰を使用して、スキー レンタル数を予測します。 Azure Data Studio のノートブックを使用してデータの準備とモデルのトレーニングを行い、T-SQL を使用してモデルを展開します。 |
| [K-Means クラスタリングを使用した顧客の分類](python-clustering-model.md) | Python を使用して、顧客を分類するための K-Means クラスタリング モデルを開発および展開します。 Azure Data Studio のノートブックを使用してデータの準備とモデルのトレーニングを行い、T-SQL を使用してモデルを展開します。 |
| [revoscalepy を使用したモデルの作成](use-python-revoscalepy-to-create-model.md) | SQL Server を計算コンテキストとして使用してリモートの Python クライアントからコードを実行する方法を示します。 このチュートリアルでは、**revoscalepy** ライブラリの **rxLinMod** を使用してモデルを作成します。 |
| [SQL 開発者向けの Python データ分析](sqldev-in-database-python-for-sql-developers.md) | このエンドツーエンド チュートリアルでは、T-SQL を使用して完全な Python ソリューションを構築するプロセスについて説明します。 |

## <a name="python-quickstarts"></a>Python のクイックスタート

SQL Server Machine Learning Services を初めて使用する場合は、Python のクイックスタートを試すこともできます。

| クイック スタート | 説明 |
|-|-|
| [Python と SQL Server での Hello World](quickstart-python-create-script.md) | [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して T-SQL で Python を呼び出す方法の基本を説明します。 |
| [SQL Server での Python を使用したデータ型とオブジェクトの処理](quickstart-python-data-structures.md) | SQL Server で Python pandas パッケージを使用してデータ構造を処理する方法について説明します。 |
| [Python での予測モデルの作成とスコア付け](quickstart-python-train-score-model.md) | Python モデルを作成、トレーニング、および使用して新しいデータから予測を行う方法について説明します。 |

## <a name="next-steps"></a>次のステップ

+ [SQL Server Machine Learning Services (Python と R) とは](../sql-server-machine-learning-services.md)
+ [SQL Server への Python の拡張機能](../concepts/extension-python.md)