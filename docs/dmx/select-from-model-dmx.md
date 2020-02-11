---
title: モデル&gt;から&lt;選択 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5611ce3da4f12bca5cb271cabe8af3e149dcbf35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928323"
---
# <a name="select-from-ltmodelgt-dmx"></a>モデル&gt;から&lt;選択 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 *条件*  
 省略可能。 スカラー値を返す式。  
  
## <a name="remarks"></a>解説  
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
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
