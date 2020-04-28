---
title: テーブルモデリング (Adventure Works チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27ac17469a96213bdd39cbf2bee5a343d117e6f0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487631"
---
# <a name="tabular-modeling-adventure-works-tutorial"></a>テーブル モデリング (Adventure Works チュートリアル)
  このチュートリアルでは、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] を使用して、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Analysis Services テーブル モデルを作成する方法を学習します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは次のことを学習します。  
  
-   [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で新しいテーブル モデル プロジェクトを作成する方法。  
  
-   SQLServer リレーショナル データベースからテーブル モデル プロジェクトにデータをインポートする方法。  
  
-   モデルに含まれるテーブル間のリレーションシップを作成および管理する方法。  
  
-   モデル データの分析を支援するための、計算、計測、および主要業績評価指標を作成および管理する方法。  
  
-   ビジネスおよびアプリケーション固有のビューポイントを提供して、ユーザーがモデル データをより簡単に参照できるようにするためのパースペクティブや階層を作成および管理する方法。  
  
-   パーティションを作成してテーブル データをより小さな論理部分に分割し、他のパーティションと分離して処理できるようにする方法。  
  
-   ユーザー メンバーのロールを作成して、モデル オブジェクトとデータを保護する方法。  
  
-   テーブル モデルを、サンドボックスや、テーブル モードで実行されている Analysis Services の実稼働インスタンスに配置する方法。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 このチュートリアルには、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]という架空の会社が登場します。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、特殊合金自転車を北米、ヨーロッパ、およびアジアの市場に供給する大規模な多国籍製造会社です。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] はワシントン州のボセルに本社を置き、500 名の従業員を抱えています。 さらに、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の各市場には、その地域を担当する販売チームがいます。  
  
 あなたは、販売チーム、マーケティング チーム、および上級管理職のデータ分析ニーズにより高度に対応するべく、AdventureWorksDW サンプル データベース内のインターネット販売データを分析するためのテーブル モデルを作成します。  
  
 このチュートリアル (および Adventure Works Internet Sales テーブル モデル) を完了するには、多数のレッスンを完了する必要があります。 1 つのレッスンはいくつかのタスクから構成され､レッスンを終えるには､各タスクを順に終了する必要があります｡ 特定のレッスン内には、同様の結果を達成する実習もいくつか存在しますが、どのように完了するかは実習ごとに少しずつ違います。 これは、同じ実習を完了するのにも複数の方法が存在する場合がよくあるためです。また、前の実習で学習したスキルが身についているかどうかを確認するためでもあります。  
  
 各レッスンの目的は、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]に含まれる多数の機能を使用して、インメモリ モードで実行される基本的なテーブル モデルを作成できるようになることです。 各レッスンは前のレッスンに基づいているので、順序どおりに完了する必要があります。 すべてのレッスンを完了すると、Analysis Services サーバー上に Adventure Works Internet Sales サンプル テーブル モデルが作成され、配置されます。  
  
> [!NOTE]  
>  このチュートリアルでは、配置したテーブル モデル データベースを SQL Server Management Studio で管理する方法や、レポート クライアント アプリケーションを使用して配置済みのモデルに接続し、モデル データを参照する方法については説明しません。  
  
## <a name="prerequisites"></a>前提条件  
 このチュートリアルを完了するには、以下が事前にインストールされている必要があります。  
  
-   テーブル モードで実行されている [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services インスタンス。  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   AdventureWorksDW サンプル データベース このサンプル データベースには、このチュートリアルを完了するのに必要なデータが含まれています。 サンプルデータベースをダウンロードするには[https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks)、「」を参照してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 2003 以降 (レッスン 11 で "Excel で分析" 機能を使用するため)  
  
## <a name="lessons"></a>レッスン  
 このチュートリアルには次のレッスンが含まれています。  
  
|レッスン|推定所要時間|  
|------------|--------------------------------|  
|[レッスン 1:新しいテーブル モデル プロジェクトの作成](lesson-1-create-a-new-tabular-model-project.md)|10 分|  
|[レッスン 2: データを追加する](lesson-2-add-data.md)|20 分|  
|[レッスン 3:列名の変更](rename-columns.md)|20 分|  
|[レッスン 4:日付テーブルとしてマーク](lesson-3-mark-as-date-table.md)|3 分|  
|[レッスン 5: [リレーションシップの作成]](lesson-4-create-relationships.md)|10 分|  
|[レッスン 6: 計算列の作成](lesson-5-create-calculated-columns.md)|約 15 分|  
|[レッスン 7: メジャーを作成する](lesson-6-create-measures.md)|30 分|  
|[レッスン 8: 主要業績評価指標を作成する](lesson-7-create-key-performance-indicators.md)|約 15 分|  
|[レッスン 9: パースペクティブを作成する](lesson-8-create-perspectives.md)|5 分|  
|[レッスン 10: 階層を作成する](lesson-9-create-hierarchies.md)|20 分|  
|[レッスン 11:パーティションの作成](lesson-10-create-partitions.md)|約 15 分|  
|[レッスン 12:ロールの作成](lesson-11-create-roles.md)|約 15 分|  
|[レッスン 13:[Excel で分析]](lesson-12-analyze-in-excel.md)|20 分|  
|[レッスン 14:配置](lesson-13-deploy.md)|5 分|  
  
## <a name="supplemental-lessons"></a>補足のレッスン  
 このチュートリアルには、 [補足レッスン](../tutorials/supplemental-lessons.md)も含まれています。 このセクションのトピックはチュートリアルを完了するのに必須ではありませんが、高度なテーブル モデル作成機能をより深く理解するために役立ちます。  
  
 このチュートリアルには次の補足レッスンが含まれています。  
  
|レッスン|推定所要時間|  
|------------|--------------------------------|  
|[行フィルターを使用した動的なセキュリティの実装](../tutorials/implement-dynamic-security-by-using-row-filters.md)|30 分|  
|[Power View レポートのレポートプロパティの構成](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)Power View レポートのレポートプロパティの構成|30 分|  
  
## <a name="next-step"></a>次の手順  
 チュートリアルを開始するには、 [「レッスン 1: 新しいテーブル モデル プロジェクトの作成」](lesson-1-create-a-new-tabular-model-project.md)に進みます。  
  
  
