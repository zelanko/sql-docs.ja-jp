---
title: 'レッスン 5: 予測クエリの実行 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822314"
---
# <a name="lesson-5-executing-prediction-queries"></a>レッスン 5: 予測クエリの実行
  このレッスンでは、SELECT [FROM \<MODEL> 予測結合 (DMX)](/sql/dmx/select-from-model-cases-dmx)形式の select ステートメントを使用して、「[レッスン 2: アソシエーションマイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)」で作成したデシジョンツリーモデルに基づいて、2種類の予測を作成します。 作成する予測の種類は次のとおりです。  
  
 単一クエリ  
 予測を行う際にアドホック値を提供するには、単一クエリを使用します。 たとえば、顧客の通勤距離、市外局番、または子供の数などをクエリに入力して、1 人の顧客が自転車を購入するかどうかを判断できます。 単一クエリは、これらの入力に基づいてこの顧客が自転車を購入する可能性を示す値を返します。  
  
 バッチ クエリ  
 複数の潜在顧客が含まれるテーブルの中から、自転車を購入する可能性がある人物を特定するには、バッチ クエリを使用します。 たとえば、マーケティング部門から顧客と顧客の属性の一覧が提供された場合、バッチ予測を使用して、テーブルの中で自転車を購入する可能性が高い人物を特定できます。  
  
 Select [ \<FROM MODEL> 予測結合 (DMX)](/sql/dmx/select-from-model-cases-dmx)形式の select ステートメントには、次の3つの部分があります。  
  
-   結果で返される、マイニング モデル列と予測関数の一覧。 結果にはソース データからの入力列を含めることもできます。  
  
-   予測の作成に使用するデータを定義しているソース クエリ。 たとえば、バッチ クエリの場合は顧客の一覧などが該当します。  
  
-   マイニング モデル列とソース データ間のマッピング。 これらの名前が同じ場合は、NATURAL 構文を使用して列マッピングを省略できます。  
  
 予測関数を使用すると、さらにクエリを改良できます。 予測関数では、予測が発生する可能性など追加の情報と、トレーニング データセットでの予測サポートが提供されます。 予測関数の詳細については、「 [functions &#40;DMX&#41;](/sql/dmx/functions-dmx)」を参照してください。  
  
 このチュートリアルの予測は、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベースの ProspectiveBuyer テーブルに基づくものです。 ProspectiveBuyer テーブルには、潜在顧客と、それらの顧客に関連付けられている特性の一覧が格納されています。 このテーブルに格納されている顧客は、デシジョン ツリー マイニング モデルの作成で使用した顧客とは異なります。  
  
 
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の予測クエリ ビルダーを使用して予測を作成することもできます。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   特定の顧客が自転車を購入するかどうかを特定する単一クエリを作成します。  
  
-   複数の顧客が含まれるテーブルの中から、自転車を購入する可能性がある顧客を特定するバッチ クエリを作成します。  
  
## <a name="singleton-query"></a>単一クエリ  
 最初の手順では、 [SELECT FROM &#60;モデル&#62; 予測結合](/sql/dmx/select-from-model-cases-dmx)を使用して、単一予測クエリで DMX&#41;&#40;します。 単一ステートメントの汎用例を次に示します。  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 コードの最初の行では、クエリで返されるマイニング モデルの列を定義し、予測の生成に使用するマイニング モデルを指定します。  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 コードの次の行では、予測の作成に使用する顧客の特性を定義します。  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 NATURAL PREDICTION JOIN を指定した場合、サーバーでは、モデルの各列と入力された列が列名に基づいて照合されます。 列名が一致しない場合は無視されます。  
  
#### <a name="to-create-a-singleton-prediction-query"></a>単一予測クエリを作成するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の単一ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     AS ステートメントは、クエリで返される列に別名を付けるために使用します。 [PredictHistogram](/sql/dmx/predicthistogram-dmx)関数は、確率やサポートなど、予測に関する統計を返します。 予測ステートメントで使用できる関数の詳細については、「 [functions &#40;DMX&#41;](/sql/dmx/functions-dmx)」を参照してください。  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Singleton_Query.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリが実行され、指定した特性の顧客が自転車を購入するかどうかの予測と、予測に関する統計が返されます。  
  
## <a name="batch-query"></a>バッチ クエリ  
 次の手順では、 [SELECT FROM &#60;モデル&#62; 予測結合 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)をバッチ予測クエリで使用します。 バッチ ステートメントの汎用例を次に示します。  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 単一クエリと同様に、コードの最初の 2 行では、クエリで返されるマイニング モデルの列と、予測の生成に使用するマイニング モデルの名前を定義します。 TOP \<number> ステートメントは、クエリが数値または number> で\<指定された結果のみを返すことを指定します。  
  
 コードの次の数行では、予測の基になるソース データを定義します。  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 ソース データを取得するにはいくつかの方法がありますが、このチュートリアルでは OPENQUERY を使用します。 使用可能なオプションの詳細については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。  
  
 次の行では、マイニング モデルのソース列とソース データの列間のマッピングを定義します。  
  
```  
ON <column mappings>  
```  
  
 WHERE 句は、予測クエリで返される結果をフィルター処理します。  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 コードの最後の省略可能な行では、結果の列の順序を指定します。  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 ORDER BY と TOP \<number> ステートメントを組み合わせて使用して、返される結果をフィルター処理します。 たとえば、今回の予測では上位 10 人の自転車購入者が返され、結果は予測の精度が高い順序で並べ替えられます。 [DESC|ASC] 構文を使用すると、結果を表示する順序を制御できます。  
  
#### <a name="to-create-a-batch-prediction-query"></a>バッチ予測クエリを作成するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上のバッチ ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     TOP 10 句を指定すると、クエリによって上位 10 個の結果だけが返されます。 このクエリの ORDER BY ステートメントでは、予測の精度が高い順序で結果が並べ替えられ、可能性が高い上位 10 件の結果だけが返されます。  
  
4.  次のプレースホルダーを置換します。  
  
    ```  
    [<mining model>]   
    ```  
  
     置換後はモデルの名前になります。  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  次の一般的な OPENQUERY ステートメントを置き換えます。  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     置換後は、AdventureWork の現在のデータ ウェアハウスを参照するステートメントであり、次のようになります。  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  次の一般的な構文を置換します。  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     置換後は、このモデルと入力データ セットで必要とされる列のマッピングになります。  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     可能性の高い順に結果が一覧されるように、`DESC` を指定します。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
8.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Batch_Prediction.dmx`、ファイル名を指定します。  
  
9. ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリが実行され、顧客名、各顧客が自転車を購入するかどうかの予測、予測の精度を含むテーブルが返されます。  
  
 以上で Bike Buyer チュートリアルは終了です。 これで、顧客の類似性を特定し、潜在顧客が自転車を購入するかどうかを予測するために使用できるマイニング モデルのセットが完成しました。  
  
 マーケットバスケットシナリオで DMX を使用する方法については、「[マーケットバスケット dmx のチュートリアル](../../2014/tutorials/market-basket-dmx-tutorial.md)」を参照してください。  
  
  
