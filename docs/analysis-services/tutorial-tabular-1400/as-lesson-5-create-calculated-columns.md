---
title: Analysis Services チュートリアル-レッスン 5:計算列の作成 |Microsoft Docs
ms.date: 04/25/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: b56fe07237faa6570fd4b8c1adb31d3cce8e4540
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64776070"
---
# <a name="create-calculated-columns"></a>計算列の作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは計算列を追加することで、モデルのデータを作成します。 (カスタム列) として計算列を作成するデータの取得を使用する場合、クエリ エディターを使用して、またはモデル デザイナーなどの後半で行います。 詳細についてを参照してください。[計算列](../tabular-models/ssas-calculated-columns.md)します。
  
3 つのテーブルでは、5 つの新しい計算列を作成します。 手順は、列を作成、変更して、およびテーブル内のさまざまな場所に配置するいくつかの方法を示す各タスクに少しずつ異なります。  

このレッスンは、Data Analysis Expressions (DAX) を最初に使用してもです。 DAX は、表形式モデルの高度にカスタマイズ可能な数式を作成するための特別な言語です。 このチュートリアルでは、計算列、メジャー、およびロール フィルターを作成するのに DAX を使用します。 詳細についてを参照してください。[テーブル モデルにおける DAX](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)します。 
  
このレッスンを完了するまでに時間を推定するには。**15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 4:リレーションシップの作成](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)です。 
  
## <a name="create-calculated-columns"></a>計算列の作成  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>DimDate テーブルに MonthCalendar 計算列を作成します。  
  
1.  をクリックして、**モデル**メニュー >**モデル ビュー** > **データ ビュー**します。  
  
    計算列は、モデル デザイナーのデータ ビューでのみ作成できます。  
  
2.  モデル デザイナーで、クリックして、 **DimDate**テーブル (タブ)。  
  
3.  右クリックし、 **CalendarQuarter**列ヘッダーをクリックして**列の挿入**します。  
  
    **Calculated Column 1** という新しい列が、 **Calendar Quarter** 列の左側に挿入されます。  
  
4.  テーブルの上、数式バーには、次の DAX 数式を入力します。オート コンプリート、列やテーブルの完全修飾名を入力できるようにし、使用可能な関数を一覧表示します。  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    すべての行の計算列に値が入力されます。 テーブルを下へスクロールする場合は行が行ごとのデータに基づく、この列に別の値を持つことができますを参照してください。    
  
5.  この列の名前を変更**MonthCalendar**します。 

    ![as-lesson5-newcolumn](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
MonthCalendar には、1 か月の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>DimDate テーブルに DayOfWeek 計算列を作成します。  
  
1.  **DimDate**テーブル中、 をクリックして、**列** メニューをクリック**列の追加**します。  
  
2.  数式バーで、次の数式を入力します。  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    数式の構築が完了したら、ENTER キーを押します。 新しい列がテーブルの右端に追加されます。  
  
3.  列の名前を変更**DayOfWeek**します。  
  
4.  列の見出しをクリックし、列の間をドラッグ、 **EnglishDayNameOfWeek**列と**DayNumberOfMonth**列。  
  
    > [!TIP]  
    > テーブル内の列を移動することで、列が参照しやすくなります。  
  
曜日を示すには、週の曜日の並べ替え可能な名前を提供する列が計算されます。  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>DimProduct テーブルに ProductSubcategoryName 計算列を作成します。  
  
  
1.  **DimProduct**テーブル、テーブルの右端までスクロールします。 右端の列がという名前に注意してください。***列の追加***、列見出しをクリックします。  
  
2.  数式バーで、次の数式を入力します。  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  列の名前を変更**ProductSubcategoryName**します。  
  
ProductSubcategoryName 計算列は DimProductSubcategory テーブルの EnglishProductSubcategoryName 列からデータを含んだ DimProduct テーブルの階層を作成するために使用します。 階層は、複数のテーブルにまたがって存在することはできません。 階層は ､ 後ほどレッスン 9 で作成します。  
  
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
  
2.  間に新しい計算列を作成、 **SalesAmount**列と**TaxAmt**列。  
  
3.  数式バーで、次の数式を入力します。  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  列の名前を **Margin**に変更します。  
 
      ![as-lesson5-newmargin](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    Margin 計算列は、各販売の利益率の分析に使用されます。  
  
## <a name="whats-next"></a>次の操作

[レッスン 6:メジャーを作成](../tutorial-tabular-1400/as-lesson-6-create-measures.md)です。
  
  
  
