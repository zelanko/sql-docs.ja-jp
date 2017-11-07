---
title: "レッスン 2: データの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f17ae5dc82279056efc825f3d6a8092ea1b7623
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-add-data"></a>レッスン 2: データの追加
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンで AdventureWorksDW SQL サンプル データベースへの接続、データの選択、プレビューし、データをフィルター処理およびモデル ワークスペースにデータをインポートする、SSDT でテーブルのインポート ウィザードを使用します。  
  
テーブルのインポート ウィザードを使用すると、Access、SQL、Oracle、Sybase、Informix、DB2、Teradata など、さまざまなリレーショナル ソースからデータをインポートできます。 それぞれのリレーショナル ソースからデータをインポートする手順は、以下で説明する手順とそれほど変わりません。 ストアド プロシージャを使用してデータを選択することもできます。 データとデータ ソースからインポートすることができますのさまざまな種類のインポートの詳細については、次を参照してください。[データソース](../analysis-services/tabular-models/data-sources-ssas-tabular.md)です。  
  
このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前の「 [レッスン 1: 新しいテーブル モデル プロジェクトの作成](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)」を完了している必要があります。  
  
## <a name="create-a-connection"></a>接続の作成  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2014-database"></a>接続を作成する、AdventureWorksDW2014 データベース  
  
1.  表形式モデル エクスプ ローラーを右クリックして**データソース** > **データ ソースからのインポート**です。  
  
    これは、データ ソースへの接続を設定することを支援するテーブルのインポート ウィザードを起動します。 表形式モデル エクスプ ローラーが表示されない、ダブルクリック**Model.bim**で**ソリューション エクスプ ローラー**をデザイナーでモデルを開きます。 
    
    ![として-表形式の lesson2-データ](../analysis-services/media/as-tabular-lesson2-tme.png) 

    注: 1400 互換性レベルでモデルを作成する場合、テーブルのインポート ウィザードではなく、新しいデータの取得エクスペリエンスが表示されます。 ダイアログ ボックスが表示されます、以下の手順とは少し異なりますが、まだことができますを進めるためにします。 
  
2.  テーブルのインポート ウィザードで [**リレーショナル データベース**、] をクリックして**Microsoft SQL Server** > **次**です。  
  
3.  **[Microsoft SQL Server データベースへの接続]** ページで、 **[接続の表示名]**に「 **Adventure Works DB from SQL**」と入力します。  
  
4.  **サーバー名**、AdventureWorksDW データベースをインストールしたサーバーの名前を入力します。  
  
5.  **データベース名**フィールドで、選択**AdventureWorksDW**、順にクリック**次**です。  
  
    ![として、表形式の lesson2-tiw-名前](../analysis-services/media/as-tabular-lesson2-tiw-name.png)
  
6.  **[権限借用情報]** ページで、データをインポートおよび処理する際、Analysis Services がデータ ソースへの接続のために使用する資格情報を指定する必要があります。 **[特定の Windows ユーザー名とパスワード]** が選択されていることを確認し、 **[ユーザー名]** と **[パスワード]**に Windows のログオン資格情報を入力して、 **[次へ]**をクリックします。  
  
    > [!NOTE]  
    > Windows のユーザー アカウントとパスワードを使用することで、最も安全なデータ ソース接続方法が提供されます。 詳細については、次を参照してください。[偽装](../analysis-services/tabular-models/impersonation-ssas-tabular.md)です。  
  
7.  **[データのインポート方法の選択]** ページで、 **[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認します。 テーブルとビューの一覧から選択するには、 **[次へ]** をクリックして、ソース データベース内のすべてのソース テーブルの一覧を表示します。  
  
8.  **[テーブルとビューの選択]** ページで、 **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および **FactInternetSales**の各テーブルのチェック ボックスをオンにします。  
  
    **[完了]** をクリック **しないでください**。  
  
## <a name="FilterData"></a>Filter the table data  
サンプル データベースからインポートしている DimCustomer テーブルには、元の SQL Server Adventure Works データベースからデータのサブセットが含まれています。 モデルにインポートするときに必要のない、DimCustomer テーブルから列のいくつかの詳細は除外されます。 可能であれば、モデルで使用されるメモリ内の領域を節約するために使用されないデータを抽出します。  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>インポート前のテーブル データにフィルターを適用するには  
  
1.  行を選択、 **DimCustomer**テーブル、およびクリックして**プレビューとフィルター**です。 **[選択したテーブルのプレビュー]** ウィンドウが開き、DimCustomer ソース テーブルのすべての列が表示されます。  
  
2.  次の列の上部にあるチェック ボックスをオフにします。 **SpanishEducation**、 **FrenchEducation**、 **SpanishOccupation**、 **FrenchOccupation**」を参照してください。 

    ![として-表形式の lesson2-tiw のクリア](../analysis-services/media/as-tabular-lesson2-tiw-clear.png)
  
    これらの列の値はインターネット売上分析と関連がないので、これらの列をインポートする必要はありません。 不要な列を排除することはことで、モデルより小さいより効率的です。  
  
3.  他の列がすべてオンになっていることを確認し、 **[OK]**をクリックします。  
  
    単語に注意してください**適用されたフィルター**に表示されるようになりました、**フィルターの詳細**内の列、 **DimCustomer**行ですそのリンクのテキスト説明が表示されます をクリックすると、。適用するフィルター。  
    
    ![として表形式の lesson2-適用のフィルター](../analysis-services/media/as-tabular-lesson2-applied-filters.png)
    
  
4.  各テーブル内の次の列のチェック ボックスをオフにして、残りのテーブルをフィルター処理します。  
    
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
  
      |列|  
      |------------------|  
      |**OrderDateKey**|  
      |**DueDateKey**|  
      |**ShipDateKey**|   
  
## <a name="Import"></a>Import the selected tables and column data  
プレビューし、不要なデータをフィルター選択したら、残りのようにするデータをインポートできます。 ウィザードでは、テーブル データと、各テーブル間のリレーションシップがインポートされます。 新しいテーブルと列がモデルで作成し、除外したデータはインポートされません。  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>選択したテーブルと列のデータのインポートするには  
  
1.  選択内容を確認します。 問題がなければ、をクリックして**完了**です。  
  
    データのインポート中、フェッチされた行数が表示されます。 すべてのデータがインポートされると、成功を示すメッセージが表示されます。  
    
    ![として表形式の lesson2-成功](../analysis-services/media/as-tabular-lesson2-success.png) 
  
    > [!TIP]  
    > インポートしたテーブル間に自動的に作成されたリレーションシップを表示するために、 **[データ準備]** 行で、 **[詳細]**をクリックします。 
  
2.  **[閉じる]**をクリックします。  
  
    ウィザードを閉じるし、モデル デザイナー、インポートされたテーブルに表示されます。 
  
## <a name="save-your-model-project"></a>モデル プロジェクトを保存します。  
これが頻繁にモデル プロジェクトを保存する重要です。  
  
#### <a name="to-save-the-model-project"></a>モデル プロジェクトを保存するには  
  
-   Click **[ファイル]** > **[すべてを保存]**」を参照してください。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 3: 日付テーブルとしてマーク](../analysis-services/lesson-3-mark-as-date-table.md)です。

  
  

