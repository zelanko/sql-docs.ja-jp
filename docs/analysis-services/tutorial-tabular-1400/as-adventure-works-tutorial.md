---
title: Analysis Services の Adventure Works チュートリアル (1400) |Microsoft ドキュメント
description: Analysis Services の Adventure Works チュートリアルが導入されています
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 10ceeb85ee97162fb753e84d997d105edb3cf9a4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="tabular-modeling-1400-compatibility-level"></a>テーブル モデリング (1400 互換性レベル)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このチュートリアルを作成およびで表形式モデルを展開する方法のレッスンでは、 [1400 互換性レベル](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)です。 、Analysis Services を表形式モデルの作成経験がない場合は、を作成し、Visual Studio を使用して基本的な表形式モデルを展開する方法を学習する最も簡単な方法ではこのチュートリアルを完了します。 前提条件を作成したら、インプレース必要がありますは 2 ~ 3 時間かかるを完了します。  
  
## <a name="what-you-learn"></a>学習内容   
  
-   新しいテーブル モデル プロジェクトを作成する方法、 **1400 互換性レベル**SSDT では Visual Studio でします。
  
-   表形式モデル プロジェクト ワークスペース データベースにリレーショナル データベースからデータをインポートする方法です。  
  
-   モデルに含まれるテーブル間のリレーションシップを作成および管理する方法。  
  
-   計算列、メジャー、および重要なビジネス メトリックを分析に役立つ主要業績評価指標を作成する方法。  
  
-   パースペクティブとビジネスとアプリケーション固有のビュー ポイントを提供することによって、モデル データを簡単に参照複数ユーザーを支援する階層を作成および管理方法です。  
  
-   パーティションを作成してテーブル データをより小さな論理部分に分割し、他のパーティションと分離して処理できるようにする方法。  
  
-   ユーザー メンバーのロールを作成して、モデル オブジェクトとデータを保護する方法。  
  
-   表形式モデルを展開する方法、 **Azure Analysis Services**サーバーまたは**SQL Server 2017 Analysis Services** SSDT を使用してサーバー。  
  
## <a name="prerequisites"></a>前提条件  

このチュートリアルを完了する必要があります。  
  
-   Azure Analysis Services サーバーまたは表形式モードでの SQL Server 2017 Analysis Services サーバー。 無料のサインアップ[Azure Analysis Services の評価版](https://azure.microsoft.com/services/analysis-services/)と[サーバーを作成する](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server)または無料ダウンロード[SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)です。

-   [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal)で、**サンプル AdventureWorksDW データベース**、またはと内部設置型 SQL Server データ ウェアハウス、 [AdventureWorksDW サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)です。 AdventureWorksDW データベースを内部設置型 SQL Server データ ウェアハウスをインストールする場合は、サーバーのバージョンと対応するサンプル データベースのバージョンを使用します。 

    **重要:** 、内部設置型 SQL Server データ ウェアハウスにサンプル データベースをインストールし、Azure Analysis Services サーバーにモデルを配置する場合、[オンプレミス データ ゲートウェイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)が必要です。

-   最新バージョン[SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx)です。 または、Visual Studio 2017 がある場合は、ダウンロードしてインストール[Microsoft Analysis Services プロジェクト](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)(VSIX) パッケージ。 このチュートリアルでは、SSDT と Visual Studio への参照は同義です。 

-   最新バージョン[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。    

-   などのクライアント アプリケーション[Power BI Desktop](https://powerbi.microsoft.com/desktop/)または Excel です。 

## <a name="scenario"></a>Scenario  

このチュートリアルは、Adventure Works Cycles、架空の会社に基づいています。 Adventure Works は、生成し、自転車、部品、および北米、ヨーロッパ、およびアジアの市場で商用アクセサリを配布するための大規模な多国籍製造会社です。 会社には、500 の作業者が採用しています。 さらに、Adventure Works では、市場には、全体で複数の地域販売チームが採用しています。 プロジェクトでは、売上およびマーケティング ユーザーが、AdventureWorksDW データベース内のインターネット販売データを分析するためのテーブル モデルを作成します。  
  
このチュートリアルを完了するには、さまざまなレッスンを完了する必要があります。 各レッスンでは、タスクがあります。 順序で各タスクの完了は、レッスンを完了する必要があります。 特定のレッスンである可能性があります、同様の結果を実現するいくつかのタスクが、各タスクを完了する方法は若干異なります。 このメソッドは、多くの場合は、複数の方法でタスクを完了しを使用して、前のレッスンとタスクで学習したスキルが身を示します。  
  
レッスンの目的は、SSDT に含まれる機能の多くを使用して基本的な表形式モデルの作成を指示します。 各レッスンは前のレッスンに基づいているので、順序どおりに完了する必要があります。
  
このチュートリアルでは、Azure ポータルで、SSMS、またはモデル データを参照するクライアント アプリケーションを使用して、サーバーまたはデータベースを管理するサーバーの管理について」のレッスンは提供されません。 


## <a name="lessons"></a>レッスン  

このチュートリアルには次のレッスンが含まれています。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[1 - 新しいテーブル モデル プロジェクトを作成します。](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)|10 分|  
|[2 - データの取得](../tutorial-tabular-1400/as-lesson-2-get-data.md)|10 分|  
|[3 - 日付テーブルとしてマーク](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)|3 分|  
|[4 - リレーションシップの作成](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)|10 分|  
|[5 - 計算列の作成](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)|15 分|
|[6 - メジャーの作成](../tutorial-tabular-1400/as-lesson-6-create-measures.md)|30 分|  
|[7 - 主要業績評価指標 (KPI) を作成します。](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)|15 分|  
|[8 - パースペクティブの作成](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)|5 分|  
|[9 - 階層の作成](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)|20 分|  
|[10 - パーティションの作成](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)|15 分|  
|[11 - ロールの作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)|15 分|  
|[12 - Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)|5 分| 
|[13 - 配置](../tutorial-tabular-1400/as-lesson-13-deploy.md)|5 分|  
  
## <a name="supplemental-lessons"></a>補足のレッスン  

これらのレッスンは、チュートリアルを完了する必要はありませんより優れたについて高度なテーブル モデル作成機能に役に立ちます。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[詳細行](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 分|
|[動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 分|
|[不規則階層](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 分| 

  
## <a name="next-steps"></a>次の手順  

最初に、次を参照してください。[レッスン 1: 新しいテーブル モデル プロジェクトを作成する](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)です。  
  
  
  

