---
title: 'レッスン 4: マーケットバスケット予測の実行 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63312108"
---
# <a name="lesson-4-executing-market-basket-predictions"></a>レッスン 4: マーケット バスケット予測の実行
  このレッスンでは、DMX `SELECT`ステートメントを使用して、 [「レッスン 2: マーケットバスケットマイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)」で作成したアソシエーションモデルに基づいて予測を作成します。 DMX の `SELECT` ステートメントを使用して、`PREDICTION JOIN` 句を追加することにより、予測クエリを作成します。 予測結合の構文の詳細については、「 [SELECT FROM &#60;model&#62; DMX&#41;&#40;の予測結合](/sql/dmx/select-from-model-cases-dmx)」を参照してください。  
  
 ステートメントの**SELECT \<FROM MODEL> 予測結合**形式には、次の3つの部分が含まれます。 `SELECT`  
  
-   結果セットで返される、マイニング モデル列と予測関数の一覧。 この一覧にはソース データからの入力列を含めることもできます。  
  
-   予測の作成に使用するデータを定義するソース クエリ。 たとえば、多数の予測をバッチで作成する場合、ソース クエリで顧客の一覧を取得できます。  
  
-   マイニング モデル列とソース データ間のマッピング。 列の名前が同じ場合は、`NATURAL PREDICTION JOIN` 構文を使用して列マッピングを省略できます。  
  
 予測関数を使用すると、クエリを改良できます。 予測関数では、予測が発生する可能性などの追加の情報や、トレーニング データセットでの予測サポートが提供されます。 予測関数の詳細については、「 [functions &#40;DMX&#41;](/sql/dmx/functions-dmx)」を参照してください。  
  
 
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で予測クエリ ビルダーを使用して、予測クエリを作成することもできます。  
  
## <a name="singleton-prediction-join-statement"></a>単一 PREDICTION JOIN ステートメント  
 最初の手順では、 **SELECT FROM \<MODEL> 予測結合**構文を使用し、入力として1つの値セットを指定して、単一クエリを作成します。 単一ステートメントの汎用例を次に示します。  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 コードの最初の行では、クエリで返されるマイニング モデルの列を定義し、予測の生成に使用するマイニング モデルの名前を指定します。  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 コードの次の行は、実行する操作を示しています。 各列に値を指定し、モデルと正確に一致するように列名を入力するため、`NATURAL PREDICTION JOIN` 構文を使用できます。 ただし、列名が異なる場合は、`ON` 句を追加して、モデルの列と新しいデータの列の間のマッピングを指定する必要があります。  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 次の行では、追加購入される製品の予測に使用する、ショッピング カート内の製品を定義します。  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   買い物かごに既に存在する商品に基づいて、顧客が購入する可能性のある他のアイテムを予測するクエリを作成します。 このクエリは、既定の*MINIMUM_PROBABILITY*を持つマイニングモデルを使用して作成します。  
  
-   既にショッピング カートに入っている製品に基づいて、他に購入される可能性のある製品を予測するクエリを作成します。 このクエリは、 *MINIMUM_PROBABILITY*が0.01 に設定されている別のモデルに基づいています。 アソシエーションモデルの*MINIMUM_PROBABILITY*の既定値は0.3 なので、このモデルのクエリでは、既定のモデルのクエリよりも多くの項目が返されます。  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a>既定の MINIMUM_PROBABILITY が設定されたモデルを使用した予測の作成  
  
#### <a name="to-create-an-association-query"></a>アソシエーション クエリを作成するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターを開きます。  
  
2.  
  `PREDICTION JOIN` ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     列名 [Products] を含めることもできますが、 [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx)関数を使用すると、アルゴリズムによって返される製品の数を3つに制限することができます。 さらに、`INCLUDE_STATISTICS` を使用して、製品ごとのサポート、確率、および調整済みの確率を返すこともできます。 これらの統計は、予測の精度を評価するときに役立ちます。  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Default Association]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     このステートメントでは、`UNION` ステートメントを使用して、予測された製品と共にショッピング カートに含まれる 3 つの製品を指定します。 
  `SELECT` ステートメント内の Model 列は、入れ子になった製品テーブル内のモデル列に対応しています。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Association Prediction.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリによって、HL Mountain Tire、Fender Set - Mountain、ML Mountain Tire の 3 つの製品が含まれたテーブルが返されます。 テーブルには、返された製品が確率の順に表示されます。 返された製品のうち、クエリで指定した 3 つの製品と同じショッピング カートに入っている可能性の最も高いものが、テーブルの一番上に表示されます。 続いて表示される 2 つは、ショッピング カートに入っている可能性が次に高い製品です。 さらに、このテーブルには、予測の精度を表す統計も含まれます。  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a>MINIMUM_PROBABILITY が 0.01 に設定されたマイニング モデルを使用した予測の作成  
  
#### <a name="to-create-an-association-query"></a>アソシエーション クエリを作成するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターを開きます。  
  
2.  
  `PREDICTION JOIN` ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Modified Association]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     このステートメントでは、`UNION` ステートメントを使用して、予測された製品と共にショッピング カートに含まれる 3 つの製品を指定します。 
  `[Model]` ステートメント内の `SELECT` 列は、入れ子になった製品テーブル内の列に対応しています。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Modified Association Prediction.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリによって、HL Mountain Tire、Water Bottle、Fender Set - Mountain の 3 つの製品が含まれたテーブルが返されます。 テーブルには、これらの製品が確率の順に表示されます。 テーブルの一番上に表示されるのは、クエリで指定した 3 つの製品と同じショッピング カートに入っている可能性の最も高い製品です。 それ以外は、ショッピング カートに入っている可能性が次に高い製品です。 このテーブルには、予測の精度を示す統計も含まれています。  
  
     このクエリの結果から、 *MINIMUM_PROBABILITY*パラメーターの値がクエリによって返される結果に影響することを確認できます。  
  
 これで、マーケット バスケットのチュートリアルの最後の手順が終了します。 このチュートリアルでは、同時に購入される可能性がある製品を予測するときに使用できる、モデルのセットを作成しました。  
  
 別の予測シナリオで DMX を使用する方法については、「[自転車購入者向け Dmx チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [アソシエーションモデルのクエリ例](../../2014/analysis-services/data-mining/association-model-query-examples.md)   
 [データ マイニング クエリ インターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
