---
title: "レッスン 11: パーティションの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 189782ffcec1c173f152146dc8f174a70c5b506d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-10-create-partitions"></a>レッスン 10: パーティションを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンではパーティションを作成するより小さな論理部分を処理するのには、FactInternetSales テーブルを分割する (更新) の他のパーティションに依存しません。 既定では、モデルに含めるすべてのテーブルにはパーティションが 1 つあり、テーブルのすべての列と行がその中に含まれます。 FactInternetSales テーブルの年です。 別のデータを分割します。1 つの各パーティション テーブルの 5 年です。 これにより、各パーティションを個別に処理できるようにします。 詳細については、「 [[パーティション]](../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>Prerequisites  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 9: 階層の作成](../analysis-services/lesson-9-create-hierarchies.md)です。  
  
## <a name="create-partitions"></a>パーティションの作成  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>FactInternetSales テーブルでパーティションを作成するには  
  
1.  表形式モデル エクスプ ローラーで、展開**テーブル**を右クリックして**FactInternetSales** > **パーティション**です。  
  
2.  [パーティション マネージャー] ダイアログ ボックスで、**コピー**です。  
  
3.  **パーティション名**、名前を変更**FactInternetSales2010**です。  
  
    > [!TIP]  
    > テーブル プレビュー ウィンドウ内の列名とソースからの列名には、(オン)、モデル テーブルに含まれている列を表示することがわかります。 これは、[テーブルのプレビュー] ウィンドウでは、モデル テーブルからではなく、ソース テーブルから取得された列が表示されるためです。  
  
4.  選択、 **SQL**真上、プレビュー ウィンドウを開くには、SQL ステートメントのエディターの右側にあるボタンをクリックします。  
  
    特定の期間内の行だけをパーティションに含めたいので、WHERE 句を含める必要があります。 WHERE 句は、SQL ステートメントによってのみ作成できます。  
  
5.  **SQL ステートメント**フィールドにコピーして、次のステートメントを貼り付けて既存のステートメントを置き換えます。  
  
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
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>2011 年用のパーティションを作成するには  
  
1.  パーティションの一覧で、 **FactInternetSales2010**で作成したパーティションに分割し、クリックして**コピー**です。  
  
2.  **パーティション名**、型**FactInternetSales2011**です。  
  
3.  SQL ステートメントで、WHERE 句を次の内容に置き換えて、2011 年の行だけがパーティションに含まれるようにします。  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2012-year"></a>2012 年度のパーティションを作成するには  
  
- 次の WHERE 句を使用して、上記の手順に従います。 
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2013-year"></a>2013 年用のパーティションを作成するには  
  
- 次の WHERE 句を使用して、上記の手順に従います。 
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2014-year"></a>2014 年のパーティションを作成するには  
  
- 次の WHERE 句を使用して、上記の手順に従います。 
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  

## <a name="delete-the-factinternetsales-partition"></a>FactInternetSales のパーティションを削除します。
これで、各年のパーティションがある、FactInternetSales パーティションを削除できます。 パーティションを処理するときに、すべてのプロセスを選択するときに、重複ができなくなります。
#### <a name="to-delete-the-factinternetsales-partition"></a>FactInternetSales パーティションを削除するには
-  FactInternetSales パーティションをクリックし、クリックして**削除**です。



## <a name="process-partitions"></a>パーティションの処理  
パーティション マネージャーで、確認、**最終処理**新しいの各列には、これらのパーティションが処理されていないで作成した番組がパーティション分割します。 新しいパーティションを作成したら、"パーティションの処理" または "テーブルの処理" 操作を実行して、それらのパーティション内のデータを更新する必要があります。  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>FactInternetSales パーティションを処理するには  
  
1.  をクリックして**OK**パーティション マネージャー ダイアログ ボックスを閉じます。  
  
2.  クリックして、 **FactInternetSales**テーブルをクリック、**モデル**メニュー >**プロセス** > **パーティションの処理**です。  
  
3.  パーティションの処理 ダイアログ ボックスで、次を確認してください。**モード**に設定されている**既定の処理**です。  
  
4.  作成した 5 つのパーティションのそれぞれについて、 **[処理]** 列のチェック ボックスをオンにし、 **[OK]**をクリックします。  

    ![として-表形式の lesson10--パーティションの処理](../analysis-services/media/as-tabular-lesson10-process-partitions.png)
  
    権限借用の資格情報の入力を求められたら、Windows ユーザー名とレッスン 2 で指定したパスワードを入力します。  
  
    **[データ処理]** ダイアログ ボックスが表示され、各パーティションのプロセスの詳細が表示されます。 転送される行数はパーティションごとに異なります。 これは、各パーティションに、SQL ステートメントの WHERE 句で指定された年の行が含められるためです。 処理が完了したら、[データ処理] ダイアログ ボックスをクリックします。  
  
    ![として-表形式の lesson10-プロセスの完了](../analysis-services/media/as-tabular-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 11: ロールの作成](../analysis-services/lesson-11-create-roles.md)です。 
