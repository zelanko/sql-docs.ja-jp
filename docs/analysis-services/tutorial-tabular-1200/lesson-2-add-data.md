---
title: レッスン 2:データの追加 |Microsoft Docs
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e5a4d0ec80da5c29d513e74df1becca2d5cbb84
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404874"
---
# <a name="lesson-2-add-data"></a>レッスン 2:データを追加する
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、AdventureWorksDW SQL サンプル データベースに接続、データを選択、プレビューと、データをフィルター処理をモデル ワークスペース データをインポートして SSDT でテーブルのインポート ウィザードを使用します。  
  
テーブルのインポート ウィザードを使用すると、さまざまなリレーショナル ソースからデータをインポートできます。アクセス、SQL、Oracle、Sybase、Informix、DB2、Teradata、および詳細。 それぞれのリレーショナル ソースからデータをインポートする手順は、以下で説明する手順とそれほど変わりません。 ストアド プロシージャを使用してデータを選択することもできます。 データとデータのソースからインポートすることのさまざまな種類のインポートの詳細については、次を参照してください。[データソース](../tabular-models/data-sources-supported-ssas-tabular.md)します。  
  
このレッスンを完了するまでに時間を推定するには。**20 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 1:新しいテーブル モデル プロジェクト作成](lesson-1-create-a-new-tabular-model-project.md)です。  
  
## <a name="create-a-connection"></a>接続の作成  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2014-database"></a>接続を作成する、AdventureWorksDW2014 データベース  
  
1.  表形式モデル エクスプ ローラーで右クリック**データソース** > **データ ソースからのインポート**します。  
  
    これにより、データ ソースへの接続を設定することを支援するテーブルのインポート ウィザードが起動します。 表形式モデル エクスプ ローラーが表示されない、ダブルクリック**Model.bim**で**ソリューション エクスプ ローラー**をデザイナーでモデルを開きます。 
    
    ![as-tabular-lesson2-tme](media/as-tabular-lesson2-tme.png) 

    注:1400 互換性レベル モデルを作成する場合は、テーブルのインポート ウィザードではなく新しい Get Data エクスペリエンスを確認します。 ダイアログ ボックスが表示されます、次の手順とは少し異なりますが、先に進むにことができますをします。 
  
2.  テーブルのインポート ウィザードで [**リレーショナル データベース**、] をクリックして**Microsoft SQL Server** > **次**します。  
  
3.  **[Microsoft SQL Server データベースへの接続]** ページで、 **[接続の表示名]** に「 **Adventure Works DB from SQL**」と入力します。  
  
4.  **サーバー名**、AdventureWorksDW データベースをインストールしたサーバーの名前を入力します。  
  
5.  **データベース名**フィールドで、 **AdventureWorksDW**、順にクリックします**次**します。  
  
    ![as-tabular-lesson2-tiw-name](media/as-tabular-lesson2-tiw-name.png)
  
6.  **[権限借用情報]** ページで、データをインポートおよび処理する際、Analysis Services がデータ ソースへの接続のために使用する資格情報を指定する必要があります。 **[特定の Windows ユーザー名とパスワード]** が選択されていることを確認し、 **[ユーザー名]** と **[パスワード]** に Windows のログオン資格情報を入力して、 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    > Windows のユーザー アカウントとパスワードを使用することで、最も安全なデータ ソース接続方法が提供されます。 詳細については、次を参照してください。[偽装](../tabular-models/impersonation-ssas-tabular.md)します。  
  
7.  **[データのインポート方法の選択]** ページで、 **[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認します。 テーブルとビューの一覧から選択するには、 **[次へ]** をクリックして、ソース データベース内のすべてのソース テーブルの一覧を表示します。  
  
8.  **テーブルおよびビュー**ページで、次のテーブルのチェック ボックスを選択します。**DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および**FactInternetSales**します。  
  
    **[完了]** をクリック **しないでください**。  
  
## <a name="FilterData"></a>Filter the table data  
サンプル データベースからインポートする DimCustomer テーブルには、元の SQL Server Adventure Works データベースからデータのサブセットが含まれています。 モデルにインポートするときに必要のない、DimCustomer テーブルの列のいくつかの詳細は除外されます。 可能であれば、モデルで使用されるメモリ内の領域を節約するために使用されないデータを抽出します。  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>インポート前のテーブル データにフィルターを適用するには  
  
1.  行を選択、 **DimCustomer**テーブル、およびクリックして**プレビューとフィルター**します。 **[選択したテーブルのプレビュー]** ウィンドウが開き、DimCustomer ソース テーブルのすべての列が表示されます。  
  
2.  次の列の上部にあるチェック ボックスをオフにします。**SpanishEducation**、 **FrenchEducation**、 **SpanishOccupation**、 **FrenchOccupation**します。 

    ![as-tabular-lesson2-tiw-clear](media/as-tabular-lesson2-tiw-clear.png)
  
    これらの列の値はインターネット売上分析と関連がないので、これらの列をインポートする必要はありません。 小さくなりより効率的に不要な列を排除モデルになります。  
  
3.  他の列がすべてオンになっていることを確認し、 **[OK]** をクリックします。  
  
    単語に注意してください**適用されたフィルター**に表示されるようになりました、**フィルターの詳細**内の列、 **DimCustomer**行のテキスト説明が表示されます、そのリンクをクリックすると、適用したフィルター。  
    
    ![テーブル-レッスン 2-適用-フィルター処理](media/as-tabular-lesson2-applied-filters.png)
    
  
4.  各テーブル内の次の列のチェック ボックスをオフにして、残りのテーブルをフィルター処理します。  
    
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
  
      |[列]|  
      |------------------|  
      |**OrderDateKey**|  
      |**DueDateKey**|  
      |**ShipDateKey**|   
  
## <a name="Import"></a>Import the selected tables and column data  
プレビューを表示し、不要なデータを除外したするには、データの残りの部分をインポートできます。 ウィザードでは、テーブル データと、各テーブル間のリレーションシップがインポートされます。 新しいテーブルと列がモデルで作成し、除外したデータはインポートされません。  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>選択したテーブルと列のデータのインポートするには  
  
1.  選択内容を確認します。 問題がなければ、クリックして**完了**します。  
  
    データのインポート中、フェッチされた行数が表示されます。 すべてのデータがインポートされると、成功を示すメッセージが表示されます。  
    
    ![として-テーブル-レッスン 2-成功](media/as-tabular-lesson2-success.png) 
  
    > [!TIP]  
    > インポートしたテーブル間に自動的に作成されたリレーションシップを表示するために、 **[データ準備]** 行で、 **[詳細]** をクリックします。 
  
2.  **[閉じる]** をクリックします。  
  
    ウィザードを閉じるし、モデル デザイナーでは、インポートされたテーブルに表示されます。 
  
## <a name="save-your-model-project"></a>モデル プロジェクトを保存します。  
頻繁にモデル プロジェクトを保存する重要です。  
  
#### <a name="to-save-the-model-project"></a>モデル プロジェクトを保存するには  
  
-   Click **[ファイル]** > **[すべてを保存]**」を参照してください。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動します。[レッスン 3:日付テーブルとしてマーク](lesson-3-mark-as-date-table.md)します。

  
  
