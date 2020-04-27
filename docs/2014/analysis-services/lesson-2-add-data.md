---
title: 'レッスン 2: データの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 370e368843fa1e9584cc341397853fcdad26922a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66078972"
---
# <a name="lesson-2-add-data"></a>レッスン 2: データを追加する
  このレッスンでは、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] のテーブルのインポート ウィザードを使用して、AdventureWorksDW SQL データベースに接続し、データを選択し、プレビューして、データをフィルター処理した後、それらのデータをモデル ワークスペース内にインポートします。  
  
 テーブルのインポート ウィザードを使用すると、Access、SQL、Oracle、Sybase、Informix、DB2、Teradata など、さまざまなリレーショナル ソースからデータをインポートできます。 それぞれのリレーショナル ソースからデータをインポートする手順は、以下で説明する手順とそれほど変わりません。 また、データはストアド プロシージャを使用して選択できます。  
  
 データのインポートと、インポート可能なデータ ソースの種類に関する詳細については、「[データ ソース (SSAS テーブル)](data-sources-ssas-tabular.md)」を参照してください。  
  
 このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前の「 [レッスン 1: 新しいテーブル モデル プロジェクトの作成](lesson-1-create-a-new-tabular-model-project.md)」を完了している必要があります。  
  
## <a name="create-a-connection"></a>接続の作成  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2012-database"></a>AdventureWorksDW2012 データベースへの接続を作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。  
  
     テーブルのインポート ウィザードが起動し、その指示に従ってデータ ソースへの接続を設定することができます。 **[データ ソースからのインポート]** がグレーで表示されている場合は、 **[ソリューション エクスプローラー]** で **Model.bim** をダブルクリックして、モデルをデザイナーで開きます。  
  
2.  **テーブルのインポート ウィザード**の **[リレーショナル データベース]** で **[Microsoft SQL Server]** をクリックし、 **[次へ]** をクリックします。  
  
3.  [ **Microsoft SQL Server データベースへの接続**] ページで、[**接続**の表示名`Adventure Works DB from SQL`] に「」と入力します。  
  
4.  **[サーバー名]** に、AdventureWorksDW データベースをインストールしたサーバーの名前を入力します。  
  
5.  **[データベース名]** フィールドで、下矢印をクリックして **[AdventureWorksDW]** を選択し、 **[次へ]** をクリックします。  
  
6.  **[権限借用情報]** ページで、データをインポートおよび処理する際、Analysis Services がデータ ソースへの接続のために使用する資格情報を指定する必要があります。 **[特定の Windows ユーザー名とパスワード]** が選択されていることを確認し、 **[ユーザー名]** と **[パスワード]** に Windows のログオン資格情報を入力して、 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  Windows のユーザー アカウントとパスワードを使用することで、最も安全なデータ ソース接続方法が提供されます。 詳細については、「[権限借用 (SSAS テーブル)](tabular-models/impersonation-ssas-tabular.md)」を参照してください。  
  
