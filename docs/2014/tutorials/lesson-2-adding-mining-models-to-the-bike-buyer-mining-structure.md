---
title: 'レッスン 2: Bike Buyer マイニング構造にマイニング モデルの追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f6d66faaa2a62d753ad865dd249078045960dc97
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312900"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a>レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加
  このレッスンでは、作成した Bike Buyer マイニング構造に 2 つのマイニング モデルを追加します[レッスン 1: Bike Buyer マイニング構造を作成する](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)です。 これら 2 つのマイニング モデルを追加すると、一方のモデルでデータを調査でき、もう一方のモデルで予測を作成できます。  
  
 探索に基づくマイニング モデルを作成するはその特性によっては、潜在顧客を分類できます、方法、 [Microsoft クラスタ リング アルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)です。 後のレッスンでは、類似した特性を持つ顧客グループがこのアルゴリズムでどのように特定されるかについて学習します。 たとえば、ある特定の顧客グループは、住居が近く、自転車で通勤し、学歴が類似しているといった情報を得られる可能性があります。 このような分類を基にさまざまな顧客の関連性を把握し、この情報を使用して特定顧客をターゲットとしたマーケティング戦略を立てることができます。  
  
 基づくマイニング モデルを作成する、潜在顧客が自転車を購入する可能性があるかどうかを予測する、 [Microsoft デシジョン ツリー アルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)です。 このアルゴリズムではそれぞれの潜在顧客に関連付けられている情報を基に、自転車を購入するかどうかの予測に役立つ特性を見つけることができます。 特性が見つかったら、以前自転車を購入した顧客と新しい潜在顧客の特性値を比較して、新しい潜在顧客が自転車を購入する可能性を判定することができます。  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE ステートメント  
 使用するマイニング構造にマイニング モデルを追加するために、[ALTER MINING STRUCTURE &#40;DMX&#41;] ((~/dmx/alter-mining-structure-dmx.md) ステートメントです。 ステートメント内のコードは、次の部分に分類されます。  
  
-   マイニング構造の指定  
  
-   マイニング モデルの名前指定  
  
-   キー列の定義  
  
-   入力列と予測可能列の定義  
  
-   アルゴリズムとパラメーターの変更を特定します。  
  
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
  
 コードの最初の行には、マイニング モデルの追加先となる既存のマイニング構造を識別します。  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の行では、マイニング構造に追加するマイニング モデルを指定します。  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 DMX でオブジェクトの名前を付ける方法については、次を参照してください。[識別子&#40;DMX&#41;](/sql/dmx/identifiers-dmx)です。  
  
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
  
 調整できるアルゴリズム パラメーターの詳細については、次を参照してください。 [Microsoft デシジョン ツリー アルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)と[Microsoft クラスタ リング アルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)です。  
  
 次の構文で、マイニング モデルの列を予測に使用するよう指定できます。  
  
```  
<mining model column> PREDICT  
```  
  
 コードの最後の行 (省略可能) では、モデルの学習およびテストを行う際に適用するフィルターを定義します。 マイニング モデルにフィルターを適用する方法の詳細については、次を参照してください。[マイニング モデル フィルターの&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)です。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクは実行します。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムを使用して、デシジョン ツリー マイニング モデルを Bike Buyer 構造に追加。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムを使用して、クラスタリング マイニング モデルを Bike Buyer 構造に追加。  
  
-   すべてのケースの結果を表示する必要があるため、どちらのモデルにもまだフィルターを追加しません。  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a>デシジョン ツリー マイニング モデルを構造に追加します。  
 最初に、[!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づくマイニング モデルを追加します。  
  
#### <a name="to-add-a-decision-tree-mining-model"></a>デシジョン ツリー マイニング モデルを追加するには  
  
1.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、クリックして**DMX**クエリ エディターと新しい空のクエリを開きます。  
  
2.  上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <mining structure name>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining model name>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    Decision Tree  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    <mining model columns>,  
    ```  
  
     これを次の文字列に置き換えます。  
  
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
  
     これを次の文字列に置き換えます。  
  
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
  
7.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
8.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`DT_Model.dmx`です。  
  
9. ツールバーで、をクリックして、 **Execute**ボタンをクリックします。  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a>構造へのクラスター マイニング モデルの追加  
 次に、[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムに基づくマイニング モデルを、Bike Buyer マイニング構造に追加します。 クラスター マイニング モデルでは、マイニング構造に定義されている列をすべて使用します。したがって、マイニング列の定義を省略して、この構造にモデルを追加できます。  
  
#### <a name="to-add-a-clustering-mining-model"></a>クラスター マイニング モデルを追加するには  
  
1.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、順にクリック**DMX**をクエリ エディターが開き、新しい空のクエリを開きます。  
  
2.  上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <mining structure name>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining model>   
    ```  
  
     これを次の文字列に置き換えます。  
  
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
  
     これを次の文字列に置き換えます。  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
8.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`Clustering_Model.dmx`です。  
  
9. ツールバーで、をクリックして、 **Execute**ボタンをクリックします。  
  
 次のレッスンでは、モデルとマイニング構造を処理します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 3: Bike Buyer マイニング構造の処理](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
