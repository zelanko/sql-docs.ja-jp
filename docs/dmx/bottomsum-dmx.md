---
title: BottomSum (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- BOTTOMSUM
dev_langs:
- DMX
helpviewer_keywords:
- BottomSum function
ms.assetid: fd4b0418-f814-4d83-b2fe-850117e1beb7
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b7bb5ede61f9ddb95c5f9d76ea09ef2667811bc7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bottomsum-dmx"></a>BottomSum (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  累積合計が指定された値以上になるテーブルの最下位行を、ランクの増加順 (昇順) に返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>適用対象  
 など、テーブルを返す式、\<テーブルの列参照 >、またはテーブルを返す関数。  
  
## <a name="return-type"></a>戻り値の型  
 \<テーブル式 >  
  
## <a name="remarks"></a>解説  
 **BottomSum**関数は、ランクの増加順に最下位行を返します。 ランクがの結果値に基づいて、\<式をランク付け > 行ごとに、引数になるようの合計、\<順位付け式 > の値は、合計で指定されている、少なくとも、 \<sum > 引数。 **BottomSum**中に指定された合計値可能な最も小さい要素数を返します。  
  
## <a name="examples"></a>使用例  
 次の例を使用して作成した Association モデルに対する予測クエリの作成、 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。  
  
 BottomSum のしくみを理解するのには、最初に、入れ子になったテーブルのみを返す予測クエリを実行すると役立つ場合があります。  
  
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
  
 BottomSum 関数はこのクエリの結果を受け取りし、その合計の最小値を持つ行を指定した数を返します。  
  
```  
SELECT   
BottomSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .1)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 BottomSum 関数は、1 番目の引数は、テーブルの列の名前です。 この例では、INCLUDE_STATISTICS 引数を使用して、Predict 関数を呼び出すことによって、入れ子になったテーブルが返されます。  
  
 BottomSum 関数は、2 番目の引数は、結果の並べ替えに使用する入れ子になったテーブル内の列です。 この例では、INCLUDE_STATISTICS オプションによって $SUPPORT 列、$PROBABILTY 列、および $ADJUSTED PROBABILITY 列が返されます。 この例では $PROBABILITY を使用して、合計して 50% 以上の確率になる行を返します。  
  
 BottomSum 関数は、3 番目の引数は、double 型として、対象の合計を指定します。 合計が 10% の確率となる、カウントが最小の製品の行を取得するには「1」と入力します。  
  
 例の結果を次に示します。  
  
|[モデル]|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0.08…|0.07…|  
|Mountain Bottle Cage|1367|0.09…|0.08…|  
  
 **注**BottomSum の使用法を示すことだけを次の例を提供します。 データセットのサイズに応じて、このクエリの実行には長い時間がかかる場合があります。  
  
## <a name="see-also"></a>参照  
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)   
 [BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)  
  
  
