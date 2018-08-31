---
title: 'レッスン 5: 計算列を作成する |Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5e23ca8ccf344ec9f250eac032946ac074a735d
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2018
ms.locfileid: "42792183"
---
# <a name="lesson-5-create-calculated-columns"></a>レッスン 5: 計算列を作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、計算列を追加して、モデル内に新しいデータを作成します。 計算列は、モデル内の既存のデータに基づいて機能します。 詳細についてを参照してください。 [Calculated Columns](../analysis-services/tabular-models/ssas-calculated-columns.md)します。  
  
このレッスンでは、3 つの異なるテーブル内に、5 つの新しい計算列を作成します。 手順は実習ごとに少しずつ異なります。 これは、新しい列を作成したり、それらの名前を変更したり、それらをテーブル内のさまざまな場所へ配置するのには、いくつかの方法があることを示すためです。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>Prerequisites  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 4: リレーションシップの作成](../analysis-services/lesson-4-create-relationships.md)です。 
  
## <a name="create-calculated-columns"></a>計算列の作成  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>DimDate テーブルに MonthCalendar 計算列を作成します。  
  
1.  をクリックして、**モデル**メニュー >**モデル ビュー** > **データ ビュー**します。  
  
    計算列は、モデル デザイナーのデータ ビューでのみ作成できます。  
  
2.  モデル デザイナーで、クリックして、 **DimDate**テーブル (タブ)。  
  
3.  右クリックし、 **CalendarQuarter**列ヘッダーをクリックして**列の挿入**します。  
  
    **Calculated Column 1** という新しい列が、 **Calendar Quarter** 列の左側に挿入されます。  
  
4.  テーブルの上にある数式バーに、以下の数式を入力します。 オートコンプリートを利用すると、列やテーブルの完全修飾名を簡単に入力できるだけでなく、使用可能な関数の一覧も表示できます。  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    すべての行の計算列に値が入力されます。 テーブルを下にスクロールすると、この列の行が、各行のデータに基づいて、異なる値を保持できることがわかります。    
  
5.  この列の名前を変更**MonthCalendar**します。 

    ![として-テーブル-lesson5-newcolumn](../analysis-services/media/as-tabular-lesson5-newcolumn.png) 
  
MonthCalendar には、1 か月の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>DimDate テーブルに DayOfWeek 計算列を作成します。  
  
1.  **DimDate**テーブルがアクティブな をクリックして、**列** メニューをクリック**列の追加**します。  
  
2.  数式バーで、次の数式を入力します。  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    数式の構築が完了したら、ENTER キーを押します。 新しい列がテーブルの右端に追加されます。  
  
3.  列の名前を変更**DayOfWeek**します。  
  
4.  、列見出しをクリックし、列の間をドラッグ、 **EnglishDayNameOfWeek**列と**DayNumberOfMonth**列。  
  
    > [!TIP]  
    > テーブル内の列を移動することで、列が参照しやすくなります。  
  
曜日を示すには、週の曜日の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>DimProduct テーブルに ProductSubcategoryName 計算列を作成します。  
  
  
1.  **DimProduct**テーブル、テーブルの右端までスクロールします。 右端にある **Add Column** (斜体) という列の列見出しをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  列の名前を変更**ProductSubcategoryName**します。  
  
ProductSubcategoryName 計算列は DimProductSubcategory テーブルの EnglishProductSubcategoryName 列からデータを含め、DimProduct テーブルの階層を作成するために使用します。 階層は、複数のテーブルにまたがって存在することはできません。 階層は ､ 後ほどレッスン 9 で作成します。  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>DimProduct テーブルに ProductCategoryName 計算列を作成します。  
  
1.  **DimProduct**テーブル中、 をクリックして、**列** メニューをクリック**列の追加**します。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  列の名前を変更**ProductCategoryName**します。  
  
ProductCategoryName 計算列は ､ DimProductCategory テーブルの EnglishProductCategoryName 列からデータを含んだ DimProduct テーブルの階層を作成するために使用します。 階層は、複数のテーブルにまたがって存在することはできません。  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>FactInternetSales テーブルに Margin 計算列を作成します。  
  
1.  モデル デザイナーで、選択、 **FactInternetSales**テーブル。  
  
2.  新しい列を追加します。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  列の名前を **Margin**に変更します。  
  
5.  列の間にドラッグ、 **SalesAmount**列と**TaxAmt**列。 
 
      ![として-テーブル-lesson5-newmargin](../analysis-services/media/as-tabular-lesson5-newmargin.png)
      
    Margin 計算列は、各販売の利益率の分析に使用されます。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 6: メジャーの作成](../analysis-services/lesson-6-create-measures.md)です。
  
  
  
