---
title: 'レッスン 10: パーティションの作成 |Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d43432a53eb2321c3707f4034e244752a5c368ba
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468670"
---
# <a name="lesson-10-create-partitions"></a>レッスン 10: パーティションの作成
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンではパーティションを作成するより小さな論理部分を処理できる、FactInternetSales テーブルに分割 (更新) 他のパーティションに依存しません。 既定では、すべてのテーブル モデルに含めることは、すべてのテーブルの列と行が含まれる 1 つのパーティションを持っています。 FactInternetSales テーブルで年間でデータを分割します。各テーブルの 5 年間の 1 つのパーティション。 これにより、各パーティションを個別に処理できるようにします。 詳細については、「 [[パーティション]](../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
このレッスンを完了するまでに時間を推定するには。**15 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 9:階層を作成する](../analysis-services/lesson-9-create-hierarchies.md)します。  
  
## <a name="create-partitions"></a>パーティションの作成  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>FactInternetSales テーブルにパーティションを作成するには  
  
1.  表形式モデル エクスプ ローラーで**テーブル**、右クリックして**FactInternetSales** > **パーティション**します。  
  
2.  [パーティション マネージャー] ダイアログ ボックスで、**コピー**します。  
  
3.  **パーティション名**、名を変更して**FactInternetSales2010**します。  
  
    > [!TIP]  
    > テーブル プレビュー ウィンドウ内の列名を元の列名には、(オン)、モデル テーブルに含まれる列を表示することがわかります。 これは、[テーブルのプレビュー] ウィンドウでは、モデル テーブルからではなく、ソース テーブルから取得された列が表示されるためです。  
  
4.  選択、 **SQL**すぐ上の SQL ステートメントのエディターを開く、プレビュー ウィンドウの右側にあるボタンをクリックします。  
  
    特定の期間内の行だけをパーティションに含めたいので、WHERE 句を含める必要があります。 WHERE 句は、SQL ステートメントによってのみ作成できます。  
  
5.  **SQL ステートメント**フィールドにコピーして、次のステートメントを貼り付けて既存のステートメントに置き換えます。  
  
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
  
1.  パーティション一覧で、 **FactInternetSales2010**で作成した、パーティション分割し、**コピー**します。  
  
2.  **パーティション名**、型**FactInternetSales2011**します。  
  
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

## <a name="delete-the-factinternetsales-partition"></a>FactInternetSales パーティションを削除します。
各年のパーティションをしたら FactInternetSales パーティションを削除できます。 これにより、パーティションを処理するときに、すべてのプロセスを選択するときに、重複をできないようにします。
#### <a name="to-delete-the-factinternetsales-partition"></a>FactInternetSales パーティションを削除するには
-  FactInternetSales パーティションをクリックし、クリックして**削除**します。



## <a name="process-partitions"></a>パーティションの処理  
Partition manager での**Last Processed**新しいの各列には、これらのパーティションが処理されたことで作成した番組がパーティション分割します。 新しいパーティションを作成したら、"パーティションの処理" または "テーブルの処理" 操作を実行して、それらのパーティション内のデータを更新する必要があります。  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>FactInternetSales パーティションを処理するには  
  
1.  クリックして**OK**パーティション マネージャー ダイアログ ボックスを閉じます。  
  
2.  をクリックして、 **FactInternetSales**テーブルををクリックし、**モデル**メニュー >**プロセス** > **パーティションの処理**します。  
  
3.  パーティションの処理 ダイアログ ボックスで、次のように確認します。**モード**に設定されている**既定の処理**します。  
  
4.  作成した 5 つのパーティションのそれぞれについて、 **[処理]** 列のチェック ボックスをオンにし、 **[OK]** をクリックします。  

    ![として-テーブル-lesson10--パーティションの処理](../analysis-services/media/as-tabular-lesson10-process-partitions.png)
  
    権限借用の資格情報を求められたらは、Windows ユーザー名とレッスン 2 で指定したパスワードを入力します。  
  
    **[データ処理]** ダイアログ ボックスが表示され、各パーティションのプロセスの詳細が表示されます。 転送される行数はパーティションごとに異なります。 これは、各パーティションに、SQL ステートメントの WHERE 句で指定された年の行が含められるためです。 処理が完了したら、[データ処理] ダイアログ ボックスをクリックします。  
  
    ![as-tabular-lesson10-process-complete](../analysis-services/media/as-tabular-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>次の操作
次のレッスンに移動します。[レッスン 11:ロールを作成](../analysis-services/lesson-11-create-roles.md)です。 
