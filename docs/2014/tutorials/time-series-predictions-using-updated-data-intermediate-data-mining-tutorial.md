---
title: 更新データ (中級者向けデータ マイニング チュートリアル」) を使用して時系列予測 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3478a52657e26fa8e376e88bc83a5c4d9813cdc8
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312360"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a>時系列予測での更新後のデータの使用 (中級者向けデータ マイニング チュートリアル)
    
## <a name="creating-predictions-using-the-extended-sales-data"></a>拡張売上データを使用した予測の作成  
 このレッスンでは、モデルに新しい売上データを追加する予測クエリを作成します。 新しいデータでモデルを拡張することにより、最新のデータ ポイントを含む現時点での予測を取得できます。  
  
 新しいデータを使用する時系列予測の作成は簡単: パラメーター EXTEND_MODEL_CASES を単に追加する、 [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx)関数を新しいデータのソースを指定して指定数予測を取得します。  
  
> [!WARNING]  
>  パラメーター EXTEND_MODEL_CASES は省略可能です。既定では、入力として新しいデータを結合して時系列予測クエリを作成するたびに、モデルが拡張されます。  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a>予測クエリを作成して新しいデータを追加するには  
  
1.  モデルがまだ開いていない場合、Forecasting 構造をダブルクリックし、データ マイニング デザイナーで、をクリックして、**マイニング モデル予測**タブです。  
  
2.  **マイニング モデルの**ペインで、モデルの予測は既に選択されている必要があります。 選択されていない場合はクリックして**モデルの選択**、モデルを選択 Forecasting です。  
  
3.  **入力テーブルの選択**] ウィンドウで、をクリックして **[ケース テーブルの**します。  
  
4.  **テーブルの選択** ダイアログ ボックスで、データ ソースを選択[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]です。  
  
     データ ソース ビューの一覧から NewSalesData を選択し、クリックして**OK**です。  
  
5.  デザイン領域の画面を右クリックし **接続の変更**です。  
  
6.  使用して、**マッピングの変更** ダイアログ ボックスで、次のように、モデル内の列を外部データ内の列にマップします。  
  
    -   NewDate の列、入力データにマイニング モデルの ReportingDate 列をマップします。  
  
    -   NewAmount の列、入力データにマイニング モデルの Amount 列をマップします。  
  
    -   NewQty の列、入力データにマイニング モデル内の数量列をマップします。  
  
    -   入力データの系列の列をマイニング モデルで、ModelRegion 列をマップします。  
  
7.  ここで、予測クエリを作成します。  
  
     最初に、列を予測クエリに追加し、予測を適用する系列を出力します。  
  
    1.  グリッドで、場合は、下にある最初の空白行をクリックして**ソース**、し、予測を選択します。  
  
    2.  **フィールド**列、モデルの Region を選択および**エイリアス**、型`Model Region`です。  
  
8.  次に、予測関数を追加して編集します。  
  
    1.  空の行をクリックし、**ソース****予測関数**です。  
  
    2.  **フィールド** **PredictTimeSeries**です。  
  
    3.  **エイリアス**、型**Predicted Values**です。  
  
    4.  Quantity フィールドをドラッグしてから、**マイニング モデルの**ペイン、**条件と引数**列です。  
  
    5.  **条件と引数** 列のフィールド名の後に、次のテキストを入力: **5, EXTEND_MODEL_CASES**  
  
         完全なテキスト、**条件と引数**テキスト ボックスは次のようにする必要があります。 `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`  
  
9. をクリックして**結果**し、結果を確認します。  
  
     予測は 7 月 (元のデータが終了した後の最初のタイム スライス) から開始し、11 月 (元のデータが終了した後の 5 番目のタイム スライス) で終了しています。  
  
 この種の予測クエリを効率よく使用するには、古いデータがいつ終了し、新しいデータにタイム スライスがいくつあるかを知る必要があります。  
  
 たとえば、このモデルでは、元のデータ系列は 6 月に終了し、データは 7 月、8 月、9 月のものになります。  
  
 EXTEND_MODEL_CASES を使用する予測は常に、元のデータ系列の終了から開始します。 そのため、不明の月の予測のみを取得するには、予測の開始位置と終了位置を指定する必要があります。 どちらの値も、古いデータの終わりから始まるタイム スライスの数として指定されます。  
  
 次の手順は、これを行う方法を示します。  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a>予測の開始位置と終了位置を変更します。  
  
1.  予測クエリ ビルダーで、をクリックして**クエリ**DMX ビューに切り替えます。  
  
2.  PredictTimeSeries 関数が含まれている DMX ステートメントを見つけて、次のように変更します。  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  をクリックして**結果**し、結果を確認します。  
  
     予測が 10 月 (元のデータが終了してから 4 番目のタイム スライス) から開始し、12 月 (元のデータが終了してから 6 番目のタイム スライス) で終了するようになります。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [置き換え後のデータを使用して時系列予測&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [タイム シリーズ モデルのマイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
