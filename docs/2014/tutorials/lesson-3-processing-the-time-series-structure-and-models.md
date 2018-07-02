---
title: 'レッスン 3: 処理時系列構造し、時系列モデル |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 652d88a0c977b45f6c1628020ae4e6fd8fae4ad9
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312650"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>レッスン 3: 時系列構造と時系列モデルの処理
  このレッスンでは使用して、 [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx)マイニング構造とマイニング モデルで作成したタイム シリーズを処理するステートメント。  
  
 マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。 マイニング モデルとマイニング構造は、最初に作成したときに必ず処理する必要があります。 INSERT INTO を使用する場合、マイニング構造を指定すると、ステートメントによってマイニング構造とそれに関連するすべてのマイニング モデルが処理されます。  
  
 処理済みのマイニング構造にマイニング モデルを追加する場合は、`INSERT INTO MINING MODEL` ステートメントを使用することにより、既存のデータを使用して新しいマイニング モデルのみを処理できます。  
  
 マイニング モデルの処理の詳細については、次を参照してください。[処理要件と考慮事項&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)です。  
  
## <a name="insert-into-statement"></a>INSERT INTO ステートメント  
 時系列マイニング構造とそのすべての関連するマイニング モデルをトレーニングするために使用して、 [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx)ステートメントです。 ステートメントのコードは次の部分に分けることができます。  
  
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
  
 このレッスンでは、`OPENQUERY` を使用してソース データを定義します。 ソース データに対するクエリを定義するその他の方法の詳細については、次を参照してください。 [&#60;ソース データ クエリ&#62;](/sql/dmx/source-data-query)です。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   マイニング構造 Forecasting_MIXED_Structure の処理  
  
-   関連するマイニング モデル Forecasting_MIXED、Forecasting_ARIMA、および Forecasting_ARTXP の処理  
  
## <a name="processing-the-time-series-mining-structure"></a>時系列マイニング構造の処理  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>INSERT INTO を使用してマイニング構造とそれに関連するマイニング モデルを処理するには  
  
1.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、クリックして**DMX**です。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    [<mining structure>]  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  次の部分を探します。  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     ソース クエリの参照、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] IntermediateTutorial サンプル プロジェクトで定義されているデータ ソース。 ソース クエリはこのデータ ソースを使用して、vTimeSeries ビューにアクセスします。 このビューには、マイニング モデルのトレーニングに使用されるソース データが含まれています。 このプロジェクトやこのビューに慣れていない場合は、次を参照してください。[レッスン 2: Building a Forecasting Scenario&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)です。  
  
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
  
6.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
7.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`ProcessForecastingAll.dmx`です。  
  
8.  ツールバーで、をクリックして、 **Execute**ボタンをクリックします。  
  
 クエリの実行が終了したら、処理済みのマイニング モデルを使用して予測を作成できます。 次のレッスンでは、作成したマイニング モデルに基づいて、いくつかの予測を作成します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4: DMX を使用した時系列予測の作成](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>参照  
 [処理の要件および考慮事項&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;ソース データ クエリ&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY &AMP;#40;DMX&AMP;#41;](/sql/dmx/source-data-query-openquery)  
  
  
