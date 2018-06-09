---
title: 算術演算子 (DMX) |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: edbe8a3404217f330b5b62a9d433c7d560b28656
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842225"
---
# <a name="operators---arithmetic"></a>演算子の算術演算子
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  算術演算を行うのため、算術演算子データ マイニング拡張機能 (DMX) を使用できます[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)](加算、減算、乗算、および除算など)。  
  
 次の表は、DMX がサポートする算術演算子について示しています。  
  
|演算子|説明|  
|--------------|-----------------|  
|[+&#40;追加&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|2 つの数値を加算します。|  
|[-&#40;減算&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|ある数値から別の数値を減算します。|  
|[&#42;&#40;乗算&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|ある数値を別の数値によって乗算します。|  
|[&#40;分割&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|ある数値を別の数値によって除算します。|  
  
 次のルールは、DMX 式内の算術演算子の優先順位の順序を判断します。  
  
-   式の中に複数の算術演算子がある場合、まず、乗算および除算が行われ、次に減算および加算が行われます。  
  
-   式の中の算術演算子の優先順位がすべて同じである場合は、左から右に計算されます。  
  
-   かっこの中の式は、他のどの演算子よりも優先されます。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [式&#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
