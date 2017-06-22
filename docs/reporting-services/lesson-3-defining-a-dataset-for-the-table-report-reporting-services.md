---
title: "レッスン 3: テーブル レポート (Reporting Services) のデータセットの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
caps.latest.revision: 53
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce3439962e88c24980615d2f2648b56cc88505fa
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>レッスン 3 : テーブル レポートのデータセットの定義 (Reporting Services)
データ ソースを定義した後、データセットを定義する必要があります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、レポートで使用するデータは *データセット*に格納されます。 データセットには、データ ソースへのポインターと、レポートで使用されるクエリ、および計算フィールドと変数が含まれています。  
  
レポート デザイナーでクエリ デザイナーを使用して、データセットをデザインします。 このチュートリアルでは、 [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースから販売注文情報を取得するクエリを作成します。  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>レポート データ用に Transact-SQL クエリを定義するには  
  
1.  **レポート データ** ペインで、 **[新規作成]**をクリックし、 **[データセット]**をクリックします。 **[データセットのプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[名前]** ボックスに「 **AdventureWorksDataset**」と入力します。  
  
3.  **[レポートに埋め込まれたデータセットを使用します]**をクリックします。  
  
4.  前のレッスンで作成したデータ ソース [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]を選択します。   
5. **[クエリの種類]** として **[テキスト]**を選択します。  
  
6.  **[クエリ]** ボックスに次の Transact-SQL クエリを入力するか、コピーして貼り付けます。  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
7.  (省略可能) **[クエリ デザイナー]** ボタンをクリックします。 クエリは、テキスト ベースのクエリ デザイナーに表示されます。 **[テキストとして編集]**をクリックすると、グラフィカル クエリ デザイナーに切り替えることができます。 クエリの結果を表示するには、クエリ デザイナー ツール バーの実行 ( ![ssrs_querydesigner_run](../reporting-services/media/ssrs-querydesigner-run.png)  ) ボタンをクリックします。  
  
    [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースの 4 つの異なるテーブルの 6 個のフィールドから取得したデータが表示されます。 クエリでは、エイリアスなど Transact-SQL の機能が利用されます。 たとえば、SalesOrderHeader テーブルは *soh*と呼ばれます。  
  
8.  **[OK]** をクリックしてクエリ デザイナーを終了します。  
  
9.  **[OK]** をクリックして **[データセットのプロパティ]** ダイアログ ボックスを閉じます。  
  
    レポート データ ペインに **AdventureWorksDataset** データセットとフィールドが表示されます。  
    ![ssrs_adventureworksdataset](../reporting-services/media/ssrs-adventureworksdataset.png)  
  
## <a name="next-task"></a>次の作業  
これで、レポートのデータを取得するクエリを指定できました。 次に、レポートのレイアウトを作成します。 「[レッスン 4: レポートへのテーブルの追加 (Reporting Services)](../reporting-services/lesson-4-adding-a-table-to-the-report-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[クエリ デザイン ツール &#40;SSRS&#41;](../reporting-services/report-data/query-design-tools-ssrs.md)  
[SQL Server の接続の種類 &#40;SSRS&#41;](../reporting-services/report-data/sql-server-connection-type-ssrs.md)  
[チュートリアル : Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
  


