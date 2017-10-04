---
title: "Reporting Services のツリー マップとサンバースト グラフ | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/31/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12307c8f-bca7-4d21-8ad5-0c07d819865b
caps.latest.revision: 17
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 7811cfe9238c92746673fac4fce40a4af44d6dcd
ms.openlocfilehash: b9f7ca16589b2383eaed959c6556f0b2b6c4cf74
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="tree-map-and-sunburst-charts-in-reporting-services"></a>Reporting Services のツリー マップとサンバースト グラフ
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ツリー マップおよびサンバースト視覚エフェクトは、階層データを視覚的に表現する上で非常に効果的です。   このトピックでは、ツリー マップまたはサンバースト グラフを [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートに追加する方法の概要を説明します。 また、使い始めるにあたって役に立つ Adventureworks クエリのサンプルも紹介します。  
  
##  <a name="bkmk_treemap_chart"></a> ツリー マップ グラフ  
 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
  
 ツリー マップ グラフでは、グラフ領域がデータ階層のさまざまなレベルと相対サイズを表す複数の四角形に分割されます。 マップは、幹から次第に小さな枝へと分かれていく、木の枝に似ています。 各四角形は、階層内の次のレベルを表す、より小さな四角形に分割されます。 最上位レベルのツリー マップ四角形は、最も大きな四角形がグラフの左上隅に、最も小さな四角形が右下隅にという並びで順々に配置されます。  四角形内では、次のレベルの四角形が同様に左上から右下へ大きい順に配置されます。  
  
 たとえば、次のサンプル ツリー マップの図では、南西区域が最も大きいし、ドイツが最も小さくなってます。 南西区域内では、ロード バイクがマウンテン バイクよりも大きくなっています。  
  
 ![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-tree-map-chart-and-configure-for-the-sample-adventureworks-data"></a>ツリー マップ グラフを挿入し、Adventureworks のサンプル データに対して構成するには  
   
[!NOTE] レポートにグラフを追加する前に、データ ソースとデータセットを作成します。  サンプル データとサンプル クエリについては、このトピックのセクション「 [AdventureWorks データのサンプル](#bkmk_sample_data) 」を参照してください。  
  
1.  デザイン画面を右クリックし、 **[挿入]**、 **[グラフ]** の順にクリックします。  
  
     ツリー マップ ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") を選択します。  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  グラフの位置の変更およびサイズの変更を行います。   サンプル データを使用する場合は、5 インチ幅のグラフで始めることをお勧めします。  
  
3.  サンプル データから、次のフィールドを追加します。  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**値:** LineTotal<br /><br /> **カテゴリ グループ:** 追加する順序<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> **系列グループ:** TerritoryName|  
  
4.  ツリー マップの全般的な形式に合わせてページ サイズを最適化するには、凡例を下部に配置します。  
  
5.  サブカテゴリと行の合計を表示するツールヒントを追加するには、 **[LineTotal]** を右クリックし、 **[系列のプロパティ]**をクリックします。  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     **[ツールヒント]** プロパティを次のように設定します。  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
     詳細については、「 [系列へのツールヒントの表示 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)の順にクリックします。  
  
6.  既定のグラフ タイトルを "区域別の売上" に変更します。  
  
7.  表示されるラベル値の数は、フォントのサイズ、グラフ領域全体のサイズ、および特定の四角形のサイズにより変わります。  より多くのラベルを表示するには、LineTotal の [ラベル フォント] プロパティを既定の 10 pt から 8 pt に変更します。  
  
  
##  <a name="bkmk_sunburst_chart"></a> サンバースト グラフ  
 ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
 サンバースト チャートでは、階層は一連の円で表現されます。最上位レベルの階層は中心に置かれ、その外側に次に高いレベルの階層から順番にリングとして配置されていきます。  最下位レベルの階層は、最も外側のリングとなります。  
  
 ![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-configure-for-the-sample-adventureworks-data"></a>サンバースト グラフを挿入し、Adventureworks のサンプル データに対して構成するには  
 [!NOTE] レポートにグラフを追加する前に、データ ソースとデータセットを作成します。  サンプル データとサンプル クエリについては、このトピックのセクション「 [AdventureWorks データのサンプル](#bkmk_sample_data) 」を参照してください。  
  
1.  デザイン画面を右クリックし、 **[挿入]**、 **[グラフ]** の順にクリックします。  
  
     サンバースト ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") を選択します。  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  グラフの位置の変更およびサイズの変更を行います。   サンプル データを使用する場合は、5 インチ幅のグラフで始めることをお勧めします。  
  
3.  サンプル データから、次のフィールドを追加します。  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**値:** LineTotal<br /><br /> **カテゴリ グループ:** 追加する順序<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> 3) SalesReasonName<br /><br /> **系列グループ:** TerritoryName|  
  
4.  サンバーストの全般的な形式に合わせてページ サイズを最適化するには、凡例を下部に配置します。  
  
5.  既定のグラフ タイトルを "区域別の売上と販売理由" に変更します。  
  
6.
    |||  
    |-|-|  
    |![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")|サンバーストにラベルとしてカテゴリ グループの値を追加するには、ラベルのプロパティ **[Visible]** を true に設定し、 **[UseValueAsLabel]**を false に設定します。<br /><br /> 表示されるラベル値は、フォントのサイズ、グラフ領域全体のサイズ、および特定の四角形のサイズに影響されます。  より多くのラベルを表示するには、LineTotal の [ラベル フォント] プロパティを既定の 10 pt から 8 pt に変更します。|
  
7.  色の範囲を変更する場合は、グラフの **[パレット]** プロパティを変更します。  
  
  
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
  
##  <a name="bkmk_sample_data"></a> AdventureWorks データのサンプル  
 このセクションでは、サンプル クエリを紹介すると共に、 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]でデータ ソースとデータセットを作成するための基本的な手順について説明します。 レポートにデータ ソースとデータセットが既に存在する場合、このセクションは省略できます。  
  
 クエリでは、Adventureworks の販売注文の詳細なデータを返します。これには販売区域、製品カテゴリ、製品サブカテゴリ、および販売理由のデータが含まれます。  
  
1.  **データの取得**  
  
     このセクションのクエリは、  [Adventure Works 2014 Full Database Backup (Adventure Works 2014: データベースの完全なバックアップ)](https://msftdbprodsamples.codeplex.com/releases/view/125550)からダウンロードできる Adventureworks データベースに基づいています。  
  
     データベースをインストールする方法の詳細については、「 [How to install Adventure Works 2014 Sample Databases.pdf (Adventure Works 2014 のサンプル データベースをインストールする方法)](https://msftdbprodsamples.codeplex.com/releases/view/125550)」を参照してください。  
  
2.  **データ ソースの作成**  
  
    1.  **[レポート データ]** ウィンドウで、 **[データ ソース]** を右クリックし、 **[データ ソースの追加]**をクリックします。  
  
    2.  **[レポートに埋め込まれた接続を使用する]**を選択します。  
  
    3.  **Microsoft SQL Server**の接続の種類を選択します。  
  
    4.  サーバーおよびデータベースへの接続文字列を入力します。次に例を示します。  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2014  
        ```  
  
    5.  **[接続テスト]** ボタンを使用して確認してから、 **[OK]**をクリックすることをお勧めします。  
  
     データセット作成の詳細については、「[データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
3.  **データセットの作成**  
  
    -   **[レポート データ]** ウィンドウで、 **[データセット]** を右クリックし、 **[データセットの追加]**をクリックします。  
  
    -   **[レポートに埋め込まれたデータセットを使用します]**を選択します。  
  
    -   前の手順で作成したデータ ソースを選択します。  
  
    -   **[テキスト]** クエリ タイプを選択し、次のクエリをコピーして **[クエリ:]** ボックスに貼り付けます。  
  
        ```  
        SELECT    Sales.SalesOrderHeader.SalesOrderID, Sales.SalesOrderHeader.OrderDate, Sales.SalesOrderDetail.SalesOrderDetailID, Sales.SalesOrderDetail.ProductID, Sales.SalesOrderDetail.LineTotal,   
                                 Sales.SalesOrderDetail.UnitPrice, Sales.SalesOrderDetail.OrderQty, Production.Product.Name, Production.Product.ProductNumber, Sales.SalesTerritory.TerritoryID, lower(Sales.SalesTerritory.Name) AS TerritoryName,   
                                 Production.ProductSubcategory.Name AS SubcategoryName, Production.ProductCategory.Name AS CategoryName, Sales.SalesReason.SalesReasonID, Sales.SalesReason.Name AS SalesReasonName  
        FROM            Sales.SalesOrderDetail INNER JOIN  
                                 Sales.SalesOrderHeader ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID INNER JOIN  
                                 Production.Product ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID INNER JOIN  
                                 Sales.SalesTerritory ON Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND   
                                 Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID INNER JOIN  
                                 Production.ProductSubcategory ON Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID INNER JOIN  
                                 Production.ProductCategory ON Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID INNER JOIN  
                                 Sales.SalesOrderHeaderSalesReason ON Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID INNER JOIN  
                                 Sales.SalesReason ON Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID  
        ```  
  
    -   **[OK]**をクリックします。  
  
     データセットの作成の詳細については、「[共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)」を参照してください。  
  
  
## <a name="see-also"></a>参照  
 [共有データセット デザイン ビュー (レポート ビルダー)](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [系列へのツールヒントの表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)   
 [チュートリアル: Power BI でのツリー マップ](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)   
 [ツリー マップ: Microsoft Research Data Visualization Apps for Office](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]


