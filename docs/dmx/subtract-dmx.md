---
title: '- (減算)(DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e15eba5f642d0506e7c23f0e5790d6867224f9a2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040450"
---
# <a name="--subtract-dmx"></a>- (減算) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つの数から別の数を減算する算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric_Expression - Numeric_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Numeric_Expression*  
 数値を返す有効なデータ マイニング拡張機能 (DMX) 式です。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>コメント  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 1 つの式が NULL 値に評価される場合、この演算子は、もう一方の式の結果を返します。  
  
## <a name="see-also"></a>参照  
 [算術演算子&#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
