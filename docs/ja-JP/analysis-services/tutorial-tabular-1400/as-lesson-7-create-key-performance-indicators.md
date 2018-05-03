---
title: 'Analysis Services のチュートリアル レッスン 7: 主要業績評価指標の作成 |Microsoft ドキュメント'
description: Analysis Services tutorial プロジェクトで主要業績評価指標を作成する方法について説明します。
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
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: b5baa301f8e9162205b4995e557f3178107a0fcc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-key-performance-indicators"></a>主要業績評価指標の作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、主要業績評価指標 (Kpi) を作成します。 Kpi がによって定義された値のパフォーマンス測定に使用される、*ベース*メジャー、に対して、*ターゲット*も、メジャーまたは絶対値によって定義されている値。 KPI を使用すると、ビジネス プロフェッショナルがレポート クライアント アプリケーションを通じて、ビジネスの成功度や傾向をすばやく簡単に把握できるようになります。 詳細については、次を参照してください[Kpi。](../tabular-models/kpis-ssas-tabular.md)
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 6: メジャーを作成する](../tutorial-tabular-1400/as-lesson-6-create-measures.md)です。   
  
## <a name="create-key-performance-indicators"></a>主要業績評価指標の作成  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>InternetCurrentQuarterSalesPerformance KPI を作成するには  
  
1.  モデル デザイナーで、をクリックして、 **FactInternetSales**テーブル。  
  
2.  メジャー グリッドで、空のセルをクリックします。  
  
3.  テーブルの上にある数式バーに、以下の数式を入力します。 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=DIVIDE([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    このメジャーは KPI のベース メジャーとして機能します。  
  
4.  メジャー グリッドで右クリック**InternetCurrentQuarterSalesPerformance** > **Create KPI**です。   
  
5.  主要業績評価指標 (KPI) ダイアログ ボックスで**ターゲット**選択**絶対値**、し、入力**1.1**です。  
  
7.  左 (下) のスライダー フィールドに「 **1**」と入力し、右 (上) のスライダー フィールドに「 **1.07**」と入力します。  
  
8.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択します。
  
    ![as-lesson7-kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > 展開可能なことを確認**説明**使用可能なアイコン スタイルの下のラベル。 クライアント アプリケーションでそれらを識別しやすくするのにには、各種の KPI 要素に対する説明を使用します。  
  
9. **[OK]** をクリックして KPI の作成を完了します。  
  
    メジャー グリッドで、アイコンが横に表示、 **InternetCurrentQuarterSalesPerformance**メジャーです。 このアイコンは、そのメジャーが KPI のベース値として機能することを示します。  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>InternetCurrentQuarterMarginPerformance KPI を作成するには  
  
1.  メジャー グリッドで、 **FactInternetSales**テーブルで、空のセルをクリックします。  
  
2.  テーブルの上にある数式バーに、以下の数式を入力します。  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  右クリック**InternetCurrentQuarterMarginPerformance** > **KPI を作成**です。  
  
4.  主要業績評価指標 (KPI) ダイアログ ボックスで**ターゲット**選択**絶対値**、し、入力**1.25**です。   
  
5.  (低) の左のスライダー フィールドにフィールドが表示されるまでスライドさせます**0.8**、および右 (高) のスライダー フィールドに、フィールドが表示されるまでスライドし**1.03**です。  
  
6.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択し、**[OK]** をクリックします。  
  
## <a name="whats-next"></a>次の操作

[レッスン 8: パースペクティブの作成](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)です。
  
  
