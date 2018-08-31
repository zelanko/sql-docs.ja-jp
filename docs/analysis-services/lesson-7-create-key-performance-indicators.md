---
title: 'レッスン 7: 主要業績評価指標の作成 |Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ecfedbbc4b7e606f1589f2b5415c5355bb0d95e1
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2018
ms.locfileid: "42790103"
---
# <a name="lesson-7-create-key-performance-indicators"></a>レッスン 7: 主要業績評価指標の作成
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、主要業績評価指標 (KPI) を作成します。 KPI は、値のパフォーマンスを測定するために使用されます。パフォーマンスは、 *"ベース"* メジャーと *"ターゲット"* 値の対比によって定義されます (メジャーまたは絶対値によっても定義できます)。 KPI を使用すると、ビジネス プロフェッショナルがレポート クライアント アプリケーションを通じて、ビジネスの成功度や傾向をすばやく簡単に把握できるようになります。 詳細についてを参照してください。 [Kpi](../analysis-services/tabular-models/kpis-ssas-tabular.md)します。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>Prerequisites  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 6: メジャーの作成](../analysis-services/lesson-6-create-measures.md)です。   
  
## <a name="create-key-performance-indicators"></a>主要業績評価指標の作成  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>InternetCurrentQuarterSalesPerformance KPI を作成するには  
  
1.  モデル デザイナーで、クリックして、 **FactInternetSales**テーブル (タブ)。  
  
2.  メジャー グリッドで、空のセルをクリックします。  
  
3.  テーブルの上にある数式バーに、以下の数式を入力します。 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IFERROR([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    このメジャーは、KPI のベース メジャーとして機能します。  
  
4.  右クリックして**InternetCurrentQuarterSalesPerformance** > **KPI の作成**です。   
  
5.  主要業績評価指標 (KPI) ダイアログ ボックスで**ターゲット**選択**絶対値**、し、入力**1.1**します。  
  
7.  左 (下) のスライダー フィールドに「 **1**」と入力し、右 (上) のスライダー フィールドに「 **1.07**」と入力します。  
  
8.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択します。
  
    ![として-テーブル-lesson7 の kpi](../analysis-services/media/as-tabular-lesson7-kpi.png)
    
    > [!TIP]  
    > 展開に注目してください**説明**使用可能なアイコン スタイルの下のラベル。 これを使用して、クライアント アプリケーションでより特定できるようにする各種の KPI 要素の説明を入力します。  
  
9. **[OK]** をクリックして KPI の作成を完了します。  
  
    メジャー グリッドの場合は、横にアイコンを見てください、 **InternetCurrentQuarterSalesPerformance**メジャーです。 このアイコンは、そのメジャーが KPI のベース値として機能することを示します。  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>InternetCurrentQuarterMarginPerformance KPI を作成するには  
  
1.  メジャー グリッドで、 **FactInternetSales**テーブルで、空のセルをクリックします。  
  
2.  テーブルの上にある数式バーに、以下の数式を入力します。  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  右クリックして**InternetCurrentQuarterMarginPerformance** > **KPI の作成**です。  
  
4.  主要業績評価指標 (KPI) ダイアログ ボックスで**ターゲット**選択**絶対値**、し、入力**1.25**します。   
  
5.  **[ステータスのしきい値の定義]** で、左 (下) のスライダー フィールドをスライドして「 **0.8**」と表示させ、右 (上) のスライダー フィールドをスライドして「 **1.03**」と表示させます。  
  
6.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択し、**[OK]** をクリックします。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 8: パースペクティブの作成」](../analysis-services/lesson-8-create-perspectives.md)します。
  
  
