---
title: 'Analysis Services tutorial 補足のレッスン: 詳細行 |Microsoft ドキュメント'
description: Analysis Services チュートリアルでは詳細行の式を作成する方法について説明します。
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 16388c1753671e9b835325535685e1d9324e9b52
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="supplemental-lesson---detail-rows"></a>補足のレッスンでは、詳細行

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

この補足のレッスンでは、カスタム詳細行の式を定義するのに DAX エディターを使用します。 詳細行式は、メジャーをプロパティの詳細については、メジャーの集計結果をエンドユーザーに提供します。 
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  

この補足のレッスン記事は、テーブル モデリング チュートリアルの一部です。 この補足のレッスンでは、タスクを実行する前に作成した前のレッスンをすべて完了した Adventure Works Internet Sales サンプル モデル プロジェクトがあるか。  
  
## <a name="whats-the-issue"></a>問題とは何ですか。

詳細行の式を追加する前に、InternetTotalSales メジャーの詳細を見てみましょう。

1.  SSDT をクリックして、**モデル**メニュー > **Excel で分析**を Excel を開き、空のピボット テーブルを作成します。
  
2.  **ピボット テーブル フィールド**、追加、 **InternetTotalSales**メジャーには、FactInternetSales テーブルから**値**、 **CalendarYear** DimDate テーブルから**列**、および**EnglishCountryRegionName**に**行**です。 ピボット テーブルで、地域および年によって InternetTotalSales メジャーの集計結果できるようになりました。 

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. ピボット テーブルでは、年と地域名の集計値をダブルクリックします。 ここでは、オーストラリアと 2014 年の値をダブルクリックします。 データはいない有用なデータを含む新しいシートが開きます。

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
どのような表示する列と行の InternetTotalSales メジャーの集計の結果に影響を与えるデータを含むテーブルを次に示します。 そのためには、メジャーのプロパティとして詳細行の式を追加できます。

## <a name="add-a-detail-rows-expression"></a>詳細行の式を追加します。

#### <a name="to-create-a-detail-rows-expression"></a>詳細行の式を作成するには 
  
1. FactInternetSales テーブルのメジャー グリッドで、クリックして、 **InternetTotalSales**メジャーです。 

2. **プロパティ** > **詳細行式**、DAX エディターを開く [エディター] をクリックします。

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

    この式は、列の名前を指定して、ユーザーがピボット テーブルまたはレポート内での集計の結果をダブルクリックすると、FactInternetSales テーブルと関連テーブルからメジャーの結果が返されます。

4. 戻る Excel では、手順 3. で作成したシートを削除し、集計値をダブルクリックします。 このとき、メジャーの定義の詳細行の式のプロパティ、新しいシートが開きますよりずっと有用なデータを格納しています。

    ![as-lesson-detail-rows-detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. モデルを再展開します。

  
## <a name="see-also"></a>参照  

[SELECTCOLUMNS 関数 (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[補足のレッスン: 動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[補足のレッスン: 不規則階層](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
