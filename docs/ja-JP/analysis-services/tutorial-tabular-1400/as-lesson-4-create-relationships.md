---
title: 'Analysis Services のチュートリアル レッスン 4: リレーションシップの作成 |Microsoft ドキュメント'
description: Analysis Services tutorial プロジェクトのリレーションシップを作成する方法について説明します。
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
ms.openlocfilehash: 14bba10123ab1161b336934286e38a32fb351bf5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-relationships"></a>リレーションシップの作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、リレーションシップ データをインポートしたときに自動的に作成されたことを確認し、異なるテーブル間に新しいリレーションシップを追加します。 リレーションシップとは、2 つのテーブル間を接続し、それらのテーブル内のデータをどのように関連付けるかを決定するものです。 たとえば、DimProduct テーブルと DimProductSubcategory テーブルには、各製品が特定のサブカテゴリに属しているということに基づくリレーションシップがあります。 詳細については、次を参照してください。[リレーションシップ](../tabular-models/relationships-ssas-tabular.md)です。
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 3: 日付テーブルとしてマーク](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)です。 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>既存のリレーションシップの確認と新しいリレーションシップの追加  

データの取得を使用してデータをインポートしたときに、AdventureWorksDW データベースから 7 つのテーブルを取得します。 通常、リレーショナル ソースからデータをインポートするときに既存のリレーションシップがデータと共に、自動的にインポートします。 データ モデルでリレーションシップを自動的に作成するには、データの取得のためには、必要がありますのリレーションシップで、データ ソースのテーブル間。

モデル作成を続行する前に、これらのテーブル間のリレーションシップを確認が正しく作成されました。 このチュートリアルでは、次の 3 つの新しいリレーションシップの追加もできます。  

  
#### <a name="to-review-existing-relationships"></a>既存のリレーションシップを確認するには  
  
1.  クリックして、**モデル**メニュー >**モデル ビュー** > **ダイアグラム ビュー**です。  

    モデル デザイナーはダイアグラム ビューに表示されるようすべてのテーブルを表示するグラフィカルな形式をインポートしたそれらを結ぶ線でします。 テーブル間の線は、データのインポート時に自動的に作成されたリレーションシップを表します。
    
    ![as-lesson4-diagram](../tutorial-tabular-1400/media/as-lesson4-diagram.png)
  
    > [!NOTE]
    > テーブル間のリレーションシップが表示されない場合は、データ ソースでこれらのテーブル間にリレーションシップがない可能性があることを意味します。

    モデル デザイナーの右下隅にあるミニマップ コントロールを使用して、多くの可能なテーブルとして含まれます。 テーブルをクリックして別の場所にドラッグすれば、テーブルどうし近づけたり、特定の順序に並べたりすることもできます。 テーブルの移動は、テーブル間のリレーションシップには影響しません。 を、特定テーブル内のすべての列を表示するには をクリックし、テーブルの端を展開または小さくドラッグします。  
  
2.  間の実線をクリックして、 **DimCustomer**テーブルおよび**DimGeography**テーブル。 これら 2 つのテーブル間の実線では、このリレーションシップがアクティブでは、DAX の数式を計算するときに既定で使用されることを示します。  
  
    通知、 **GeographyKey**内の列、 **DimCustomer**テーブルおよび**GeographyKey**内の列、 **DimGeography**これで、ボックス内にそれぞれ表示両方のテーブルです。 これらの列はリレーションシップで使用されます。 リレーションシップのプロパティが、**[プロパティ]** ウィンドウに表示されます。  
  
    > [!TIP]  
    > リレーションシップの管理 ダイアログ ボックスを使用して、表形式ですべてのテーブル間のリレーションシップを表示することができますも。 表形式モデル エクスプ ローラーを右クリックして**リレーションシップ** > **リレーションシップの管理**です。
  
