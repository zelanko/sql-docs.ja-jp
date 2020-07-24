---
title: '* 乗じる(DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3a8df192cc04741ca1136f0c89c46893e5463370
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971638"
---
# <a name="-multiply-dmx"></a>* (乗算) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  1つの数値を別の数値で乗算する算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Numeric_Expression*  
 数値を返す有効なデータマイニング拡張機能 (DMX) 式です。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>注釈  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 1 つの式が NULL 値と評価される場合は、NULL 値が返されます。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;算術演算子](../dmx/operators-arithmetic.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
