---
title: Analysis Services チュートリアル レッスン 7:主要業績評価指標の作成 |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f3b3de71cb60a27613482255556bfbff6bcc8cf
ms.sourcegitcommit: 6193aa9b4967302424270d67c27dbc601ca6849a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877620"
---
# <a name="create-key-performance-indicators"></a>主要業績評価指標の作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、主要業績評価指標 (Kpi) を作成します。 Kpi がによって定義された値のパフォーマンス測定に使用される、*ベース*メジャーに対して、*ターゲット*も、メジャーまたは絶対値によって定義されている値。 KPI を使用すると、ビジネス プロフェッショナルがレポート クライアント アプリケーションを通じて、ビジネスの成功度や傾向をすばやく簡単に把握できるようになります。 詳細についてを参照してください[Kpi。](../tabular-models/kpis-ssas-tabular.md)
  
このレッスンを完了するまでに時間を推定するには。**15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 6:メジャーを作成](../tutorial-tabular-1400/as-lesson-6-create-measures.md)です。   
  
## <a name="create-key-performance-indicators"></a>主要業績評価指標の作成  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>InternetCurrentQuarterSalesPerformance KPI を作成するには  
  
1.  モデル デザイナーで、クリックして、 **FactInternetSales**テーブル。  
  
2.  メジャー グリッドで、空のセルをクリックします。  
  
3.  テーブルの上にある数式バーに、以下の数式を入力します。 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IF([InternetPreviousQuarterSalesProportionToQTD]<>0,([InternetCurrentQuarterSales]-[InternetPreviousQuarterSalesProportionToQTD])/[InternetPreviousQuarterSalesProportionToQTD],BLANK()) 
    ```

    このメジャーは KPI のベース メジャーとして機能します。  
  
4.  メジャー グリッドで右クリック**InternetCurrentQuarterSalesPerformance** > **Create KPI**します。   
  
5.  主要業績評価指標 (KPI) ダイアログ ボックスで**ターゲット**選択**絶対値**、し、入力**1.1**します。  
  
7.  左 (下) のスライダー フィールドに「 **1**」と入力し、右 (上) のスライダー フィールドに「 **1.07**」と入力します。  
  
8.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択します。
  
    ![as-lesson7-kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > 展開に注目してください**説明**使用可能なアイコン スタイルの下のラベル。 クライアント アプリケーションでより特定できるようにするのにには、さまざまな KPI 要素の説明を使用します。  
  
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
  
5.  左 (下) のスライダー フィールドに、スライド、フィールドが表示されるまで**0.8**と右 (高) のスライダー フィールドに、フィールドが表示されるまでスライドし**1.03**します。  
  
6.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択し、**[OK]** をクリックします。  
  
## <a name="whats-next"></a>次の操作

[レッスン 8: パースペクティブを作成する](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)します。
  
  
