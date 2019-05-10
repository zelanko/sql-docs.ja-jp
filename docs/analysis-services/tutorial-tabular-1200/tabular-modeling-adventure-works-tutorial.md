---
title: Analysis Services テーブル モデリング (1200 互換性レベル) |Microsoft Docs
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7ae9dd208d151dc3b8fb8117ba6e672ada2aecdd
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403354"
---
# <a name="tabular-modeling-1200-compatibility-level"></a>テーブル モデリング (1200 互換性レベル)
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

このチュートリアルでは、Analysis Services 表形式モデルを作成する方法のレッスンを提供する、[互換性レベル 1200](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)を使用して[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)、Analysis services モデルをデプロイし、サーバーをオンプレミスまたは Azure です。  
 
SQL Server 2017 または Azure Analysis Services を使用しているし、1400 の互換性のレベルで、モデルを作成、使用する場合、[テーブル モデリング (1400 互換性レベル)](../tutorial-tabular-1400/as-adventure-works-tutorial.md)します。 この更新されたバージョンは、最新のデータの取得機能を使用して接続し、ソース データをインポート、M 言語を使用して、パーティションを構成する、およびその他の補足のレッスンが含まれています。

> [!IMPORTANT]
> サーバーでサポートされている最新の互換性レベルで、表形式モデルを作成する必要があります。 以降の互換性レベル モデルでは、パフォーマンスの向上、追加の機能を提供しよりシームレスに将来の互換性レベルにアップグレードされます。
 
  
## <a name="what-you-learn"></a>学習内容   
  
-   SSDT で新しいテーブル モデル プロジェクトを作成する方法。
  
-   SQLServer リレーショナル データベースからテーブル モデル プロジェクトにデータをインポートする方法。  
  
-   モデルに含まれるテーブル間のリレーションシップを作成および管理する方法。  
  
-   モデル データの分析を支援するための、計算、計測、および主要業績評価指標を作成および管理する方法。  
  
-   パースペクティブと階層ヘルプのユーザーはビジネスとアプリケーション固有のビュー ポイントを提供することで、モデル データを簡単に参照を作成および管理する方法。  
  
-   他のパーティションから独立したテーブルのデータをより小さな論理部分を処理できるに分割するパーティションを作成する方法。  
  
-   ユーザー メンバーのロールを作成して、モデル オブジェクトとデータを保護する方法。  
  
-   Analysis Services サーバー、オンプレミスまたは Azure では、表形式モデルをデプロイする方法。  
  
## <a name="scenario"></a>シナリオ  
このチュートリアルは、Adventure Works Cycles という架空の会社に基づいています。 Adventure Works は、自転車、部品、および北アメリカ、ヨーロッパ、およびアジアに流通市場のアクセサリを生成するための大規模な多国籍製造会社です。 会社では、ワシントン州ボセルに本社 500 を採用しています。 さらに、Adventure Works では、その市場拠点の複数の地域販売チームを採用しています。  
  
あなたは、販売チーム、マーケティング チーム、および上級管理職のデータ分析ニーズにより高度に対応するべく、AdventureWorksDW サンプル データベース内のインターネット販売データを分析するためのテーブル モデルを作成します。  
  
このチュートリアル (および Adventure Works Internet Sales テーブル モデル) を完了するには、多数のレッスンを完了する必要があります。 各レッスンでは、さまざまなタスクです。順序で各タスクの完了は、レッスンを完了する必要があります。 特定のレッスンである可能性があります、似たような結果をいくつかのタスクが、各タスクを完了する方法は若干異なります。 これは、特定のタスクを完了して、前のタスクで学習したスキルを活用してチャレンジを 1 つ以上の方法が多くの場合、ことを説明します。  
  
各レッスンの目的を SSDT に含まれる機能の多くを使用して、インメモリ モードで実行されている基本的な表形式モデルを作成することを紹介します。 各レッスンは前のレッスンに基づいているので、順序どおりに完了する必要があります。 すべてのレッスンを完了すると、作成し、Analysis Services サーバーには、Adventure Works Internet Sales サンプル テーブル モデルをデプロイしました。  
  
このチュートリアルでは、配置したテーブル モデル データベースを SQL Server Management Studio で管理する方法や、レポート クライアント アプリケーションを使用して配置済みのモデルに接続し、モデル データを参照する方法については説明しません。  
  
## <a name="prerequisites"></a>前提条件  
このチュートリアルを完了するのには、次の前提条件が必要です。  
  
-   最新バージョンの[SSDT](../../ssdt/download-sql-server-data-tools-ssdt.md)します。

-   SQL Server Management Studio の最新バージョン。 [最新バージョンの取得](../../ssms/download-sql-server-management-studio-ssms.md)します。 
  
-   などのクライアント アプリケーション[Power BI Desktop](https://powerbi.microsoft.com/desktop/)または Excel。    
  
-   Adventure Works DW サンプル データベースで SQL Server インスタンス。 このサンプル データベースには、このチュートリアルを完了するのに必要なデータが含まれています。 [最新バージョンの取得](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)します。  
  

-   Azure Analysis Services または SQL Server 2016 または以降の Analysis Services インスタンスにモデルをデプロイします。 [無料の Azure Analysis Services 試用版にサインアップ](https://azure.microsoft.com/services/analysis-services/)します。
  
## <a name="lessons"></a>レッスン  
このチュートリアルには次のレッスンが含まれています。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[レッスン 1:新しい表形式モデル プロジェクトを作成します。](lesson-1-create-a-new-tabular-model-project.md)|10 分|  
|[レッスン 2:データを追加します。](lesson-2-add-data.md)|20 分|  
|[レッスン 3:日付テーブルとしてマークします。](lesson-3-mark-as-date-table.md)|3 分|  
|[レッスン 4:リレーションシップを作成します。](lesson-4-create-relationships.md)|10 分|  
|[レッスン 5: 計算列を作成します。](lesson-5-create-calculated-columns.md)|15 分|
|[レッスン 6:メジャーを作成します。](lesson-6-create-measures.md)|30 分|  
|[レッスン 7: 主要業績評価指標を作成します。](lesson-7-create-key-performance-indicators.md)|15 分|  
|[レッスン 8: パースペクティブを作成します。](lesson-8-create-perspectives.md)|5 分|  
|[レッスン 9:階層を作成します。](lesson-9-create-hierarchies.md)|20 分|  
|[レッスン 10:パーティションを作成します。](lesson-10-create-partitions.md)|15 分|  
|[レッスン 11:ロールを作成します。](lesson-11-create-roles.md)|15 分|  
|[レッスン 12:Excel で分析します。](lesson-12-analyze-in-excel.md)|20 分| 
|[レッスン 13:展開](lesson-13-deploy.md)|5 分|  
  
## <a name="supplemental-lessons"></a>補足のレッスン  
このチュートリアルでは、補足のレッスンも含まれています。 このセクションのトピックはチュートリアルを完了するのに必須ではありませんが、高度なテーブル モデル作成機能をより深く理解するために役立ちます。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[行フィルターを使用した動的なセキュリティの実装](supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)|30 分|  
|[Power View レポートのレポート プロパティの構成](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)|30 分| 

  
## <a name="next-step"></a>次の手順  
チュートリアルを開始するには、最初のレッスンに進んでください。[レッスン 1:新しいテーブル モデル プロジェクト作成](lesson-1-create-a-new-tabular-model-project.md)です。  
  
  
  

