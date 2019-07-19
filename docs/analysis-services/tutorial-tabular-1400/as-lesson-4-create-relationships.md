---
title: Analysis Services チュートリアル-レッスン 4:リレーションシップの作成 |Microsoft Docs
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
ms.openlocfilehash: 7f593dafc1a734cd5f3a0c9fde4f47987f0b92af
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207412"
---
# <a name="create-relationships"></a>リレーションシップの作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、リレーションシップ、データのインポート時に自動的に作成されたことを確認し、異なるテーブル間に新しいリレーションシップを追加します。 リレーションシップとは、2 つのテーブル間を接続し、それらのテーブル内のデータをどのように関連付けるかを決定するものです。 たとえば、DimProduct テーブルと DimProductSubcategory テーブルには、各製品が特定のサブカテゴリに属しているということに基づくリレーションシップがあります。 詳細についてを参照してください。[リレーションシップ](../tabular-models/relationships-ssas-tabular.md)します。
  
このレッスンを完了するまでに時間を推定するには。**10 分**  
  
## <a name="prerequisites"></a>必須コンポーネント  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 3:日付テーブルとしてマーク](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)します。 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>既存のリレーションシップの確認と新しいリレーションシップの追加  

データをインポートするには、データの取得を使用して、AdventureWorksDW データベースから 7 つのテーブルがあります。 一般に、リレーショナル ソースからデータをインポートするときに既存のリレーションシップがデータと共に自動的にインポートします。 データ モデルでリレーションシップを自動的に作成するには、データの取得のためには、リレーションシップ間ありますデータ ソースのテーブル。

テーブル間のリレーションシップを確認する必要があります、モデルのオーサリングを続行する前に正しく作成されました。 このチュートリアルでは、3 つの新しいリレーションシップも追加します。  

  
#### <a name="to-review-existing-relationships"></a>既存のリレーションシップを確認するには  
  
1.  をクリックして、**モデル**メニュー >**モデル ビュー** > **ダイアグラム ビュー**します。  

    モデル デザイナーがダイアグラム ビューで表示されます、すべてのテーブルを表示するグラフィカルな形式をインポートしたでそれらを結ぶ線。 テーブル間の線は、データのインポート時に自動的に作成されたリレーションシップを表します。
    
    ![as-lesson4-diagram](../tutorial-tabular-1400/media/as-lesson4-diagram.png)
  
    > [!NOTE]
    > テーブル間のリレーションシップが表示されない場合は、データ ソースでこれらのテーブル間のリレーションシップがない場合意味します。

    モデル デザイナーの右上隅にあるミニマップ コントロールを使用して、多くの可能なテーブルが含まれます。 テーブルをクリックして別の場所にドラッグすれば、テーブルどうし近づけたり、特定の順序に並べたりすることもできます。 テーブルを移動しても、テーブル間のリレーションシップには影響しません。 特定のテーブル内のすべての列を表示するには、] をクリックし、[して縮小または展開する、テーブルの端にドラッグします。  
  
2.  間の実線をクリックして、 **DimCustomer**テーブルおよび**DimGeography**テーブル。 これら 2 つのテーブル間の実線は、このリレーションシップがアクティブ、つまり、DAX の数式を計算するときに既定で使用されては示しています。  
  
    通知、 **GeographyKey**内の列、 **DimCustomer**テーブルおよび**GeographyKey**内の列、 **DimGeography**テーブル両方のようになりましたボックス内に表示されます。 これらの列はリレーションシップで使用されます。 リレーションシップのプロパティに表示されます、**プロパティ**ウィンドウ。  
  
    > [!TIP]  
    > 表形式ですべてのテーブル間のリレーションシップを表示するのにリレーションシップの管理 ダイアログ ボックスを使用することもできます。 表形式モデル エクスプ ローラーで右クリック**リレーションシップ** > **リレーションシップの管理**します。
  
3.  際に、次のリレーションシップが作成されたことを確認、AdventureWorksDW データベースからインポートされた各テーブル。  
  
    |Active|テーブル|関連する参照テーブル|  
    |----------|---------|------------------------|  
    |[はい]|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |[はい]|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |はい|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |[はい]|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |はい|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    リレーションシップのいずれかが存在しない場合は、モデルには、次の表が含まれることを確認します。DimCustomer、DimDate、DimGeography、DimProduct、DimProductCategory、DimProductSubcategory、および FactInternetSales します。 同じデータ ソース接続のテーブルが別々 の間のリレーションシップ時期にインポートされた場合、それらのテーブルは作成されず、手動で作成する必要があります。 リレーションシップが表示されない場合がデータ ソースに関係がないことを意味します。 その操作は、データ モデルに手動で作成できます。

### <a name="take-a-closer-look"></a>詳しく見てください。

ダイアグラム ビューで、矢印、アスタリスク、およびテーブル間のリレーションシップを示す行番号に注意してください。

![as-lesson4-line](../tutorial-tabular-1400/media/as-lesson4-line.png)

矢印は、フィルターの方向を示しています。 このテーブルは、アスタリスクを示しています、*多く*このテーブルはリレーションシップのカーディナリティと 1 つの側面を示しています、 *1 つ*リレーションシップの側です。 リレーションシップを編集する必要がある場合たとえば、リレーションシップのフィルターの方向やカーディナリティの変更、リレーションシップの編集 ダイアログを開きますリレーションシップの線をダブルクリックします。

![as-lesson4-edit](../tutorial-tabular-1400/media/as-lesson4-edit.png)

これらの機能は高度なデータ モデリングのためのものし、このチュートリアルの範囲外です。 詳細についてを参照してください。[双方向で Analysis Services 表形式モデルのクロス フィルター](../tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md)します。

場合によっては、特定のビジネス ロジックをサポートするために、モデル内のテーブル間に追加のリレーションシップを作成する必要があります。 このチュートリアルでは、FactInternetSales テーブルと DimDate テーブルの間の 3 つの追加のリレーションシップを作成する必要があります。  
  
#### <a name="to-add-new-relationships-between-tables"></a>テーブル間に新しいリレーションシップを追加するには  
  
1.  モデル デザイナーでの**FactInternetSales**テーブルをクリックして、保持、 **OrderDate**列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、および離します。  

    間のアクティブなリレーションシップを作成したを示す実線が表示されます、 **OrderDate**内の列、 **Internet Sales**テーブル、および**日付**内の列**日付**テーブル。 
  
      ![as-lesson4-new](../tutorial-tabular-1400/media/as-lesson4-new.png) 
  
    > [!NOTE]  
    > リレーションシップを作成するときに、主テーブルと関連する参照テーブルの間のカーディナリティとフィルターの方向が自動的に選択します。  
  
2.  **FactInternetSales**テーブルをクリックし、保持、 **DueDate**  列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、および離します。  
  
    間の非アクティブなリレーションシップを作成したを示す点線が表示されます、 **DueDate**内の列、 **FactInternetSales**テーブル、および**日付**内の列**DimDate**テーブル。 テーブル間には複数のリレーションシップを設定できますが、一度にアクティブにできるのは 1 つだけです。 カスタムの DAX 式で特別な集計を実行するアクティブ、非アクティブなリレーションシップを作成できます。  
  
3.  最後に、もう 1 つリレーションシップを作成します。 **FactInternetSales**テーブルをクリックし、保持、 **ShipDate**  列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、および離します。  
    
     ![as-lesson4-newinactive](../tutorial-tabular-1400/media/as-lesson4-newinactive.png)
  
## <a name="whats-next"></a>次の操作

[レッスン 5: 計算列を作成](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)です。
  
  
  
