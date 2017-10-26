---
title: "予測 (DMX) |Microsoft ドキュメント"
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
f1_keywords:
- PREDICT
dev_langs:
- DMX
helpviewer_keywords:
- Predict function
ms.assetid: f02ff4b3-9bd7-409d-ad14-ead67b3206c4
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a976011c3b892d826d29038fb0501e57db4c5008
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="predict-dmx"></a>Predict (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Predict**関数は、予測された値、または指定された列の値のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列参照またはテーブル列参照です。  
  
## <a name="return-type"></a>戻り値の型  
 \<スカラー列参照 >  
  
 または  
  
 \<テーブルの列参照 >  
  
 戻り値の型は、この関数が適用される列の型によって異なります。  
  
> [!NOTE]  
>  INCLUSIVE、EXCLUSIVE、INPUT_ONLY、および INCLUDE_STATISTICS はテーブル列の参照にのみ適用され、EXCLUDE_NULL および INCLUDE_NULL はスカラー列の参照にのみ適用されます。  
  
## <a name="remarks"></a>解説  
 オプションには、EXCLUDE_NULL (既定)、INCLUDE_NULL、INCLUSIVE、EXCLUSIVE (既定)、INPUT_ONLY、および INCLUDE_STATISTICS が含まれています。  
  
> [!NOTE]  
>  タイム シリーズ モデルの予測関数は INCLUDE_STATISTICS をサポートしていません。  
  
 INCLUDE_NODE_ID パラメーターは、結果に $NODEID 列を返します。 NODE_ID は、特定のケースに対して予測が実行されるコンテンツ ノードです。 テーブルの列に対して予測を使用する場合、このパラメーターは省略できます。  
  
  *n* パラメーター テーブルの列に適用されます。 これにより、予測の種類に基づいて、返される列の数が設定されます。 呼び出す、基になる列がシーケンスの場合、 **PredictSequence**関数。 基になる列が時系列の場合は、呼び出し、 **PredictTimeSeries**関数。 予測の種類が結合型を呼び出し、 **PredictAssociation**関数。  
  
 **Predict**関数はポリモーフィズムをサポートします。  
  
 使用される頻度の高い代替省略形は次のとおりです。  
  
-   [Gender] には、代わりの**Predict**([Gender], EXCLUDE_)。  
  
-   [Products Purchases] は、代替の**Predict**([Products Purchases], exclude _、排他)。  
  
    > [!NOTE]  
    >  この関数の戻り値の型は、列の参照として扱われる元々の型と同じです。 つまり、 **Predict**を引数として列参照を受け取るその他の関数の引数として関数を使用できます (を除き、 **Predict**関数自体)。  
  
 列を追加する INCLUDE_STATISTICS をテーブル値列の予測に渡す**$Probability**と**$Support**結果のテーブルにします。 これらのメタ列は、入れ子になった関連テーブルのレコードが存在する確率を説明します。  
  
## <a name="examples"></a>使用例  
 次の例では、Predict 関数を使用して、一緒に販売できる可能性が最も高い Adventure Works データベースの 4 つの製品を返します。 自動的に使用して、関数は、アソシエーション ルール マイニング モデルに対して予測を行う、ため、 **PredictAssociation**前に説明したとおりに機能します。  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 サンプルの結果 :  
  
 このクエリは、1 つの列で、データの単一行を返す`Expression`が、その列には、次の入れ子になったテーブルが含まれています。  
  
|[モデル]|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Water Bottle|2866|0.192620471805901|0.175205052318795|  
|Patch Kit|2113|0.142012232004839|0.132389356196586|  
|Mountain Tire Tube|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

