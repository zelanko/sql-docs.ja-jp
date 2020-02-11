---
title: 'レッスン 1: マーケットバスケットのマイニング構造を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676269"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>レッスン 1: Market Basket マイニング構造の作成
  このレッスンでは、同時に購入される可能性が高い [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の製品を予測するためのマイニング構造を作成します。 データマイニングでのマイニング構造とそのロールの詳細については、「[マイニング構造 &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」を参照してください。  
  
 このレッスンで作成するアソシエーションマイニング構造では、 [Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)に基づくマイニングモデルの追加をサポートしています。 後のレッスンでは、マイニング モデルを使用して、同時に購入される可能性が高い製品の種類を予測します。これはマーケット バスケット分析と呼ばれます。 たとえば、この予測で、マウンテン バイクとタイヤ、およびヘルメットが同時に購入される傾向にあることがわかります。  
  
 このレッスンでは、入れ子になったテーブルを使用してマイニング構造を定義します。 入れ子になったテーブルを使用するのは、マイニング構造で定義するデータ ドメインが、2 つの異なるソース テーブル内に含まれているためです。 入れ子になったテーブルの詳細については、「[入れ子になったテーブル &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="create-mining-structure-statement"></a>CREATE マイニング構造ステートメント  
 入れ子になったテーブルを含むマイニング構造を作成するには、 [CREATE マイニング structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)ステートメントを使用します。 ステートメント内のコードは、次の部分に分けることができます。  
  
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
  
 DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。  
  
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
  
 定義できるマイニング構造列の種類の詳細については、「[マイニング構造列](../../2014/analysis-services/data-mining/mining-structure-columns.md)」を参照してください。  
  
> [!NOTE]  
>  
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、既定で、マイニング構造ごとに 30% の予約データ セットが作成されます。ただし、DMX を使用してマイニング構造を作成する場合は、必要に応じて予約データ セットを手動で追加する必要があります。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   新しい空のクエリの作成  
  
-   マイニング構造を作成するためのクエリの変更  
  
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
 次の手順では、上の CREATE MINING STRUCTURE ステートメントを変更し、Market Basket マイニング構造を作成します。  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>CREATE MINING STRUCTURE ステートメントをカスタマイズするには  
  
1.  クエリエディターで、CREATE マイニング STRUCTURE ステートメントの汎用例を空のクエリにコピーします。  
  
2.  次の部分を探します。  
  
    ```  
    [mining structure name]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Market Basket]  
    ```  
  
3.  次の部分を探します。  
  
    ```  
    <key column>  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     を以下に置き換えます。  
  
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
  
5.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
6.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Market Basket Structure.dmx`、ファイル名を指定します。  
  
## <a name="executing-the-query"></a>クエリの実行  
 最後の手順では、クエリを実行します。 クエリを作成して保存したら、サーバー上にマイニング構造を作成するためクエリを実行 (ステートメントを実行) します。 クエリエディターでのクエリの実行の詳細については、「[データベースエンジンクエリエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)」を参照してください。  
  
#### <a name="to-execute-the-query"></a>クエリを実行するには  
  
-   クエリエディターのツールバーで、[**実行**] をクリックします。  
  
     クエリの状態は、ステートメントの実行が完了した後、クエリエディターの下部にある [**メッセージ**] タブに表示されます。 この場合次のメッセージが表示されます。  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     **マーケットバスケット**という名前の新しい構造がサーバーに存在するようになりました。  
  
 次のレッスンでは、作成した Market Basket マイニング構造にマイニング モデルを追加します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
