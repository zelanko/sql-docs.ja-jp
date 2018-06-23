---
title: 'レッスン 1: Bike Buyer マイニング構造の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 53bacee483c3c36075cefcc789a8262b683e5370
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312520"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>レッスン 1: Bike Buyer マイニング構造の作成
  このレッスンでは、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の潜在顧客が自転車を購入するかどうかを予測するためのマイニング構造を作成します。 マイニング構造およびデータ マイニングでは、そのロールに慣れていない場合は、次を参照してください。[マイニング構造&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)です。  
  
 このレッスンで作成する Bike Buyer マイニング構造に基づく追加のマイニング モデルをサポートしている、 [Microsoft クラスタ リング アルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft デシジョン ツリー アルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)です。 後のレッスンでは、クラスター マイニング モデルを使用して顧客をグループ化するさまざまな方法を確認し、デシジョン ツリー マイニング モデルを使用して潜在顧客が自転車を購入するかどうかを予測します。  
  
## <a name="create-mining-structure-statement"></a>マイニング構造のステートメントを作成します。  
 使用するマイニング構造を作成する、 [CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx)ステートメントです。 ステートメント内のコードは、次の部分に分類されます。  
  
-   構造の名前を指定します。  
  
-   キー列を定義します。  
  
-   マイニング列の定義  
  
-   省略可能なテスト データセットの定義  
  
 CREATE MINING STRUCTURE ステートメントの汎用例を次に示します。  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 コードの 1 行目では、構造の名前を定義します。  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 オブジェクトのデータ マイニング拡張機能 (DMX) の名前付け規則については、次を参照してください。[識別子&#40;DMX&#41;](/sql/dmx/identifiers-dmx)です。  
  
 コードの次の行では、マイニング構造のキー列を定義します。キー列は、ソース データ内のエンティティを一意に識別します。  
  
```  
<key column>,  
```  
  
 作成するマイニング構造では、顧客の識別子 `CustomerKey` でソース データ内のエンティティが定義されます。  
  
 その次の行では、マイニング構造に関連付けられたマイニング モデルで使用される、マイニング列を定義します。  
  
```  
<mining structure columns>  
```  
  
 内で DISCRETIZE 関数を使用する\<マイニング構造列 > を次の構文を使用して、連続列を分離します。  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 列の分離の詳細については、次を参照してください。[分離メソッド&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)です。 マイニング構造列を定義することの種類の詳細については、次を参照してください。[マイニング構造列](../../2014/analysis-services/data-mining/mining-structure-columns.md)です。  
  
 コードの最後の行では、マイニング構造の省略可能なパーティションを定義します。  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 構造に関連するマイニング モデルのテストに使用するためにデータの一部を指定し、残りのデータはモデルのトレーニングに使用します。 既定では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって、全ケース データの 30% から成るテスト データセットが作成されます。 テスト データセットがケースの 30% になるように指定を追加します (最大 1000 ケース)。 ケースの 30% が 1000 より小さい場合、テスト データセットの量はもっと少なくなります。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクは実行します。  
  
-   新しい空のクエリを作成します。  
  
-   マイニング構造を作成するクエリを変更します。  
  
-   クエリを実行します。  
  
## <a name="creating-the-query"></a>クエリを作成します。  
 最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio で新しい DMX クエリを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。  
  
2.  **サーバーへの接続**] ダイアログ ボックスの**サーバーの種類**[ **Analysis Services**です。 **サーバー名**、型`LocalHost`のインスタンスの名前を入力または[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]このレッスン用に接続します。 **[接続]** をクリックします。  
  
3.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、指す**新しいクエリ**、順にクリック**DMX**を開くには、**クエリ エディター**と新しい空のクエリ。  
  
## <a name="altering-the-query"></a>クエリの変更  
 次の手順では、上の CREATE MINING STRUCTURE ステートメントを変更し、Bike Buyer マイニング構造を作成します。  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>CREATE MINING STRUCTURE ステートメントをカスタマイズするには  
  
1.  クエリ エディターで、CREATE MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
2.  次の部分を探します。  
  
    ```  
    [<mining structure>]   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  次の部分を探します。  
  
    ```  
    <key column>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  次の部分を探します。  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     最終的なマイニング構造のステートメントは次のようになります。  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
7.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`Bike Buyer Structure.dmx`です。  
  
## <a name="executing-the-query"></a>クエリの実行  
 最後の手順では、クエリを実行します。 クエリを作成して保存したら、そのクエリを実行する必要があります。 つまり、サーバーでマイニング構造を作成するには、ステートメントを実行する必要があります。 クエリ エディターでクエリの実行の詳細については、次を参照してください。[データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)です。  
  
#### <a name="to-execute-the-query"></a>クエリを実行するには  
  
1.  クエリ エディターで、ツールバーで、クリックして**Execute**です。  
  
     クエリの状態が表示されて、**メッセージ**ステートメントの実行完了後のクエリ エディター下部にあるタブ。 この場合次のメッセージが表示されます。  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     という名前の新しい構造**Bike Buyer**サーバーに存在するようになりました。  
  
 次のレッスンでは、作成した構造にマイニング モデルを追加します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
