---
title: 'レッスン 3: マーケットバスケットマイニング構造の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62653864"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a>レッスン 3: Market Basket マイニング構造の処理
  このレッスンでは、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用し、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]サンプルデータベースの vAssocSeqLineItems と vAssocSeqOrders を使用して、「[レッスン 1: マーケットバスケットマイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)」および「[レッスン 2: マーケットバスケットマイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)」で作成したマイニング構造とマイニングモデルを処理します。  
  
 マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。 マイニングモデルを処理する場合、マイニング構造によって定義されるデータは、選択したデータマイニングアルゴリズムによって渡されます。 このアルゴリズムでは傾向とパターンが検索され、結果の情報がマイニング モデルに保存されます。 したがって、マイニング モデルには、実際のソース データではなく、アルゴリズムで検出された情報が含まれます。 マイニングモデルの処理の詳細については、「[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。  
  
 マイニング構造の再処理は、構造列またはソース データを変更した場合にのみ必要です。 処理済みのマイニング構造にマイニング モデルを追加する場合は、`INSERT INTO MINING MODEL` ステートメントを使用して既存のデータに対して新しいマイニング モデルをトレーニングできます。  
  
 Market Basket マイニング構造には入れ子になったテーブルが含まれるため、入れ子になったテーブル構造でトレーニングするようにマイニング列を定義する必要があります。また、`SHAPE` コマンドを使用して、ソース テーブルからトレーニング データを抽出するクエリを定義する必要があります。  
  
## <a name="insert-into-statement"></a>INSERT INTO ステートメント  
 マーケットバスケットのマイニング構造とそれに関連付けられているマイニングモデルをトレーニングするには、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用します。 ステートメントのコードは次の部分に分けることができます。  
  
-   マイニング構造の指定  
  
-   マイニング構造の列の一覧  
  
-   
  `SHAPE` によるトレーニング データの定義  
  
 
  `INSERT INTO` ステートメントの汎用例を次に示します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 コードの最初の行では、トレーニングするマイニング構造を指定します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の数行では、マイニング構造で定義される列を指定します。 ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。 
  `SKIP` を使用すると、ソース データに存在するがマイニング構造に存在しない列を無視できます。 の使用`SKIP`方法の詳細については、「 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)」を参照してください。  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 コードの最後の行では、マイニング構造のトレーニングに使用されるデータを定義します。 ソース データは 2 つのテーブルに格納されているため、`SHAPE` を使用してテーブルを関連付けます。  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 このレッスンでは、`OPENQUERY` を使用してソース データを定義します。 ソースデータに対するクエリを定義するその他の方法については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次の作業を実行します。  
  
-   マーケットバスケットのマイニング構造を処理する  
  
## <a name="processing-the-market-basket-mining-structure"></a>Market Basket マイニング構造の処理  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>INSERT INTO を使用してマイニング構造を処理するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    [<mining structure>]  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    Market Basket  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     このステートメントでは、`Products` は SHAPE ステートメントで定義される Products テーブルを参照します。 
  `SKIP` は、ソース データにキーとして存在する Model 列を無視するために使用します。マイニング構造に対しては使用できません。  
  
5.  次の部分を探します。  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     ソースクエリは、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]サンプルプロジェクトで定義されているデータソースを参照します。 ソース クエリはこのデータ ソースを使用して、vAssocSeqLineItems ビューと vAssocSeqOrders ビューにアクセスします。 これら 2 つのビューには、マイニング モデルのトレーニングに使用されるソース データが含まれます。 このプロジェクトまたはこれらのビューを作成していない場合は、「[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)」を参照してください。  
  
     
  `SHAPE` コマンド内では、`OPENQUERY` を使用して 2 つのクエリを定義します。 最初のクエリでは親テーブルを定義し、2 つ目のクエリでは入れ子になったテーブルを定義します。 2 つのテーブルは、両方のテーブルに存在する OrderNumber 列を使用して関連付けられます。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Process Market Basket.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
 クエリの実行終了後、見つかったパターンとアイテムセットを表示したり、関連付けを表示したり、アイテムセット、確率、または重要度でフィルタリングしたりできます。 この情報を表示するに[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]は、でデータモデルの名前を右クリックし、[**参照**] をクリックします。  
  
 次のレッスンでは、Market Basket 構造に追加したマイニング モデルに基づいて、いくつかの予測を作成します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4: マーケット バスケット予測の実行](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
