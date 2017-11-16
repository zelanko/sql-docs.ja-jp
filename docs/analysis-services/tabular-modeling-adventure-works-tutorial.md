---
title: "テーブル モデリング (Adventure Works チュートリアル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
keywords:
- Analysis Services
- "テーブル モデル"
- "チュートリアル"
- SSAS
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 811b5df37a88fa7a03eec2b9bc05acb87ec67bcc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="tabular-modeling-adventure-works-tutorial"></a>テーブル モデリング (Adventure Works チュートリアル)
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このチュートリアルでの Analysis Services 表形式モデルを作成する方法のレッスンでは、[互換性レベル 1200](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)を使用して[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)、Analysis Services にモデルを配置およびサーバーをオンプレミスまたは Azure です。  
 
SQL Server 2017 または Azure Analysis Services を使用して、1400 互換性のレベルでモデルを作成、使用する場合、 [Azure Analysis Services - Adventure Works チュートリアル](https://review.docs.microsoft.com/azure/analysis-services/tutorials/aas-adventure-works-tutorial?branch=master)です。 この更新されたバージョンは、新しい、最新のデータの取得機能を使用して接続し、ソース データをインポートし、パーティションを構成する、M 言語を使用します。
 
  
## <a name="what-youll-learn"></a>学習する内容   
  
-   SSDT で新しいテーブル モデル プロジェクトを作成する方法。
  
-   SQLServer リレーショナル データベースからテーブル モデル プロジェクトにデータをインポートする方法。  
  
-   モデルに含まれるテーブル間のリレーションシップを作成および管理する方法。  
  
-   モデル データの分析を支援するための、計算、計測、および主要業績評価指標を作成および管理する方法。  
  
-   ビジネスおよびアプリケーション固有のビューポイントを提供して、ユーザーがモデル データをより簡単に参照できるようにするためのパースペクティブや階層を作成および管理する方法。  
  
-   パーティションを作成してテーブル データをより小さな論理部分に分割し、他のパーティションと分離して処理できるようにする方法。  
  
-   ユーザー メンバーのロールを作成して、モデル オブジェクトとデータを保護する方法。  
  
-   Analysis Services サーバーにオンプレミスまたは Azure では、表形式モデルを展開する方法です。  
  
## <a name="scenario"></a>Scenario  
このチュートリアルは、Adventure Works Cycles、架空の会社に基づいています。 Adventure Works は、生成し、金属製自転車を北アメリカ、ヨーロッパ、およびアジアの市場を配布する、大規模な多国籍製造会社です。 ワシントン州ボセルに本社では、会社には、500 の作業者が採用しています。 さらに、Adventure Works では、市場には、全体で複数の地域販売チームが採用しています。  
  
あなたは、販売チーム、マーケティング チーム、および上級管理職のデータ分析ニーズにより高度に対応するべく、AdventureWorksDW サンプル データベース内のインターネット販売データを分析するためのテーブル モデルを作成します。  
  
このチュートリアル (および Adventure Works Internet Sales テーブル モデル) を完了するには、多数のレッスンを完了する必要があります。 各レッスンに多数の実習が含まれています。レッスンを完了するには、各実習を順序どおりに完了する必要があります。 特定のレッスンである可能性があります、同様の結果を実現するいくつかのタスクが、各タスクを完了する方法は若干異なります。 これは、特定のタスクを完了して、前のタスクで学習したスキルが身に複数の 1 つの方法が多くの場合、ことを示します。  
  
各レッスンの目的は、SSDT に含まれる機能の多くを使用して、インメモリ モードで実行されている基本的な表形式モデルの作成を指示します。 各レッスンは前のレッスンに基づいているので、順序どおりに完了する必要があります。 すべてのレッスンを完了したら、作成し、Adventure Works Internet Sales サンプル テーブル モデルの Analysis Services サーバーを展開したされます。  
  
このチュートリアルでは、配置したテーブル モデル データベースを SQL Server Management Studio で管理する方法や、レポート クライアント アプリケーションを使用して配置済みのモデルに接続し、モデル データを参照する方法については説明しません。  
  
## <a name="prerequisites"></a>前提条件  
このチュートリアルを完了するために次の前提条件が必要です。  
  
-   最新バージョンの [!含める[ssBIDevStudioFull](../ssdt/download-sql-server-data-tools-ssdt.md)です。

-   SQL Server Management Studio の最新バージョン。 [最新バージョンを入手](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。 
  
-   などのクライアント アプリケーション[Power BI Desktop](https://powerbi.microsoft.com/desktop/)または[!INCLUDE[msCoName](../includes/msconame-md.md)]Excel です。    
  
-   Adventure Works DW 2014 サンプル データベースと SQL Server インスタンス。 このサンプル データベースには、このチュートリアルを完了するのに必要なデータが含まれています。 [最新バージョンを入手](http://go.microsoft.com/fwlink/?LinkID=335807)です。  
  

-   Azure Analysis Services または SQL Server 2016 またはそれ以降の Analysis Services インスタンスにモデルを配置します。 [Azure Analysis Services の無料試用版にサインアップする](https://azure.microsoft.com/services/analysis-services/)です。
  
## <a name="lessons"></a>レッスン  
このチュートリアルには次のレッスンが含まれています。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[レッスン 1: 新しいテーブル モデル プロジェクトの作成](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)|10 分|  
|[レッスン 2: データの追加](../analysis-services/lesson-2-add-data.md)|20 分|  
|[レッスン 3: 日付テーブルとしてマーク](../analysis-services/lesson-3-mark-as-date-table.md)|3 分|  
|[レッスン 4: リレーションシップを作成します。](../analysis-services/lesson-4-create-relationships.md)|10 分|  
|[レッスン 5: 計算列を作成します。](../analysis-services/lesson-5-create-calculated-columns.md)|15 分|
|[レッスン 6: メジャーを作成します。](../analysis-services/lesson-6-create-measures.md)|30 分|  
|[レッスン 7: 主要業績評価指標の作成](../analysis-services/lesson-7-create-key-performance-indicators.md)|15 分|  
|[レッスン 8: パースペクティブを作成します。](../analysis-services/lesson-8-create-perspectives.md)|5 分|  
|[レッスン 9: 階層を作成します。](../analysis-services/lesson-9-create-hierarchies.md)|20 分|  
|[レッスン 10: パーティションを作成します。](../analysis-services/lesson-10-create-partitions.md)|15 分|  
|[レッスン 11: ロールを作成します。](../analysis-services/lesson-11-create-roles.md)|15 分|  
|[レッスン 12: Excel での分析](../analysis-services/lesson-12-analyze-in-excel.md)|20 分| 
|[レッスン 13: 配置](../analysis-services/lesson-13-deploy.md)|5 分|  
  
## <a name="supplemental-lessons"></a>補足のレッスン  
このチュートリアルには、 [補足レッスン](http://msdn.microsoft.com/library/2018456f-b4a6-496c-89fb-043c62d8b82e)も含まれています。 このセクションのトピックはチュートリアルを完了するのに必須ではありませんが、高度なテーブル モデル作成機能をより深く理解するために役立ちます。  
  
|レッスン|推定所要時間|  
|----------|------------------------------|  
|[行フィルターを使用した動的なセキュリティの実装](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)|30 分|  

  
## <a name="next-step"></a>次の手順  
チュートリアルを開始するには、 [「レッスン 1: 新しいテーブル モデル プロジェクトの作成」](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)に進みます。  
  
  
  


