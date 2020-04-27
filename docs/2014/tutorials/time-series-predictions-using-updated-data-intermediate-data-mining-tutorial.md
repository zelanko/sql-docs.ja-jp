---
title: 更新されたデータを使用した時系列予測 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067558"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a>時系列予測での更新後のデータの使用 (中級者向けデータ マイニング チュートリアル)
    
## <a name="creating-predictions-using-the-extended-sales-data"></a>拡張売上データを使用した予測の作成  
 このレッスンでは、モデルに新しい売上データを追加する予測クエリを作成します。 新しいデータでモデルを拡張することにより、最新のデータ ポイントを含む現時点での予測を取得できます。  
  
 新しいデータを使用する時系列予測を作成するのは簡単です。 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)関数にパラメーター EXTEND_MODEL_CASES を追加し、新しいデータのソースを指定して、取得する予測の数を指定するだけです。  
  
> [!WARNING]  
>  パラメーター EXTEND_MODEL_CASES は省略可能です。既定では、入力として新しいデータを結合して時系列予測クエリを作成するたびに、モデルが拡張されます。  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a>予測クエリを作成して新しいデータを追加するには  
  
1.  モデルがまだ開いていない場合は、予測構造をダブルクリックし、データマイニングデザイナーで [**マイニングモデル予測**] タブをクリックします。  
  
2.  [**マイニングモデル**] ペインで、モデルの予測を選択しておく必要があります。 選択されていない場合は、[**モデルの選択**] をクリックし、モデルの予測を選択します。  
  
3.  [**入力テーブルの選択**] ペインで、[**ケーステーブルの選択**] をクリックします。  
  
4.  **[テーブルの選択**] ダイアログボックスで、データソースを[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]選択します。  
  
     データソースビューの一覧から [NewSalesData] を選択し、[ **OK**] をクリックします。  
  
5.  デザイン領域の画面を右クリックし、[**接続の変更**] を選択します。  
  
6.  [**マッピングの変更**] ダイアログボックスを使用して、次のように、モデル内の列を外部データの列にマップします。  
  
    -   マイニングモデルの ReportingDate 列を入力データの NewDate 列にマップします。  
  
    -   マイニングモデルの Amount 列を入力データの NewAmount 列にマップします。  
  
    -   マイニングモデルの Quantity 列を入力データの NewQty 列にマップします。  
  
    -   マイニングモデルの ModelRegion 列を入力データの系列列にマップします。  
  
7.  ここで、予測クエリを作成します。  
  
     最初に、列を予測クエリに追加し、予測を適用する系列を出力します。  
  
    1.  グリッドで、[**ソース**] の下の最初の空の行をクリックし、[予測] を選択します。  
  
    2.  [**フィールド**] 列で [モデル領域] を選択し、 `Model Region`[**別名**] に「」と入力します。  
  
8.  次に、予測関数を追加して編集します。  
  
    1.  空の行をクリックし、[**ソース**] で [**予測関数**] を選択します。  
  
    2.  [**フィールド**] で [ **PredictTimeSeries**] を選択します。  
  
    3.  [**別名**] に「予測される**値**」と入力します。  
  
    4.  [**マイニングモデル**] ペインの [Quantity] フィールドを [**条件と引数**] 列にドラッグします。  
  
    5.  [**条件と引数**] 列で、フィールド名の後に次のテキストを入力します: **5, EXTEND_MODEL_CASES**  
  
         [**条件と引数**] テキストボックスの完全なテキストは次のようになります。`[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`  
  
9. [**結果**] をクリックし、結果を確認します。  
  
     予測は 7 月 (元のデータが終了した後の最初のタイム スライス) から開始し、11 月 (元のデータが終了した後の 5 番目のタイム スライス) で終了しています。  
  
 この種の予測クエリを効率よく使用するには、古いデータがいつ終了し、新しいデータにタイム スライスがいくつあるかを知る必要があります。  
  
 たとえば、このモデルでは、元のデータ系列は 6 月に終了し、データは 7 月、8 月、9 月のものになります。  
  
 EXTEND_MODEL_CASES を使用する予測は常に、元のデータ系列の終了から開始します。 そのため、不明の月の予測のみを取得するには、予測の開始位置と終了位置を指定する必要があります。 どちらの値も、古いデータの終わりから始まるタイム スライスの数として指定されます。  
  
 次の手順は、これを行う方法を示します。  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a>予測の開始位置と終了位置を変更します。  
  
1.  [予測クエリビルダーで、[**クエリ**] をクリックして DMX ビューに切り替えます。  
  
2.  PredictTimeSeries 関数が含まれている DMX ステートメントを見つけて、次のように変更します。  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  [**結果**] をクリックし、結果を確認します。  
  
     予測が 10 月 (元のデータが終了してから 4 番目のタイム スライス) から開始し、12 月 (元のデータが終了してから 6 番目のタイム スライス) で終了するようになります。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [交換データ &#40;中間データマイニングチュートリアル&#41;を使用した時系列予測](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
