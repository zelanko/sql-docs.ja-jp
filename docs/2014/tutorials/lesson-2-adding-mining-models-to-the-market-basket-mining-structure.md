---
title: 'レッスン 2: マーケットバスケットマイニング構造へのマイニングモデルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63204720"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a>レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加
  このレッスンでは、「[レッスン 1: マーケットバスケットマイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)」で作成したマーケットバスケットマイニング構造に2つのマイニングモデルを追加します。 これらのマイニング モデルを使用すると、予測を作成できます。  
  
 顧客が同時に購入する傾向のある製品の種類を予測するには、 [Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)を使用して2つのマイニングモデルを作成し、 *MINIMUM_PROBABILTY*パラメーターに2つの異なる値を指定します。  
  
 *MINIMUM_PROBABILTY*は、 [!INCLUDE[msCoName](../includes/msconame-md.md)]ルールに必要な最小の確率を指定することによって、マイニングモデルに含まれるルールの数を決定するために使用されるアソシエーションアルゴリズムパラメーターです。 たとえば、この値を 0.4 に設定すると、ルールで記述する製品の組み合わせの発生確率が 40% 以上である場合にのみ、ルールが生成されます。  
  
 後のレッスンでは、 *MINIMUM_PROBABILTY*パラメーターを変更した場合の影響を確認します。  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE ステートメント  
 入れ子になったテーブルを含むマイニングモデルをマイニング構造に追加するには、 [ALTER マイニング構造 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)ステートメントを使用します。 ステートメント内のコードは、次の部分に分けることができます。  
  
-   マイニング構造の指定  
  
-   マイニング モデルの名前指定  
  
-   キー列の定義  
  
-   入力列と予測可能列の定義  
  
-   入れ子になったテーブル列の定義  
  
-   アルゴリズムとパラメーターの変更の特定  
  
 入れ子になったテーブル列を含む構造にマイニング モデルを追加する `ALTER MINING STRUCTURE` ステートメントの汎用例を次に示します。  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 コードの最初の行では、マイニング モデルの追加先となる既存のマイニング構造を指定します。  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の行では、マイニング構造に追加するマイニング モデルを指定します。  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 データマイニング拡張機能 (DMX) でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。  
  
 コードの次の行では、マイニングモデルによって使用されるマイニング構造の列を定義します。  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 使用できるのは、マイニング構造内に既に存在する列だけです。  
  
 マイニング モデル列の一覧の最初の列は、マイニング構造のキー列にする必要があります。 ただし、使用法を指定するため`KEY`にキー列の後に入力する必要はありません。 マイニング構造の作成時に、この列をキーとして定義済みであるためです。  
  
 残りの行では、新しいマイニング モデルにおける列の使用法を指定します。 次の構文を使用して、マイニングモデルの列が予測に使用されるように指定できます。  
  
```  
<column name> PREDICT,  
```  
  
 使用法を指定しない場合は、データ マイニング構造列を一覧に含める必要がありません。 参照されたデータ マイニング構造で使用されているすべての列が、その構造に基づくマイニング モデルで自動的に使用可能になります。 ただし、使用法を指定していない列は、モデルのトレーニングに使用されません。  
  
 コードの最後の行では、マイニング モデルの生成に使用するアルゴリズムとアルゴリズム パラメーターを定義します。  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   既定の確率を使用して、アソシエーション マイニング モデルを構造に追加します。  
  
-   変更した確率を使用して、アソシエーション マイニング モデルを構造に追加します。  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimum_probability"></a>既定の MINIMUM_PROBABILITY を使用した、構造への Association マイニング モデルの追加  
 最初のタスクでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] *MINIMUM_PROBABILITY*の既定値を使用して、アソシエーションアルゴリズムに基づいて新しいマイニングモデルをマーケットバスケットマイニング構造に追加します。  
  
#### <a name="to-add-an-association-mining-model"></a>Association マイニング モデルを追加するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
    > [!NOTE]  
    >  特定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに対する DMX クエリを作成するには、インスタンスではなくデータベースを右クリックします。  
  
2.  `ALTER MINING STRUCTURE` ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <mining structure name>   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [Market Basket]  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining model name>   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [Default Association]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     この場合、`[Products]` テーブルは予測可能列として指定されています。`.`また、`[Model]` 列は入れ子になったテーブルのキー列であるため、入れ子になったテーブル列の一覧に含まれています。  
  
    > [!NOTE]  
    >  入れ子になったキーは、ケース キーとは異なります。 Case キーは、大文字小文字を区別する一意の識別子ですが、入れ子になったキーはモデル化する属性です。  
  
6.  次の部分を探します。  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     これで、ステートメントは次のようになります。  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
8.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Default_Association_Model.dmx`、ファイル名を指定します。  
  
9. ツールバーの [**実行**] ボタンをクリックします。  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimum_probability"></a>既定の MINIMUM_PROBABILITY を変更した値による、構造への Association マイニング モデルの追加  
 次に、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムに基づいて、Market Basket マイニング構造に別のマイニング モデルを追加します。このとき、MINIMUM_PROBABILITY の既定値を 0.01 に変更します。 パラメーターを変更すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムによってさらに多くのルールが作成されます。  
  
#### <a name="to-add-an-association-mining-model"></a>Association マイニング モデルを追加するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  `ALTER MINING STRUCTURE` ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    <mining structure name>   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    Market Basket  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining model name>   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [Modified Association]  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     この場合、`[Products]` テーブルは予測可能列として指定されています。 また、`[MODEL]` 列は入れ子になったテーブルのキー列であるため、一覧に含まれています。  
  
6.  次の部分を探します。  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     これで、ステートメントは次のようになります。  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
8.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Modified Association_Model.dmx`、ファイル名を指定します。  
  
9. ツールバーの [**実行**] ボタンをクリックします。  
  
 次のレッスンでは、Market Basket マイニング構造とそれに関連するマイニング モデルを処理します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 3: Market Basket マイニング構造の処理](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
