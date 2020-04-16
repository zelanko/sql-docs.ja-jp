---
title: 高度な時系列予測 (中間データ マイニング チュートリアル) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ca144d1d473f7df49f73d5ed170052c61ce6107d
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "68893689"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a>高度な時系列予測 (中級者向けデータ マイニング チュートリアル)
  予測モデルの検証によって、ほとんどの地域の売上が似たパターンに合致するものの、太平洋地域の M200 モデルなど、一部の地域とモデルについては、傾向が大きく異なることがわかりました。 これは驚くことではなく、地域間で違いが生じることは一般的で、その要因は販売促進の有無、レポートの不正確性、地政学的なイベントの有無など多岐にわたります。  
  
 しかし、ユーザーは世界中で適用できるモデルを求めています。 したがって、個別の要因が予測に与える影響を最小限に抑えるため、全世界の売上の集計メジャーに基づくモデルを作成することにします。 その後、このモデルを使用して、個々の地域に対する予測を行います。  
  
 このタスクでは、高度な予測タスクの実行に必要なすべてのデータ ソースを構築します。 予測クエリへの入力として使用する 2 つのデータ ソース ビューと、新しいモデルの構築に使用する 1 つのデータ ソース ビューを作成します。  
  
 **手順**  
  
1.  [(予測用の) 拡張売上データを準備する](#bkmk_newExtendData)  
  
2.  [(モデルを構築するための) 集計データを準備する](#bkmk_newReplaceData)  
  
3.  [(クロス予測のための) 系列データを準備する](#bkmk_CrossData2)  
  
4.  [EXTEND を使用して予測する](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [クロス予測モデルを作成する](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [REPLACE を使用して予測する](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [新しい予測を検討する](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="creating-the-new-extended-sales-data"></a><a name="bkmk_newExtendData"></a>新しい拡張販売データの作成  
 売上データを更新するには、最新の売上の数値を取得する必要があります。 特に関心があるのは太平洋地域のデータです。この地域では、地域の販売促進を開始して、新しい店への関心を引きつけ、製品の認知度を高めています。  
  
 このシナリオでは、いくつかの地域の新しいデータがわずか 3 か月含まれている Excel ブックからデータがインポートされたと仮定します。 Transact-SQL スクリプトを使用してデータのテーブルを作成し、予測に使用するデータ ソース ビューを定義します。  
  
#### <a name="create-the-table-with-new-sales-data"></a>新しい売上データでのテーブルの作成  
  
1.  Transact-SQL クエリ ウィンドウで次のステートメントを実行し、AdventureWorksDW データベース (またはその他のデータベース) に売上データを追加します。  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  次のスクリプトを使用して、新しい値を挿入します。  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  通貨の値と共に引用符を使用し、コンマ区切り記号および通貨記号の問題を防ぎます。 また、`130170.22` の形式で通貨の値を渡すこともできます。  
    >   
    >  サンプル データベースで使用されている日付は、このリリース用に更新されています。 AdventureWorks の以前のエディションを使用している場合は、それに合わせて、挿入する日付を調整しなければならない場合があります。  
  
###  <a name="create-a-data-source-view-using-the-new-sales-data"></a><a name="bkmk_newReplaceData"></a>新しい売上データを使用してデータ ソース ビューを作成する  
  
1.  **ソリューション エクスプローラ**で、[データ**ソース ビュー**] を右クリックし、[**新しいデータ ソース ビュー**] を選択します。  
  
2.  データ ソース ビュー ウィザードで、以下の選択を行います。  
  
     **データ ソース**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **テーブルとビューの選択**: 作成したテーブルを選択します。  
  
3.  **[完了]** をクリックします。  
  
4.  データ ソース ビューのデザイン画面で、[NewSalesData] を右クリックし、[**データの探索**] を選択してデータを検証します。  
  
> [!WARNING]  
>  このデータは予測だけに使用するので、データが不完全でもかまいません。  
  
##  <a name="creating-the-data-for-the-cross-prediction-model"></a><a name="bkmk_CrossData2"></a>クロス予測モデルのデータの作成  
 元の予測モデルで使用されていたデータは既にビュー vTimeSeries によってグループ化されており、複数の自転車モデルが少数のカテゴリにまとめられ、個別の国の結果が地域に結合されていました。 世界的な予測に使用できるモデルを作成するには、データ ソース ビュー デザイナーで直接、追加の簡単な集計をいくつか作成します。 新しいデータ ソース ビューには、すべての地域におけるすべての製品の売上の合計と平均だけが含まれます。  
  
 モデルに使用するデータ ソースを作成した後、予測に使用する新しいデータ ソース ビューを作成する必要があります。 たとえば、新しい全世界モデルを使用してヨーロッパの売上を予測する場合は、ヨーロッパ地域のみのデータを提供する必要があります。 そこで、元のデータをフィルター処理する新しいデータ ソース ビューを設定し、各予測クエリ セットごとにフィルター条件を変更します。  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a>カスタム データ ソース ビューを使用してモデル データを作成するには  
  
1.  **ソリューション エクスプローラ**で、[データ**ソース ビュー**] を右クリックし、[**新しいデータ ソース ビュー**] を選択します。  
  
2.  ウィザードの [ようこそ] ページで、 **[次へ]** をクリックします。  
  
3.  **[データ ソースの選択]** ページで [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]を選択し、 **[次へ]** をクリックします。  
  
4.  [**テーブルとビューの選択**] ページで、テーブルを追加しない [**次へ**] をクリックします。  
  
5.  [**ウィザードの完了**] ページで、`AllRegions`の名前を入力し、 [**完了**] をクリックします。  
  
6.  次に、空白のデータ ソース ビューのデザイン画面を右クリックし、選択した**名前付きクエリの新規作成**します。  
  
7.  [**名前付きクエリの作成**] ダイアログ`AllRegions`ボックスで、[**名前**] と入力し、[**説明**] に **「 すべてのモデルと地域の売上の合計と平均**」と入力します。  
  
8.  SQL テキスト ペインに、以下のステートメントを入力して [OK] をクリックします。  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. テーブルを右クリック`AllRegions`し、[**データの探索**] を選択します。  
  
###  <a name="to-create-the-series-data-for-cross-prediction"></a><a name="bkmk_CrossData"></a>クロス予測の系列データを作成するには  
  
1.  **ソリューション エクスプローラ**で、[データ**ソース ビュー**] を右クリックし、[**新しいデータ ソース ビュー**] を選択します。  
  
2.  データ ソース ビュー ウィザードで、以下の選択を行います。  
  
     **データ ソース**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **[テーブルとビューの選択]**: テーブルを選択しない  
  
     **名前**:`T1000 Pacific Region`  
  
3.  **[完了]** をクリックします。  
  
4.  **[T1000 Pacific Region.dsv]** の空のデザインサーフェイスを右クリックし、[**新しい名前付きクエリ**] を選択します。  
  
     **[名前付きクエリの作成]** ダイアログ ボックスが表示されます。 名前を再入力し、以下の説明を追加します。  
  
     **名前**:`T1000 Pacific Region`  
  
     **説明**:**地域とモデルによるフィルタ`vTimeSeries`**  
  
5.  テキスト ペインに、以下のクエリを入力して [OK] をクリックします。  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  各系列で個別に予測を作成する必要があるので、クエリ テキストをコピーしてテキスト ファイルに保存し、他のデータ系列で再利用できます。  
  
6.  データ ソース ビューのデザイン画面で、[T1000 Pacific] を右クリックし、[**データの探索**] を選択してデータが正しくフィルターされていることを確認します。  
  
     クロス予測クエリを作成するときは、このデータをモデルへの入力として使用します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [更新されたデータ&#40;中間データ マイニング チュートリアルを使用した時系列予測&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [マイクロソフト時系列アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [マイクロソフト時系列アルゴリズムテクニカル リファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [多次元モデル内のデータ ソース ビュー](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
