---
title: "レッスン 6: 計算列の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c59e137942d45cbe6c20a71b9fa785988b9876fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-5-create-calculated-columns"></a>レッスン 5: 計算列を作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、計算列を追加して、モデル内に新しいデータを作成します。 計算列は、モデル内の既存のデータに基づいて機能します。 詳細については、次を参照してください。 [Calculated Columns](../analysis-services/tabular-models/ssas-calculated-columns.md)です。  
  
このレッスンでは、3 つの異なるテーブル内に、5 つの新しい計算列を作成します。 手順は実習ごとに少しずつ異なります。 これは、新しい列を作成したり、それらの名前を変更したり、それらをテーブル内のさまざまな場所へ配置するのには、いくつかの方法があることを示すためです。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 4: リレーションシップの作成](../analysis-services/lesson-4-create-relationships.md)です。 
  
## <a name="create-calculated-columns"></a>計算列の作成  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>DimDate テーブルの MonthCalendar の計算列を作成します。  
  
1.  クリックして、**モデル**メニュー >**モデル ビュー** > **データ ビュー**です。  
  
    計算列は、モデル デザイナーのデータ ビューでのみ作成できます。  
  
2.  モデル デザイナーで、をクリックして、 **DimDate**テーブル (タブ)。  
  
3.  右クリックし、 **CalendarQuarter**列ヘッダーをクリックして**列の挿入**です。  
  
    **Calculated Column 1** という新しい列が、 **Calendar Quarter** 列の左側に挿入されます。  
  
4.  テーブルの上にある数式バーに、以下の数式を入力します。 オートコンプリートを利用すると、列やテーブルの完全修飾名を簡単に入力できるだけでなく、使用可能な関数の一覧も表示できます。  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    すべての行の計算列に値が入力されます。 テーブルを下にスクロールすると、この列の行が、各行のデータに基づいて、異なる値を保持できることがわかります。    
  
5.  この列の名前を変更**MonthCalendar**です。 

    ![として-表形式の lesson5-newcolumn](../analysis-services/media/as-tabular-lesson5-newcolumn.png) 
  
月表示カレンダー月の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>DimDate テーブルの DayOfWeek 計算列を作成します。  
  
1.  **DimDate**テーブル アクティブのままで、をクリックして、**列** メニューをクリックして**列の追加**です。  
  
2.  数式バーで、次の数式を入力します。  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    式の作成が完了したら、ENTER キーを押します。 新しい列がテーブルの右端に追加されます。  
  
3.  列の名前を変更**DayOfWeek**です。  
  
4.  列見出しをクリックし、列の間をドラッグ、 **EnglishDayNameOfWeek**列と**DayNumberOfMonth**列です。  
  
    > [!TIP]  
    > テーブル内の列を移動することで、列が参照しやすくなります。  
  
曜日を示す、曜日、週の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>ProductSubcategoryName 計算列を DimProduct テーブルの作成します。  
  
  
1.  **DimProduct**テーブル、テーブルの一番右にスクロールします。 右端にある **Add Column** (斜体) という列の列見出しをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  列の名前を変更**ProductSubcategoryName**です。  
  
ProductSubcategoryName 計算列は DimProductSubcategory テーブルで、[EnglishProductSubcategoryName] 列からデータが含まれている DimProduct テーブルの階層を作成するために使用します。 階層は、複数のテーブルにまたがって存在することはできません。 レッスン 9 で後で階層を作成します。  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>DimProduct テーブルに、ProductCategoryName の計算列を作成します。  
  
1.  **DimProduct**テーブル アクティブであるをクリックして、**列** メニューをクリックして**列の追加**です。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  列の名前を変更**ProductCategoryName**です。  
  
ProductCategoryName の計算列は DimProductCategory テーブルに EnglishProductCategoryName 列からデータを含め、DimProduct テーブルの階層を作成するために使用します。 階層は、複数のテーブルにまたがって存在することはできません。  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>FactInternetSales テーブルで Margin 計算列を作成します。  
  
1.  モデル デザイナーで、選択、 **FactInternetSales**テーブル。  
  
2.  新しい列を追加します。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  列の名前を **Margin**に変更します。  
  
5.  間で列をドラッグして、 **SalesAmount**列と**TaxAmt**列です。 
 
      ![として-表形式の lesson5-newmargin](../analysis-services/media/as-tabular-lesson5-newmargin.png)
      
    Margin 計算列を使用して、各販売の利益率を分析できます。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 6: メジャーの作成](../analysis-services/lesson-6-create-measures.md)です。
  
  
  

