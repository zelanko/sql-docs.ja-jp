---
title: Analysis Services Adventure Works チュートリアル (1400) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28aa401eb037fecadca17ededf041ab82a4bc498
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042450"
---
# <a name="tabular-modeling-1400-compatibility-level"></a>テーブル モデリング (1400 互換性レベル)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このチュートリアルを作成して、表形式モデルをデプロイする方法のレッスンでは、 [1400 互換性レベル](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)します。 Analysis Services および表形式モデルに慣れていない場合は、作成して、Visual Studio を使用して基本的な表形式モデルをデプロイする方法を学習する最も簡単な方法ではこのチュートリアルを完了します。 前提条件を作成したらインプレース、2 ~ 3 時間かかるにする必要があります。  
  
## <a name="what-you-learn"></a>学習内容   
  
-   新しいテーブル モデル プロジェクトを作成する方法、 **1400 互換性レベル**Visual Studio と SSDT でします。
  
-   テーブル モデル プロジェクト ワークスペース データベースにリレーショナル データベースからデータをインポートする方法。  
  
-   モデルに含まれるテーブル間のリレーションシップを作成および管理する方法。  
  
-   計算列、メジャー、およびユーザーの重要なビジネス メトリックを分析するのに役立つ主要業績評価指標を作成する方法。  
  
-   パースペクティブと階層ヘルプのユーザーはビジネスとアプリケーション固有のビュー ポイントを提供することで、モデル データを簡単に参照を作成および管理する方法。  
  
-   パーティションを作成してテーブル データをより小さな論理部分に分割し、他のパーティションと分離して処理できるようにする方法。  
  
-   ユーザー メンバーのロールを作成して、モデル オブジェクトとデータを保護する方法。  
  
-   表形式モデルをデプロイする方法、 **Azure Analysis Services**サーバーまたは**SQL Server 2017 Analysis Services** SSDT を使用してサーバー。  
  
## <a name="prerequisites"></a>前提条件  

このチュートリアルでは、次の操作をする必要があります。  
  
-   Azure Analysis Services サーバーまたは表形式モードでの SQL Server 2017 Analysis Services サーバー。 無料のサインアップ[Azure Analysis Services の試用版](https://azure.microsoft.com/services/analysis-services/)と[サーバーを作成する](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server)を無料でダウンロードまたは[SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)します。

-   [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal)で、**サンプル AdventureWorksDW データベース**、またはでオンプレミス SQL Server Data Warehouse、 [AdventureWorksDW サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)します。 オンプレミス SQL Server データ ウェアハウスに、AdventureWorksDW データベースをインストールするときに、サーバー バージョンに対応するサンプル データベースのバージョンを使用します。 

    **重要:** サンプル データベース、オンプレミス SQL Server データ ウェアハウスをインストールし、Azure Analysis Services サーバーにモデルを配置する場合、 [、オンプレミス データ ゲートウェイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)が必要です。

-   最新バージョンの[SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx)します。 または、Visual Studio 2017 既にある場合は、ダウンロードしてインストール[Microsoft Analysis Services プロジェクト](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)(VSIX) パッケージ。 このチュートリアルでは、SSDT と Visual Studio への参照は同義です。 

-   最新バージョンの[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)します。    

-   などのクライアント アプリケーション[Power BI Desktop](https://powerbi.microsoft.com/desktop/)または Excel。 

## <a name="scenario"></a>シナリオ  

このチュートリアルは、Adventure Works Cycles という架空の会社に基づいています。 Adventure Works が生成され、自転車、部品、および北アメリカ、ヨーロッパ、およびアジアに流通市場のアクセサリを配布するための大規模な多国籍製造会社です。 会社では、500 を採用しています。 さらに、Adventure Works では、その市場拠点の複数の地域販売チームを採用しています。 プロジェクトでは、売上およびマーケティング AdventureWorksDW データベース内のインターネット販売データを分析するための表形式モデルを作成します。  
  
このチュートリアルを完了するには、さまざまなレッスンを完了する必要があります。 各レッスンでは、タスクがあります。 順序で各タスクの完了は、レッスンを完了する必要があります。 特定のレッスンである可能性があります、似たような結果をいくつかのタスクが、各タスクを完了する方法は若干異なります。 このメソッドは、タスクを完了して、前のレッスンやタスクで学習したスキルを活用してチャレンジを 1 つ以上の方法があることを示しています。  
  
各レッスンの目的を SSDT に含まれる機能の多くを使用して基本的な表形式モデルを作成することを紹介します。 各レッスンは前のレッスンに基づいているので、順序どおりに完了する必要があります。
  
このチュートリアルでは、Azure ポータルで、SSMS、またはモデル データを参照するクライアント アプリケーションを使用して、サーバーやデータベースの管理サーバーの管理についてのレッスンは提供されません。 


## <a name="lessons"></a>レッスン  

このチュートリアルには次のレッスンが含まれています。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[1 - 新しい表形式モデル プロジェクトを作成します。](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)|10 分|  
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

これらのレッスンは、チュートリアルを完了する必要はありませんが、向上について高度なテーブル モデル作成機能に役に立ちます。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[詳細行](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 分|
|[動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 分|
|[不規則階層](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 分| 

  
## <a name="next-steps"></a>次のステップ  

最初に、次を参照してください。[レッスン 1: 新しい表形式モデル プロジェクトを作成する](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)します。  
  
  
  

