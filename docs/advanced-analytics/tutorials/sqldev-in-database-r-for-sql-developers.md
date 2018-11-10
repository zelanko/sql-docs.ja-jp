---
title: R と SQL Server Machine Learning を使用してデータベース内分析のチュートリアル |Microsoft Docs
description: R プログラミング言語のコードでは、SQL Server のストアド プロシージャおよび T-SQL 関数を埋め込む方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80c4d39e87984b022340079be4d944ed6ad963e3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030649"
---
# <a name="tutorial-in-database-r-analytics-for-sql-developers"></a>SQL 開発者向けのチュートリアル: データベース内の R の分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

構築し、R ベースの machine learning を使用してソリューションを展開する R の統合について説明します SQL プログラマ向けのこのチュートリアルでは、 [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) SQL Server データベース。 

このチュートリアルでは、ワークフローをモデル化データで使用される R 関数を紹介します。 手順には、データの探索、ビルドして二項分類モデルとモデルのデプロイが含まれます。 ニューヨーク市タクシーのデータセットと Limosine 委員会のサンプル データを使用し、ビルドは、モデルが旅行に日、しかも、距離、乗車場所の時間に基づくヒントに可能性があるかどうかを予測します。 このチュートリアルで使用する R コードのすべては、作成して、Management Studio で実行するストアド プロシージャにラップされます。


> [!NOTE]
> 
> このチュートリアルは、R と Python の両方で使用できます。 Python のバージョンについては、次を参照してください。 [in-database analytics Python 開発者向けの](../tutorials/sqldev-in-database-python-for-sql-developers.md)します。

## <a name="overview"></a>概要

Machine learning ソリューションを構築するプロセスをいくつかのフェーズの間で複数のツール、および領域の専門家の調整を伴う複雑なものを示します。

+ 取得して、データのクリーニング
+ データの探索とモデリングの便利な機能の作成
+ トレーニング セットと、モデルの調整
+ 運用環境へのデプロイ

実際のコードの開発とテストに専用の開発環境を使用してを実行が最適です。 ただし、スクリプトを完全にテストした後に簡単にデプロイできますを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い慣れた環境でのストアド プロシージャ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。

R に新しい SQL プログラマでは、R 開発者が SQL では、このマルチパート チュートリアルに新しいされるかは、R と SQL Server の in-database 分析を実施するための一般的なワークフローを紹介します。 

- [レッスン 1: の探索し、ストアド プロシージャで R 関数を呼び出すことによってデータのシェイプと分布を視覚化](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [レッスン 2: T-SQL 関数で R を使用してデータ機能を作成します。](sqldev-create-data-features-using-t-sql.md)
  
- [レッスン 3: トレーニングし、関数およびストアド プロシージャを使用して R モデルの保存](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [レッスン 4: ストアド プロシージャで R モデルを使用して潜在的な結果を予測します。](../tutorials/sqldev-operationalize-the-model.md)

モデルをデータベースに保存した後から予測モデルを呼び出す[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを使用します。

## <a name="prerequisites"></a>前提条件

すべてのタスクを行うことができますを使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。

このチュートリアルは、データベースとテーブルを作成、データをインポートする SQL クエリの記述などの基本的なデータベース操作に関する知識を前提とします。 R. を把握することを想定しませんそのため、すべての R コードが提供されます。 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation)または[有効になっている R を使用した SQL Server 2017 Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R ライブラリ](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)

+ [権限](../security/user-permission.md)

+ [NYC タクシー デモ データベース](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [NYC タクシーのデータベースを設定します。](demo-data-nyctaxi-in-sql.md)