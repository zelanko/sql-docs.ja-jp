---
title: 置換データを使用した時系列予測 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a23a6e1d-1d49-41ea-8314-925dc8e4df5e
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c96b70775105ea9446810ac3b064ae7cb07d4337
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63312880"
---
# <a name="time-series-predictions-using-replacement-data-intermediate-data-mining-tutorial"></a>時系列予測での置き換え後のデータの使用 (中級者向けデータ マイニング チュートリアル)
  ここでは、全世界の売上データに基づく新しいモデルを作成します。 その後、全世界の売上モデルを個々の地域のいずれかに適用する予測クエリを作成します。  
  
## <a name="building-a-general-model"></a>汎用モデルの作成  
 元のマイニング モデルの結果を分析したところ、地域間や製品ライン間で大きな差が見られました。 たとえば、North America では M200 モデルの売上が強い一方で、T1000 モデルの売上はそれほどでもありません。 ただし、一部の系列に多くのデータが含まれていなかったり、別の時点でデータが開始されていたりすると、分析が複雑になります。 不足しているデータもあります。  
  
 ![M200 および T1000 の数量を予測するシリーズ](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 および T1000 の数量を予測するシリーズ")  
  
 データの品質の問題の一部に対処するために、全世界の売上データをマージし、その全体的な売上傾向を使用して、任意の地域の将来の売上を予測するために適用できるモデルを作成します。  
  
 予測を作成する際、全世界の売上データをトレーニングして生成されるパターンを使用しますが、履歴データのポイントをそれぞれの地域の売上データに置き換えます。 これにより、全体的な傾向は維持しながら、各予測値をそれぞれの地域やモデルの売上額の履歴と対応させることができます。  
  
## <a name="performing-cross-prediction-with-a-time-series-model"></a>時系列モデルでのクロス予測の実行  
 ある系列のデータを使用して別の系列の傾向を予測するプロセスのことをクロス予測と呼びます。 クロス予測はさまざまなシナリオで使用できます。たとえば、テレビの売上が経済活動全般の適切な予測子であると特定できれば、テレビの売上でトレーニングしたモデルを全般的な経済データに適用できます。  
  
 SQL Server のデータマイニングでは、パラメーター REPLACE_MODEL_CASES を使用してクロス予測を実行します。これには、関数[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を引数として指定します。  
  
 次の作業では、REPLACE_MODEL_CASES の使用方法について学習します。 マージした全世界の売上データを使用してモデルを作成し、汎用モデルを置き換え後のデータにマップする予測クエリを作成します。  
  
 データ マイニング モデルの作成方法については、既に理解していることを前提に、ここでは簡略化して説明しています。  
  
#### <a name="to-build-a-mining-structure-and-mining-model-using-the-aggregated-data"></a>集計データを使用してマイニング構造とマイニング モデルを作成するには  
  
1.  **ソリューションエクスプローラー**で、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックして、データマイニングウィザードを起動します。  
  
2.  データ マイニング ウィザードで、以下の選択を行います。  
  
    -   [アルゴリズム]: [Microsoft タイム シリーズ]  
  
    -   モデルのソースとして、この高度なレッスンで既に作成したデータ ソースを使用する。 「[高度な時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)」を参照してください。  
  
         データソースビュー:`AllRegions`  
  
    -   系列キーおよび時間キーの列として、次の列を選択する。  
  
         キー時刻: ReportingDate  
  
         キー: リージョン  
  
    -   
  `Input` および `Predict` の列として、次の列を選択する。  
  
         SumQty  
  
         SumAmt  
  
         AvgAmt  
  
         AvgQty  
  
    -   [**マイニング構造名**] に、次のように入力します。`All Regions`  
  
    -   [**マイニングモデル名**] に、次のように入力します。`All Regions`  
  
3.  新しい構造と新しいモデルを処理します。  
  
#### <a name="to-build-the-prediction-query-and-map-the-replacement-data"></a>予測クエリを作成して置き換え後のデータをマップするには  
  
1.  モデルがまだ開いていない場合は、AllRegions 構造をダブルクリックし、データマイニングデザイナーで [**マイニングモデル予測**] タブをクリックします。  
  
2.  [**マイニングモデル**] ペインで、モデル allregions が既に選択されている必要があります。 選択されていない場合は、[**モデルの選択**] をクリックし、モデル allregions を選択します。  
  
3.  [**入力テーブルの選択**] ペインで、[**ケーステーブルの選択**] をクリックします。  
  
4.  [**テーブルの選択**] ダイアログボックスで、データソースを T1000 太平洋地域に変更し、[ **OK**] をクリックします。  
  
5.  マイニングモデルと入力データの間の結合線を右クリックし、[**接続の変更**] を選択します。 次のように、データ ソース ビューのデータをモデルにマップします。  
  
    1.  マイニングモデルの ReportingDate 列が入力データの ReportingDate 列にマップされていることを確認します。  
  
    2.  [**マッピングの変更**] ダイアログボックスで、モデル列 AvgQty の行の [**テーブル列**] をクリックし、[T1000] を選択します。 **[OK]** をクリックします。  
  
         この手順によって、平均数量を予測するモデルで作成した列が T1000 系列の販売数量の実際のデータにマップされます。  
  
    3.  モデル内の列領域を入力列にマップしないでください。  
  
         モデルはすべての系列にわたってデータを集計しているので、T1000 Pacific などの系列値に一致するものはなく、予測クエリが実行されるとエラーが発生します。  
  
6.  ここで、予測クエリを作成します。  
  
     まず、モデルから予測と共に AllRegions ラベルを出力する列を結果に追加します。 これにより、汎用モデルに基づく結果であることがわかるようになります。  
  
    1.  グリッドで、[**ソース**] の下の最初の空の行をクリックし、[allregions マイニングモデル] を選択します。  
  
    2.  [**フィールド**] で [Region] を選択します。  
  
    3.  [**別名**] に「 **Model Used**」と入力します。  
  
7.  次に、予測がどの系列に対するものかを表す別のラベルを結果に追加します。  
  
    1.  空の行をクリックし、[**ソース**] で [**カスタム式**] を選択します。  
  
    2.  [**別名**] 列に「 **modelregion**」と入力します。  
  
    3.  [**条件と引数**] 列に「 `'T1000 Pacific'`」と入力します。  
  
8.  ここで、クロス予測関数を設定します。  
  
    1.  空の行をクリックし、[**ソース**] で [**予測関数**] を選択します。  
  
    2.  [**フィールド]** 列で、[ **PredictTimeSeries**] を選択します。  
  
    3.  [**別名**] に「予測される**値**」と入力します。  
  
    4.  ドラッグアンドドロップ操作を使用して、[**マイニングモデル**] ペインのフィールド AvgQty を [**条件と引数**] 列にドラッグします。  
  
    5.  [**条件と引数**] 列で、フィールド名の後に次のテキストを入力します。`,5, REPLACE_MODEL_CASES`  
  
         [**条件と引数**] テキストボックスの完全なテキストは次のようになります。`[AllRegions].[AvgQty],5,REPLACE_MODEL_CASES`  
  
9. [**結果**] をクリックします。  
  
## <a name="creating-the-cross-prediction-query-in-dmx"></a>DMX でのクロス予測クエリの作成  
 既にお気付きかもしれませんが、クロス予測で別のデータ系列 (北米地域の T1000 製品モデルなど) に汎用モデルを適用するには、系列ごとに異なるクエリを作成し、それぞれの入力セットをモデルにマップできるようにする必要があります。  
  
 ただし、デザイナーでクエリを作成する代わりに、DMX ビューに切り替えて、作成した DMX ステートメントを編集することができます。 たとえば、次の DMX ステートメントは、先ほど作成したクエリを表します。  
  
```  
SELECT  
      ([All Regions].[Region]) as [Model Used],  
      ('T-1000 Pacific') as [ModelRegion],  
      (PredictTimeSeries([All Regions].[Avg Qty],5, REPLACE_MODEL_CASES)) as [Predicted Quantity]  
     FROM [All Regions]  
PREDICTION JOIN  
    OPENQUERY([Adventure Works DW2003R2], 'SELECT [ReportingDate] FROM  
      (  
       SELECT  ReportingDate, ModelRegion, Quantity, Amount   
       FROM dbo.vTimeSeries   
       WHERE (ModelRegion = N''T1000 Pacific'')  
       ) as [T1000 Pacific]    ')   
    AS t  
ON   
[All Regions].[Reporting Date] = t.[ReportingDate]   
AND   
[All Regions].[Avg Qty] = t.[Quantity]  
```  
  
 このクエリを別のモデルに適用するには、クエリ ステートメントを編集して、フィルター条件を置き換え、各結果に関連付けられているラベルを更新するだけで済みます。  
  
 たとえば、'Pacific' を 'North America' に置き換えてフィルター条件と列ラベルを変更すると、汎用モデル内のパターンに基づく北米の T1000 製品の予測を取得できます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [予測モデルの予測の比較 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [DMX&#41;&#40;PredictTimeSeries](/sql/dmx/predicttimeseries-dmx)  
  
  
