---
title: 'チュートリアル: レポートへの円グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 39633ecaa8c0fbb73e712d1d227c4fe39c8f00dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084713"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a>チュートリアル: レポートへの円グラフの追加 (レポート ビルダー)
  円グラフおよびドーナツ グラフは、データを全体に対する比率として表示します。 円グラフは、主に、グループ間の比較を示すために使用されます。 円グラフおよびドーナツ グラフ、ピラミッド グラフやじょうごグラフとでは、図形グラフと呼ばれるグラフのグループを構成します。 図形グラフには軸がありません。 図形グラフに数値フィールドをドロップすると、それぞれの値の全体に占める比率が計算されます。  
  
 円グラフのデータ ポイントが多すぎると、データ ポイント ラベルが過密状態になって見づらくなる場合があります。 その場合は、折れ線グラフの使用を検討してください。 円グラフは、データを少数のデータ ポイントに集計したうえで使用するようにします。  
  
 次の図に、ここで作成する円グラフを示します。  
  
 ![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")  
  
##  <a name="BackToTop"></a> 学習する内容  
 このチュートリアルでは、次の内容を学習します。  
  
1.  [グラフ ウィザードから円グラフを作成します。](#Chart)  
  
2.  [グラフの種類を選択します。](#ChartType)  
  
3.  [各スライスにパーセンテージを表示します。](#Percentages)  
  
4.  [小さいスライスをまとめて 1 つのスライス](#CombineSlices)  
  
5.  [描画効果をカスタマイズします。](#DrawingEffect)  
  
6.  [レポート タイトルを追加します。](#Title)  
  
7.  [レポートを保存します。](#Save)  
  
> [!NOTE]  
>  このチュートリアルでは、ウィザードに関する手順を 2 つにまとめて示します。 レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 (レポート ビルダー)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。  
  
 このチュートリアルの推定所要時間: 10 分  
  
## <a name="requirements"></a>要件  
 要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。  
  
##  <a name="Chart"></a> 1.グラフ ウィザードから円グラフを作成する  
 [作業の開始] ダイアログ ボックスで、グラフ ウィザードを使用して埋め込みデータセットを作成し、共有データ ソースを選択して、円グラフを作成します。  
  
> [!NOTE]  
>  このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。 このため、クエリが非常に長くなっています。 ビジネス環境でクエリにデータを含めることはありません。 これは、学習に使用することのみを目的としています。  
  
#### <a name="to-create-a-new-chart-report"></a>新しいグラフ レポートを作成するには  
  
1.  **[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。  
  
     [作業の開始] ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  作業の開始 ダイアログ ボックスが表示されない場合、レポート ビルダーのボタンをクリックして**新規**です。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[グラフ ウィザード]** をクリックします。  
  
4.  **[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。  
  
5.  **[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。 ユーザー名とパスワードの入力が必要な場合があります。  
  
    > [!NOTE]  
    >  適切な権限を持っている限り、選択するデータ ソースは重要ではありません。 データ ソースからはデータを取得しません。 詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。  
  
6.  **[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。  
  
7.  次のクエリをクエリ ペインに貼り付けます。  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。  
  
9. **[次へ]** をクリックします。  
  
##  <a name="ChartType"></a> 2.グラフの種類を選択する  
 あらかじめ定義されているさまざまなグラフの種類から選択できます。  
  
#### <a name="to-add-a-pie-chart"></a>円グラフを追加するには  
  
1.  **グラフの種類を選択** ページで、をクリックして**円**、順にクリック**次**です。 **[グラフのフィールドの配置]** ページが開きます。  
  
     **[グラフのフィールドの配置]** ページで、Product フィールドを **[カテゴリ]** ペインにドラッグします。 カテゴリは円グラフのスライスの数を定義します。 この例では、各製品に 1 つずつ、合計 8 個のスライスになります。  
  
2.  Sales フィールドを **[値]** ペインにドラッグします。 Sales は、サブカテゴリの売上高を表します。 各販売員の集計がグラフに表示されるため、 **[値]** ペインには " `[Sum(Sales)]` " と表示されます。  
  
3.  **[次へ]** をクリックします。  
  
4.  **スタイルを選択する** ページで、スタイルのウィンドウで、スタイルを選択します。  
  
     スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。 スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。  
  
5.  **[完了]** をクリックします。  
  
     グラフがデザイン画面に追加されます。  
  
6.  グラフをクリックして、グラフのハンドルを表示します。 グラフの右下隅をドラッグして、グラフのサイズを大きくします。 レポート デザイン画面も、グラフ サイズに合わせて大きくなります。  
  
7.  **[実行]** をクリックして、レポートをプレビューします。  
  
 各製品に 1 つずつ、合計 8 個のスライスを含む円グラフがレポートに表示されます。 各スライスのサイズはその製品の売上を表します。 これらのスライスのうち 3 つは、非常に小さくなります。  
  
##  <a name="Percentages"></a> 3.各スライスにパーセンテージを表示する  
 円グラフの各スライスには、そのスライスの全体に占めるパーセンテージを表示できます。  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a>円グラフの各スライスにパーセンテージを表示するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  円グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。 グラフにデータ ラベルが表示されます。  
  
3.  ラベルを右クリックし、をクリックして**系列ラベルのプロパティ**です。  
  
4.  ラベル データ ドロップダウン ボックスから選択 **#PERCENT**です。  
  
     値をパーセンテージとして表示するには、UseValueAsLabel プロパティを false に設定する必要があります。 **[アクションの確認]** ダイアログでこの値の設定を求めるメッセージが表示されたら、 **[はい]** をクリックします。  
  
5.  (省略可能)ラベルに表示する数の小数点以下桁数を指定する入力`#PERCENT{Pn}`場所*n*を表示する小数点以下桁数の数です。 たとえば、小数点以下桁数を表示しない場合に次のように入力します。`#PERCENT{P0}`です。  
  
    > [!NOTE]  
    >  **[系列ラベルのプロパティ]** ダイアログ ボックスの **[数値書式]** は、パーセンテージの表示形式には影響しません。 この場合、ラベルの表示形式がパーセンテージに設定されるだけで、円グラフに対する各スライスのパーセンテージが計算されるわけではありません。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  **[実行]** をクリックして、レポートをプレビューします。  
  
 円グラフの各スライスがそれぞれ全体の何パーセントを占めているかが表示されます。  
  
##  <a name="CombineSlices"></a> 4.小さな複数のスライスを 1 つのスライスにまとめる  
 円グラフ内の 3 つのスライスは、非常に小さくなります。 複数の小さなスライスをまとめて 1 つの大きなスライスで表すことができます。  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a>円グラフの 5% 未満のスライスを 1 つのスライスにまとめるには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  **ビュー** ] タブで、**表示/非表示**グループで、[**プロパティ**です。  
  
3.  デザイン画面で、円グラフの任意のスライスをクリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
4.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。  
  
5.  **[CollectedStyle]** プロパティを **[SingleSlice]** に設定します。  
  
6.  **[CollectedThreshold]** プロパティが 5 に設定されていることを確認します。  
  
7.  **[CollectedThresholdUsePercent]** プロパティが **True**に設定されていることを確認します。  
  
8.  リボンで、上、**ホーム** タブで、をクリックして**実行**レポートをプレビューします。  
  
 凡例に "その他" というカテゴリが追加されています。 この新しいスライスでは、5% 未満のすべてのスライスが 1 つにまとめられて、円グラフ全体の 6% を占めるスライスが作成されています。  
  
##  <a name="DrawingEffect"></a> 5.描画効果をカスタマイズする  
 グラフ ウィザードの場合、円グラフの既定のスタイルは、凹型の描画効果が特徴的な [オーシャン] です。 スタイルは、ウィザードの実行後にも変更できます。  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a>円グラフに描画効果を追加するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  プロパティ ペインが開いていない場合、、**ビュー**  タブで **プロパティ**です。  
  
3.  円グラフ自体をダブルクリックします。 プロパティ ペインに、円グラフの系列のプロパティが表示されます。  
  
4.  プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。  
  
5.  設定、 **[piedrawingstyle]** に**SoftEdge**です。  
  
    > [!NOTE]  
    >  描画効果と 3 次元効果を同時に使用することはできません。 グラフに適用すると、3 次元効果がある場合**piedrawingstyle**プロパティ ペインでは使用できません。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
 次の図に、ぼかし効果が適用された円グラフを示します。  
  
 ![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")  
  
##  <a name="Title"></a> 6.レポート タイトルを追加する  
  
#### <a name="to-add-a-report-title"></a>レポート タイトルを追加するには  
  
1.  デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。  
  
2.  「 **Camera and Camcorder Sales**」と入力して Enter キーを押し、さらに「 **As a Percentage of Total Sales**」と入力します。次のように表示されます。  
  
     **Camera and Camcorder Sales**  
  
     **As a Percentage of Total Sales**  
  
3.  選択**Camera and Camcorder Sales**、 をクリックし、**太字**ボタンから、**フォント**のセクションで、**ホーム**リボンのタブです。  
  
4.  選択**として a Percentage of Total Sales**、し、[、**フォント**セクションで、**ホーム**] タブで、フォント サイズを設定**10**です。  
  
5.  (省略可) 2 行のテキストに合わせて、[タイトル] テキスト ボックスの高さを高くする必要が生じる場合もあります。  
  
     このタイトルは、レポートの最上部に表示されます。 ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="Save"></a> 7.レポートを保存する  
  
#### <a name="to-save-the-report"></a>レポートを保存するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  レポート ビルダーのボタンの **[名前を付けて保存]** をクリックします。  
  
3.  **[名前]** に「 **Sales Pie Chart**」と入力します。  
  
4.  **[保存]** をクリックします。  
  
 レポートがレポート サーバーに保存されます。  
  
## <a name="next-steps"></a>次の手順  
 これで、「レポートへの円グラフの追加」チュートリアルを終了します。 グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [チュートリアル&#40;レポート ビルダー&#41;](report-builder-tutorials.md)   
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  