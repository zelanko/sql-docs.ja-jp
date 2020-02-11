---
title: 'レッスン 5: タイムシリーズモデルの拡張 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2716e985897f8115d189d9410b7cdb13fb1af291
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822072"
---
# <a name="lesson-5-extending-the-time-series-model"></a>レッスン 5 : 時系列モデルの拡張
  
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise Edition では、時系列モデルに新しいデータを追加し、モデルに新しいデータを自動的に組み込むことができます。 次の 2 つの方法のいずれかで、時系列マイニング モデルに新しいデータを追加します。  
  
-   PREDICTION JOIN を使用してトレーニング データに外部ソースのデータを結合します。  
  
-   単一予測クエリを使用してデータにスライスを 1 つずつ指定します。  
  
 たとえば、数か月前に既存の売上データでマイニング モデルをトレーニングしたとします。 新たな売上があったときに、新しいデータを組み込んで売上予測を更新する必要があります。 この処理は 1 回の操作で実行できます。具体的には、新しい売上数値を入力データとして指定し、複合データセットに基づいて新しい予測を生成します。  
  
## <a name="making-predictions-with-extend_model_cases"></a>EXTEND_MODEL_CASES を使用した予測の作成  
 次に示すのは、EXTEND_MODEL_CASES を使用する時系列予測の汎用例です。 最初の例では、元のモデルの最後の時間ステップから始まる予測の数を指定します。  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 2 番目の例では、予測を開始する時間ステップと予測を終了する時間ステップを指定します。 既定では、予測クエリに使用される時間ステップが常に元の系列の末尾から開始されるため、モデル ケースを拡張する場合はこのオプションが重要となります。  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 このチュートリアルでは、両方の種類のクエリを作成します。  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a>時系列モデルに対する単一予測クエリを作成するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の単一ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     最初の行では、系列を識別する値がモデルから取得されます。  
  
     2 行目には、Quantity に関する 6 つの予測を取得する予測関数が示されています。 予測結果の列には、結果をわかりやすくするために `PredictQty` という別名が割り当てられています。  
  
4.  次の部分を探します。  
  
    ```  
    FROM <mining model>  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  次の部分を探します。  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
8.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Singleton_TimeSeries_Query.dmx`、ファイル名を指定します。  
  
9. ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリから、ヨーロッパ地域および太平洋地域での M200 自転車の販売数量の予測が返されます。  
  
## <a name="understanding-prediction-start-with-extend_model_cases"></a>EXTEND_MODEL_CASES を使用した予測の開始について  
 元のモデルを基に新しいデータで予測を作成しました。次に、結果を比較して、売上データの更新が予測に与える影響を確認します。 その前に、作成したコードを確認し、次の点を確認してください。  
  
-   ヨーロッパ地域についてのみ新しいデータを指定しています。  
  
-   新しいデータは 2 か月分のみ指定しています。  
  
 "M200 Europe" に対して指定した新しい値が予測に与える影響を次の表に示します。 太平洋地域の M200 製品には新しいデータを指定していませんが、比較のためにこの系列も示されています。  
  
 **製品と地域: M200 ヨーロッパ**  
  
|||||  
|-|-|-|-|  
|||既存のモデル (`PredictTimeSeries`)|更新された売上データを使用するモデル (`PredictTimeSeries` が指定された `EXTEND_MODEL_CASES`)|  
|M200 ヨーロッパ|7/25/2008 12:00:00 AM|77|10|  
|M200 ヨーロッパ|8/25/2008 12:00:00 AM|64|15|  
|M200 ヨーロッパ|9/25/2008 12:00:00 AM|59|72|  
|M200 ヨーロッパ|10/25/2008 12:00:00 AM|56|69|  
|M200 ヨーロッパ|11/25/2008 12:00:00 AM|56|68|  
|M200 ヨーロッパ|12/25/2008 12:00:00 AM|74|89|  
  
 **製品と地域: M200 太平洋**  
  
