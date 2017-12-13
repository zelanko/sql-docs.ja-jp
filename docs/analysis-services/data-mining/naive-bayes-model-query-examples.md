---
title: "Naive Bayes モデルのクエリ例 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- naive bayes model [Analysis Services]
- naive bayes algorithms [Analysis Services]
- content queries [DMX]
ms.assetid: e642bd7d-5afa-4dfb-8cca-4f84aadf61b0
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5efdf95cb4a87acd7c2b1e626dd20d3105aa1f6b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="naive-bayes-model-query-examples"></a>Naive Bayes モデルのクエリ例
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニング モデルに対するクエリを作成する場合は、いずれか、コンテンツ クエリ、分析で検出されたパターンの詳細情報を提供するを作成するか、パターンを使用して、モデルに新しいデータについて予測する予測クエリを作成することができます。 データ マイニング スキーマ行セットに対するクエリによって、モデルに関するメタデータを取得することもできます。 ここでは、Microsoft Naive Bayes アルゴリズムに基づくモデルに対するクエリの作成方法について説明します。  
  
 **Content Queries**  
  
 [DMX を使用してモデル メタデータを取得する](#bkmk_Query1)  
  
 [トレーニング データの一覧を取得する](#bkmk_Query2)  
  
 [属性に関する詳細情報を検索する](#bkmk_Query3)  
  
 [システム ストアド プロシージャを使用する](#bkmk_Query4)  
  
 **予測クエリ**  
  
 [単一クエリを使用して結果を予測する](#bkmk_Query5)  
  
 [確率およびサポート値付きの予測を取得する](#bkmk_Query6)  
  
 [アソシエーションを予測する](#bkmk_Query7)  
  
## <a name="finding-information-about-a-naive-bayes-model"></a>Naive Bayes モデルに関する情報の入手  
 Naive Bayes モデルのモデル コンテンツは、トレーニング データの値の分布に関する集計情報です。 データ マイニング スキーマ行セットに対するクエリを作成することによって、モデルのメタデータに関する情報を取得することもできます。  
  
###  <a name="bkmk_Query1"></a> サンプル クエリ 1: DMX を使用してモデル メタデータを取得する  
 データ マイニング スキーマ行セットに対してクエリを実行すると、モデルにのメタデータを取得できます。 このメタデータには、モデルが作成された日時、モデルが最後に処理された日時、モデルの基になるマイニング構造の名前、予測可能な属性として使用されている列の名前などが含まれます。 モデルが作成されたときに使用されたパラメーターを取得することもできます。  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, DATE_CREATED, LAST_PROCESSED,  
SERVICE_NAME, PREDICTION_ENTITY, FILTER  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_NaiveBayes_Filtered'  
```  
  
 サンプルの結果 :  
  
|||  
|-|-|  
|MODEL_CATALOG|AdventureWorks|  
|MODEL_NAME|TM_NaiveBayes_Filtered|  
|DATE_CREATED|3/1/2008 19:15|  
|LAST_PROCESSED|3/2/2008 20:00|  
|SERVICE_NAME|Microsoft_Naive_Bayes|  
|PREDICTION_ENTITY|Bike Buyer,Yearly Income|  
|FILTER|[Region] = 'Europe' OR [Region] = 'North America'|  
  
 この例で使用するモデルは、「 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」で作成した Naive Bayes モデルを基にしていますが、予測可能な属性をもう 1 つ追加し、トレーニング データにフィルターを適用するという修正を加えています。  
  
###  <a name="bkmk_Query2"></a> サンプル クエリ 2: トレーニング データの一覧を取得する  
 Naive Bayes モデルでは、マージナル統計ノードにトレーニング データの値の分布に関する集計情報を格納します。 この一覧はトレーニング データに対する SQL クエリと同じ情報が得られるので、SQL クエリを作成しなくて済むため便利です。  
  
 次の例は、DMX コンテンツ クエリを使用してノード (NODE_TYPE = 24) からデータを取得しています。 統計は入れ子になったテーブルに格納されており、結果を見やすくするために FLATTENED キーワードが使用されています。  
  
```  
SELECT FLATTENED MODEL_NAME,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE FROM NODE_DISTRIBUTION) AS t  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
> [!NOTE]  
>  SUPPORT および PROBABILITY という列名は、多次元式 (MDX) の同名の予約済みキーワードと区別するために角かっこで囲む必要があります。  
  
 結果の一部 :  
  
|MODEL_NAME|t.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VALUETYPE|  
|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|TM_NaiveBayes|Bike Buyer|Missing|0|0|1|  
|TM_NaiveBayes|Bike Buyer|0|8869|0.507263784|4|  
|TM_NaiveBayes|Bike Buyer|1|8615|0.492736216|4|  
|TM_NaiveBayes|Gender|Missing|0|0|1|  
|TM_NaiveBayes|Gender|F|8656|0.495081217|4|  
|TM_NaiveBayes|Gender|M|8828|0.504918783|4|  
  
 たとえば、これらの結果は各不連続値に対するトレーニング ケースの数 (VALUETYPE = 4) と計算された確率、不足値の調整 (VALUETYPE = 1) を示しています。  
  
 Naive Bayes モデルの NODE_DISTRIBUTION テーブルに指定される値の定義については、「[Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)」をご覧ください。 サポートと確率の計算がどのように不足値の影響を受けるかについては、「[不足値 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/missing-values-analysis-services-data-mining.md)」をご覧ください。  
  
###  <a name="bkmk_Query3"></a> サンプル クエリ 3: 属性に関する詳細情報を検索する  
 Naive Bayes モデルには、多くの場合さまざまな属性間のリレーションシップに関する複雑な情報が含まれていますが、このリレーションシップを最も簡単に表示するには、 [Microsoft Naive Bayes ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)を使用します。 また、データを返す DMX クエリを作成できます。  
  
 次の例は、モデルから特定の属性 `Region`に関する情報を取得する方法を示します。  
  
```  
SELECT NODE_TYPE, NODE_CAPTION,   
NODE_PROBABILITY, NODE_SUPPORT, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE ATTRIBUTE_NAME = 'Region'  
```  
  
 このクエリは、入力属性を表すノード (NODE_TYPE = 10) と属性のそれぞれの値に対応するノード (NODE_TYPE = 11) の 2 種類のノードを返します。 ノードのキャプションは属性の名前と値の両方を示すため、ノード名の代わりに、ノードを識別するために使用します。  
  
|NODE_TYPE|NODE_CAPTION|NODE_PROBABILITY|NODE_SUPPORT|MSOLAP_NODE_SCORE|NODE_TYPE|  
|----------------|-------------------|-----------------------|-------------------|-------------------------|----------------|  
|10|Bike Buyer -> Region|1|17484|84.51555875|10|  
|11|Bike Buyer -> Region = Missing|0|0|0|11|  
|11|Bike Buyer -> Region = North America|0.508236102|8886|0|11|  
|11|Bike Buyer -> Region = Pacific|0.193891558|3390|0|11|  
|11|Bike Buyer -> Region = Europe|0.29787234|5208|0|11|  
  
 ノードに格納されている列の一部は、ノードの確率スコアやノードのサポート値など、マージナル統計ノードから取得できるものと同じです。 ただし、MSOLAP_NODE_SCORE は、入力属性ノードにのみ与えられる特殊な値で、モデル内でのこの属性の相対的な重要度を示します。 ビューアーの [依存関係ネットワーク] ペインで同じ情報を参照できますが、ビューアーにはスコアが表示されません。  
  
 次のクエリはモデル内のすべての属性の重要度スコアを返します。  
  
```  
SELECT NODE_CAPTION, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
ORDER BY MSOLAP_NODE_SCORE DESC  
```  
  
 サンプルの結果 :  
  
|NODE_CAPTION|MSOLAP_NODE_SCORE|  
|-------------------|-------------------------|  
|Bike Buyer -> Total Children|181.3654836|  
|Bike Buyer -> Commute Distance|179.8419482|  
|Bike Buyer -> English Education|156.9841928|  
|Bike Buyer -> Number Children At Home|111.8122599|  
|Bike Buyer -> Region|84.51555875|  
|Bike Buyer -> Marital Status|23.13297354|  
|Bike Buyer -> English Occupation|2.832069191|  
  
 [Microsoft 汎用コンテンツ ツリー ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)でモデル コンテンツを参照すると、どの統計が興味深いかがわかります。 ここでは簡単な例をいくつか示しています。複数のクエリの実行や、結果を格納した後のクライアント上での処理が必要な場合もあります。  
  
###  <a name="bkmk_Query4"></a> サンプル クエリ 4: システム ストアド プロシージャを使用する  
 独自のコンテンツ クエリを記述することに加え、Analysis Services システム ストアド プロシージャを使用して結果を検証できます。 システム ストアド プロシージャを使用するには、ストアド プロシージャ名に CALL キーワードのプレフィックスを付けます。  
  
```  
CALL GetPredictableAttributes ('TM_NaiveBayes')  
```  
  
 結果の一部 :  
  
|ATTRIBUTE_NAME|NODE_UNIQUE_NAME|  
|---------------------|------------------------|  
|Bike Buyer|100000001|  
  
> [!NOTE]  
>  これらのシステム ストアド プロシージャは、Analysis Services のサーバーとクライアントの間での内部通信用で、マイニング モデルの開発とテストを容易にするためにのみ使用します。 実稼働システムのクエリを作成するときには、常に DMX を使用して独自のクエリを作成してください。  
  
 Analysis Services システム ストアド プロシージャの詳細については、「[データ マイニングのストアド プロシージャ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md)」をご覧ください。  
  
## <a name="using-a-naive-bayes-model-to-make-predictions"></a>Naive Bayes モデルを使用して予測を作成する  
 Microsoft Naive Bayes アルゴリズムは、通常、予測に使用するよりも、入力属性と予測可能な属性の間のリレーションシップの検証に使用されます。 ただし、モデルでは予測とアソシエーションの両方に予測関数を使用できます。  
  
###  <a name="bkmk_Query5"></a> サンプル クエリ 5: 単一クエリを使用して結果を予測する  
 次のクエリでは、単一クエリを使用して、新しい値を指定し、モデルに基づいてこれらの特性を持つ顧客が自転車を購入するかどうかを予測します。 回帰モデルで単一クエリを作成する最も簡単な方法は、 **[単一クエリ入力]** ダイアログ ボックスを使用することです。 たとえば、次の DMX クエリを作成するには、 `TM_NaiveBayes` モデルを選択し、 **[単一クエリ]**をクリックして、 `[Commute Distance]` および `Gender`のドロップダウン リストから値を選択します。  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 例の結果を次に示します。  
  
|式|  
|----------------|  
|0|  
  
 予測関数は、最も可能性の高い値を返します。この場合は 0 で、この種類の顧客は自転車を購入する可能性が低いことを表します。  
  
###  <a name="bkmk_Query6"></a> サンプル クエリ 6: 確率およびサポート値付きの予測を取得する  
 結果の予測に加えて、予測の信頼性の高さを調べることもあります。 次のクエリでは、前の例と同じ単一クエリを使用しますが、予測関数 [PredictHistogram &#40;DMX&#41;](../../dmx/predicthistogram-dmx.md) を追加し、予測の裏付けとなる統計を含む入れ子になったテーブルを返します。  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer]),  
  PredictHistogram([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 例の結果を次に示します。  
  
|Bike Buyer|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|$VARIANCE|$STDEV|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|0|10161.5714|0.581192599|0.010530981|0|0|  
|1|7321.428768|0.418750215|0.008945684|0|0|  
||0.999828444|5.72E-05|5.72E-05|0|0|  
  
 テーブルの最後の行は、不足値のサポートと確率に対する調整を示します。 Naive Bayes モデルは連続値をモデリングできないため、分散値と標準偏差値は常に 0 です。  
  
###  <a name="bkmk_Query7"></a> サンプル クエリ 7: アソシエーションを予測する  
 予測可能な属性をキーとして持つ入れ子になったテーブルがマイニング構造に含まれる場合、Microsoft Naive Bayes アルゴリズムをアソシエーション分析に使用できます。 たとえば、データ マイニング チュートリアルの「[レッスン 3: マーケット バスケット シナリオの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](http://msdn.microsoft.com/library/651eef38-772e-4d97-af51-075b1b27fc5a)」で作成したマイニング構造を使用して、Naive Bayes モデルを作成できます。 この例で使用したモデルは、ケース テーブルに収入および顧客の地域に関する情報を加えるよう変更されています。  
  
 次のクエリの例では、製品 `'Road Tire Tube'`の購入に関連する製品を予測する単一クエリを示します。 この情報は、特定の種類の顧客に製品を勧めるために使用できます。  
  
```  
SELECT   PredictAssociation([Association].[v Assoc Seq Line Items])  
FROM [Association_NB]  
NATURAL PREDICTION JOIN  
(SELECT 'High' AS [Income Group],  
  'Europe' AS [Region],  
  (SELECT 'Road Tire Tube' AS [Model])   
AS [v Assoc Seq Line Items])   
AS t  
```  
  
 結果の一部 :  
  
|[モデル]|  
|-----------|  
|Women's Mountain Shorts|  
|Water Bottle|  
|Touring-3000|  
|Touring-2000|  
|Touring 1000|  
  
## <a name="function-list"></a>関数一覧  
 すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。 ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、次の表のような追加の関数がサポートされています。  
  
|||  
|-|-|  
|予測関数|使用方法|  
|[IsDescendant &#40;DMX&#41;](../../dmx/isdescendant-dmx.md)|あるノードがモデル内の別のノードの子であるかどうかを示します。|  
|[Predict &#40;DMX&#41;](../../dmx/predict-dmx.md)|指定された列に対して、予測された値、または値のセットを返します。|  
|[PredictAdjustedProbability &#40;DMX&#41;](../../dmx/predictadjustedprobability-dmx.md)|重み付け確率を返します。|  
|[PredictAssociation &#40;DMX&#41;](../../dmx/predictassociation-dmx.md)|結合データセットのメンバーシップを予測します。|  
|[PredictNodeId &#40;DMX&#41;](../../dmx/predictnodeid-dmx.md)|各ケースの Node_ID を返します。|  
|[PredictProbability &#40;DMX&#41;](../../dmx/predictprobability-dmx.md)|予測値の確率を返します。|  
|[PredictSupport &#40;DMX&#41;](../../dmx/predictsupport-dmx.md)|指定された状態に対するサポート値を返します。|  
  
 特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](../../dmx/data-mining-extensions-dmx-function-reference.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)   
 [Microsoft Naive Bayes アルゴリズム](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)   
 [Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
