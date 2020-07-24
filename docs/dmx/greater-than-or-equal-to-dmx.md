---
title: '&gt;= (以上) (DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f4dfae8259c1ea9379500d426ce1c8ac22762068
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971660"
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (以上) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  あるデータ マイニング拡張機能 (DMX) 式の値が他の DMX 式の値以上かどうかを判断する比較演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが null 以外で、1番目のパラメーターの値が2番目のパラメーターの値以上の場合に TRUE を含むブール値です。 両方のパラメーターが NULL 以外であり、1 番目のパラメーターの値が 2 番目のパラメーターの値より小さい場合、FALSE を含むブール値です。 ブール値には、いずれかのパラメーターまたは両方のパラメーターが null 値に評価される場合、null 値が含まれます。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;比較演算子](../dmx/operators-comparison.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
