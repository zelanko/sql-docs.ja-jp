---
title: 'レッスン 6: 計算列を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
ms.openlocfilehash: b39909acacb29f68b0de49ba2093c9b812510172
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542714"
---
# <a name="lesson-6-create-calculated-columns"></a>レッスン 6: 計算列の作成
  このレッスンでは、計算列を追加して、モデル内に新しいデータを作成します。 計算列は、モデル内の既存のデータに基づいて機能します。 詳細については、「[計算列 (SSAS テーブル)](tabular-models/ssas-calculated-columns.md)」を参照してください。  
  
 3 つのテーブルに 5 つの計算列を新しく作成します｡ 手順は実習ごとに少しずつ異なります。 これは、新しい列を作成したり、それらの名前を変更したり、それらをテーブル内のさまざまな場所へ配置するのには、いくつかの方法があることを示すためです。  
  
 このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「 [レッスン 5: リレーションシップの作成](lesson-4-create-relationships.md)」を完了している必要があります。  
  
## <a name="create-calculated-columns"></a>計算列の作成  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a>Date テーブル内に Month Calendar 計算列を作成する  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントして、 **[データ ビュー]** をクリックします。  
  
     計算列は、モデル デザイナーのデータ ビューでのみ作成できます。  
  
2.  モデル デザイナーで、 **Date** テーブル (タブ) をクリックします。  
  
3.  [ **Calendar Quarter** ] 列を右クリックし、[**列の挿入**] をクリックします。  
  
     **CalculatedColumn1**という名前の新しい列が、 **Calendar Quarter**列の左側に挿入されます。  
  
4.  テーブルの上にある数式バーに、以下の数式を入力します。 AutoComplete は列やテーブルの完全修飾名を入力するのに役立つとともに､使用可能な関数をすべて一覧表示します｡  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
     計算列のすべての行に値が入力されます｡ テーブルを下方向にスクロールすると､この列の各行のデータに基づいて､行にさまざまな値が設定さていることが分かります｡  
  
    > [!NOTE]  
    >  エラーが返された場合は、数式内の列名が、「 [レッスン 3: 列名の変更](rename-columns.md)」で変更した列名と一致していることを確認してください。  
  
5.  この列の名前をに変更 `Month Calendar` します。  
  
 Month Calendar 計算列は、Month の並べ替え可能な名前を提供します。  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a>Date テーブル内に Day of Week 計算列を作成する  
  
1.  **Date** テーブルがアクティブな状態のままで、 **[列]** メニューをクリックし、 **[列の追加]** をクリックします。  
  
     新しい列がテーブルの右端に追加されます。  
  
2.  数式バーに次の式を入力します｡  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
3.  列の名前をに変更 `Day of Week` します。  
  
4.  列見出しをクリックし、列を **Day Name** 列と **Day of Month** 列の間にドラッグします。  
  
    > [!TIP]  
    >  テーブル内の列を移動することで、列が参照しやすくなります。  
  
 Day of Week 計算列では、曜日を表す、並べ替え可能な名前が提供されます。  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a>Product テーブル内に Product Subcategory Name 計算列を作成する  
  
1.  モデル デザイナーで、 **Product** テーブルを選択します。  
  
2.  テーブルの右端までスクロールします。 右端の列名が **Add Column** (斜体) になっています｡この列の見出しをクリックします｡  
  
3.  数式バーに次の式を入力します｡  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
4.  列の名前をに変更 `Product Subcategory Name` します。  
  
 Product Subcategory Name 計算列は、Product テーブル内に、Product Subcategory テーブルの Product Subcategory Name 列のデータを含んだ階層を作成するために使用されます。 階層が複数のテーブルにまたがることはできません｡ 階層の作成は、この後のレッスン 7 で行います。  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a>Product テーブル内に Product Category Name 計算列を作成する  
  
1.  **Product** テーブルがアクティブな状態のままで、 **[列]** メニューをクリックし、 **[列の追加]** をクリックします。  
  
2.  数式バーに次の式を入力します｡  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
3.  列の名前をに変更 `Product Category Name` します。  
  
 Product Category Name 計算列は、Product テーブル内に、Product Category テーブルの Product Category Name 列のデータを含んだ階層を作成するために使用されます。 階層が複数のテーブルにまたがることはできません｡  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a>Internet Sales テーブル内に Margin 計算列を作成する  
  
1.  モデル デザイナーで、 **[Internet Sales]** テーブルを選択します。  
  
2.  新しい列を追加します。  
  
3.  数式バーに次の式を入力します｡  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
4.  列の名前をに変更 `Margin` します。  
  
5.  列を、 **Sales Amount** 列と **Tax Amt** 列の間にドラッグします。  
  
 Margin 計算列は、各 (製品) 行の利益率を分析するために使用されます。  
  
## <a name="next-step"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 7: メジャーの作成](lesson-6-create-measures.md)」に進んでください。  
  
  
