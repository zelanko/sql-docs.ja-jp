---
title: R と SQL Server Machine Learning を使用してデータベース内分析のチュートリアル |Microsoft Docs
description: SQL Server に R を埋め込む方法を示すチュートリアルはストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7adfda1c31bd1fc32dc4149a568cfdd2149ab0b3
ms.sourcegitcommit: 9d0ff4f3e40db48fc01788684d34719065d159b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44724306"
---
# <a name="tutorial-learn-in-database-analytics-using-r-in-sql-server"></a>チュートリアル: SQL Server で R を使用した in-database 分析を説明します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL プログラマ向けのこのチュートリアルでは、R 言語をビルドして machine learning のストアド プロシージャで R コードをラップすることによってソリューションのデプロイを使用して実際に体験を行えます。

このチュートリアルでは、ニューヨーク市のタクシーの乗車回数に基づいて、よく知られているパブリック データセットを使用します。 サンプル コードをすばやく実行するためには、データの代表的な 1% のサンプリングを作成しました。 このデータがかどうか、特定の乗車か、ヒントを取得するのに日の時刻、距離、乗車場所などの列に基づいて予測する二項分類モデルの構築に使用します。

> [!NOTE]
> 
> 同じソリューションは、Python で使用できます。 SQL Server 2017 が必要です。 参照してください[in-database analytics Python 開発者向け](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>概要

通常、エンド ツー エンド ソリューションを構築するプロセスは、取得とクリーニング、データ、データの探索と特徴エンジニア リング、モデルのトレーニングおよびチューニング、および最後に実稼働環境でモデルの配置で構成されます。 実際のコードの開発とテストに専用の開発環境を使用してを実行が最適です。 R、RStudio を意味する可能性がありますまたは[!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]します。

ただし、ソリューションの作成後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の使い慣れた環境で [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを使用して、ソリューションを [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に容易に展開することができます。

- [レッスン 1: NYC タクシーのデモ データの設定します。](../tutorials/sqldev-download-the-sample-data.md)

- [レッスン 2: の探索し、ストアド プロシージャで R 関数を呼び出すことによってデータのシェイプと分布を視覚化](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [レッスン 3: T-SQL 関数で R を使用してデータ機能を作成します。](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [レッスン 4: トレーニングし、関数およびストアド プロシージャを使用して R モデルの保存](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [レッスン 5: 運用化するためのストアド プロシージャにラップ R コード](../tutorials/sqldev-operationalize-the-model.md)します。 
  データベースにモデルが保存されたら、ストアド プロシージャを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] から予測モデルを呼び出します。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルは、データベースとテーブルを作成、データをインポートする SQL クエリの記述などの基本的なデータベース操作に関する知識を前提とします。 R. を把握することを想定しませんそのため、すべての R コードが提供されます。 スキルを持つ SQL プログラマが提供されている PowerShell スクリプトでは、github のサンプル データを使用し、[!INCLUDE[tsql](../../includes/tsql-md.md)]で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]この例を完了します。 

前に、チュートリアルを開始するには。

- インスタンスの構成があることを確認[SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation)または[有効になっている R を使用した SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md#verify-installation)します。 さらに、 [R ライブラリがあることを確認します。](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)します。
- このチュートリアルで使用するログインはデータベースを作成する権限が必要と、データをアップロードするその他のオブジェクトは、データを選択し、ストアド プロシージャを実行します。

> [!NOTE]
> 実行することをお勧めします。**いない**使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]R コードを記述またはテストします。 ストアド プロシージャに埋め込むことがコードに問題がある場合は、ストアド プロシージャから返される情報は、エラーの原因を解明するすれば十分ではありません。
> 
> デバッグをお勧めなどのツールを使用する[!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]、RStudio またはします。 このチュートリアルで示す R スクリプトは、従来の R ツールを使用して既に開発およびデバッグされています。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [レッスン 1: サンプル データをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)