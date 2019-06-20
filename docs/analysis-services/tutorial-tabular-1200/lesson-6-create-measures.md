---
title: 'レッスン 6: メジャーの作成 |Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f8ad53f78acb862101ff633f663ea03198825ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404664"
---
# <a name="lesson-6-create-measures"></a>レッスン 6: メジャーを作成する
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、モデルに含められるメジャーを作成します。 同様に、前のレッスンで作成した計算列、メジャーとは、DAX の数式を使用して作成される計算です。 ただし、計算列とは違い、メジャーはユーザーが選択した " *フィルター*" に基づいて評価されます (たとえば、PivotTable 内の行ラベル フィールドに追加された特定の列やスライサーなど)。 フィルター内の各セルの値は、適用されたメジャーによって計算されます。 メジャーは、数値データに対して動的な計算を実行するほぼすべてのテーブル モデルに含める強力で柔軟な計算です。 詳細についてを参照してください。[メジャー](../tabular-models/measures-ssas-tabular.md)します。  
  
使用するメジャーを作成する、*メジャー グリッド*します。 既定では、各テーブルに空のメジャー グリッドがあります。ただし、通常はすべてのテーブルにメジャーを作成することはありません。 メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。 テーブルのメジャー グリッドを表示または非表示にするには、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]** をクリックします。  
  
メジャーを作成するには、メジャー グリッド内で空のセルをクリックし、数式バーに DAX 数式を入力します。 Enter キーを押して式の入力を完了すると、そのセルにメジャーが表示されます。 標準の集計関数を使用してメジャーを作成することもできます。その場合は、列をクリックし、ツール バーの [オート SUM] ボタン (**∑**) をクリックします。 オート Sum 機能を使用して作成したメジャーは、列の真下のメジャー グリッド セルに表示されますが、移動することができます。  
  
このレッスンでは、数式バーに DAX 数式を入力する方法と、オート SUM 機能を使用する方法の両方でメジャーを作成します。  
  
このレッスンを完了するまでに時間を推定するには。**30 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 5: 計算列を作成](lesson-5-create-calculated-columns.md)です。  
  
## <a name="create-measures"></a>メジャーを作成する  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>DimDate テーブルに DaysCurrentQuarterToDate メジャーを作成するには  
  
1.  モデル デザイナーで、クリックして、 **DimDate**テーブル。  
  
2.  メジャー グリッドで、左上にある空のセルをクリックします。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    左上のセルのメジャーの名前では、すぐに**DaysCurrentQuarterToDate**、結果、その後に**92**します。
    
      ![として-テーブル-lesson6-newmeasure](media/as-tabular-lesson6-newmeasure.png) 
    
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
    
       ![as-tabular-lesson6-newmeasure2](media/as-tabular-lesson6-newmeasure2.png)
  
4.  メジャー グリッドで、新しいメジャー をクリックし、**プロパティ**ウィンドウで、**メジャー名**にメジャーの名前を変更**InternetDistinctCountSalesOrder**します。 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>FactInternetSales テーブルに追加のメジャーを作成するには  
  
1.  オート SUM 機能を使用して、次の名前のメジャーを作成します。  
  
    |[メジャー名]|[列]|オート SUM (∑)|[数式]|  
    |----------------|----------|-----------------|-----------|  
    |InternetOrderLinesCount|SalesOrderLineNumber|Count|=COUNTA([SalesOrderLineNumber])|  
    |InternetTotalUnits|OrderQuantity|Sum|=SUM([OrderQuantity])|  
    |InternetTotalDiscountAmount|DiscountAmount|Sum|=SUM([DiscountAmount])|  
    |InternetTotalProductCost|TotalProductCost|Sum|=SUM([TotalProductCost])|  
    |InternetTotalSales|SalesAmount|Sum|=SUM([SalesAmount])|  
    |InternetTotalMargin|Margin|Sum|=SUM([Margin])|  
    |InternetTotalTaxAmt|TaxAmt|Sum|=SUM([TaxAmt])|  
    |InternetTotalFreight|Freight|Sum|=SUM([Freight])|  
  
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
次のレッスンに移動します。[レッスン 7: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)です。  

  
