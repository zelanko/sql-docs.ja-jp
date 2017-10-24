---
title: "レッスン 5: リレーションシップの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 096f19dc25973b2d515c6ccfb9961e7b0fe07c21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-4-create-relationships"></a>レッスン 4: リレーションシップを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、リレーションシップ データをインポートしたときに自動的に作成されたことを確認し、異なるテーブル間に新しいリレーションシップを追加します。 リレーションシップとは、2 つのテーブル間を接続し、それらのテーブル内のデータをどのように関連付けるかを決定するものです。 たとえば、DimProduct テーブルと DimProductSubcategory テーブルには、各製品が特定のサブカテゴリに属しているということに基づくリレーションシップがあります。 詳細については、次を参照してください。[リレーションシップ](../analysis-services/tabular-models/relationships-ssas-tabular.md)です。
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 3: 日付テーブルとしてマーク](../analysis-services/lesson-3-mark-as-date-table.md)です。 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>既存のリレーションシップの確認と新しいリレーションシップの追加  
テーブルのインポート ウィザードを使用してデータをインポートしたときに、AdventureWorksDW データベースから 7 つのテーブルを取得します。 通常、リレーショナル ソースからデータをインポートするときに既存のリレーションシップがデータと共に、自動的にインポートします。 ただし、モデルの作成を進める前に、それらのテーブル間リレーションシップが適切に作成されたかどうかを確認する必要があります。 またこのチュートリアルでは、3 つの新しいリレーションシップの追加も行います。  
  
#### <a name="to-review-existing-relationships"></a>既存のリレーションシップを確認するには  
  
1.  クリックして、**モデル**メニュー >**モデル ビュー** > **ダイアグラム ビュー**です。  

    モデル デザイナーがダイアグラム ビューで表示されます。このグラフィカルな形式では、インポートしたすべてのテーブルが、それらを結ぶ線と共に表示されます。 テーブル間の線は、データのインポート時に自動的に作成されたリレーションシップを表します。
    
    ![として-表形式の lesson4-図](../analysis-services/media/as-tabular-lesson4-diagram.png)
  
    モデル デザイナーの右下隅にあるミニマップ コントロールを使用すると、できるだけ多くのテーブルが表示されるようにビューを調整できます。 テーブルをクリックして別の場所にドラッグすれば、テーブルどうし近づけたり、特定の順序に並べたりすることもできます。 テーブルを移動しても、テーブル間の既存のリレーションシップには影響しません。 特定のテーブル内のすべての列を表示するには、テーブルの端をクリックしてドラッグし、大きさを調整します。  
  
2.  間の実線をクリックして、 **DimCustomer**テーブルおよび**DimGeography**テーブル。 これら 2 つのテーブル間の実線は、そのリレーションシップがアクティブであることを示します。つまり、そのリレーションシップは DAX 数式の計算時に既定で使用されます。  
  
    通知、 **GeographyKey**内の列、 **DimCustomer**テーブルおよび**GeographyKey**内の列、 **DimGeography**これで、ボックス内にそれぞれ表示両方のテーブルです。 これは、これらがリレーションシップに使用される列であるということを示しています。 リレーションシップのプロパティが、[ **プロパティ** ] ウィンドウに表示されます。  
  
    > [!TIP]  
    > だけでなく、モデル デザイナーを使用して、ダイアグラム ビューで、表形式ですべてのテーブル間のリレーションシップを表示するのにリレーションシップの管理 ダイアログ ボックスを使用することができます。 右クリック**リレーションシップ**をクリックして、表形式モデル エクスプ ローラー**リレーションシップの管理**です。 リレーションシップの管理 ダイアログ ボックスでは、データのインポート時に自動的に作成されたリレーションシップを示します。  
  
3.  ダイアグラム ビュー、または [リレーションシップの管理] ダイアログ ボックスで、モデル デザイナーを使用して、AdventureWorksDW データベースからインポートされた各テーブルのときに次のリレーションシップが作成されたことを確認します。  
  
    |Active|テーブル|関連する参照テーブル|  
    |----------|---------|------------------------|  
    |はい|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |はい|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |はい|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |はい|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |はい|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    上の表に、リレーションシップのいずれかが存在しない場合は、次のテーブルがモデルに含まれることを確認してください: DimCustomer、DimDate、DimGeography、DimProduct、DimProductCategory、DimProductSubcategory、および FactInternetSales です。 同じデータ ソース接続からのテーブルが複数回インポートされた場合、それらのテーブル間のリレーションシップは作成されず、手動で作成する必要があります。  

### <a name="take-a-closer-look"></a>詳しく見てをみましょう
ダイアグラム ビューでは、矢印、アスタリスク、およびテーブル間のリレーションシップを表示する、行の数がわかります。

![として表形式の lesson4-行](../analysis-services/media/as-tabular-lesson4-line.png)

矢印は、テーブルがリレーションシップの基数の"多"側であり、1 は、このテーブルは、リレーションシップの一方の側を示しています。 このアスタリスク表示フィルターの方向を示しています。 リレーションシップを編集する必要がある場合たとえば、リレーションシップのフィルターの方向またはカーディナリティを変更、リレーションシップの編集 ダイアログを開くのダイアグラム ビューでのリレーションシップの線をダブルクリックします。

![として表形式の lesson4 の編集](../analysis-services/media/as-tabular-lesson4-edit.png)

ほとんどの場合、リレーションシップを編集する必要はありません。 これらの機能は、高度なデータ モデリングのものし、このチュートリアルの範囲外にあります。 詳細については、次を参照してください。[双方向クロス フィルターの SQL Server 2016 Analysis services 表形式モデル](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md)です。

場合によっては、特定のビジネス ロジックをサポートするために、モデル内のテーブル間に追加のリレーションシップを作成する必要があります。 このチュートリアルでは、FactInternetSales テーブルと DimDate テーブルの間の 3 つの追加のリレーションシップを作成する必要があります。  
  
#### <a name="to-add-new-relationships-between-tables"></a>テーブル間に新しいリレーションシップを追加するには  
  
1.  モデル デザイナーでの**FactInternetSales**テーブルをクリックし、保持、 **OrderDate**  列にカーソルをドラッグ、**日付**内の列、 **DimDate**テーブル、および離します。  

    実線が表示されます、アクティブなリレーションシップを作成した、 **OrderDate**内の列、 **Internet Sales**テーブルおよび**日付**内の列**日付**テーブル。 
  
      ![として表形式の lesson4-新しい](../analysis-services/media/as-tabular-lesson4-new.png) 
  
    > [!NOTE]  
    > リレーションシップを作成するときに、主テーブルと関連する参照テーブルの間で基数とフィルターの方向が自動的に選択します。  
  
2.  **FactInternetSales**テーブルをクリックし、保持、 **DueDate**  列にカーソルをドラッグ、**日付**内の列、 **DimDate**テーブル、および離します。  
  
    点線が表示されます、非アクティブなリレーションシップを作成した、 **DueDate**内の列、 **FactInternetSales**テーブルおよび**日付**内の列**DimDate**テーブル。 テーブル間には複数のリレーションシップを設定できますが、一度にアクティブにできるのは 1 つだけです。  
  
3.  最後に、もう 1 つのリレーションシップ; の作成します。**FactInternetSales**テーブルをクリックし、保持、 **ShipDate**  列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、およびを離します。  
    
     ![として-表形式の lesson4-newinactive](../analysis-services/media/as-tabular-lesson4-newinactive.png)
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 5: 計算列の作成](../analysis-services/lesson-5-create-calculated-columns.md)です。
  
  
  

