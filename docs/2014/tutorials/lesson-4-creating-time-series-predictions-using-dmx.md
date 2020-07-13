---
title: 'レッスン 4: DMX を使用した時系列予測の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63312091"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>レッスン 4: DMX を使用した時系列予測の作成
  このレッスンと次のレッスンでは、データマイニング拡張機能 (DMX) を使用して、 [「レッスン 1: 時系列マイニングモデルとマイニング構造の作成](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)」で作成したタイムシリーズモデルに基づいてさまざまな種類の予測を作成し、「[レッスン 2: 時系列マイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)」を使用します。  
  
 時系列モデルでは、さまざまな方法で予測を作成できます。  
  
-   マイニング モデル内の既存のパターンとデータを使用する。  
  
-   マイニング モデル内の既存のパターンを使用し、データは新たに供給する。  
  
-   モデルに新しいデータを追加するか、モデルを更新する。  
  
 このような予測を作成するための構文を以下にまとめます。  
  
 既定の時系列予測  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を使用して、トレーニング済みのマイニングモデルから指定された数の予測を返します。  
  
 例については、「 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)または[タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)」を参照してください。  
  
 EXTEND_MODEL_CASES  
 新しいデータの追加、系列の拡張、および更新されたマイニングモデルに基づく予測の作成を行うには、 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を EXTEND_MODEL_CASES 引数と共に使用します。  
  
 このチュートリアルには、EXTEND_MODEL_CASES の使用例が示されています。  
  
 REPLACE_MODEL_CASES  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を REPLACE_MODEL_CASES 引数と共に使用して元のデータを新しいデータ系列に置き換え、マイニングモデルのパターンを新しいデータ系列に適用することに基づいて予測を作成します。  
  
 REPLACE_MODEL_CASES の使用方法の例については、「[レッスン 2: 予測シナリオの作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   既存のデータに基づいて既定の予測を取得するクエリの作成  
  
 この次のレッスンでは、関連する次の作業を行います。  
  
-   新しいデータを提供して更新された予測を取得するクエリの作成  
  
 DMX を使用して手動でクエリを作成する以外に、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で予測クエリ ビルダーを使用して予測を作成することもできます。  
  
## <a name="simple-time-series-prediction-query"></a>簡単な時系列予測クエリ  
 最初の手順では、`SELECT FROM` ステートメントを `PredictTimeSeries` 関数と共に使用して時系列予測を作成します。 時系列モデルでは、予測を作成するための簡略化された構文がサポートされます。入力データを提供する必要ありませんが、作成する予測の数を指定する必要があります。 使用するステートメントの汎用例を次に示します。  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 選択リストには、モデルの列を含めることができます。たとえば、予測を作成している製品ラインの名前や、タイムシリーズマイニングモデルに特化した[&#40;dmx&#41;](/sql/dmx/lag-dmx)や[PredictTimeSeries &#40;dmx&#41;](/sql/dmx/predicttimeseries-dmx)などの予測関数などです。  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>簡単な時系列予測クエリを作成するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     最初の行では、系列を識別する値をマイニング モデルから取得します。  
  
     2 行目と 3 行目では、`PredictTimeSeries` 関数を使用します。 各行で別々の属性 (`[Quantity]` または `[Amount]`) が予測されます。 予測可能な属性の名前の後の数値は、予測する時間ステップの数を示します。  
  
     `AS` 句は、各予測関数から返される列の名前を指定するために使用します。 別名を指定しない場合は、既定で両方の列が `Expression` というラベルで返されます。  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`SimpleTimeSeriesPrediction.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリから、`WHERE` 句で指定した製品と地域の 2 とおりの組み合わせごとに 6 つの予測が返されます。  
  
 次のレッスンでは、モデルに新しいデータを提供するクエリを作成し、その予測結果をここで作成した予測と比較します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [レッスン 5 : 時系列モデルの拡張](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;PredictTimeSeries](/sql/dmx/predicttimeseries-dmx)   
 [DMX&#41;&#40;Lag](/sql/dmx/lag-dmx)   
 [タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
