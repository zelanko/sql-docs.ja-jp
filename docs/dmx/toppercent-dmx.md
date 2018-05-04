---
title: TopPercent (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TOPPERCENT
dev_langs:
- DMX
helpviewer_keywords:
- TopPercent function
ms.assetid: 0b407ab2-2a69-4cbd-ae13-bdd29654fa86
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a750c0f666bc3f9b4ce043ab70c925144fe67203
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="toppercent-dmx"></a>TopPercent (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  **TopPercent**関数を返します、ランクの減少順に最上位の行の累積合計が、少なくともテーブルの指定された割合。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="applies-to"></a>適用対象  
 など、テーブルを返す式、\<テーブルの列参照 >、またはテーブルを返す関数。  
  
## <a name="return-type"></a>戻り値の型  
 \<テーブル式 >  
  
## <a name="remarks"></a>解説  
 **TopPercent**関数の評価値に基づいてランクの減少順に最上位の行が返されます、\<式をランク付け > 行ごとに、引数になるようの合計、\<式をランク付け > によって指定された割合の値は、少なくとも、 \<% > 引数。 **TopPercent**指定した割合の値を満たしながら可能な最も小さい要素数を返します。  
  
## <a name="examples"></a>使用例  
 次の例を使用して作成した Association モデルに対する予測クエリの作成、 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。  
  
 TopPercent のしくみを理解するのには、最初に、入れ子になったテーブルのみを返す予測クエリを実行すると役立つ場合があります。  
  
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
  
 TopPercent 関数はこのクエリの結果を受け取りし、指定した割合に最大の値を持つ行その合計を返します。  
  
```  
SELECT   
TopPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 TopPercent 関数は、1 番目の引数は、テーブルの列の名前です。 この例では、INCLUDE_STATISTICS 引数を使用して、Predict 関数を呼び出すことによって、入れ子になったテーブルが返されます。  
  
 TopPercent 関数は、2 番目の引数は、結果の並べ替えに使用する入れ子になったテーブル内の列です。 この例では、INCLUDE_STATISTICS オプションによって $SUPPORT 列、$PROBABILTY 列、および $ADJUSTED PROBABILITY 列が返されます。 この例では、$SUPPORT を使用しています。サポート値は小数ではないため、検証しやすいからです。  
  
 TopPercent 関数は、3 番目の引数は、double 型として、割合を指定します。 合計が合計サポートの 50% となる上位の製品の行を取得するには「50」と入力します。  
  
 例の結果を次に示します。  
  
|[モデル]|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.29…|0.25…|  
|Water Bottle|2866|0.19…|0.17…|  
|Patch kit|2113|0.14…|0.13…|  
|Mountain Tire Tube|1992|0.133…|0.12…|  
  
 **注**この例は、TopPercent の使用を示すことだけを提供します。 データセットのサイズに応じて、このクエリの実行には長い時間がかかる場合があります。  
  
> [!WARNING]  
>  TOPPERCENT および BOTTOMPERCENT の MDX 関数は、比率の計算に使用される値に負の数が含まれていた場合に、予期しない結果を生成する場合があります。 この動作は、DMX 関数には影響しません。 詳細については、次を参照してください。 [BottomPercent &#40;MDX&#41;](../mdx/bottompercent-mdx.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