|||||  
|-|-|-|-|  
|||既存のモデル (`PredictTimeSeries`)|更新された売上データを使用するモデル (`PredictTimeSeries` が指定された `EXTEND_MODEL_CASES`)|  
|M200 太平洋|7/25/2008 12:00:00 AM|41|41|  
|M200 太平洋|8/25/2008 12:00:00 AM|44|44|  
|M200 太平洋|9/25/2008 12:00:00 AM|38|38|  
|M200 太平洋|10/25/2008 12:00:00 AM|41|41|  
|M200 太平洋|11/25/2008 12:00:00 AM|36|36|  
|M200 太平洋|12/25/2008 12:00:00 AM|39|39|  
  
 これらの結果から、次の 2 つのことがわかります。  
  
-   M200 Europe 系列に対する最初の 2 つの予測は、指定した新しいデータとまったく同じです。 Analysis Services の仕様では、予測を作成するのではなく実際の新しいデータ ポイントが返されます。 これは、モデル ケースを拡張する際に、予測クエリに使用される時間ステップが常に元の系列の末尾から開始されるためです。 このため、2 つの新しいデータ ポイントを追加すると、返される最初の 2 つの予測が新しいデータと重複します。  
  
-   新しいデータ ポイントがすべて使用された後に、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で更新されたモデルに基づいて予測が作成されます。 このため、2005 年 9 月以降は、左の列に示された元のモデルの M200 Europe と右の列に示された EXTEND_MODEL_CASES を使用するモデルとで予測が異なっています。 予測が異なっているのは、モデルが新しいデータで更新されたためです。  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a>開始および終了時間ステップを使用した予測の制御  
 モデルを拡張すると、新しいデータは常に系列の末尾に追加されます。 ただし、予測の目的から、予測クエリに使用されるタイム スライスは元の系列の末尾から開始されます。 新しいデータを追加する場合に新しい予測のみを取得するには、開始位置をタイム スライスの番号で指定する必要があります。 たとえば、2 つの新しいデータ ポイントを追加して 4 つの新しい予測を作成するには、次の操作を行います。  
  
-   時系列モデルに PREDICTION JOIN を作成し、2 か月分の新しいデータを指定します。  
  
-   4 つのタイム スライスについて予測を要求します。この場合、開始位置がタイム スライス 3、終了位置がタイム スライス 6 です。  
  
 つまり、新しいデータに n 個のタイムスライスが含まれていて、時間ステップ 1 ~ n の予測を要求した場合、予測は新しいデータと同じ期間になります。 データに含まれていない期間の新しい予測を取得するには、新しいデータ系列後のタイム スライス n+1 から予測を開始するか、他のタイム スライスの要求を行うようにする必要があります。  
  
> [!NOTE]  
>  新しいデータを追加するときは履歴予測を作成することはできません。  
  
 次の例は、前の例の 2 つの系列に対する新しい予測のみを取得する DMX ステートメントを示しています。  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 予測結果はタイム スライス 3、つまり指定した 2 か月分の新しいデータの後から開始しています。  
  
 **製品と地域: M200 ヨーロッパ**  
  
 更新されたデータを使用するモデル (EXTEND_MODEL_CASES を指定した PredictTimeSeries)  
  
||||  
|-|-|-|  
|M200 ヨーロッパ|9/25/2008 12:00:00 AM|72|  
|M200 ヨーロッパ|10/25/2008 12:00:00 AM|69|  
|M200 ヨーロッパ|11/25/2008 12:00:00 AM|68|  
|M200 ヨーロッパ|12/25/2008 12:00:00 AM|89|  
  
## <a name="making-predictions-with-replace_model_cases"></a>REPLACE_MODEL_CASES を使用した予測の作成  
 1 セットのケースでモデルをトレーニングし、そのモデルを別のデータ系列に適用するときは、モデル ケースの置換が便利です。 このシナリオの詳細なチュートリアルについては、 [「レッスン 2: 予測シナリオの構築 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)」で説明されています。  
  
## <a name="see-also"></a>参照  
 [タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [DMX&#41;&#40;PredictTimeSeries](/sql/dmx/predicttimeseries-dmx)  
  
  
