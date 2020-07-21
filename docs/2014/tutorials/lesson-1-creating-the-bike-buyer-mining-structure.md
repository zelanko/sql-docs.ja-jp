---
title: 'レッスン 1: 自転車購入者マイニング構造の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678502"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>レッスン 1: Bike Buyer マイニング構造の作成
  このレッスンでは、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の潜在顧客が自転車を購入するかどうかを予測するためのマイニング構造を作成します。 データマイニングでのマイニング構造とそのロールの詳細については、「[マイニング構造 &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」を参照してください。  
  
 このレッスンで作成する自転車購入者マイニング構造は、microsoft[クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)に基づくマイニングモデルの追加をサポートしています。 後のレッスンでは、クラスター マイニング モデルを使用して顧客をグループ化するさまざまな方法を確認し、デシジョン ツリー マイニング モデルを使用して潜在顧客が自転車を購入するかどうかを予測します。  
  
## <a name="create-mining-structure-statement"></a>CREATE マイニング構造ステートメント  
 マイニング構造を作成するには、 [CREATE マイニング structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)ステートメントを使用します。 ステートメント内のコードは、次の部分に分けることができます。  
  
-   構造に名前を付けます。  
  
-   キー列を定義しています。  
  
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
  
 データマイニング拡張機能 (DMX) でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。  
  
 コードの次の行では、マイニング構造のキー列を定義します。キー列は、ソース データ内のエンティティを一意に識別します。  
  
```  
<key column>,  
```  
  
 作成するマイニング構造では、顧客の識別子 `CustomerKey` でソース データ内のエンティティが定義されます。  
  
 その次の行では、マイニング構造に関連付けられたマイニング モデルで使用される、マイニング列を定義します。  
  
```  
<mining structure columns>  
```  
  
 次の構文を使用すると\<、分離関数をマイニング構造列> 内で使用して連続列を分離できます。  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 分離列の詳細については、「[データマイニング&#41;&#40;分離メソッド](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)」を参照してください。 定義できるマイニング構造列の種類の詳細については、「[マイニング構造列](../../2014/analysis-services/data-mining/mining-structure-columns.md)」を参照してください。  
  
 コードの最後の行では、マイニング構造の省略可能なパーティションを定義します。  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 構造に関連するマイニング モデルのテストに使用するためにデータの一部を指定し、残りのデータはモデルのトレーニングに使用します。 既定では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって、全ケース データの 30% から成るテスト データセットが作成されます。 テスト データセットがケースの 30% になるように指定を追加します (最大 1000 ケース)。 ケースの 30% が 1000 より小さい場合、テスト データセットの量はもっと少なくなります。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   新しい空のクエリを作成します。  
  
-   マイニング構造を作成するようにクエリを変更します。  
  
-   クエリを実行します。  
  
## <a name="creating-the-query"></a>クエリの作成  
 最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio で新しい DMX クエリを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。  
  
2.  [**サーバーへの接続**] ダイアログボックスの [**サーバーの種類**] で、[ **Analysis Services**] を選択します。 [**サーバー名**] に`LocalHost`、このレッスンで接続するの[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスの名前を入力するか、入力します。 **[Connect]** をクリックします。  
  
3.  **オブジェクトエクスプローラー**で[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、のインスタンスを右クリックし、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックして**クエリエディター**を開き、新しい空のクエリをクリックします。  
  
## <a name="altering-the-query"></a>クエリの変更  
 次の手順では、上の CREATE MINING STRUCTURE ステートメントを変更し、Bike Buyer マイニング構造を作成します。  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>CREATE MINING STRUCTURE ステートメントをカスタマイズするには  
  
1.  クエリ エディターで、CREATE MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
2.  次の部分を探します。  
  
    ```  
    [<mining structure>]   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  次の部分を探します。  
  
    ```  
    <key column>   
    ```  
  
     次の内容に置き換えます。  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>   
    ```  
  
     次の内容に置き換えます。  
  
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
  
     次の内容に置き換えます。  
  
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
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Bike Buyer Structure.dmx`、ファイル名を指定します。  
  
## <a name="executing-the-query"></a>クエリの実行  
 最後の手順では、クエリを実行します。 クエリを作成して保存したら、そのクエリを実行する必要があります。 つまり、サーバーでマイニング構造を作成するには、ステートメントを実行する必要があります。 クエリエディターでのクエリの実行の詳細については、「[データベースエンジンクエリエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)」を参照してください。  
  
#### <a name="to-execute-the-query"></a>クエリを実行するには  
  
1.  クエリエディターのツールバーで、[**実行**] をクリックします。  
  
     クエリの状態は、ステートメントの実行が完了した後、クエリエディターの下部にある [**メッセージ**] タブに表示されます。 この場合次のメッセージが表示されます。  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     **自転車購入**者という名前の新しい構造がサーバーに存在するようになりました。  
  
 次のレッスンでは、作成した構造にマイニング モデルを追加します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
