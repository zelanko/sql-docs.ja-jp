---
title: "一般的な予測関数 (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- DMX [Analysis Services], functions
- mapping functions to query types [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- SELECT statement [DMX]
- Data Mining Extensions [Analysis Services], functions
- Data Mining Extensions [Analysis Services], prediction queries
ms.assetid: e128159a-0458-43c9-bfe9-129cb6cfbe1c
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f63573a32882c40619e28666e2a251794c121621
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="general-prediction-functions-dmx"></a>一般的な予測関数 (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用することができます、**選択**ステートメントでデータ マイニング拡張機能 (DMX) クエリの種類を作成します。 クエリを使用すると、マイニング モデル自体の情報を返したり、新しい予測を作成したり、新しいデータを使用してトレーニングしてモデルを変更したりできます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]さまざまなクエリで返される情報の種類を制御する特別な関数を提供します。 これらの関数を DMX クエリに追加すると、データの統計または列を取得できます。 ただし、各クエリの種類とモデルの種類では、特定の関数しかサポートされていません。  
  
## <a name="common-functions"></a>[共通の関数]  
 関数を使用して、マイニング モデルによって返される結果を拡張できます。 に対して、次の関数を使用することができます**選択**はテーブル式を返すステートメントです。  
  
|||  
|-|-|  
|[BottomCount (&) #40";"DMX"&"#41;](../dmx/bottomcount-dmx.md)|[RangeMin (&) #40";"DMX"&"#41;](../dmx/rangemin-dmx.md)|  
|[BottomPercent (&) #40";"DMX"&"#41;](../dmx/bottompercent-dmx.md)|[TopCount (&) #40";"DMX"&"#41;](../dmx/topcount-dmx.md)|  
|[予測 (& a) # #40; DMX &#41;](../dmx/predict-dmx.md)|[TopPercent & #40";"DMX"&"#41;](../dmx/toppercent-dmx.md)|  
|[RangeMax & #40";"DMX"&"#41;](../dmx/rangemax-dmx.md)|[TopSum (&) #40";"DMX"&"#41;](../dmx/topsum-dmx.md)|  
|[RangeMid & #40";"DMX"&"#41;](../dmx/rangemid-dmx.md)||  
  
 さらに、ほぼすべてのモデルの種類で、次の関数がサポートされています。  
  
-   [存在する (& a) # #40; DMX &#41;](../dmx/exists-dmx.md)  
  
-   [IsDescendant (&) #40";"DMX"&"#41;](../dmx/isdescendant-dmx.md)  
  
-   [IsTestCase (&) #40";"DMX"&"#41;](../dmx/istestcase-dmx.md)  
  
-   [IsTrainingCase (&) #40";"DMX"&"#41;](../dmx/istrainingcase-dmx.md)  
  
-   [予測 (& a) # #40; DMX &#41;](../dmx/predict-dmx.md)  
  
-   [RangeMax & #40";"DMX"&"#41;](../dmx/rangemax-dmx.md)  
  
-   [RangeMid & #40";"DMX"&"#41;](../dmx/rangemid-dmx.md)  
  
-   [RangeMin (&) #40";"DMX"&"#41;](../dmx/rangemin-dmx.md)  
  
-   [StructureColumn & #40";"DMX"&"#41;](../dmx/structurecolumn-dmx.md)  
  
 個々のアルゴリズムでは、これ以外の関数がサポートされている場合もあります。 各モデルの種類によってサポートされている関数の一覧は、次を参照してください。[データ マイニング クエリの](../analysis-services/data-mining/data-mining-queries.md)します。  
  
## <a name="functions-specific-to-select-syntax"></a>SELECT 構文固有の関数  
 次の表に、関数の種類ごとに使用できる**選択**ステートメントです。  
  
 DMX の関数の詳細については、次を参照してください[データ マイニング拡張機能 (&) #40";"DMX"&"#41;。関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)です。  
  
|[クエリの種類]|サポートされる関数|解説|  
|----------------|-------------------------|-------------|  
|[SELECT DISTINCT FROM\<モデル >](../dmx/select-distinct-from-model-dmx.md)|[RangeMin (&) #40";"DMX"&"#41;](../dmx/rangemin-dmx.md)<br /><br /> [RangeMid & #40";"DMX"&"#41;](../dmx/rangemid-dmx.md)<br /><br /> [RangeMax & #40";"DMX"&"#41;](../dmx/rangemax-dmx.md)|これらの関数を使用すると、数値データ型を含む任意の列の最大値、最小値、および平均値を提供できます。列が連続しているか離散しているかは関係ありません。|  
|[SELECT FROM\<モデル >。コンテンツ](../dmx/select-from-model-content-dmx.md)<br /><br /> または<br /><br /> [SELECT FROM\<モデル >。DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)|[IsDescendant (&) #40";"DMX"&"#41;](../dmx/isdescendant-dmx.md)|この関数は、モデル内の指定されたノードの子ノードを取得します。また、この関数を使用すると、たとえば、マイニング モデル コンテンツのノードを繰り返し処理できます。 マイニング モデル コンテンツ内でのノードの配置は、モデルの種類によって異なります。 各マイニング モデルの種類の構造については、次を参照してください。[マイニング モデル コンテンツ & #40 です。Analysis Services - データ マイニング &#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).<br /><br /> マイニング モデル コンテンツをディメンションとして保存した場合は、属性階層のクエリに使用できる他の多次元式 (MDX) 関数も使用できます。|  
|[SELECT FROM\<モデル >。場合](../dmx/select-from-model-cases-dmx.md)|[IsInNode (&) #40";"DMX"&"#41;](../dmx/isinnode-dmx.md)<br /><br /> [ClientSettingsGeneralFlag クラス](../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md)<br /><br /> [IsTrainingCase (&) #40";"DMX"&"#41;](../dmx/istrainingcase-dmx.md)<br /><br /> [IsTestCase (&) #40";"DMX"&"#41;](../dmx/istestcase-dmx.md)|Lag 関数は、タイム シリーズ モデルでのみサポートされます。<br /><br /> IsTestCase 関数はテスト データ セットを作成する、提示オプションを使用して作成された構造に基づくモデルでサポートされます。 提示されたテスト セットを含む構造に基づいていない場合は、すべてのケースがトレーニング ケースと見なされます。|  
|[SELECT FROM\<モデル >。SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)|[IsInNode (&) #40";"DMX"&"#41;](../dmx/isinnode-dmx.md)|このコンテキストでは、IsInNode 関数は、理想的なサンプル ケースのセットに属するケースを返します。|  
|SELECT FROM\<モデル >。PMML|該当なし。 代わりに、XML クエリ関数を使用してください。|PMML 表現は、次のモデルの種類のみでサポートされます。<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)]デシジョン ツリー<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスター|  
|[SELECT FROM\<モデル > PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)|モデルの作成に使用するアルゴリズムに特有の予測関数です。|各種類のモデルの予測関数の一覧は、次を参照してください。[データ マイニング クエリの](../analysis-services/data-mining/data-mining-queries.md)します。|  
|[SELECT FROM\<モデル >](../dmx/select-from-model-dmx.md)|モデルの作成に使用するアルゴリズムに特有の予測関数です。|各種類のモデルの予測関数の一覧は、次を参照してください。[データ マイニング クエリの](../analysis-services/data-mining/data-mining-queries.md)します。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

