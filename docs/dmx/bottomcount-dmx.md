---
title: BottomCount (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 382cfe7e7ce77fec66d2b9e5b370f397abd14dce
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602912"
---
# <a name="bottomcount-dmx"></a>BottomCount (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  式によって指定されたランクの増加順に、指定された最下位の行数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>適用対象  
 など、テーブルを返す式、\<テーブルの列参照 >、またはテーブルを返す関数。  
  
## <a name="return-type"></a>戻り値の型  
 \<テーブル式 >  
  
## <a name="remarks"></a>コメント  
 によって指定された値、\<式をランク付け > 引数で指定される行のランクの増加順を決定、\<テーブル式 > 引数とで指定されている最下位行の数、\<count > 引数が返されます。  
  
## <a name="examples"></a>使用例  
 次の例を使用して作成した Association モデルに対する予測クエリの作成、 [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)します。  
  
 BottomCount のしくみを理解するのには、最初に、入れ子になったテーブルのみを返す予測クエリを実行に役立つ場合があります。  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  この例では、入力値として指定された値には単一引用符が含まれているため、この単一引用符の前にもう 1 つ単一引用符に追加してエスケープする必要があります。 エスケープ文字を挿入するための構文がわからない場合は、予測クエリ ビルダーを使用してクエリを作成できます。 ドロップダウン リストから値を選択すると、必要なエスケープ文字が挿入されます。 詳細については、次を参照してください。[データ マイニング デザイナーで単一クエリの作成](../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)です。  
  
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
  
 BottomCount 関数は、このクエリの結果を受け取り、その合計の最小値を持つ行を指定した割合を返します。  
  
```  
SELECT   
BottomCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 BottomCount 関数の最初の引数は、テーブルの列の名前です。 この例では、Predict 関数を呼び出すと、INCLUDE_STATISTICS 引数を使用して入れ子になったテーブルが返されます。  
  
 BottomCount 関数は、2 番目の引数は、結果の順序を使用する入れ子になったテーブル列です。 この例では、INCLUDE_STATISTICS オプションによって $SUPPORT 列、$PROBABILTY 列、および $ADJUSTED PROBABILITY 列が返されます。 この例では、$SUPPORT を使用しています。サポート値は小数ではないため、検証しやすいからです。  
  
 BottomCount 関数の 3 番目の引数には、行の数を指定します。 $SUPPORT で順位が付けられた、最下位 3 つの行を取得するには、「3」と入力します。  
  
 例の結果を次に示します。  
  
|[モデル]|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
  
 **注**BottomCount の使用を示すためにのみこの例が提供されます。 データセットのサイズに応じて、このクエリの実行には長い時間がかかる場合があります。  
  
## <a name="see-also"></a>参照  
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)   
 [BottomSum &#40;DMX&#41;](../dmx/bottomsum-dmx.md)   
 [TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)  
  
  
