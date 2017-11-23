---
title: "レッスン 7: メジャーを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 7854640d3f9ddbc829e2a9110c771816aa1aa87d
ms.sourcegitcommit: 50e9ac6ae10bfeb8ee718c96c0eeb4b95481b892
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="lesson-6-create-measures"></a>レッスン 6: メジャーを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、モデルに含められるメジャーを作成します。 前のレッスンで作成した計算列と同様に、メジャーとは、計算、DAX の数式を使用して作成します。 ただし、計算列とは違い、メジャーはユーザーが選択した " *フィルター*" に基づいて評価されます (たとえば、PivotTable 内の行ラベル フィールドに追加された特定の列やスライサーなど)。 フィルター内の各セルの値は、適用されたメジャーによって計算されます。 メジャーは、数値データに対する動的な計算を実行するほとんどすべてのテーブル モデルに含めるか強力で柔軟な計算です。 詳細については、次を参照してください。[メジャー](../analysis-services/tabular-models/measures-ssas-tabular.md)です。  
  
メジャーを作成するには、使用して、*メジャー グリッド*です。 既定では、各テーブルに空のメジャー グリッドがあります。ただし、通常はすべてのテーブルにメジャーを作成することはありません。 メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。 テーブルのメジャー グリッドを表示または非表示にするには、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]**をクリックします。  
  
メジャーを作成するには、メジャー グリッド内で空のセルをクリックし、数式バーに DAX 数式を入力します。 Enter キーを押して式の入力を完了すると、そのセルにメジャーが表示されます。 標準の集計関数を使用してメジャーを作成することもできます。その場合は、列をクリックし、ツール バーの [オート SUM] ボタン (**∑**) をクリックします。 オート Sum 機能を使用して作成したメジャーは、列のすぐ下のメジャー グリッド セルに表示されますが、移動することができます。  
  
このレッスンでは、数式バーに DAX 数式を入力する方法と、オート SUM 機能を使用する方法の両方でメジャーを作成します。  
  
このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 5: 計算列の作成](../analysis-services/lesson-5-create-calculated-columns.md)です。  
  
## <a name="create-measures"></a>メジャーを作成する  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>DimDate テーブルのメジャーを DaysCurrentQuarterToDate を作成するには  
  
1.  モデル デザイナーで、をクリックして、 **DimDate**テーブル。  
  
2.  メジャー グリッドで、左上にある空のセルをクリックします。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    左上のセルが含まれています、メジャー名に注意してください**DaysCurrentQuarterToDate**」と入力し、結果を**92**です。
    
      ![として-表形式の lesson6-newmeasure](../analysis-services/media/as-tabular-lesson6-newmeasure.png) 
    
    メジャーの数式、計算列とは異なり、続いて、数式を続けて、コンマ、メジャーの名前を入力することができます。

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>DimDate テーブルのメジャーを DaysInCurrentQuarter を作成するには  
  
1.  **DimDate**テーブル モデル デザイナーの メジャー グリッドで、まだアクティブで、作成したメジャーの下の空のセルをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    未完了の期間と前の期間との間に比較率を作成する場合、数式では、経過した期間の比率を考慮に入れて、それを前の期間内の同じ比率と比較する必要があります。 この場合、[DaysCurrentQuarterToDate]/[DaysInCurrentQuarter] 比率は、現在の期間経過しました。  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>FactInternetSales テーブルで InternetDistinctCountSalesOrder メジャーを作成するには  
  
1.  クリックして、 **FactInternetSales**テーブル。   
  
2.  をクリックして、 **SalesOrderNumber**列見出し。  
  
3.  ツール バーで、[オート SUM] (**∑**) ボタンの横にある下矢印をクリックし、 **[DistinctCount]**を選択します。  
  
    オート SUM 機能が、DistinctCount 標準集計式を使用して、選択された列に対するメジャーを自動的に作成します。  
    
       ![として-表形式の lesson6-newmeasure2](../analysis-services/media/as-tabular-lesson6-newmeasure2.png)
  
4.  メジャー グリッドで、新しいメジャーをクリックし、**プロパティ** ウィンドウで、**メジャー名**、するメジャーの名前を変更**InternetDistinctCountSalesOrder**です。 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>FactInternetSales テーブルでその他のメジャーを作成するには  
  
1.  オート SUM 機能を使用して、次の名前のメジャーを作成します。  
  
    |[メジャー名]|列|オート SUM (∑)|[数式]|  
    |----------------|----------|-----------------|-----------|  
    |InternetOrderLinesCount|SalesOrderLineNumber|Count|=COUNTA([SalesOrderLineNumber])|  
    |InternetTotalUnits|OrderQuantity|Sum|=SUM([OrderQuantity])|  
    |InternetTotalDiscountAmount|DiscountAmount|Sum|=SUM([DiscountAmount])|  
    |InternetTotalProductCost|TotalProductCost|Sum|=SUM([TotalProductCost])|  
    |InternetTotalSales|SalesAmount|Sum|=SUM([SalesAmount])|  
    |InternetTotalMargin|Margin|Sum|=SUM([Margin])|  
    |InternetTotalTaxAmt|TaxAmt|Sum|=SUM([TaxAmt])|  
    |InternetTotalFreight|Freight|Sum|=SUM([Freight])|  
  
2.  メジャー グリッドで空のセルをクリックすると、数式バーを使用して、作成し、名前は次のメジャーの順序で。  
  
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
  
FactInternetSales テーブルの作成したメジャーは、売上、コスト、およびユーザーの選択したフィルターによって定義された項目の利益率などの重要な財務データの分析に使用できます。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 7: 主要業績評価指標の作成](../analysis-services/lesson-7-create-key-performance-indicators.md)です。  

  
