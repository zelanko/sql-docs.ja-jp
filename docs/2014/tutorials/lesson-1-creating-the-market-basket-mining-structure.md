---
title: 'レッスン 1: Market Basket マイニング構造の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2201afdb7226267e44686b76edb22e77b11dd199
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312440"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>レッスン 1: Market Basket マイニング構造の作成
  このレッスンでは、同時に購入される可能性が高い [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の製品を予測するためのマイニング構造を作成します。 マイニング構造およびデータ マイニングでは、そのロールに慣れていない場合は、次を参照してください。[マイニング構造&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)です。  
  
 このレッスンで作成するアソシエーション マイニング構造に基づく追加のマイニング モデルをサポートしている、 [Microsoft アソシエーション アルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)です。 後のレッスンでは、マイニング モデルを使用して、同時に購入される可能性が高い製品の種類を予測します。これはマーケット バスケット分析と呼ばれます。 たとえば、この予測で、マウンテン バイクとタイヤ、およびヘルメットが同時に購入される傾向にあることがわかります。  
  
 このレッスンでは、入れ子になったテーブルを使用してマイニング構造を定義します。 入れ子になったテーブルを使用するのは、マイニング構造で定義するデータ ドメインが、2 つの異なるソース テーブル内に含まれているためです。 入れ子になったテーブルの詳細については、次を参照してください。[入れ子になったテーブル&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)です。  
  
## <a name="create-mining-structure-statement"></a>マイニング構造のステートメントを作成します。  
 入れ子になったテーブルを含むマイニング構造を作成するために使用する、 [CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx)ステートメントです。 ステートメント内のコードは、次の部分に分類されます。  
  
-   構造の名前指定  
  
-   キー列の定義  
  
-   マイニング列の定義  
  
-   入れ子になったテーブル列の定義  
  
 CREATE MINING STRUCTURE ステートメントの汎用例を次に示します。  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 コードの 1 行目では、構造の名前を定義します。  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 DMX でオブジェクトの名前を付ける方法については、次を参照してください。[識別子&#40;DMX&#41;](/sql/dmx/identifiers-dmx)です。  
  
 コードの次の行では、マイニング構造のキー列を定義します。キー列は、ソース データ内のエンティティを一意に識別します。  
  
```  
<key column>  
```  
  
 その次の行では、マイニング構造に関連付けられたマイニング モデルで使用される、マイニング列を定義します。  
  
```  
<mining structure columns>  
```  
  
 コードの次の行では、入れ子になったテーブル列を定義します。  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 マイニング構造列を定義できるの種類については、次を参照してください。[マイニング構造列](../../2014/analysis-services/data-mining/mining-structure-columns.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、既定で、マイニング構造ごとに 30% の予約データ セットが作成されます。ただし、DMX を使用してマイニング構造を作成する場合は、必要に応じて予約データ セットを手動で追加する必要があります。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクは実行します。  
  
-   新しい空のクエリの作成  
  
-   マイニング構造を作成するためのクエリの変更  
  
-   クエリを実行します。  
  
## <a name="creating-the-query"></a>クエリを作成します。  
 最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio で新しい DMX クエリを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。  
  
2.  **サーバーへの接続**] ダイアログ ボックスの**サーバーの種類**[ **Analysis Services**です。 **サーバー名**、型`LocalHost`のインスタンスの名前または[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]このレッスン用に接続します。 **[接続]** をクリックします。  
  
3.  **オブジェクト エクスプ ローラー**のインスタンスを右クリックして[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、] をポイント**新しいクエリ**、クリックして**DMX**です。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
## <a name="altering-the-query"></a>クエリの変更  
 次の手順では、上の CREATE MINING STRUCTURE ステートメントを変更し、Market Basket マイニング構造を作成します。  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>CREATE MINING STRUCTURE ステートメントをカスタマイズするには  
  
1.  クエリ エディターでは、空のクエリに、CREATE MINING STRUCTURE ステートメントの汎用例をコピーします。  
  
2.  次の部分を探します。  
  
    ```  
    [mining structure name]   
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Market Basket]  
    ```  
  
3.  次の部分を探します。  
  
    ```  
    <key column>  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     これを次の文字列に置き換えます。  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     TEXT KEY 言語は、Model 列が入れ子になったテーブルのキー列であることを示します。  
  
     最終的なマイニング構造のステートメントは次のようになります。  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  **ファイル** メニューのをクリックして**付けて DMXQuery1.dmx を保存**です。  
  
6.  **名前を付けて保存**ダイアログ ボックスで、適切なフォルダーを参照し、ファイル名前`Market Basket Structure.dmx`です。  
  
## <a name="executing-the-query"></a>クエリの実行  
 最後の手順では、クエリを実行します。 クエリを作成して保存したら、サーバー上にマイニング構造を作成するためクエリを実行 (ステートメントを実行) します。 クエリ エディターでクエリの実行の詳細については、次を参照してください。[データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)です。  
  
#### <a name="to-execute-the-query"></a>クエリを実行するには  
  
-   クエリ エディターで、ツールバーで、クリックして**Execute**です。  
  
     クエリの状態が表示されて、**メッセージ**ステートメントの実行完了後のクエリ エディター下部にあるタブ。 この場合次のメッセージが表示されます。  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     という名前の新しい構造**マーケット バスケット**サーバーに存在するようになりました。  
  
 次のレッスンでは、作成した Market Basket マイニング構造にマイニング モデルを追加します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
