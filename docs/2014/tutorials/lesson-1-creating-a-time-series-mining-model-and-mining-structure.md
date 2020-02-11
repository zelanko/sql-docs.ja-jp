---
title: 'レッスン 1: タイムシリーズマイニングモデルとマイニング構造の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62678449"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a>レッスン 1: 時系列マイニング モデルおよびマイニング構造の作成
  このレッスンでは、履歴データを基に時間の経過に応じて値を予測するためのマイニング モデルを作成します。 モデルを作成すると、基になる構造が自動的に生成され、追加のマイニング モデルのベースとして使用できるようになります。  
  
 このレッスンは、予測モデルおよび Microsoft Time Series アルゴリズムの要件について理解していることを前提としています。 詳細については、「 [Microsoft Time Series アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)」を参照してください。  
  
## <a name="create-mining-model-statement"></a>CREATE マイニングモデルステートメント  
 マイニングモデルを直接作成し、基になるマイニング構造を自動的に生成するには、 [CREATE マイニング model &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)ステートメントを使用します。 ステートメント内のコードは、次の部分に分けることができます。  
  
-   モデルの名前指定  
  
-   タイム スタンプの定義  
  
-   省略可能な系列キー列の定義  
  
-   予測可能な属性の定義  
  
 CREATE MINING MODEL ステートメントの汎用例を次に示します。  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 コードの 1 行目では、マイニング モデルの名前を定義します。  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 Analysis Services では、基になる構造に対し、モデル名の後に「_structure」を追加した名前が自動的に生成されます。これにより、構造名がモデル名と重複しないことが保証されます。 DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。  
  
 コードの次の行では、マイニング モデルのキー列を定義します。キー列は、時系列モデルでソース データの時間ステップを一意に識別します。 Time ステップは、列名と`KEY TIME`データ型の後にあるキーワードを使用して識別されます。 時系列モデルに別の系列キーが含まれている場合は、`KEY` キーワードでそのキーが識別されます。  
  
```  
<key columns>  
```  
  
 コードの次の行では、予測対象となるモデル内の列を定義します。 1 つのマイニング モデルに複数の予測可能な属性を含めることができます。 予測可能な属性が複数ある場合は、Microsoft Time Series アルゴリズムによって系列ごとに個別に分析が生成されます。  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   新しい空のクエリの作成  
  
-   マイニング モデルを作成するためのクエリの変更  
  
-   クエリを実行する  
  
## <a name="creating-the-query"></a>クエリの作成  
 最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio で新しい DMX クエリを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。  
  
2.  [**サーバーへの接続**] ダイアログボックスの [**サーバーの種類**] で、[ **Analysis Services**] を選択します。 [**サーバー名**] に`LocalHost`、このレッスンで接続するの[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスの名前またはを入力します。 
  **[接続]** をクリックします。  
  
3.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
## <a name="altering-the-query"></a>クエリの変更  
 次の手順では、CREATE MINING MODEL ステートメントを変更して、予測に使用されるマイニング モデルがその基になるマイニング構造と共に作成されるようにします。  
  
#### <a name="to-customize-the-create-mining-model-statement"></a>CREATE MINING MODEL ステートメントをカスタマイズするには  
  
1.  クエリ エディターで、CREATE MINING MODEL ステートメントの汎用例を空のクエリにコピーします。  
  
2.  次の部分を探します。  
  
    ```  
    [mining model name]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  次の部分を探します。  
  
    ```  
    <key columns>  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     
  `TIME KEY` キーワードは、ReportingDate 列に値を順に並べるための時間ステップ値が含まれていることを示します。 時間ステップのデータ型は、値が一意でデータの並べ替えが可能であれば、日付/時刻型、整数型、任意の順序付きデータ型のどれでもかまいません。  
  
     
  `TEXT` キーワードと `KEY` キーワードは、ModelRegion 列に追加の系列キーが含まれていることを示します。 使用できる系列キーは 1 つに限られており、列内の値は一意である必要があります。  
  
4.  次の部分を探します。  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     アルゴリズム パラメーター `AUTO_DETECT_PERIODICITY` = 0.8 では、アルゴリズムでデータの周期を検出するように指定しています。 1 に近い値を設定すると、多数のパターンを検出できますが、処理に時間がかかる可能性があります。  
  
     アルゴリズム パラメーター `FORECAST_METHOD` では、ARTXP、ARIMA、ARTXP と ARIMA の両方のうち、どれを使用してデータを分析するかを指定します。  
  
     キーワード `WITH DRILLTHROUGH` では、モデルが完成した後にソース データの詳細な統計を表示できるようにすることを指定します。 Microsoft タイム シリーズ ビューアーでモデルを参照する場合は、この句を追加する必要があります。 予測にはこの句は必要ありません。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Forecasting_MIXED.dmx`、ファイル名を指定します。  
  
## <a name="executing-the-query"></a>クエリの実行  
 最後の手順では、クエリを実行します。 クエリを作成して保存したら、そのクエリを実行してサーバーにマイニング モデルとそのマイニング構造を作成します。 クエリエディターでのクエリの実行の詳細については、「[データベースエンジンクエリエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)」を参照してください。  
  
#### <a name="to-execute-the-query"></a>クエリを実行するには  
  
-   クエリエディターのツールバーで、[**実行**] をクリックします。  
  
     クエリの状態は、ステートメントの実行が完了した後、クエリエディターの下部にある [**メッセージ**] タブに表示されます。 この場合次のメッセージが表示されます。  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     **Forecasting_MIXED_Structure**という名前の新しい構造が、関連するマイニングモデル**Forecasting_MIXED**と共にサーバーに存在するようになりました。  
  
 次のレッスンでは、作成した**Forecasting_MIXED**マイニング構造にマイニングモデルを追加します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: 時系列マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a>参照  
 [タイムシリーズモデルのマイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)   
 [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
