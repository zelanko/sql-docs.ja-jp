---
title: 'レッスン 4: 自転車購入者マイニングモデルの参照 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63070893"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a>レッスン 4: Bike Buyer マイニング モデルの参照
  このレッスンでは、 [select (DMX)](/sql/dmx/select-dmx)ステートメントを使用して、「[レッスン 2: 予測マイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)」で作成したデシジョンツリーおよびクラスターマイニングモデルの内容を調査します。  
  
 マイニング モデルに含まれる列は、マイニング構造で定義されている列ではなく、アルゴリズムによって検出された傾向とパターンを記述している、特定の列のセットです。 これらのマイニングモデル列については、「 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)スキーマ行セット」を参照してください。 たとえば、コンテンツ スキーマ行セットの MODEL_NAME 列には、マイニング モデルの名前が含まれます。 クラスター マイニング モデルの場合、NODE_CAPTION 列には各クラスターの名前が含まれ、NODE_DESCRIPTION 列には各クラスターの特性の説明が含まれます。 これらの列を参照するには、[ \<モデルから選択]> を使用します。DMX の CONTENT ステートメント。 このステートメントを使用すると、マイニング モデルの作成に使用されたデータを調査することもできます。 このステートメントを使用するには、マイニング構造上でドリルスルーを有効にする必要があります。 ステートメントの詳細については、「 [SELECT FROM &#60;model&#62;」を参照してください。DMX&#41;&#40;ケース](/sql/dmx/select-from-model-content-dmx)。  
  
 SELECT DISTINCT ステートメントを使用することにより、不連続列のすべての状態を返すこともできます。 たとえば、性別の列でこの操作を実行すると、クエリでは `male` と `female` が返されます。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンでは、次のタスクを実行します。  
  
-   マイニング モデルに含まれる内容の調査  
  
-   マイニング モデルのトレーニングに使用されたソース データからケースを返す  
  
-   特定の不連続列に対して可能な状態の調査  
  
## <a name="returning-the-content-of-a-mining-model"></a>マイニング モデルの内容を返す  
 このレッスンでは、 [SELECT FROM &#60;model&#62; を使用します。コンテンツ &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)ステートメントによって、クラスターモデルの内容が返されます。  
  
 次に、[モデルから\<の選択]> の一般的な例を示します。コンテンツステートメント:  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 コードの 1 行目では、マイニング モデルの内容から返す列と、それらの列が関連付けられているマイニング モデルを定義します。  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 マイニング モデル名の後の .CONTENT 句は、マイニング モデルから内容を返すことを示します。 マイニングモデルに含まれる列の詳細については、「 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)」を参照してください。  
  
 コードの最終行では、ステートメントで返される結果をフィルター選択します。この行は省略可能です。  
  
```  
WHERE <where clause>  
```  
  
 たとえば、クエリの結果を制限して、多数のケースが含まれるクラスターのみを返すようにする場合は、SELECT ステートメントに次の WHERE 句を追加します。  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 WHERE ステートメントの使用方法の詳細については、「 [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)」を参照してください。  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a>クラスター マイニング モデルの内容を返すには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  [モデルから\<選択]> の汎用的な例をコピーします。空のクエリに CONTENT ステートメントを指定します。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    *  
    ```  
  
     また、* を[DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)内に含まれる任意の列の一覧に置き換えることもできます。  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Clustering]  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
6.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`SELECT_CONTENT.dmx`、ファイル名を指定します。  
  
7.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリが実行され、マイニング モデルの内容が返されます。  
  
## <a name="use-drillthrough"></a>ドリルスルーの使用  
 次の手順では、ドリルスルー ステートメントを使用して、デシジョン ツリー マイニング モデルのトレーニングに使用されたケースの一部を返します。 このレッスンでは、 [SELECT FROM &#60;model&#62; を使用します。](/sql/dmx/select-from-model-content-dmx)デシジョンツリーモデルの内容を返す DMX&#41;ステートメント &#40;ケース。  
  
 次に、[モデルから\<の選択]> の一般的な例を示します。CASE ステートメント:  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 コードの 1 行目では、ソース データから返す列と、それらの列が含まれるマイニング モデルを定義します。  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 .CASES 句は、ドリルスルー クエリを実行することを示します。 ドリルスルーを使用するには、マイニング モデルの作成時にドリルスルーを有効にする必要があります。  
  
 コードの最終行では、ケースを要求するマイニング モデル内のノードを指定します。この行は省略可能です。  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 WHERE ステートメントを IsInNode と共に使用する方法の詳細については、「 [SELECT FROM &#60;model&#62;」を参照してください。DMX&#41;&#40;ケース](/sql/dmx/select-from-model-content-dmx)。  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a>マイニング モデルのトレーニングに使用されたケースを返すには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  [モデルから\<選択]> の汎用的な例をコピーします。空のクエリに CASE ステートメントを記述します。  
  
3.  次の部分を探します。  
  
    ```  
    <select list>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    *  
    ```  
  
     * は、ソース データ内に含まれる任意の列の一覧 ([Bike Buyer] など) に置き換えることもできます。  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Decision Tree]  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
6.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`SELECT_DRILLTHROUGH.dmx`、ファイル名を指定します。  
  
7.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリが実行され、デシジョン ツリー マイニング モデルのトレーニングに使用されたソース データが返されます。  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a>マイニング モデルの不連続列の状態を返す  
 次の手順では、SELECT DISTINCT ステートメントを使用して、指定されたマイニング モデル列に対して可能な状態を返します。  
  
 SELECT DISTINCT ステートメントの汎用例を次に示します。  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 コードの 1 行目では、状態を返すマイニング モデル列を定義します。  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 列のすべての状態を返すには、DISTINCT を含める必要があります。 DISTINCT を指定しない場合は、ステートメント全体が予測用のショートカットとなり、指定した列で最も可能性の高い状態が返されます。 詳細については、「[SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)」を参照してください。  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a>不連続列の状態を返すには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスを右クリックし、[**新しいクエリ**] をポイントして [ **DMX**] をクリックします。  
  
     クエリ エディターが開き、新しい空のクエリが表示されます。  
  
2.  上の SELECT Distinct ステートメントの汎用例を空のクエリにコピーします。  
  
3.  次の部分を探します。  
  
    ```  
    [<column,name>   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  次の部分を探します。  
  
    ```  
    [<mining model>]   
    ```  
  
     を以下に置き換えます。  
  
    ```  
    [Decision Tree]  
    ```  
  
     最終的なステートメントは次のようになります。  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  [**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。  
  
6.  [名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し`SELECT_DISCRETE.dmx`、ファイル名を指定します。  
  
7.  ツールバーの [**実行**] ボタンをクリックします。  
  
     クエリが実行され、Bike Buyer 列の可能な状態が返されます。  
  
 次のレッスンでは、デシジョン ツリー マイニング モデルを使用して、潜在顧客が自転車の購入者になるかどうかを予測します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 5: 予測クエリの実行](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
