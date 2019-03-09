---
title: Analysis Services チュートリアル補足のレッスン:詳細行 |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 20f5f32d4cca8b69d94410296e3653a92a1d6d46
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685245"
---
# <a name="supplemental-lesson---detail-rows"></a>補足のレッスン: 詳細行

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

この補足のレッスンでは、カスタム詳細行の式を定義するのに DAX エディターを使用します。 詳細行の式はメジャーの集計された結果の詳細についてをエンドユーザーに提供する、メジャーのプロパティです。 
  
このレッスンを完了するまでに時間を推定するには。**10 分**  
  
## <a name="prerequisites"></a>前提条件  

この補足のレッスンの記事では、表形式モデルのチュートリアルの一部です。 この補足のレッスンの実習を行う前に作成した前のレッスンをすべて完了した Adventure Works Internet Sales サンプル モデル プロジェクトがあるか。  
  
## <a name="whats-the-issue"></a>この問題は何ですか。

詳細行の式を追加する前に、InternetTotalSales メジャーの詳細を見てみましょう。

1.  SSDT で、**モデル**メニュー > **Excel で分析**する Excel を開き、空のピボット テーブルを作成します。
  
2.  **ピボット テーブル フィールド**、追加、 **InternetTotalSales** FactInternetSales テーブルからメジャー**値**、 **CalendarYear**からDimDate テーブル**列**、および**EnglishCountryRegionName**に**行**します。 ピボット テーブルで、リージョンと年ごと InternetTotalSales メジャーから集計結果が、できるようになりました。 

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. ピボット テーブルでは、年およびリージョン名値を集計をダブルクリックします。 ここでは、Australia と 2014 年の値をダブルクリックします。 データが有用でないデータを格納している新しいシートが開きます。

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
今度は、InternetTotalSales メジャーの集計結果に寄与するデータの列と行を含むテーブルを参照してください。 そのためには、メジャーのプロパティとして詳細行の式を追加できます。

## <a name="add-a-detail-rows-expression"></a>詳細行の式を追加します。

#### <a name="to-create-a-detail-rows-expression"></a>詳細行の式を作成するには 
  
1. FactInternetSales テーブルのメジャー グリッドで、クリックして、 **InternetTotalSales**メジャーです。 

2. **プロパティ** > **詳細行式**、DAX エディターを開くエディター ボタンをクリックします。

    ![as-lesson-detail-rows-ellipse](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

3. DAX エディターでは、次の式を入力します。

    ```
    SELECTCOLUMNS(
    FactInternetSales,
    "Sales Order Number", FactInternetSales[SalesOrderNumber],
    "Customer First Name", RELATED(DimCustomer[FirstName]),
    "Customer Last Name", RELATED(DimCustomer[LastName]),
    "City", RELATED(DimGeography[City]),
    "Order Date", FactInternetSales[OrderDate],
    "Internet Total Sales", [InternetTotalSales]
    )

    ```

    この式は、名前、列を指定し、FactInternetSales テーブルと関連テーブルからのメジャーの結果が返されるは、ユーザーがピボット テーブルまたはレポート内での集計の結果をダブルクリックするとします。

4. Excel に戻って、手順 3 で作成したシートを削除し、集計の値をダブルクリックします。 今回は、詳細行の式プロパティにメジャーの定義、新しいシートが開きますより有用なデータを格納しています。

    ![as-lesson-detail-rows-detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. モデルを再デプロイします。

  
## <a name="see-also"></a>関連項目  

[SELECTCOLUMNS 関数 (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[補足のレッスン: 動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[補足のレッスン: 不規則階層](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
