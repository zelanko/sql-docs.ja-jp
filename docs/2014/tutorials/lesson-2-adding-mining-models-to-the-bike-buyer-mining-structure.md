---
title: 'レッスン 2: 自転車購入者マイニング構造へのマイニングモデルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63131747"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a>レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加
  このレッスンでは、「[レッスン 1: 自転車購入者マイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)」で作成した自転車購入者マイニング構造に2つのマイニングモデルを追加します。 これら 2 つのマイニング モデルを追加すると、一方のモデルでデータを調査でき、もう一方のモデルで予測を作成できます。  
  
 潜在的な顧客がその特性によってどのように分類されるかを調べるには、 [Microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)に基づいてマイニングモデルを作成します。 後のレッスンでは、類似した特性を持つ顧客グループがこのアルゴリズムでどのように特定されるかについて学習します。 たとえば、ある特定の顧客グループは、住居が近く、自転車で通勤し、学歴が類似しているといった情報を得られる可能性があります。 このような分類を基にさまざまな顧客の関連性を把握し、この情報を使用して特定顧客をターゲットとしたマーケティング戦略を立てることができます。  
  
 潜在顧客が自転車を購入する可能性があるかどうかを予測するには、 [Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)に基づいてマイニングモデルを作成します。 このアルゴリズムではそれぞれの潜在顧客に関連付けられている情報を基に、自転車を購入するかどうかの予測に役立つ特性を見つけることができます。 特性が見つかったら、以前自転車を購入した顧客と新しい潜在顧客の特性値を比較して、新しい潜在顧客が自転車を購入する可能性を判定することができます。  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE ステートメント  
 マイニングモデルをマイニング構造に追加するには、 [ALTER マイニング構造 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)ステートメントを使用します。 ステートメント内のコードは、次の部分に分けることができます。  
  
-   マイニング構造の指定  
  
-   マイニング モデルの名前指定  
  
-   キー列の定義  
  
-   入力列と予測可能列の定義  
  
-   アルゴリズムとパラメーターの変更の特定  
  
 ALTER MINING MODEL ステートメントの汎用例を次に示します。  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 コードの最初の行では、マイニングモデルを追加する既存のマイニング構造を指定します。  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の行では、マイニング構造に追加するマイニング モデルを指定します。  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。  
  
 コードの次の数行では、マイニング モデルで使用するマイニング構造の列を定義します。  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 使用できるのは、マイニング構造内に既に存在する列だけです。一覧の最初の列は、マイニング構造のキー列にする必要があります。  
  
 コードの次の行では、マイニング モデルを生成するマイニング アルゴリズムと、アルゴリズムに設定できるアルゴリズム パラメーターを定義します。  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 調整できるアルゴリズムパラメーターの詳細については、「 [Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)」および「 [microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)」を参照してください。  
  
 次の構文で、マイニング モデルの列を予測に使用するよう指定できます。  
  
```  
<mining model column> PREDICT  
```  
  
 コードの最後の行 (省略可能) では、モデルの学習およびテストを行う際に適用するフィルターを定義します。 マイニングモデルにフィルターを適用する方法の詳細については、「 [Analysis Services データマイニング&#41;&#40;マイニングモデルのフィルター ](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   
  [!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムを使用して、デシジョン ツリー マイニング モデルを Bike Buyer 構造に追加。  
  
-   
  [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムを使用して、クラスタリング マイニング モデルを Bike Buyer 構造に追加。  
  
-   すべてのケースの結果を表示する必要があるため、どちらのモデルにもまだフィルターを追加しません。  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a>構造へのデシジョンツリーマイニングモデルの追加  
 最初に、[!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づくマイニング モデルを追加します。  
  
#### <a name="to-add-a-decision-tree-mining-model"></a>デシジョン ツリー マイニング モデルを追加するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターと、新しい空のクエリを開きます。  
  
2.  上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <mining structure name>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining model name>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    Decision Tree  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    <mining model columns>,  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     この場合、`[Bike Buyer]` 列は PREDICT 列として指定されています。  
  
6.  次の部分を探します。  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     WITH DRILLTHROUGH ステートメントを指定すると、マイニング モデルの構築に使用されたケースを閲覧できます。  
  
     これで、ステートメントは次のようになります。  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
8.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`DT_Model.dmx`、ファイル名を指定します。  
  
9. ツールバーの [**実行**] ボタンをクリックします。  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a>構造へのクラスター マイニング モデルの追加  
 次に、[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムに基づくマイニング モデルを、Bike Buyer マイニング構造に追加します。 クラスター マイニング モデルでは、マイニング構造に定義されている列をすべて使用します。したがって、マイニング列の定義を省略して、この構造にモデルを追加できます。  
  
#### <a name="to-add-a-clustering-mining-model"></a>クラスター マイニング モデルを追加するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックすると、クエリエディターが開き、新しい空のクエリが表示されます。  
  
2.  上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <mining structure name>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining model>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    Clustering Model  
    ```  
  
5.  次の部分を削除します。  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  次の部分を探します。  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
8.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Clustering_Model.dmx`、ファイル名を指定します。  
  
9. ツールバーの [**実行**] ボタンをクリックします。  
  
 次のレッスンでは、モデルとマイニング構造を処理します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 3: Bike Buyer マイニング構造の処理](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
