---
title: 'Analysis Services のチュートリアル レッスン 2: データの取得 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb7c9b19950036baff8dbe4dd52447040cd9a571
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="get-data"></a>データを取得します。

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは使用して**データの取得**AdventureWorksDW サンプル データベースに接続する、データ、プレビューとフィルター選択し、モデル ワークスペースにインポートします。  
  
データの取得を使用すると、さまざまなソースからデータをインポートすることができます。 電源クエリ M 数式を使用してデータをクエリすることができますもまたは[ネイティブ SQL クエリ式](../tabular-models/ssas-import-query.md)です。

> [!NOTE]
> タスクとこのチュートリアルではイメージは、社内設置のサーバー上にある AdventureWorksDW2014 データベースに接続することを示しています。 場合によっては、Azure SQL Data Warehouse 上にある AdventureWorksDW データベースが別のオブジェクトを表示します。ただし、基本的に、同じです。
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 1: 新しいテーブル モデル プロジェクトを作成する](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)です。  
  
## <a name="create-a-connection"></a>接続の作成  
  
#### <a name="to-create-a-connection-to-the-adventureworksdw-database"></a>AdventureWorksDW データベースへの接続を作成するには  
  
1.  **表形式モデル エクスプ ローラー**を右クリックして**データソース** > **データ ソースからのインポート**です。  
  
    これにより、起動**データの取得**、データ ソースへの接続をします。 表形式のモデル エクスプ ローラーが表示されない場合**ソリューション エクスプ ローラー**をダブルクリックして**Model.bim**をデザイナーでモデルを開きます。 
    
    ![as-lesson2-getdata](../tutorial-tabular-1400/media/as-lesson2-getdata.png)
  
2.  データの取り込み でクリックして**データベース** > **SQL Server データベース** > **接続**です。  
  
3.  **SQL Server データベース**ダイアログで、**サーバー**AdventureWorksDW データベースをインストールしたサーバーの名前を入力して、をクリックして**接続**です。  

4.  資格情報の入力を求められたら、インポートおよびデータを処理するときに、データ ソースに接続する Analysis Services を使用して資格情報を指定する必要があります。 **権限借用モード****アカウントを偽装**し、資格情報を入力し、クリックして**接続**です。 アカウントを使用すると、パスワードが無期限をお勧めします。

    ![as-lesson2-account](../tutorial-tabular-1400/media/as-lesson2-account.png)
  
    > [!NOTE]  
    > Windows のユーザー アカウントとパスワードを使用することで、最も安全なデータ ソース接続方法が提供されます。
  
5.  ナビゲーターの選択、 **AdventureWorksDW**データベースをクリックして **[ok]** です。これにより、データベースへの接続が作成されます。 
  
6.  ナビゲーターで、次の表のチェック ボックスをオンにします。 **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および**FactInternetSales**です。  

    ![as-lesson2-select-tables](../tutorial-tabular-1400/media/as-lesson2-select-tables.png)
  
[Ok] をクリックすると、クエリ エディターが開きます。 次のセクションでは、インポートするデータのみを選択します。

  
## <a name="filter-the-table-data"></a>テーブルのデータをフィルター処理します。  

AdventureWorksDW サンプル データベース内のテーブル モデルに含める必要がないデータであります。 可能であれば、フィルター処理する送信不要なデータ モデルで使用されるメモリ内の領域を節約します。 フィルター処理するいくつかのテーブルの列のため、展開した後、ワークスペース データベースまたは model データベースにインポートされません。 
  
#### <a name="to-filter-the-table-data-before-importing"></a>インポートする前に、テーブル データをフィルター処理するには  
  
1.  クエリ エディターで、選択、 **DimCustomer**テーブル。 データ ソース (AdventureWorksDW サンプル データベース) に、DimCustomer テーブルのビューが表示されます。 
  
2.  複数の選択 (ctrl キーを押しながらクリック) **SpanishEducation**、 **FrenchEducation**、 **SpanishOccupation**、 **FrenchOccupation**、し、右クリックし、クリック**列の削除**です。 

    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-columns.png)
  
    これらの列の値はインターネット売上分析と関連がないので、これらの列をインポートする必要はありません。 不要な列を排除することによりモデルをより小さいより効率的です。  

    > [!TIP]
    > ステップを削除することでバックアップすることができます、間違えた場合**適用される手順**です。   
    
    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-step.png)

  
4.  各テーブルで、次の列を削除することで、残りのテーブルをフィルター処理します。  
    
    **DimDate**
    
      |列|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |列|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |列|  
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
  
      |列|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |列|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      列は削除されません。
  
## <a name="Import"></a>Import the selected tables and column data  

プレビューし、不要なデータをフィルター選択したら、残りのようにするデータをインポートできます。 ウィザードでは、テーブル データと、各テーブル間のリレーションシップがインポートされます。 新しいテーブルと列がモデルの作成し、フィルターで除外するデータはインポートできません。  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>選択したテーブルと列のデータのインポートするには  
  
1.  選択内容を確認します。 問題がなければ、をクリックして**インポート**です。 データの処理 ダイアログは、ワークスペース データベースに、データ ソースからインポートされるデータの状態を示しています。
  
    ![as-lesson2-success](../tutorial-tabular-1400/media/as-lesson2-success.png) 
  
2.  **[閉じる]** をクリックします。  

  
## <a name="save-your-model-project"></a>モデル プロジェクトを保存します。  

これが頻繁にモデル プロジェクトを保存する重要です。  
  
#### <a name="to-save-the-model-project"></a>モデル プロジェクトを保存するには  
  
-   Click **[ファイル]** > **[すべてを保存]**」を参照してください。  
  
## <a name="whats-next"></a>次の操作

[レッスン 3: 日付テーブルとしてマークして](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)です。

  
  