3.  ときに次のリレーションシップが作成されたことを確認、AdventureWorksDW データベースからインポートされた各テーブル。  
  
    |Active|テーブル|関連する参照テーブル|  
    |----------|---------|------------------------|  
    |はい|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |はい|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |はい|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |はい|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |はい|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    リレーションシップのいずれかが存在しない場合は、モデルには、次の表が含まれることを確認します。 DimCustomer、DimDate、DimGeography、DimProduct、DimProductCategory、DimProductSubcategory、および FactInternetSales です。 別の時刻、間のリレーションシップで、同じデータ ソース接続のテーブルがインポートされた場合は、それらのテーブルは作成されず、手動で作成する必要があります。 リレーションシップが表示されない場合は、データ ソースにリレーションシップがないを意味します。 その操作は、データ モデルで手動で作成できます。

### <a name="take-a-closer-look"></a>詳しく見てをみましょう

ダイアグラム ビューで、矢印、アスタリスク、およびテーブル間のリレーションシップを表示する、行の番号を確認します。

![as-lesson4-line](../tutorial-tabular-1400/media/as-lesson4-line.png)

矢印は、フィルターの方向を示しています。 このテーブルは、アスタリスクを示しています、*多く*このテーブルはリレーションシップの基数、および 1 つの辺を示しています、 *1*リレーションシップの側です。 リレーションシップを編集する必要がある場合たとえば、リレーションシップのフィルターの方向またはカーディナリティを変更、リレーションシップの編集 ダイアログを開くのリレーションシップの線をダブルクリックします。

![as-lesson4-edit](../tutorial-tabular-1400/media/as-lesson4-edit.png)

これらの機能は、高度なデータ モデリングのものし、このチュートリアルの範囲外にあります。 詳細については、次を参照してください。[双方向クロス フィルターの Analysis services 表形式モデル](../tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md)です。

場合によっては、特定のビジネス ロジックをサポートするために、モデル内のテーブル間に追加のリレーションシップを作成する必要があります。 このチュートリアルでは、FactInternetSales テーブルと DimDate テーブルの間の 3 つの追加のリレーションシップを作成する必要があります。  
  
#### <a name="to-add-new-relationships-between-tables"></a>テーブル間に新しいリレーションシップを追加するには  
  
1.  モデル デザイナーでの**FactInternetSales**の表をクリックし、保持、 **OrderDate**列にカーソルをドラッグ、**日付**内の列、 **DimDate**テーブル、および離します。  

    実線が表示されます、アクティブなリレーションシップを作成した、 **OrderDate**内の列、 **Internet Sales**テーブル、および**日付**内の列、**日付**テーブル。 
  
      ![as-lesson4-new](../tutorial-tabular-1400/media/as-lesson4-new.png) 
  
    > [!NOTE]  
    > リレーションシップを作成するときに、主テーブルと関連する参照テーブルの間で基数とフィルターの方向が自動的に選択します。  
  
2.  **FactInternetSales**テーブルをクリックし、保持、 **DueDate**  列にカーソルをドラッグ、**日付**内の列、 **DimDate**テーブル、および離します。  
  
    点線が表示されます、非アクティブなリレーションシップを作成した、 **DueDate**内の列、 **FactInternetSales**テーブル、および**日付**内の列、 **DimDate**テーブル。 テーブル間には複数のリレーションシップを設定できますが、一度にアクティブにできるのは 1 つだけです。 非アクティブなリレーションシップは、集計を実行する特別なカスタムの DAX 式で有効にすることができます。  
  
3.  最後に、もう 1 つリレーションシップを作成します。 **FactInternetSales**テーブルをクリックし、保持、 **ShipDate**  列にカーソルをドラッグ、**日付**内の列、 **DimDate**テーブル、および離します。  
    
     ![as-lesson4-newinactive](../tutorial-tabular-1400/media/as-lesson4-newinactive.png)
  
## <a name="whats-next"></a>次の操作

[レッスン 5: 計算列を作成](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)です。
  
  
  
