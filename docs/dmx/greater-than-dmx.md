---
title: '&gt;(より大きい)(DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 67ba5385ab11091ca45b50556fe63983fee01aac
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971700"
---
# <a name="gt-greater-than-dmx"></a>&gt;(より大きい)DMX
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  あるデータ マイニング拡張機能 (DMX) 式の値が他の DMX 式の値より大きいかどうかを判断する比較演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression > DMX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 ブール値。両方のパラメーターが null 以外で、最初のパラメーターの値が2番目のパラメーターの値よりも大きい場合に TRUE を格納します。 両方のパラメーターが null 以外で、最初のパラメーターの値が2番目のパラメーターの値以下である場合、ブール値には FALSE が含まれます。 ブール値には、いずれかのパラメーターまたは両方のパラメーターが null 値に評価される場合、null 値が含まれます。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;比較演算子](../dmx/operators-comparison.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
