---
title: "Analysis Services のチュートリアル レッスン 6: メジャーを作成 |Microsoft ドキュメント"
description: "Analysis Services tutorial プロジェクトのメジャーを作成する方法について説明します。"
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: b4de99f18366afefaeb5411e0fc5454d378b87f7
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2018
---
# <a name="create-measures"></a>メジャーを作成する

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、モデルに含まれるメジャーを作成します。 作成した計算列と同様に、メジャーとは、計算、DAX の数式を使用して作成します。 ただし、計算列とは異なりメジャーに基づいて評価されます、ユーザーが選択した*フィルター*です。 など、特定の列やスライサーをピボット テーブルの行ラベル フィールドに追加します。 フィルター内の各セルの値は、適用されたメジャーによって計算されます。 メジャーは、強力で柔軟な計算を数値データに対する動的な計算を実行するほとんどすべてのテーブル モデルに追加することです。 詳細については、次を参照してください。[メジャー](../tabular-models/measures-ssas-tabular.md)です。
  
使用するメジャーを作成する、*メジャー グリッド*です。 既定では、各テーブルには空のメジャー グリッドです。ただし、通常作成しないすべてのテーブルのメジャーです。 メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。 テーブルのメジャー グリッドを表示または非表示にするには、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]**をクリックします。  
  
メジャー グリッドで空のセルをクリックし、数式バーに DAX 数式を入力することによって、メジャーを作成することができます。 メジャーの数式を完了するには、enter キーを押しますをする場合、セルに表示されます。 列をクリックし、[オート sum] ボタンをクリックし、標準の集計関数を使用してメジャーを作成することもできます (**∑**) ツールバー。 オート Sum 機能を使用して作成したメジャーは、列のすぐ下のメジャー グリッド セルに表示されますが、移動することができます。  
  
このレッスンでは、両方が、数式バーに DAX 数式を入力し、オート Sum 機能を使用してメジャーを作成します。  
  
このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 5: 計算列を作成](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)です。  
  
## <a name="create-measures"></a>メジャーを作成する  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>DimDate テーブルのメジャーを DaysCurrentQuarterToDate を作成するには  
  
1.  モデル デザイナーで、をクリックして、 **DimDate**テーブル。  
  
2.  メジャー グリッドで、左上にある空のセルをクリックします。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    左上のセルが含まれています、メジャー名に注意してください**DaysCurrentQuarterToDate**」と入力し、結果を**92**です。 結果は無効この時点でユーザーのフィルターが適用されていないためです。
    
      ![as-lesson6-newmeasure](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    メジャーの数式、計算列とは異なり、後に、数式を続けて、コロン、メジャーの名前を入力することができます。

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>DimDate テーブルのメジャーを DaysInCurrentQuarter を作成するには  
  
1.  **DimDate**テーブル、メジャー グリッドで、モデル デザイナーではまだアクティブで、作成したメジャーの下の空のセルをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    ときに、未完了の期間と前の期間の間の比較率を作成します。 数式が経過し、前の期間内の同じ比率と比較した期間の比率を計算する必要があります。 この場合、[DaysCurrentQuarterToDate]/[DaysInCurrentQuarter] 比率は、現在の期間経過しました。  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>FactInternetSales テーブルで InternetDistinctCountSalesOrder メジャーを作成するには  
  
1.  クリックして、 **FactInternetSales**テーブル。   
  
2.  クリックして、 **SalesOrderNumber**列見出し。  
  
3.  ツール バーで、[オート SUM] \(**∑**) ボタンの横にある下矢印をクリックし、 **[DistinctCount]**を選択します。  
  
    オート SUM 機能が、DistinctCount 標準集計式を使用して、選択された列に対するメジャーを自動的に作成します。  
    
       ![as-lesson6-newmeasure2](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  メジャー グリッドで、新しいメジャーをクリックし、**プロパティ** ウィンドウで、**メジャー名**、するメジャーの名前を変更**InternetDistinctCountSalesOrder**です。 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>FactInternetSales テーブルでその他のメジャーを作成するには  
  
1.  オート SUM 機能を使用して、次の名前のメジャーを作成します。  

    |列|メジャー名|オート SUM (∑)|[数式]|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Count|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|Sum|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|Sum|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|Sum|=SUM([TotalProductCost])|  
    |SalesAmount|InternetTotalSales|Sum|=SUM([SalesAmount])|  
    |Margin|InternetTotalMargin|Sum|=SUM([Margin])|  
    |TaxAmt|InternetTotalTaxAmt|Sum|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|Sum|=SUM([Freight])|  
  
2.  メジャー グリッドで空のセルをクリックし、数式バーを使用して、作成、次のカスタム メジャーの順序で。  
  
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

[レッスン 7: 主要業績評価指標の作成](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)です。  

  
