---
title: 'レッスン 4: マーケット バスケット予測の実行 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7f5ba3de919c8d38287e09061d399a331870f89a
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312860"
---
# <a name="lesson-4-executing-market-basket-predictions"></a>レッスン 4: マーケット バスケット予測の実行
  このレッスンでは、DMX を使用して`SELECT`を関連付けに基づく予測を作成するステートメントをモデルで作成した[レッスン 2: Market Basket マイニング構造にマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)です。 DMX の `SELECT` ステートメントを使用して、`PREDICTION JOIN` 句を追加することにより、予測クエリを作成します。 予測結合の構文の詳細については、次を参照してください。 [SELECT FROM&#60;モデル&#62;予測結合&#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)です。  
  
 **SELECT FROM\<モデル > PREDICTION JOIN**形式の`SELECT`ステートメントには、3 つの部分が含まれています。  
  
-   結果セットで返される、マイニング モデル列と予測関数の一覧。 この一覧にはソース データからの入力列を含めることもできます。  
  
-   予測の作成に使用するデータを定義するソース クエリ。 たとえば、多数の予測をバッチで作成する場合、ソース クエリで顧客の一覧を取得できます。  
  
-   マイニング モデル列とソース データ間のマッピング。 列の名前が同じ場合は、`NATURAL PREDICTION JOIN` 構文を使用して列マッピングを省略できます。  
  
 予測関数を使用すると、クエリを改良できます。 予測関数では、予測が発生する可能性などの追加の情報や、トレーニング データセットでの予測サポートが提供されます。 予測関数の詳細については、次を参照してください。[関数&#40;DMX&#41;](/sql/dmx/functions-dmx)です。  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で予測クエリ ビルダーを使用して、予測クエリを作成することもできます。  
  
## <a name="singleton-prediction-join-statement"></a>単一 PREDICTION JOIN ステートメント  
 使用して、単一クエリを作成するには、まず、 **SELECT FROM\<モデル > PREDICTION JOIN**構文を入力として値の 1 つのセットを指定することです。 単一ステートメントの汎用例を次に示します。  
  
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
 このレッスンでは、次のタスクは実行します。  
  
-   ショッピング カート内の既存のアイテムに基づいて、顧客が購入の場合、どのような他のアイテムを予測するクエリを作成します。 既定値は、マイニング モデルを使用して、このクエリを作成する*MINIMUM_PROBABILITY*です。  
  
-   既にショッピング カートに入っている製品に基づいて、他に購入される可能性のある製品を予測するクエリを作成します。 このクエリは、別のモデルに基づいて*MINIMUM_PROBABILITY* 0.01 に設定されています。 既定値ため*MINIMUM_PROBABILITY*アソシエーション モデルでは 0.3、このモデルに対するクエリは、既定のモデルのクエリよりも多くのアイテムを返す必要があります。  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimumprobability"></a>既定の MINIMUM_PROBABILITY が設定されたモデルを使用した予測の作成  
  
#### <a name="to-create-an-association-query"></a>アソシエーション クエリを作成するには  
  
1.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、クリックして**DMX**クエリ エディターを開きます。  
  
2.  `PREDICTION JOIN` ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     列名 [Products] だけを含めるを使用して、 [Predict &#40;DMX&#41; ](/sql/dmx/predict-dmx)関数の場合、3 つに、アルゴリズムによって返される製品の数を制限することができます。 さらに、`INCLUDE_STATISTICS` を使用して、製品ごとのサポート、確率、および調整済みの確率を返すこともできます。 これらの統計は、予測の精度を評価するときに役立ちます。  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     これを次の文字列に置き換えます。  
  
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
  
     これを次の文字列に置き換えます。  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     このステートメントでは、`UNION` ステートメントを使用して、予測された製品と共にショッピング カートに含まれる 3 つの製品を指定します。 `SELECT` ステートメント内の Model 列は、入れ子になった製品テーブル内のモデル列に対応しています。  
  
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
  
6.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
7.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`Association Prediction.dmx`です。  
  
8.  ツールバーで、をクリックして、 **Execute**ボタンをクリックします。  
  
     クエリによって、HL Mountain Tire、Fender Set - Mountain、ML Mountain Tire の 3 つの製品が含まれたテーブルが返されます。 テーブルには、返された製品が確率の順に表示されます。 返された製品のうち、クエリで指定した 3 つの製品と同じショッピング カートに入っている可能性の最も高いものが、テーブルの一番上に表示されます。 続いて表示される 2 つは、ショッピング カートに入っている可能性が次に高い製品です。 さらに、このテーブルには、予測の精度を表す統計も含まれます。  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimumprobability-of-001"></a>MINIMUM_PROBABILITY が 0.01 に設定されたマイニング モデルを使用した予測の作成  
  
#### <a name="to-create-an-association-query"></a>アソシエーション クエリを作成するには  
  
1.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、クリックして**DMX**クエリ エディターを開きます。  
  
2.  `PREDICTION JOIN` ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     これを次の文字列に置き換えます。  
  
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
  
     これを次の文字列に置き換えます。  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     このステートメントでは、`UNION` ステートメントを使用して、予測された製品と共にショッピング カートに含まれる 3 つの製品を指定します。 `SELECT` ステートメント内の `[Model]` 列は、入れ子になった製品テーブル内の列に対応しています。  
  
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
  
6.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
7.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`Modified Association Prediction.dmx`です。  
  
8.  ツールバーで、をクリックして、 **Execute**ボタンをクリックします。  
  
     クエリによって、HL Mountain Tire、Water Bottle、Fender Set - Mountain の 3 つの製品が含まれたテーブルが返されます。 テーブルには、これらの製品が確率の順に表示されます。 テーブルの一番上に表示されるのは、クエリで指定した 3 つの製品と同じショッピング カートに入っている可能性の最も高い製品です。 それ以外は、ショッピング カートに入っている可能性が次に高い製品です。 テーブルには、予測の精度を示す統計情報も含まれます。  
  
     わかるように、このクエリの結果の値、 *MINIMUM_PROBABILITY*パラメーターは、クエリによって返される結果に影響します。  
  
 これで、マーケット バスケットのチュートリアルの最後の手順が終了します。 このチュートリアルでは、同時に購入される可能性がある製品を予測するときに使用できる、モデルのセットを作成しました。  
  
 別の予測シナリオで DMX を使用する方法については、次を参照してください。 [Bike Buyer DMX のチュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)です。  
  
## <a name="see-also"></a>参照  
 [アソシエーション モデルのクエリ例](../../2014/analysis-services/data-mining/association-model-query-examples.md)   
 [データ マイニング クエリ インターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
