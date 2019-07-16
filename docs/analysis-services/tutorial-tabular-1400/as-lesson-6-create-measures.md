---
title: Analysis Services チュートリアル-レッスン 6:メジャーの作成 |Microsoft Docs
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
ms.openlocfilehash: 715fe6144cc430e545feb3c484d148531cff6ec9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207347"
---
# <a name="create-measures"></a>メジャーを作成する

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、モデルに含まれるメジャーを作成します。 メジャーは DAX 数式を使用して作成される計算を作成した計算列と同様に、します。 ただし、計算列とは異なりメジャーに基づいて評価されますユーザーが選択した*フィルター*します。 例を特定の列やスライサーをピボット テーブルの行ラベル フィールドに追加します。 フィルター内の各セルの値は、適用されたメジャーによって計算されます。 メジャーは、数値データに対して動的な計算を実行するほぼすべてのテーブル モデルに含める強力で柔軟な計算です。 詳細についてを参照してください。[メジャー](../tabular-models/measures-ssas-tabular.md)します。
  
使用するメジャーを作成する、*メジャー グリッド*します。 既定では、各テーブルには空のメジャー グリッドです。ただし、通常は作成しないすべてのテーブルのメジャー。 メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。 テーブルのメジャー グリッドを表示または非表示にするには、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]** をクリックします。  
  
メジャーを作成するには、メジャー グリッドで空のセルをクリックして、数式バーに DAX 数式を入力します。 ときに、メジャーの数式を完了するには ENTER をクリックし、セルに表示されます。 オート Sum ボタンをクリックして、列で標準の集計関数を使用してメジャーを作成することもできます (**∑**) ツールバー。 オート Sum 機能を使用して作成したメジャーは、列の真下のメジャー グリッド セルに表示されますが、移動することができます。  
  
このレッスンでは、両方が、数式バーで DAX 数式を入力し、オート Sum 機能を使用してメジャーを作成します。  
  
このレッスンを完了するまでに時間を推定するには。**30 分**  
  
## <a name="prerequisites"></a>必須コンポーネント  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 5: 計算列を作成](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)です。  
  
## <a name="create-measures"></a>メジャーを作成する  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>DimDate テーブルに DaysCurrentQuarterToDate メジャーを作成するには  
  
1.  モデル デザイナーで、クリックして、 **DimDate**テーブル。  
  
2.  メジャー グリッドで、左上にある空のセルをクリックします。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    左上のセルのメジャーの名前では、すぐに**DaysCurrentQuarterToDate**、結果、その後に**92**します。 結果は関連しませんこの時点でユーザーのフィルターが適用されていません。
    
      ![as-lesson6-newmeasure](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    メジャーの数式で計算列とは異なり、数式を続けて、コロンの後に、メジャーの名前を入力できます。

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>DimDate テーブルで DaysInCurrentQuarter メジャーを作成するには  
  
1.  **DimDate**テーブルのメジャー グリッドで、モデル デザイナーで引き続きアクティブで、作成したメジャーの下の空のセルをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    未完了の期間と前の期間の間の比較率を作成するときに 数式が経過し、前の期間内の同じ比率と比較した期間の割合を計算する必要があります。 この場合、[､ DaysCurrentQuarterToDate]/[DaysInCurrentQuarter] 割合は、現在の期間で経過しました。  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>FactInternetSales テーブルに InternetDistinctCountSalesOrder メジャーを作成するには  
  
1.  をクリックして、 **FactInternetSales**テーブル。   
  
2.  をクリックして、 **SalesOrderNumber**列見出し。  
  
3.  ツール バーで、[オート SUM] \(**∑**) ボタンの横にある下矢印をクリックし、 **[DistinctCount]** を選択します。  
  
    オート SUM 機能が、DistinctCount 標準集計式を使用して、選択された列に対するメジャーを自動的に作成します。  
    
       ![as-lesson6-newmeasure2](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  メジャー グリッドで、新しいメジャー をクリックし、**プロパティ**ウィンドウで、**メジャー名**にメジャーの名前を変更**InternetDistinctCountSalesOrder**します。 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>FactInternetSales テーブルに追加のメジャーを作成するには  
  
1.  オート SUM 機能を使用して、次の名前のメジャーを作成します。  

    |[列]|メジャー名|オート SUM (∑)|[数式]|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Count|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|Sum|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|Sum|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|Sum|=SUM([TotalProductCost])|  
    |SalesAmount|InternetTotalSales|Sum|=SUM([SalesAmount])|  
    |余白|InternetTotalMargin|Sum|=SUM([Margin])|  
    |TaxAmt|InternetTotalTaxAmt|Sum|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|Sum|=SUM([Freight])|  
  
2.  メジャー グリッドで空のセルをクリックし、数式バーを使用して作成する順序で次のカスタム メジャー。  
  
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

[レッスン 7: 主要業績評価指標の作成](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)です。  

  
