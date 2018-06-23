---
title: 'チュートリアル: レポートへの横棒グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f54e95b0b9bee1e989d9d9ccf85f513210302367
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165525"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a>チュートリアル: レポートへの横棒グラフの追加 (レポート ビルダー)
  横棒グラフでは、カテゴリ データが水平方向に表示されます。 これは、次のようなことに役立ちます。  
  
-   長いカテゴリ名を読みやすくする。  
  
-   値としてプロットされた時間をわかりやすく示す。  
  
-   複数の系列の相対値を比較する。  
  
 次の図は、ここで作成する横棒グラフを示しています。このグラフでは、2008 年と 2009 年の上位 5 人の販売員の売上をアルファベット順に示します。  
  
 ![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")  
  
##  <a name="BackToTop"></a> 学習する内容  
 このチュートリアルでは、次の方法を学習します。  
  
1.  [グラフ ウィザードからグラフを作成します。](#Chart)  
  
2.  [グラフの種類を選択します。](#ChartType)  
  
3.  [垂直軸上のすべてのカテゴリ値を表示します。](#AllValues)  
  
4.  [垂直軸上の名前の表示を変更します。](#Sort)  
  
5.  [凡例を移動します。](#Legend)  
  
6.  [グラフのタイトルを移動します。](#ChartTitle)  
  
7.  [形式し、水平軸のラベル](#Horizontal)  
  
8.  [上位 5 つの値を表示するフィルターを追加します。](#Filter)  
  
9. [レポート タイトルを追加します。](#Title)  
  
10. [レポートを保存します。](#Save)  
  
> [!NOTE]  
>  このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。 レポート サーバーの参照、データセットの作成、データ ソースの選択に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 (レポート ビルダー)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。  
  
 このチュートリアルの推定所要時間: 15 分  
  
## <a name="requirements"></a>要件  
 要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。  
  
##  <a name="Chart"></a> 1.グラフ ウィザードからグラフ レポートを作成する  
 **作業の開始**ダイアログ ボックスでは、埋め込みデータセットを作成、共有データ ソースを選択し、グラフ ウィザードを使用して横棒グラフを作成します。  
  
> [!NOTE]  
>  このチュートリアルでは、外部のデータ ソースが必要ないようにクエリにデータ値が含まれています。 このため、クエリが非常に長くなっています。 ビジネス環境でクエリにデータを含めることはありません。 これは、学習に使用することのみを目的としています。  
  
#### <a name="to-create-a-new-chart-report"></a>新しいグラフ レポートを作成するには  
  
1.  **[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。  
  
     **[作業の開始]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  場合、**作業の開始** ダイアログ ボックスは、レポート ビルダー ボタンをクリックし、をクリックして**新規**です。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[グラフ ウィザード]** をクリックします。  
  
4.  **[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。  
  
5.  **[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。 ユーザー名とパスワードの入力が必要な場合があります。  
  
    > [!NOTE]  
    >  適切な権限を持っている限り、選択するデータ ソースは重要ではありません。 データ ソースからはデータを取得しません。 詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。  
  
6.  **[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。  
  
7.  次のクエリをクエリ ペインに貼り付けます。  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。  
  
9. **[次へ]** をクリックします。  
  
##  <a name="ChartType"></a> 2.グラフの種類を選択する  
 あらかじめ定義されているさまざまなグラフの種類から選択できます。  
  
#### <a name="to-add-a-column-chart"></a>縦棒グラフを追加するには  
  
1.  **[グラフの種類の選択]** ページでは、縦棒グラフが既定のグラフの種類です。  
  
2.  **[横棒]** をクリックし、 **[次へ]** をクリックします。  
  
     **グラフのフィールドの配置** ページで、4 つのフィールドがある、**利用可能なフィールド**ペイン: FirstName、LastName、SalesYear2009、および SalesYear2008 です。  
  
3.  LastName をカテゴリ ペインにドラッグします。  
  
4.  SalesYear2009 を値ペインにドラッグします。 SalesYear2009 は、2009 年の各販売員の売上高を表します。 各製品の集計がグラフに表示されるため、値ペインには "`[Sum(SalesYear2009)]`" と表示されます。  
  
5.  SalesYear2008 を、値ペインの SalesYear2009 の下にドラッグします。 SalesYear2008 は、2008 年の各販売員の売上高を表します。  
  
6.  **[次へ]** をクリックします。  
  
7.  **スタイルを選択する** ページで、スタイルのウィンドウで、スタイルを選択します。  
  
     スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。 スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。  
  
8.  **[完了]** をクリックします。  
  
     グラフがデザイン画面に追加されます。  
  
9. グラフをクリックして、グラフのハンドルを表示します。 グラフの右下隅をドラッグして、グラフのサイズを大きくします。  
  
10. **[実行]** をクリックして、レポートをプレビューします。  
  
 2008 年と 2009 年の各販売員の売上を示す横棒グラフがレポートに表示されます。 横棒の長さは、売上総額に対応します。  
  
##  <a name="AllValues"></a> 3.縦軸の名前の表示を変更する  
 既定では、縦軸の値の一部のみが表示されます。 すべてのカテゴリを表示するようにグラフを変更できます。  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a>横棒グラフのカテゴリ軸に沿ってすべての販売員を表示するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  垂直の軸を右クリックし、をクリックして**縦軸のプロパティ**です。  
  
3.  **[軸の範囲と間隔]** の **[間隔]** ボックスに「 **1**」と入力します。  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  垂直を右クリックして**軸のタイトル**をオフにし、 **軸のタイトル**チェック ボックスをオンします。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
> [!NOTE]  
>  縦軸に表示される販売員の名前が読みにくい場合は、グラフを縦方向に大きくするか、軸ラベルの形式オプションを変更します。  
  
###  <a name="CategoryExpression"></a> 縦軸に姓と名を表示します。  
 各販売員の姓と名を含むように、カテゴリ式を変更できます。  
  
##### <a name="to-change-the-category-expression"></a>カテゴリ式を変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフをダブルクリックして、 **グラフ データ** ペインを表示します。  
  
3.  **[カテゴリ グループ]** 領域で、[LastName] を右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。  
  
4.  [ラベル] で、式 ([Fx]) ボタンをクリックします。  
  
5.  次の式を入力します。 `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
     この式は、姓、コンマ、および名を連結します。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  **[実行]** をクリックして、レポートをプレビューします。  
  
 レポートを実行したときに名が表示されない場合は、データを手動で更新します。 プレビュー モードのまま、 **[実行]** タブの **[ナビゲーション]** グループで、 **[更新]** をクリックします。  
  
> [!NOTE]  
>  縦軸に表示される販売員の名前が読みにくい場合は、グラフを縦方向に大きくするか、軸ラベルの形式オプションを変更します。  
  
##  <a name="Sort"></a> 4.縦軸に表示される名前を並べ替える  
 グラフのデータを並べ替えると、カテゴリ軸の値の順序が変更されます。  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a>横棒グラフで名前をアルファベット順に並べ替えるには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフをダブルクリックして、 **グラフ データ** ペインを表示します。  
  
3.  **[カテゴリ グループ]** 領域で、[LastName] を右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。  
  
4.  **[並べ替え]** をクリックします。 **[並べ替えのオプションを変更します]** ページに、並べ替え式の一覧が表示されます。 既定では、この一覧には、元のカテゴリ グループの式と同じである 1 つの並べ替え式が含まれています。  
  
5.  並べ替え で、式 をクリックします (**Fx**) ボタンをクリックします。  
  
6.  次の式を入力します。 `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
7.  **[OK]** をクリックします。  
  
8.  戻り、**カテゴリ グループのプロパティ**] ページの [、**順序**ドロップダウン リストで、 **Z ~ A**です。アルファベットの逆順が選択され、名前が降順に表示されます。  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. **[実行]** をクリックして、レポートをプレビューします。  
  
 横軸の名前が並べ替えられ、逆の順序で**Alerca**上部にあると**Zeng**下部にあります。  
  
##  <a name="Legend"></a> 5.凡例を移動する  
 グラフの凡例を移動することで、グラフの値を読みやすくすることができます。 たとえば、バーが横方向に表示される横棒グラフでは、グラフ領域の上または下に来るように凡例の位置を変更します。 こうすることで、バーの水平方向のスペースを広げることができます。  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a>凡例を横棒グラフのグラフ領域の下に表示するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフの凡例を右クリックします。  
  
3.  **[凡例のプロパティ]** を選択します。  
  
4.  **[凡例の位置]** で、異なる位置を選択します。 たとえば、下部中央の位置を選択します。  
  
     凡例をグラフの上または下に配置すると、凡例のレイアウトが縦方向から横方向に変更されます。 **[レイアウト]** ドロップダウン リストから、異なるレイアウトを選択できます。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="ChartTitle"></a> 6.グラフのタイトルを設定する  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a>横棒グラフのグラフ領域の上に表示されるグラフのタイトルを変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  ある単語を選択**グラフのタイトル**上部のグラフ、および次のテキストを入力: **Sales for 2008 and 2009**です。  
  
3.  テキスト外の任意の場所をクリックします。  
  
4.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="Horizontal"></a> 7.横軸の形式とラベルを設定する  
 既定では、横軸の値が一般的な形式で表示されます。この場合、グラフのサイズに合わせて自動的にスケーリングされます。  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a>横軸に表示される数値の書式を変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフの底辺に沿った横軸をクリックして選択します。  
  
     リボンで、上、**ホーム** タブの 、**数**グループで、、**通貨**ボタンをクリックします。 横軸ラベルが通貨に変更されます。  
  
3.  (省略可) 小数点以下の桁を削除します。 **[通貨]** ボタンの近くにある **[小数点表示桁下げ]** ボタンを 2 回クリックします。  
  
4.  横軸を右クリックし、 **[横軸のプロパティ]** をクリックします。  
  
5.  **数**] タブで [**何千もの値を表示します。**  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  右クリック**軸のタイトル** をクリック**軸のタイトルのプロパティ**です。  
  
8.  **タイトル テキスト**ボックスに、入力**何千もの販売** をクリック**OK**です。  
  
9. **[実行]** をクリックして、レポートをプレビューします。  
  
 レポートの横軸に売上高が千単位の通貨で表示され、小数点以下の桁が省略されます。  
  
##  <a name="Filter"></a> 8 です。フィルターを追加して上位 5 件の値を表示する  
 グラフにフィルターを追加して、データセットのどのデータをグラフに含め、どのデータをグラフに含めないかを指定できます。  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a>フィルターを追加して上位 5 件の値を表示するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフをダブルクリックして、 **グラフ データ** ペインを表示します。  
  
3.  **[カテゴリ グループ]** 領域で、[LastName] フィールドを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。  
  
4.  **[フィルター]** をクリックします。 **[フィルターを変更します]** ページに、フィルター式の一覧を表示することもできます。 既定では、この一覧には何も表示されません。  
  
5.  **[追加]** をクリックします。 新しい空のフィルターが表示されます。  
  
6.  **式**、型 **[Sum(SalesYear2009)]** です。 こうと、基になる式`=Sum(Fields!SalesYear2009.Value)`をクリックすること確認、 **fx**ボタンをクリックします。  
  
7.  データ型が **Text**であることを確認します。  
  
8.  **[演算子]** で、ドロップダウン リストから **[上位 N]** を選択します。  
  
9. **[値]** に式「 **=5**」を入力します。  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. **[実行]** をクリックして、レポートをプレビューします。  
  
 レポートを実行したときに結果がフィルター選択されない場合は、データを手動で更新します。 **[実行]** タブの **[ナビゲーション]** グループで、 **[更新]** をクリックします。  
  
 グラフに、2009 年の売上データから取得された上位 5 人の販売員の名前が表示されます。  
  
##  <a name="Title"></a> 9 です。レポート タイトルを追加する  
  
#### <a name="to-add-a-report-title"></a>レポート タイトルを追加するには  
  
1.  デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。  
  
2.  型**Sales Bar Chart**を入力し、enter キーを押しながら、 **Top Five Sellers for 2009**ので、次のようにします。  
  
     **Sales Bar Chart**  
  
     **Top Five Sellers for 2009**  
  
3.  **[Sales Bar Chart]** を選択し、 **[太字]** ボタンをクリックします。  
  
4.  選択**Top Five Sellers for 2009**、し、[、**フォント**セクションで、**ホーム**] タブで、フォント サイズを設定**10**です。  
  
5.  (省略可) 2 行のテキストに合わせて、[タイトル] テキスト ボックスの高さを高くする必要が生じる場合もあります。  
  
     このタイトルは、レポートの最上部に表示されます。 ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="Save"></a> 10 です。レポートを保存する  
  
#### <a name="to-save-the-report"></a>レポートを保存するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  **レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。  
  
3.  **[名前]** に「 **Sales Bar Chart**」と入力します。  
  
4.  **[保存]** をクリックします。  
  
 レポートがレポート サーバーに保存されます。  
  
## <a name="next-steps"></a>次の手順  
 これで、「レポートへの横棒グラフの追加」チュートリアルを終了します。 グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [チュートリアル&#40;レポート ビルダー&#41;](report-builder-tutorials.md)   
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  