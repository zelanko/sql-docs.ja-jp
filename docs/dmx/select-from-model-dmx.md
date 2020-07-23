---
title: モデルから &lt; 選択 &gt; (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 43a7157c5ec7889b2f8cb7018423d909f3db3cb7
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970560"
---
# <a name="select-from-ltmodelgt-dmx"></a>モデルから &lt; 選択 &gt; (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  空の予測結合を実行し、指定された列の最も可能性の高い値を返します。 マイニング モデルのコンテンツのみが予測の作成に使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *式の一覧*  
 式、予測、または列のみの予測のコンマ区切りのリストです。  
  
 *n*  
 省略可能。 返す行数を指定する整数値です。  
  
 *model*  
 モデル識別子。  
  
 *条件一覧*  
 省略可能。 列リストから返される値を制限する条件。  
  
 *式 (expression)*  
 省略可能。 スカラー値を返す式。  
  
## <a name="remarks"></a>注釈  
 [*式] ボックスの一覧*の列は、予測または予測のみとして定義するか、予測可能列に関連付けられている必要があります。  
  
## <a name="naive-bayes-example"></a>Naive Bayes の例  
 次の例は、Bike Buyer 列で空の予測結合を実行し、TM Naive Bayes マイニング モデルの最も可能性の高い状態を返します。  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>時系列の例  
 次の例は、Forecasting モデルの Amount 列で予測を実行し、次の 4 回のステップを返します。 Model Region 列は、自転車のモデルと地域を単一の識別子に結合します。 このクエリでは、 [PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md)関数を使用して予測を実行します。  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41;を選択 &#40;](../dmx/select-dmx.md)   
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
