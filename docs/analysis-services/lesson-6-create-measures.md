---
title: 'レッスン 7: メジャーの作成 |Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 146d93bc2c7257ce409f3a293f6c9050acde9ca7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994964"
---
# <a name="lesson-6-create-measures"></a>レッスン 6: メジャーを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、モデルに含められるメジャーを作成します。 同様に、前のレッスンで作成した計算列、メジャーとは、DAX の数式を使用して作成される計算です。 ただし、計算列とは違い、メジャーはユーザーが選択した " *フィルター*" に基づいて評価されます (たとえば、PivotTable 内の行ラベル フィールドに追加された特定の列やスライサーなど)。 フィルター内の各セルの値は、適用されたメジャーによって計算されます。 メジャーは、数値データに対して動的な計算を実行するほぼすべてのテーブル モデルに含める強力で柔軟な計算です。 詳細についてを参照してください。[メジャー](../analysis-services/tabular-models/measures-ssas-tabular.md)します。  
  
使用するメジャーを作成する、*メジャー グリッド*します。 既定では、各テーブルに空のメジャー グリッドがあります。ただし、通常はすべてのテーブルにメジャーを作成することはありません。 メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。 テーブルのメジャー グリッドを表示または非表示にするには、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]** をクリックします。  
  
メジャーを作成するには、メジャー グリッド内で空のセルをクリックし、数式バーに DAX 数式を入力します。 Enter キーを押して式の入力を完了すると、そのセルにメジャーが表示されます。 標準の集計関数を使用してメジャーを作成することもできます。その場合は、列をクリックし、ツール バーの [オート SUM] ボタン (**∑**) をクリックします。 オート Sum 機能を使用して作成したメジャーは、列の真下のメジャー グリッド セルに表示されますが、移動することができます。  
  
このレッスンでは、数式バーに DAX 数式を入力する方法と、オート SUM 機能を使用する方法の両方でメジャーを作成します。  
  
このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 5: 計算列の作成](../analysis-services/lesson-5-create-calculated-columns.md)です。  
  
## <a name="create-measures"></a>メジャーを作成する  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>DimDate テーブルに DaysCurrentQuarterToDate メジャーを作成するには  
  
1.  モデル デザイナーで、クリックして、 **DimDate**テーブル。  
  
2.  メジャー グリッドで、左上にある空のセルをクリックします。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    左上のセルのメジャーの名前では、すぐに**DaysCurrentQuarterToDate**、結果、その後に**92**します。
    
      ![として-テーブル-lesson6-newmeasure](../analysis-services/media/as-tabular-lesson6-newmeasure.png) 
    
    メジャーの数式で計算列とは異なり、コンマの後に、数式を続けて、メジャーの名前を入力できます。

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>DimDate テーブルで DaysInCurrentQuarter メジャーを作成するには  
  
1.  **DimDate**テーブルのメジャー グリッドで、モデル デザイナーで引き続きアクティブで、先ほど作成したメジャーの下の空のセルをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    未完了の期間と前の期間との間に比較率を作成する場合、数式では、経過した期間の比率を考慮に入れて、それを前の期間内の同じ比率と比較する必要があります。 この場合、[､ DaysCurrentQuarterToDate]/[DaysInCurrentQuarter] 割合は、現在の期間で経過しました。  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>FactInternetSales テーブルに InternetDistinctCountSalesOrder メジャーを作成するには  
  
1.  をクリックして、 **FactInternetSales**テーブル。   
  
2.  をクリックして、 **SalesOrderNumber**列見出し。  
  
3.  ツール バーで、[オート SUM] \(**∑**) ボタンの横にある下矢印をクリックし、 **[DistinctCount]** を選択します。  
  
    オート SUM 機能が、DistinctCount 標準集計式を使用して、選択された列に対するメジャーを自動的に作成します。  
    
       ![として-テーブル-lesson6-newmeasure2](../analysis-services/media/as-tabular-lesson6-newmeasure2.png)
  
4.  メジャー グリッドで、新しいメジャー をクリックし、**プロパティ**ウィンドウで、**メジャー名**にメジャーの名前を変更**InternetDistinctCountSalesOrder**します。 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>FactInternetSales テーブルに追加のメジャーを作成するには  
  
1.  オート SUM 機能を使用して、次の名前のメジャーを作成します。  
  
    |[メジャー名]|[列]|オート SUM (∑)|[数式]|  
    |----------------|----------|-----------------|-----------|  
    |InternetOrderLinesCount|SalesOrderLineNumber|Count|=COUNTA([SalesOrderLineNumber])|  
    |InternetTotalUnits|OrderQuantity|SUM|=SUM([OrderQuantity])|  
    |InternetTotalDiscountAmount|DiscountAmount|SUM|=SUM([DiscountAmount])|  
    |InternetTotalProductCost|TotalProductCost|SUM|=SUM([TotalProductCost])|  
    |InternetTotalSales|SalesAmount|SUM|=SUM([SalesAmount])|  
    |InternetTotalMargin|Margin|SUM|=SUM([Margin])|  
    |InternetTotalTaxAmt|TaxAmt|SUM|=SUM([TaxAmt])|  
    |InternetTotalFreight|Freight|SUM|=SUM([Freight])|  
  
2.  メジャー グリッドで空のセルをクリックし、数式バーを使用して作成し、順序で次のメジャーの名前します。  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
FactInternetSales テーブルに作成したメジャーは、売上、コスト、およびユーザーの選択したフィルターによって定義されている項目の利益率などの重要な財務データの分析に使用できます。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 7: 主要業績評価指標の作成](../analysis-services/lesson-7-create-key-performance-indicators.md)です。  

  
