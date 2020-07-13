---
title: 'レッスン 3: タイムシリーズの構造とモデルの処理 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63042878"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>レッスン 3: 時系列構造と時系列モデルの処理
  このレッスンでは、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用して、作成した時系列マイニング構造とマイニングモデルを処理します。  
  
 マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。 マイニング モデルとマイニング構造は、最初に作成したときに必ず処理する必要があります。 INSERT INTO を使用する場合、マイニング構造を指定すると、ステートメントによってマイニング構造とそれに関連するすべてのマイニング モデルが処理されます。  
  
 処理済みのマイニング構造にマイニング モデルを追加する場合は、`INSERT INTO MINING MODEL` ステートメントを使用することにより、既存のデータを使用して新しいマイニング モデルのみを処理できます。  
  
 マイニングモデルの処理の詳細については、「[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。  
  
## <a name="insert-into-statement"></a>INSERT INTO ステートメント  
 タイムシリーズマイニング構造とそれに関連付けられているすべてのマイニングモデルをトレーニングするには、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用します。 ステートメントのコードは次の部分に分けることができます。  
  
-   マイニング構造の指定  
  
-   マイニング構造の列の一覧  
  
-   トレーニング データの定義  
  
 `INSERT INTO` ステートメントの汎用例を次に示します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 コードの最初の行では、トレーニングするマイニング構造を指定します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の数行では、マイニング構造で定義される列を指定します。 ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 コードの最後の行では、マイニング構造のトレーニングに使用されるデータを定義します。  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 このレッスンでは、`OPENQUERY` を使用してソース データを定義します。 ソースデータに対するクエリを定義するその他の方法の詳細については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次の作業を実行します。  
  
-   マイニング構造 Forecasting_MIXED_Structure の処理  
  
-   関連するマイニング モデル Forecasting_MIXED、Forecasting_ARIMA、および Forecasting_ARTXP の処理  
  
## <a name="processing-the-time-series-mining-structure"></a>時系列マイニング構造の処理  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>INSERT INTO を使用してマイニング構造とそれに関連するマイニング モデルを処理するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    [<mining structure>]  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  次の部分を探します。  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     ソースクエリは、IntermediateTutorial [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]サンプルプロジェクトで定義されているデータソースを参照します。 ソース クエリはこのデータ ソースを使用して、vTimeSeries ビューにアクセスします。 このビューには、マイニング モデルのトレーニングに使用されるソース データが含まれています。 このプロジェクトまたはこのビューに慣れていない場合は、「[レッスン 2: 予測シナリオの構築」 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)を参照してください。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`ProcessForecastingAll.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
 クエリの実行が終了したら、処理済みのマイニング モデルを使用して予測を作成できます。 次のレッスンでは、作成したマイニング モデルに基づいて、いくつかの予測を作成します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4: DMX を使用した時系列予測の作成](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>参照  
 [データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;ソースデータクエリ&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery)  
  
  
