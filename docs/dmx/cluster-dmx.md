---
title: クラスター (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa7df2782b8102e386c70d5e874a25f7868dbb1c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071077"
---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  入力ケースを含んでいる可能性が最も高いクラスターを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>適用対象  
 この関数は、基になるデータマイニングモデルでクラスタリングがサポートされている場合にのみ使用できます。  
  
## <a name="return-type"></a>戻り値の型  
 **クラスター**関数では、パラメーターは必要ありません。  
  
 **クラスター**関数は、クラスター名のスカラー値を返します。 ただし、この関数を別の関数の引数として使用する場合は、> \<クラスター列参照として考慮する必要があります。  
  
## <a name="remarks"></a>解説  
 **クラスター**は、PredictHistogram 関数の`<`クラスター列参照`>`として**** 使用することもできます。  
  
## <a name="examples"></a>例  
 次の例では、 [PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md)およびクラスター関数と共に単一クエリを使用して、TM クラスターマイニングモデルの各クラスターから個々のケースの距離と、各クラスターに個別のケースが存在する確率を返します。  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)  
  
  
