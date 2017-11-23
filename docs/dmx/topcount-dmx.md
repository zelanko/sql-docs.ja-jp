---
title: "TopCount (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
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
ms.topic: language-reference
f1_keywords: TOPCOUNT
dev_langs: DMX
helpviewer_keywords: TopCount function
ms.assetid: cbe031c9-4ff0-45df-9810-ebaebacf161d
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b5d0020ea38edda21d5aec96b0b5a469d2f5f963
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="topcount-dmx"></a>TopCount (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  式によって指定された降順のランクで、指定された件数の上位行を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>適用対象  
 など、テーブルを返す式、\<テーブルの列参照 >、またはテーブルを返す関数。  
  
## <a name="return-type"></a>戻り値の型  
 \<テーブル式 >  
  
## <a name="remarks"></a>解説  
 によって指定された値、\<式をランク付け > 引数で指定される行のランクの減少順を決定する、\<テーブル式 > 引数とで指定されている最上位の行の数、 \<count > 引数が返されます。  
  
 TopCount 関数が結合型の予測を有効にするのには導入最初および一般に、同じ結果を含むステートメントとして**SELECT TOP**と**ORDER BY**句。 使用する場合は、結合型の予測のパフォーマンスが向上を取得するが、 **Predict (DMX)**関数で、さまざまな予測を返すの仕様をサポートします。  
  
 ただし、ここで TopCount を使用する必要がありますも状況もあります。 たとえば、DMX はサポートされません、**上部**サブ select ステートメント内の修飾子です。 [PredictHistogram & # #40; DMX &#41;](../dmx/predicthistogram-dmx.md)機能もサポートされていませんの追加**上部**です。  
  
## <a name="examples"></a>使用例  
 次の例としてを使用して作成した Association モデルに対する予測クエリ、 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。 クエリは、同じ結果を返しますが、最初の例では、TopCount、および 2 番目の例では、予測関数を使用しています。  
  
 TopCount のしくみを理解するのには、最初に、入れ子になったテーブルのみを返す予測クエリの実行に役立つ場合があります。  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  この例では、入力値として指定された値には単一引用符が含まれているため、この単一引用符の前にもう 1 つ単一引用符に追加してエスケープする必要があります。 エスケープ文字を挿入するための構文がわからない場合は、予測クエリ ビルダーを使用してクエリを作成できます。 ドロップダウン リストから値を選択すると、必要なエスケープ文字が挿入されます。 詳細については、次を参照してください。[データ マイニング デザイナーで単一クエリを作成する](../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)です。  
  
 例の結果を次に示します。  
  
|[モデル]|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Water Bottle|2866|0.192620472|0.175205052|  
|Patch kit|2113|0.142012232|0.132389356|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Road Tire Tube|1588|0.106727603|0.101229538|  
|Cycling Cap|1473|0.098998589|0.094256014|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
  
 TopCount 関数はこのクエリの結果を受け取りし、指定した最小値を持つ行の数を返します。  
  
```  
SELECT   
TopCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 TopCount 関数の最初の引数は、テーブルの列の名前です。 この例では、INCLUDE_STATISTICS 引数を使用して、Predict 関数を呼び出すことによって、入れ子になったテーブルが返されます。  
  
 TopCount 関数の 2 番目の引数は、結果の並べ替えに使用する入れ子になったテーブル内の列です。 この例では、INCLUDE_STATISTICS オプションによって $SUPPORT 列、$PROBABILTY 列、および $ADJUSTED PROBABILITY 列が返されます。 この例では、$SUPPORT を使用して結果に順位を付けます。  
  
 TopCount 関数の 3 番目の引数は、戻るには、整数として行の数を指定します。 $SUPPORT で順位が付けられた上位 3 製品を取得するには、「3」と入力します。  
  
 例の結果を次に示します。  
  
|[モデル]|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.29…|0.25…|  
|Water Bottle|2866|0.19…|0.17…|  
|Patch kit|2113|0.14…|0.13…|  
  
 ただし、この種のクエリは、実稼働設定でのパフォーマンスに影響する可能性があります。 これは、クエリによってアルゴリズムからすべての予測のセットが返され、これらの予測が並べ替えられて上位 3 件が返されるためです。  
  
 次の例は、同じ結果を返すが実行時間が大幅に短縮される代替ステートメントを示しています。 この例では、予測関数を引数として予測の数を受け付ける TopCount を置き換えます。 またこの例では、 **$SUPPORT**直接入れ子になったテーブル列を取得するキーワードです。  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3, $SUPPORT)  
```  
  
 結果には、サポート値に基づいて並べ替えられた上位 3 件の予測が含まれます。 $SUPPORT を $PROBABILITY または $ADJUSTED_PROBABILITY に置き換えると、確率または調整済みの確率で順位付けされた予測を取得できます。 詳細については、次を参照してください。 **Predict (DMX)**です。  
  
## <a name="see-also"></a>参照  
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)   
 [TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)   
 [TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)  
  
  
