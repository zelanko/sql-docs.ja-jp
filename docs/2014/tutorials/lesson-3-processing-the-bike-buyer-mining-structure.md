---
title: 'レッスン 3: 自転車購入者マイニング構造の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62655799"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>レッスン 3: Bike Buyer マイニング構造の処理
  このレッスンでは、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]サンプルデータベースの INSERT INTO ステートメントと vTargetMail ビューを使用して、「[レッスン 1: 自転車の購入者マイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)」と「[レッスン 2: 自転車購入者マイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)」で作成したマイニング構造とマイニングモデルを処理します。  
  
 マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。 マイニング モデルの処理では、マイニング構造で定義されたデータが、選択したデータ マイニング アルゴリズムを介して受け渡されます。 このアルゴリズムでは傾向とパターンが検索され、結果の情報がマイニング モデルに保存されます。 したがって、マイニング モデルには、実際のソース データではなく、アルゴリズムで検出された情報が含まれます。 マイニングモデルの処理の詳細については、「[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。  
  
 マイニング構造の再処理は、構造列またはソース データを変更した場合に必要です。 処理済みのマイニング構造にマイニング モデルを追加する場合は、INSERT INTO MINING MODEL ステートメントを使用して新しいマイニング モデルをトレーニングできます。  
  
## <a name="train-structure-template"></a>構造テンプレートのトレーニング  
 マイニング構造とそれに関連付けられているマイニングモデルをトレーニングするには、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用します。 ステートメント内のコードは、次の部分に分けることができます。  
  
-   マイニング構造の指定  
  
-   マイニング構造の列の一覧  
  
-   トレーニング データの定義  
  
 INSERT INTO ステートメントの汎用例を次に示します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 コードの最初の行では、トレーニングするマイニング構造を指定します。  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 コードの次の行では、マイニング構造で定義される列を指定します。 ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 コードの最後の行では、マイニング構造のトレーニングに使用するデータを定義します。  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 このレッスンでは、`OPENQUERY` を使用してソース データを定義します。 ソースクエリを定義するその他の方法については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次の作業を実行します。  
  
-   Bike Buyer マイニング構造の処理  
  
## <a name="processing-the-predictive-mining-structure"></a>予測マイニング構造の処理  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>INSERT INTO を使用してマイニング構造を処理するには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    [<mining structure name>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    Bike Buyer  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    <mining structure columns>  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
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
  
5.  次の部分を探します。  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     を以下に置き換えます。  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     OPENQUERY ステートメントは、[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] データ ソースを参照して、vTargetMail ビューにアクセスしています。 ビューには、マイニングモデルのトレーニングに使用されるソースデータが含まれています。  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
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
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
7.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`Process Bike Buyer Structure.dmx`、ファイル名を指定します。  
  
8.  ツールバーの [**実行**] ボタンをクリックします。  
  
 次のレッスンでは、このレッスンでマイニング構造に追加したマイニング モデルの内容を調査します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4: Bike Buyer マイニング モデルの参照](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
