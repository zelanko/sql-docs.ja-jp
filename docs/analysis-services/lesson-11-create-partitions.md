---
title: "レッスン 11: パーティションの作成 | Microsoft Docs"
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
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# レッスン 11: パーティションの作成
このレッスンでは、パーティションを作成して Internet Sales テーブルをより小さな論理部分に分割し、他のパーティションと分離して処理 (更新) できるようにします。 既定では、モデルに含めるすべてのテーブルにはパーティションが 1 つあり、テーブルのすべての列と行がその中に含まれます。 ここでは、Internet Sales テーブルに含まれる 5 年間のデータを、年ごとのパーティションに分割します。  これにより、各パーティションを個別に処理できるようにします。 詳細については、「[パーティション (SSAS テーブル)](../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
このレッスンの推定所要時間: **15 分**  
  
## 前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「[レッスン 10: 階層の作成](../analysis-services/lesson-10-create-hierarchies.md)」を完了している必要があります。  
  
## パーティションの作成  
  
#### Internet Sales テーブル内にパーティションを作成するには  
  
1.  モデル デザイナーで **[Internet Sales]** テーブルをクリックし、**[テーブル]** メニュー、**[パーティション]** の順にクリックします。  
  
    **[パーティション マネージャー]** ダイアログ ボックスが表示されます。  
  
2.  **[パーティション マネージャー]** ダイアログ ボックスのパーティションの一覧で、**[Internet Sales]** パーティションをクリックします。  
  
3.  **[パーティション名]** で、名前を「**Internet Sales 2010**」に変更します。  
  
    > [!TIP]  
    > 次の手順に進む前に、[テーブルのプレビュー] ウィンドウの列名が、モデル テーブル (チェックされている) に含まれている列を、ソースの列名で表示していることに注意してください。 これは、[テーブルのプレビュー] ウィンドウでは、モデル テーブルからではなく、ソース テーブルから取得された列が表示されるためです。  
  
4.  プレビュー ウィンドウの右上にある **[クエリ エディター]** ボタンを選択します。  
  
    特定の期間内の行だけをパーティションに含めたいので、WHERE 句を含める必要があります。 WHERE 句は、SQL ステートメントによってのみ作成できます。  
  
5.  **[SQL ステートメント]** フィールドで、次のステートメントを貼り付けて既存のステートメントを置き換えます。  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2010-01-01 00:00:00') AND ([OrderDate] < N'2011-01-01 00:00:00'))  
    ```  
  
    このステートメントは、WHERE 句で指定されているように、OrderDate が 2010 年度に該当する行のすべてのデータをパーティションに含めるよう指定しています。  
  
6.  **[検証]** をクリックします。  
  
  
#### 2011 年用のパーティションを作成するには  
  
1.  パーティションの一覧で、先ほど作成した **[Internet Sales 2010]** パーティションをクリックし、**[コピー]** をクリックします。  
  
2.  **[パーティション名]** に「**Internet Sales 2011**」と入力します。  
  
3.  SQL ステートメントで、WHERE 句を次の内容に置き換えて、2011 年の行だけがパーティションに含まれるようにします。  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### 2012 年度のパーティションを作成するには  
  
1.  **[パーティション マネージャー]** ダイアログ ボックスで **[コピー]** をクリックします。  
  
2.  **[パーティション名]** に「**Internet Sales 2012**」と入力します。  
  
3.  SQL ステートメントで、WHERE 句を次の内容に置き換えて、2012 年の行だけがパーティションに含まれるようにします。  
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### 2013 年用のパーティションを作成するには  
  
1.  **[パーティション マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  **[パーティション名]** に「**Internet Sales 2013**」と入力します。  
  
3.  SQL ステートメントで、WHERE 句を次の内容に置き換えて、2013 年の行だけがパーティションに含まれるようにします。  
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### Internet Sales テーブル内に 2014 年用のパーティションを作成するには  
  
1.  **[パーティション マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  **[パーティション名]** に「**Internet Sales 2014**」と入力します。  
  
3.  SQL ステートメントで、WHERE 句を次の内容に置き換えて、2014 年の行だけがパーティションに含まれるようにします。  
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  
  
## パーティションの処理  
**[パーティション マネージャー]** ダイアログ ボックスで、新たに作成した各パーティションのパーティション名の隣にアスタリスク (**\***) が表示されます。 これは、パーティションがまだ処理 (更新) されていないことを示します。 新しいパーティションを作成したら、"パーティションの処理" または "テーブルの処理" 操作を実行して、それらのパーティション内のデータを更新する必要があります。  
  
#### Internet Sales パーティションを処理するには  
  
1.  **[OK]** をクリックし、**[パーティション マネージャー]** ダイアログ ボックスを閉じます。  
  
2.  モデル デザイナーで **[Internet Sales]** テーブルをクリックし、**[モデル]** メニューをクリックした後、**[処理]** (更新) をポイントし、**[パーティションの処理]** をクリックします。  
  
3.  **[パーティションの処理]** ダイアログ ボックスで、**[モード]** が **[既定の処理]** に設定されていることを確認します。  
  
4.  作成した 5 つのパーティションのそれぞれについて、**[処理]** 列のチェック ボックスをオンにし、**[OK]** をクリックします。  
  
    権限借用資格情報の入力を求められた場合は、レッスン 2 の手順 6. で指定した、Windows のユーザー名とパスワードを入力します。  
  
    **[データ処理]** ダイアログ ボックスが表示され、各パーティションのプロセスの詳細が表示されます。 転送される行数はパーティションごとに異なります。 これは、各パーティションに、SQL ステートメントの WHERE 句で指定された年の行が含められるためです。 処理が完了したら、[データ処理] ダイアログ ボックスをクリックします。  
  
  
  
## 次の手順  
このチュートリアルを続行するには、次のレッスン「[レッスン 12: ロールの作成](../analysis-services/lesson-12-create-roles.md)」に進んでください。  
  
  
  
