---
title: "SQL Server Reporting Services でのツリー マップとサンバースト グラフ |Microsoft ドキュメント"
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 5e15fa8674a09821becd437e78cfb0bb472e3bc8
ms.openlocfilehash: 50224e926c08951887a6423ab1c95eb7ac23a944
ms.contentlocale: ja-jp
ms.lasthandoff: 10/30/2017

---
# <a name="treemap-and-sunburst-charts-in-reporting-services"></a>Reporting Services でのツリー マップとサンバースト グラフ
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

SQL Server[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ツリーマップおよびサンバースト視覚エフェクトは階層データを視覚的に表すに適しています。 この記事では、ツリー マップまたはサンバースト グラフを追加する方法の概要、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポートします。 アーティクルには、作業を開始するために、クエリの AdventureWorks サンプルも含まれています。  
  
##  <a name="bkmk_treemap_chart"></a>ツリー マップ グラフ  

ツリー マップ グラフでは、さまざまなレベルおよびデータの階層の相対サイズを表す四角形にグラフ領域を除算します。 マップは、幹から次第に小さな枝へと分かれていく、木の枝に似ています。 各四角形は、階層内の次のレベルを表す小さな四角形に分割します。 最上位のツリーマップ四角形は、グラフの右下隅で最も小さな四角形の左上隅の最も大きな四角形で配置されます。  四角形内では、次のレベルの四角形が同様に左上から右下へ大きい順に配置されます。  

たとえば、サンプル ツリーマップの次の図の南西区域が最も大きいと、ドイツが最も小さくなってます。 南西区域内では、ロード バイクがマウンテン バイクよりも大きくなっています。  
 
![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-treemap-chart-and-set-up-the-sample-adventureworks-data"></a>ツリーマップのグラフを挿入し、AdventureWorks のサンプル データを設定するには  
   
> [!NOTE]
> レポートにグラフを追加する前に、データ ソースとデータセットを作成します。  サンプル データとサンプル クエリでは、次を参照してください。 [AdventureWorks データのサンプル](#bkmk_sample_data)です。  
  
1.  デザイン サーフェイスを右クリックし **挿入** > **グラフ**です。 選択、**ツリーマップ**アイコン。

    ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
   
2.  グラフの位置の変更およびサイズの変更を行います。 使用してサンプル データを 5 インチ幅のグラフは、適切な開始します。  
  
3.  サンプル データから、次のフィールドを追加します。  
  
    * **値**: LineTotal
    * **カテゴリ グループ**(次の順序) で。
        1. CategoryName
        2. SubcategoryName
    * **系列グループ**: TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4.  ツリーマップの全般的な形式のページ サイズを最適化するのには、最下位に凡例の位置を設定します。  
  
5.  サブカテゴリと行の合計を表示するツールヒントを追加するを右クリックして**LineTotal**、し、**系列のプロパティ**です。  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     設定、**ツールヒント**プロパティを次の値にします。  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
    詳細については、次を参照してください[系列 &#40; 上のツールヒントの表示。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6.  既定のグラフ タイトルを変更**販売区域ごとの売り上げ高をカテゴリ化される**です。  
  
7.  表示されるラベル値の数は、フォントのサイズ、グラフ領域全体のサイズ、および特定の四角形のサイズにより変わります。 複数のラベルを表示するには、変更、**ラベルのフォント**のプロパティ**LineTotal**に**10 pt**の既定値から**8 pt**です。  
  
  
##  <a name="bkmk_sunburst_chart"></a>サンバースト グラフ  
 
サンバースト チャートでは、階層は一連の円で表されます。 階層の最上位レベルは、センターであり、階層の下位レベルは、センターの外部リング。  最下位レベルの階層は、最も外側のリングとなります。  
  
![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-set-up-the-sample-adventureworks-data"></a>サンバースト グラフを挿入し、AdventureWorks のサンプル データを設定するには  
> [!NOTE] 
> レポートにグラフを追加する前に、データ ソースとデータセットを作成します。 サンプル データとサンプル クエリでは、次を参照してください。 [AdventureWorks データのサンプル](#bkmk_sample_data)です。  
  
1.  デザイン画面を右クリックし、**挿入** > **グラフ**です。 選択、**サンバースト**アイコン。
     
     ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
2.  グラフの位置の変更およびサイズの変更を行います。 使用してサンプル データを 5 インチ幅のグラフは、適切な開始します。  
  
3.  サンプル データから、次のフィールドを追加します。  

    * **値**: LineTotal
    * **カテゴリ グループ**(次の順序) で。
        1. CategoryName
        2. SubcategoryName
        3. SalesReasonName
    * **系列グループ**: TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4.  サンバースト グラフの全般的な形式のページ サイズを最適化するのには、最下位に凡例の位置を設定します。  
  
5.  既定のグラフ タイトルを変更**と販売理由の販売区域ごとの販売分類**です。  
  
6. サンバーストにラベルとしてカテゴリ グループの値を追加するには、ラベルのプロパティを設定**Visible = true**と**UseValueAsLabel = false**です。<br /><br /> 表示されるラベル値は、フォントのサイズ、グラフ領域全体のサイズ、および特定の四角形のサイズに影響されます。  複数のラベルを表示するには、変更、**ラベルのフォント**のプロパティ**LineTotal**に**10 pt**の既定値から**8 pt**です。

    ![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")
  
7.  色の範囲を変更する場合は、グラフの **[パレット]** プロパティを変更します。  
    
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
  
##  <a name="bkmk_sample_data"></a>AdventureWorks のサンプル データ  
 このセクションには、データ ソースとデータセットを作成する基本的な手順と、クエリのサンプルが含まれています。[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]です。 レポートには、データ ソースとデータセットが既に含まれています場合、は、このセクションを省略できます。  
  
 クエリでは、AdventureWorks の販売注文詳細なデータを販売区域、product category、product subcategory、および販売理由のデータを返します。  
  
1.  **データの取得**です。  
  
     このセクションのクエリはこれは、GitHub からダウンロードできる AdventureWorks データベースに基づいて: [AdventureWorks 2016 データベースの完全バックアップ](https://github.com/Microsoft/sql-server-samples/releases)です。  
  
  
2.  **データ ソースを作成**です。  
  
    1.  **レポート データ**を右クリックして**データソース**、し、**データ ソースの追加**です。  
  
    2.  **[レポートに埋め込まれた接続を使用する]**を選択します。  
  
    3.  接続の種類を選択**Microsoft SQL Server**です。  
  
    4.  サーバーおよびデータベースへの接続文字列を入力します。 例:  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2016  
        ```  
  
    5.  接続を確認するには、次のように選択します。、**接続のテスト**ボタンをクリックし、 **OK**です。  
  
     データ ソースの作成の詳細については、次を参照してください[追加データの接続 &#40; を確認してください。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3.  **データセットを作成する**です。  
  
    1. **レポート データ**を右クリックして**データセット**、し、**データセットを追加**です。  
  
    2. **[レポートに埋め込まれたデータセットを使用します]**を選択します。  
  
    3. 作成したデータ ソースを選択します。  
  
    4. 選択、**テキスト**クエリの種類をコピーして貼り付けるには、次のクエリ、**クエリ**テキスト ボックス。  
  
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
  
    5. [ **OK**] を選択します。  
  
     データセットの作成の詳細については、次を参照してください[共有データセットまたは埋め込みデータセット &#40; を作成する。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>参照  
* [共有データセット デザイン ビュー &#40;です。レポート ビルダー&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
* [系列 &#40; にツールヒントを表示します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)
* [Power BI のツリーマップをチュートリアル:](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)
* [ツリー マップ: Microsoft Research Data Visualization Apps for Office](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
<br>  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]


