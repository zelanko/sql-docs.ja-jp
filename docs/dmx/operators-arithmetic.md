---
title: "算術演算子 (DMX) |Microsoft ドキュメント"
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
dev_langs:
- DMX
helpviewer_keywords:
- arithmetic operators
ms.assetid: befe4f0c-e5dd-4ae1-b88e-6ac7aab2181a
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 032f285a3f9df3f63f85ad7b2e01122f25964dd3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="operators---arithmetic"></a>演算子の算術演算子
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  算術演算を行うのため、算術演算子データ マイニング拡張機能 (DMX) を使用できます[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)](加算、減算、乗算、および除算など)。  
  
 次の表は、DMX がサポートする算術演算子について示しています。  
  
|演算子|Description|  
|--------------|-----------------|  
|[+ (& a) #40 です。追加 (& a) #41;& # #40; DMX &#41;](../dmx/add-dmx.md)|2 つの数値を加算します。|  
|[-(& a) #40 です。減算 (& a) #41;& # #40; DMX &#41;](../dmx/subtract-dmx.md)|ある数値から別の数値を減算します。|  
|[&#42;です。&#40;です。乗算 (& a) #41;& # #40; DMX &#41;](../dmx/multiply-dmx.md)|ある数値を別の数値によって乗算します。|  
|[& # #40; 除算 &#41;& # #40; DMX &#41;](../dmx/divide-dmx.md)|ある数値を別の数値によって除算します。|  
  
 次のルールは、DMX 式内の算術演算子の優先順位の順序を判断します。  
  
-   式の中に複数の算術演算子がある場合、まず、乗算および除算が行われ、次に減算および加算が行われます。  
  
-   式の中の算術演算子の優先順位がすべて同じである場合は、左から右に計算されます。  
  
-   かっこの中の式は、他のどの演算子よりも優先されます。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [式 &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