7.  **[データのインポート方法の選択]** ページで、 **[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認します。 テーブルとビューの一覧から選択するには、 **[次へ]** をクリックして、ソース データベース内のすべてのソース テーブルの一覧を表示します。  
  
8.  **[テーブルとビューの選択]** ページで、 **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および **FactInternetSales**の各テーブルのチェック ボックスをオンにします。  
  
9. モデル内のテーブルによりわかりやすい名前を付けましょう。 **DimCustomer** の **[表示名]** 列内にあるセルをクリックします。 DimCustomer から "Dim" を削除して、テーブルの名前を変更します。  
  
10. その他のテーブルの名前を次のように変更します。  
  
    |ソース名|フレンドリ名|  
    |-----------------|-------------------|  
    |DimDate|日付|  
    |DimGeography|[地理的な場所]|  
    |DimProduct|Product|  
    |DimProductCategory|製品カテゴリ|  
    |DimProductSubcategory|Product Subcategory|  
    |FactInternetSales|Internet Sales|  
  
     **[完了]** をクリック **しないでください**。  
  
 データベースに接続し、インポートするテーブルを選択し、テーブルに表示名を付けたので、次のセクション「 [インポート前のテーブル データに対するフィルターの適用](#FilterData)」に進んでください。  
  
##  <a name="filter-the-table-data"></a><a name="FilterData"></a>テーブルデータのフィルター処理  
 データベースからインポートしようとしている DimCustomer テーブルには、元の SQL Server Adventure Works データベースから取得されたデータのサブセットが含まれています。 必要のない DimCustomer テーブルの一部の列を除外します。 可能な場合は、モデルによって使用されるメモリ内領域を節約するために、使用されないデータを除外します。  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>インポート前のテーブル データにフィルターを適用するには  
  
1.  **Customer** テーブルの行を選択し、**[プレビューとフィルター]** をクリックします。 **[選択したテーブルのプレビュー]** ウィンドウが開き、DimCustomer ソース テーブルのすべての列が表示されます。  
  
2.  次の列の上部にあるチェック ボックスをオフにします。  
  
    |Customer|  
    |--------------|  
    |**SpanishEducation**|  
    |**FrenchEducation**|  
    |**SpanishOccupation**|  
    |**FrenchOccupation**|  
  
     これらの列の値はインターネット売上分析と関連がないので、これらの列をインポートする必要はありません。 不要な列を削除することで、モデルのサイズを減らせます。  
  
3.  他の列がすべてオンになっていることを確認し、 **[OK]** をクリックします。  
  
     "**適用さ**れたフィルター" という単語が**Customer**行の [**フィルターの詳細**列に表示されることに注意してください。そのリンクをクリックすると、適用したフィルターの説明テキストが表示されます。  
  
4.  各テーブル内の次の列のチェック ボックスをオフにして、残りのテーブルをフィルター処理します。  
  
    |日付|  
    |----------|  
    |**DateKey**|  
    |**SpanishDayNameOfWeek**|  
    |**FrenchDayNameOfWeek**|  
    |**SpanishMonthName**|  
    |**FrenchMonthName**|  
  
    |[地理的な場所]|  
    |---------------|  
    |**SpanishCountryRegionName**|  
    |**FrenchCountryRegionName**|  
    |**IpAddressLocator**|  
  
    |Product|  
    |-------------|  
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
  
    |製品カテゴリ|  
    |----------------------|  
    |**SpanishProductCategoryName**|  
    |**FrenchProductCategoryName**|  
  
    |Product Subcategory|  
    |-------------------------|  
    |**SpanishProductSubcategoryName**|  
    |**FrenchProductSubcategoryName**|  
  
    |Internet Sales|  
    |--------------------|  
    |**OrderDateKey**|  
    |**DueDateKey**|  
    |**ShipDateKey**|  
  
 不要なデータをプレビューして除外したので、データをインポートする準備が整いました。 次のセクション「 **選択したテーブルと列のデータのインポート**」に進んでください。  
  
##  <a name="import-the-selected-tables-and-column-data"></a><a name="Import"></a>選択したテーブルと列のデータをインポートします  
 選択したデータをインポートします。 ウィザードでは、テーブル データと、各テーブル間のリレーションシップがインポートされます。 指定した表示名を使用して、モデル内に新しいテーブルと列が作成されます。除外したデータはインポートされません。  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>選択したテーブルと列のデータをインポートする  
  
1.  選択内容を確認します｡ 問題がなければ **[完了]** をクリックします。  
  
     データのインポート中、フェッチされた行数が表示されます。 すべてのデータがインポートされると、成功を示すメッセージが表示されます。  
  
    > [!TIP]  
    >  インポートしたテーブル間に自動的に作成されたリレーションシップを表示するために、 **[データ準備]** 行で、 **[詳細]** をクリックします。  
  
2.  **[閉じる]** をクリックします。  
  
     ウィザードが閉じ、モデル デザイナーが表示されます。 各テーブルが新しいタブとしてモデル デザイナーに追加されています。  
  
## <a name="save-the-model-project"></a>モデル プロジェクトの保存  
 モデル プロジェクトは頻繁に保存することが重要です。  
  
#### <a name="to-save-the-model-project"></a>モデル プロジェクトを保存する  
  
-   [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[ファイル]** メニューをクリックし、 **[すべてを保存]** をクリックします。  
  
## <a name="next-step"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 3: 列名の変更](rename-columns.md)」に進んでください。  
  
  
