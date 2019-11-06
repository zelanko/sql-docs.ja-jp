---
title: Python のチュートリアル
description: この記事では、SQL Server Machine Learning Services の Python チュートリアルについて説明します。 Python スクリプトの実行方法について説明します。 Python モデルをビルドし、トレーニングして、SQL Server に配置します。 リモートとローカルのコンピューティングコンテキストについて説明します。 データサイエンスと機械学習のための Microsoft Python パッケージについて説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 80f714810acd8c04c80fe0b8abe5214a456f6dd6
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199409"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の Python チュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、 [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)の Python のチュートリアルとクイックスタートについて説明します。

+ Python スクリプトの実行方法について説明します。
+ Python モデルをビルドし、トレーニングして、SQL Server に配置します。
+ リモートとローカルのコンピューティングコンテキストについて説明します。
+ データサイエンスと機械学習のための Microsoft Python パッケージについて説明します。

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Python のチュートリアル

| チュートリアル | 説明 |
|-|-|
| [線形回帰による ski レンタルの予測](python-ski-rental-linear-regression.md) | Python と線形回帰を使用して、ski のレンタル数を予測します。 Azure Data Studio のノートブックを使用して、データを準備し、モデルをトレーニングし、モデルを配置するための T-sql を使用します。 |
| [K を使用して顧客を分類する方法クラスタリング](python-clustering-model.md) | Python を使用して、顧客を分類する K の意味のあるクラスターモデルを開発およびデプロイします。 Azure Data Studio のノートブックを使用して、データを準備し、モデルをトレーニングし、モデルを配置するための T-sql を使用します。 |
| [Revoscalepy を使用してモデルを作成する](use-python-revoscalepy-to-create-model.md) | SQL Server を計算コンテキストとして使用してリモート Python クライアントからコードを実行する方法を示します。 このチュートリアルでは、 **revoscalepy**ライブラリの**rxLinMod**を使用してモデルを作成します。 |
| [SQL 開発者向けの Python Data Analytics](sqldev-in-database-python-for-sql-developers.md) | このエンドツーエンドチュートリアルでは、T-sql を使用して完全な Python ソリューションを構築するプロセスについて説明します。 |

## <a name="python-quickstarts"></a>Python クイックスタート

SQL Server Machine Learning Services を初めて使用する場合は、Python のクイックスタートを試すこともできます。

| クイック スタート | 説明 |
|-|-|
| [Python および SQL Server での Hello World](quickstart-python-create-script.md) | [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して T-sql で Python を呼び出す方法の基本について説明します。 |
| [SQL Server での Python を使用したデータ型とオブジェクトの処理](quickstart-python-data-structures.md) | SQL Server が Python パンダパッケージを使用してデータ構造を処理する方法について説明します。 |
| [Python で予測モデルを作成してスコア付けする](quickstart-python-train-score-model.md) | Python モデルを作成、トレーニング、および使用して、新しいデータから予測を行う方法について説明します。 |

## <a name="next-steps"></a>次の手順

+ [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
+ [SQL Server するための Python 拡張機能](../concepts/extension-python.md)