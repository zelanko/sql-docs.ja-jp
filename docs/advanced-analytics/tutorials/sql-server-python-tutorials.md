---
title: SQL Server 2017 の Python チュートリアルの概要 - SQL Server Machine Learning
description: SQL Server 2017 データベース内分析用の Python のチュートリアルを紹介します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9101471c53ea1e253f7a6eb13e0c2cb2bc137ed3
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046462"
---
# <a name="sql-server-2017-python-tutorials"></a>SQL Server 2017 の Python のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事でデータベース内分析用の Python のチュートリアルを説明します[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)します。 

+ ラップして、ストアド プロシージャで Python コードを実行する方法について説明します。
+ シリアル化し、Python ベースのモデルを SQL Server データベースに保存します。
+ リモートとローカル コンピューティング コンテキストを使用する状況について説明します。
+ データ サイエンスと機械学習タスク用 Microsoft Python モジュールをについて説明します。

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Python のクイック スタートとチュートリアル

| リンク | 説明 |
|------|-------------|
| [クイック スタート:SQL Server での Python スクリプトの"hello world"](quickstart-r-run-using-tsql.md) | T-SQL で Python を呼び出す方法の基本について説明します。 |
| [クイック スタート:作成、トレーニング、および SQL Server でのストアド プロシージャで Python モデルを使用](quickstart-python-train-score-in-tsql.md) | ストアド プロシージャは、入力、およびストアド プロシージャの実行を提供することで Python コードを埋め込みのしくみについて説明します。 |
| [チュートリアル:Revoscalepy を使用して、モデルを作成します。](use-python-revoscalepy-to-create-model.md) | SQL Server コンピューティング コンテキストを使用して、リモート Python ターミナルからコードを実行する方法を示します。 Python ツールと環境についての知識があります。 サンプル コードを使用してモデルを作成する提供**rxLinMod**、新しい**revoscalepy**ライブラリ。 |
| [チュートリアル:SQL 開発者向けの In-database Python 分析について説明します](sqldev-in-database-python-for-sql-developers.md) | このエンド ツー エンド チュートリアルでは、T-SQL ストアド プロシージャを使用して完全な Python ソリューションを構築するプロセスについて説明します。 すべての Python コードが含まれます。|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>コード サンプル

これらのサンプルとデモの SQL Server 開発チームによって提供されることは、実際のアプリケーションで埋め込み分析を使用する方法を選択します。

| リンク | 説明 |
|------|-------------|
| [Python と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | スキー レンタル ビジネスを予測する機械学習、今後のレンタルを今後の需要を満たすためには、ビジネスの計画と人員配置を一層使用方法について説明します。 |
| [顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | K-平均法アルゴリズムを使用して、顧客の教師なしのクラスタ リングを実行する方法について説明します。 |

## <a name="see-also"></a>関連項目

+ [SQL Server への Python 拡張機能](../concepts/extension-python.md)
+ [SQL Server Machine Learning Services のチュートリアル](machine-learning-services-tutorials.md)
