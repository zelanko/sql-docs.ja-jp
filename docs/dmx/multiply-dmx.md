---
title: '* (乗算)(DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f73e3e55045dd4ea9d4c2476540d2f7223d16eb0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62502076"
---
# <a name="-multiply-dmx"></a>* (乗算) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  別の数がその倍数 1 つの数値の算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Numeric_Expression*  
 数値の値を返す有効なデータ マイニング拡張機能 (DMX) 式。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>コメント  
 1 つの式は、その他の式のデータ型に暗黙的に変換できる必要がありますか、同じデータ型の両方の式があります。 1 つの式が NULL 値と評価される場合は、NULL 値が返されます。  
  
## <a name="see-also"></a>参照  
 [算術演算子&#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
