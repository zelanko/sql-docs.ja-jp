---
title: "レッスン 6: 計算列の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# レッスン 6: 計算列の作成
このレッスンでは、計算列を追加して、モデル内に新しいデータを作成します。 計算列は、モデル内の既存のデータに基づいて機能します。 詳細については、「[計算列 (SSAS テーブル)](../analysis-services/tabular-models/calculated-columns-ssas-tabular.md)」を参照してください。  
  
このレッスンでは、3 つの異なるテーブル内に、5 つの新しい計算列を作成します。 手順は実習ごとに少しずつ異なります。 これは、新しい列を作成したり、それらの名前を変更したり、それらをテーブル内のさまざまな場所へ配置するのには、いくつかの方法があることを示すためです。  
  
このレッスンの推定所要時間: **15 分**  
  
## 前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「[レッスン 5: リレーションシップの作成](../analysis-services/lesson-5-create-relationships.md)」を完了している必要があります。  
  
## 計算列の作成  
  
#### Date テーブル内に Month Calendar 計算列を作成する  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[モデル]** メニューをクリックし、**[モデル ビュー]** をポイントして、**[データ ビュー]** をクリックします。  
  
    計算列は、モデル デザイナーのデータ ビューでのみ作成できます。  
  
2.  モデル デザイナーで、**Date** テーブル (タブ) をクリックします。  
  
3.  **[Calendar Quarter]** 列ヘッダーを右クリックし、**[列の挿入]** をクリックします。  
  
    **Calculated Column 1** という新しい列が、**Calendar Quarter** 列の左側に挿入されます。  
  
4.  テーブルの上にある数式バーに、以下の数式を入力します。 オートコンプリートを利用すると、列やテーブルの完全修飾名を簡単に入力できるだけでなく、使用可能な関数の一覧も表示できます。  
  
    **=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]**  
  
    数式の入力が終了したら、Enter キーを押します。  
  
    すべての行の計算列に値が入力されます。 テーブルを下にスクロールすると、この列の行が、各行のデータに基づいて、異なる値を保持できることがわかります。  
  
    > [!NOTE]  
    > エラーが返された場合は、数式内の列名が、「[レッスン 3: 列名の変更](../analysis-services/lesson-3-rename-columns.md)」で変更した列名と一致していることを確認してください。  
  
5.  この列の名前を **Month Calendar** に変更します。  
  
Month Calendar 計算列は、Month の並べ替え可能な名前を提供します。  
  
#### Date テーブル内に Day of Week 計算列を作成する  
  
1.  **Date** テーブルがアクティブな状態のままで、**[列]** メニューをクリックし、**[列の追加]** をクリックします。  
  
2.  数式バーで、次の数式を入力します。  
  
    **=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]**  
  
    数式の入力が終了したら、Enter キーを押します。 新しい列がテーブルの右端に追加されます。  
  
3.  列の名前を **Day of Week** に変更します。  
  
4.  列見出しをクリックし、列を **Day Name** 列と **Day of Month** 列の間にドラッグします。  
  
    > [!TIP]  
    > テーブル内の列を移動することで、列が参照しやすくなります。  
  
Day of Week 計算列では、曜日を表す、並べ替え可能な名前が提供されます。  
  
#### Product テーブル内に Product Subcategory Name 計算列を作成する  
  
1.  モデル デザイナーで、**Product** テーブルを選択します。  
  
2.  テーブルの右端までスクロールします。 右端にある **Add Column** (斜体) という列の列見出しをクリックします。  
  
3.  数式バーで、次の数式を入力します。  
  
    **=RELATED('Product Subcategory'[Product Subcategory Name])**  
  
    数式の入力が終了したら、Enter キーを押します。  
  
4.  列の名前を **Product Subcategory Name** に変更します。  
  
Product Subcategory Name 計算列は、Product テーブル内に、Product Subcategory テーブルの Product Subcategory Name 列のデータを含んだ階層を作成するために使用されます。 階層は、複数のテーブルにまたがって存在することはできません。 階層の作成は、この後のレッスン 7 で行います。  
  
#### Product テーブル内に Product Category Name 計算列を作成する  
  
1.  **Product** テーブルがアクティブな状態のままで、**[列]** メニューをクリックし、**[列の追加]** をクリックします。  
  
2.  数式バーで、次の数式を入力します。  
  
    **=RELATED('Product Category'[Product Category Name])**  
  
    数式の入力が終了したら、Enter キーを押します。  
  
3.  列の名前を **Product Category Name** に変更します。  
  
Product Category Name 計算列は、Product テーブル内に、Product Category テーブルの Product Category Name 列のデータを含んだ階層を作成するために使用されます。 階層は、複数のテーブルにまたがって存在することはできません。  
  
#### Internet Sales テーブル内に Margin 計算列を作成する  
  
1.  モデル デザイナーで、**[Internet Sales]** テーブルを選択します。  
  
2.  新しい列を追加します。  
  
3.  数式バーで、次の数式を入力します。  
  
    **=[Sales Amount]-[Total Product Cost]**  
  
    数式の入力が終了したら、Enter キーを押します。  
  
4.  列の名前を **Margin** に変更します。  
  
5.  列を、**Sales Amount** 列と **Tax Amt** 列の間にドラッグします。  
  
Margin 計算列は、各 (製品) 行の利益率を分析するために使用されます。  
  
## 次の手順  
このチュートリアルを続行するには、次のレッスン「[レッスン 7: メジャーの作成](../analysis-services/lesson-7-create-measures.md)」に進んでください。  
  
  
  
