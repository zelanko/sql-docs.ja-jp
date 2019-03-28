---
title: SQL 開発者向けの SQL Server Machine Learning の in-database Python 分析のチュートリアル
description: SQL Server のストアド プロシージャおよび T-SQL 関数での Python コードを埋め込む方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e036aa2a4c104eaf92e3e9aaf4513f2542bf23b4
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511689"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>チュートリアル:SQL 開発者向けの Python データの分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

構築して Python に基づく機械学習ソリューションを導入する Python の統合について説明します SQL プログラマ向けのこのチュートリアルでは、 [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) SQL Server データベース。 T-SQL、SQL Server Management Studio とでは、データベース エンジンのインスタンスを使用します[Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)と Python 言語のサポート。

このチュートリアルでは、データ モデリング ワークフローで使用される Python 関数について説明します。 手順には、データの探索、ビルドして二項分類モデルとモデルのデプロイが含まれます。 ニューヨーク市タクシーのデータセットと Limosine 委員会のサンプル データを使用し、ビルドは、モデルが旅行に日、しかも、距離、乗車場所の時間に基づくヒントに可能性があるかどうかを予測します。 

このチュートリアルで使用する Python コードのすべては、作成して、Management Studio で実行するストアド プロシージャにラップされます。

> [!NOTE]
> このチュートリアルは、R と Python の両方で使用できます。 R のバージョンについては、次を参照してください。 [in-database analytics R 開発者向け](sqldev-in-database-r-for-sql-developers.md)します。

## <a name="overview"></a>概要

Machine learning ソリューションを構築するプロセスをいくつかのフェーズの間で複数のツール、および領域の専門家の調整を伴う複雑なものを示します。

+ 取得して、データのクリーニング
+ データの探索とモデリングの便利な機能の作成
+ トレーニング セットと、モデルの調整
+ 運用環境へのデプロイ

実際のコードの開発とテストに専用の開発環境を使用してを実行が最適です。 ただし、スクリプトを完全にテストした後に簡単にデプロイできますを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い慣れた環境でのストアド プロシージャ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 SQL Server で操作可能化コードの主要なメカニズムは、外部コードをストアド プロシージャにラップします。

Python、または SQL に新しい Python 開発者に新しい SQL プログラマでは、かどうか、このマルチパート チュートリアルには、Python と SQL Server の in-database 分析を実施するための一般的なワークフローが導入されています。 

+ [レッスン 1:探索し、Python を使用してデータを視覚化します。](sqldev-py3-explore-and-visualize-the-data.md)

+ [レッスン 2:カスタム SQL 関数を使用してデータ機能を作成します。](sqldev-py4-create-data-features-using-t-sql.md)

+ [レッスン 3:トレーニングし、T-SQL を使用して Python モデルの保存](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [レッスン 4:ストアド プロシージャで Python モデルを使用して潜在的な結果を予測します。](sqldev-py6-operationalize-the-model.md)

モデルをデータベースに保存した後から予測モデルを呼び出すことができます[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを使用します。

## <a name="prerequisites"></a>前提条件

+ [Python を使用した SQL Server 2017 Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [権限](../security/user-permission.md)

+ [NYC タクシー デモ データベース](demo-data-nyctaxi-in-sql.md)

すべてのタスクを行うことができますを使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。

このチュートリアルは、データベースとテーブルを作成、データをインポートする SQL クエリの記述などの基本的なデータベース操作に関する知識を前提とします。 Python を理解することを想定しません。 そのため、すべての Python コードが提供されます。 

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [探索し、Python を使用してデータを視覚化します。](sqldev-py3-explore-and-visualize-the-data.md)
