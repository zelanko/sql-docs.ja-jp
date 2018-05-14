---
title: 'Analysis Services のチュートリアル レッスン 5: 計算列を作成 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 476eca07ed1367141372586ca13bd2a93d9d8105
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="create-calculated-columns"></a>計算列の作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは計算列を追加することで、モデルでデータを作成します。 (カスタムの列) として計算列を作成するデータの取得を使用する場合、クエリ エディターを使用して、またはモデル デザイナーなどの作業を行うここです。 詳細については、次を参照してください。[集計列](../tabular-models/ssas-calculated-columns.md)です。
  
次の 3 つの異なるテーブルには、5 つの新しい計算列を作成します。 手順は、列を作成、それらの名前を変更し、テーブル内のさまざまな場所に配置するいくつかの方法を示すタスクごとに少しずつ異なります。  

このレッスンは、Data Analysis Expressions (DAX) を最初に使用してもです。 DAX は、表形式モデルの高度にカスタマイズ可能な式の式を作成するための特別な言語です。 このチュートリアルでは、計算列、メジャー、およびロール フィルターを作成するのに DAX を使用します。 詳細については、次を参照してください。[表形式モデルでの DAX](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)です。 
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 4: リレーションシップの作成](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)です。 
  
## <a name="create-calculated-columns"></a>計算列の作成  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>DimDate テーブルの MonthCalendar の計算列を作成します。  
  
1.  クリックして、**モデル**メニュー >**モデル ビュー** > **データ ビュー**です。  
  
    計算列は、モデル デザイナーのデータ ビューでのみ作成できます。  
  
2.  モデル デザイナーで、をクリックして、 **DimDate**テーブル (タブ)。  
  
3.  右クリックし、 **CalendarQuarter**列ヘッダーをクリックして**列の挿入**です。  
  
    **Calculated Column 1** という新しい列が、 **Calendar Quarter** 列の左側に挿入されます。  
  
4.  テーブルの上、数式バーに次の DAX 数式を入力: オートコンプリートは、列やテーブルの完全修飾名を入力することができ、使用可能な関数が一覧表示します。  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    すべての行の計算列に値が入力されます。 テーブルを下へスクロールする場合は、行が行ごとのデータに基づく、この列に異なる値を持つことが表示されます。    
  
5.  この列の名前を変更**MonthCalendar**です。 

    ![as-lesson5-newcolumn](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
月表示カレンダー月の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>DimDate テーブルの DayOfWeek 計算列を作成します。  
  
1.  **DimDate**テーブル アクティブであるをクリックして、**列** メニューをクリックして**列の追加**です。  
  
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
  
ProductSubcategoryName 計算列を使用して、DimProductSubcategory テーブルで、[EnglishProductSubcategoryName] 列からデータが含まれています、DimProduct テーブルの階層を作成します。 階層は、複数のテーブルにまたがって存在することはできません。 レッスン 9 の後半では、階層を作成します。  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>DimProduct テーブルに、ProductCategoryName の計算列を作成します。  
  
1.  **DimProduct**テーブル アクティブであるをクリックして、**列** メニューをクリックして**列の追加**です。  
  
2.  数式バーで、次の数式を入力します。  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  列の名前を変更**ProductCategoryName**です。  
  
ProductCategoryName の計算列は DimProductCategory テーブルの EnglishProductCategoryName 列からデータを含んだ DimProduct テーブルの階層を作成するために使用します。 階層は、複数のテーブルにまたがって存在することはできません。  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>FactInternetSales テーブルで Margin 計算列を作成します。  
  
1.  モデル デザイナーで、選択、 **FactInternetSales**テーブル。  
  
2.  間に新しい計算列を作成、 **SalesAmount**列と**TaxAmt**列です。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  列の名前を **Margin**に変更します。  
 
      ![as-lesson5-newmargin](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    Margin 計算列を使用して、各販売の利益率を分析できます。  
  
## <a name="whats-next"></a>次の操作

[レッスン 6: メジャーを作成](../tutorial-tabular-1400/as-lesson-6-create-measures.md)です。
  
  
  
