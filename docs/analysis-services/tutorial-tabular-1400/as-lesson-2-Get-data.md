---
title: 'Analysis Services チュートリアル-レッスン 2: データの取得 |Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9adeebfbd3c49761adb816a7d28472a61ffca5cc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007203"
---
# <a name="get-data"></a>データを取得します。

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは使用して**データの取得**AdventureWorksDW サンプル データベースに接続するの データ、プレビューおよびフィルターを選択し、モデル ワークスペースにインポートします。  
  
データの取得を使用すると、さまざまなソースからデータをインポートすることができます。 データは、Power Query M 数式を使用して照会することもできますまたは[ネイティブ SQL クエリ式](../tabular-models/ssas-import-query.md)します。

> [!NOTE]
> このチュートリアルのタスクと画像は、オンプレミス サーバー上の AdventureWorksDW2014 データベースへの接続を表示します。 場合によっては、Azure SQL Data Warehouse では、AdventureWorksDW データベースが別のオブジェクトを表示します。ただし、これらは基本的に、同じです。
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 1: 新しい表形式モデル プロジェクトを作成する](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)します。  
  
## <a name="create-a-connection"></a>接続の作成  
  
#### <a name="to-create-a-connection-to-the-adventureworksdw-database"></a>AdventureWorksDW データベースへの接続を作成するには  
  
1.  **Tabular Model Explorer**を右クリックして**データソース** > **データ ソースからのインポート**します。  
  
    これにより、起動**データの取得**、データ ソースに接続することを説明します。 表形式モデル エクスプ ローラーで表示されない場合**ソリューション エクスプ ローラー**、 をダブルクリックします**Model.bim**をデザイナーでモデルを開きます。 
    
    ![as-lesson2-getdata](../tutorial-tabular-1400/media/as-lesson2-getdata.png)
  
2.  データの取得 をクリックして**データベース** > **SQL Server データベース** > **Connect**します。  
  
3.  **SQL Server データベース**ダイアログで、 **Server**、AdventureWorksDW データベースをインストールしたサーバーの名前を入力し、クリックして**Connect**します。  

4.  資格情報の入力を求められたら、インポート、およびデータを処理する際のデータ ソースに接続する Analysis Services を使用して資格情報を指定する必要があります。 **権限借用モード**を選択します**アカウントを偽装**し、資格情報を入力し、クリックして**Connect**します。 アカウントを使用すると、パスワードが無期限をお勧めします。

    ![as-lesson2-account](../tutorial-tabular-1400/media/as-lesson2-account.png)
  
    > [!NOTE]  
    > Windows のユーザー アカウントとパスワードを使用することで、最も安全なデータ ソース接続方法が提供されます。
  
5.  ナビゲーターで、次のように選択します。、 **AdventureWorksDW**データベースをクリックして**OK**。これは、データベースへの接続を作成します。 
  
6.  ナビゲーターで、次のテーブルのチェック ボックスを選択します: **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および**FactInternetSales**します。  

    ![as-lesson2-select-tables](../tutorial-tabular-1400/media/as-lesson2-select-tables.png)
  
[Ok] をクリックすると、クエリ エディターが開きます。 次のセクションでは、インポートするデータのみを選択します。

  
## <a name="filter-the-table-data"></a>テーブルのデータをフィルター処理します。  

AdventureWorksDW サンプル データベース内のテーブルは、モデルに含める必要のないデータであります。 可能であれば、モデルで使用されるメモリ内の領域を節約する不要なデータを抽出します。 いくつかのテーブルの列のフィルター処理が配置された後、ワークスペース データベースまたは model データベースにインポートされないようにします。 
  
#### <a name="to-filter-the-table-data-before-importing"></a>インポートする前にテーブル データをフィルター処理  
  
1.  クエリ エディターで、選択、 **DimCustomer**テーブル。 データ ソース (AdventureWorksDW サンプル データベース) にある DimCustomer テーブルのビューが表示されます。 
  
2.  複数の選択 (ctrl キーを押しながらクリック) **SpanishEducation**、 **FrenchEducation**、 **SpanishOccupation**、 **FrenchOccupation**、し、右クリックして、をクリックし、**列の削除**します。 

    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-columns.png)
  
    これらの列の値はインターネット売上分析と関連がないので、これらの列をインポートする必要はありません。 不要な列を排除することによりモデルを小さくなりより効率的です。  

    > [!TIP]
    > 設定を間違えた場合の手順を削除することによってバックアップできます**適用される手順**します。   
    
    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-step.png)

  
4.  その他のテーブルをフィルターするには、各テーブルで、次の列を削除します。  
    
    **DimDate**
    
      |[列]|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |[列]|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |[列]|  
      |-----------|  
      |**SpanishProductName**|  
      |**FrenchProductName**|  
      |**FrenchDescription**|  
      |**ChineseDescription**|  
      |**ArabicDescription**|  
      |**HebrewDescription**|  
      |**ThaiDescription**|  
      |**GermanDescription**|  
      |**JapaneseDescription**|  
      |**TurkishDescription**|  
  
    **DimProductCategory**
  
      |[列]|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |[列]|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      列は削除されません。
  
## <a name="Import"></a>Import the selected tables and column data  

プレビューを表示し、不要なデータを除外したするには、データの残りの部分をインポートできます。 ウィザードでは、テーブル データと、各テーブル間のリレーションシップがインポートされます。 新しいテーブルと列がモデルで作成し、除外したデータはインポートされません。  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>選択したテーブルと列のデータのインポートするには  
  
1.  選択内容を確認します。 問題がなければ、クリックして**インポート**します。 データ処理ダイアログには、ワークスペース データベースへのデータ ソースからインポートされるデータの状態が表示されます。
  
    ![as-lesson2-success](../tutorial-tabular-1400/media/as-lesson2-success.png) 
  
2.  **[閉じる]** をクリックします。  

  
## <a name="save-your-model-project"></a>モデル プロジェクトを保存します。  

頻繁にモデル プロジェクトを保存する重要です。  
  
#### <a name="to-save-the-model-project"></a>モデル プロジェクトを保存するには  
  
-   Click **[ファイル]** > **[すべてを保存]**」を参照してください。  
  
## <a name="whats-next"></a>次の操作

[レッスン 3: 日付テーブルとしてマーク](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)します。

  
  
