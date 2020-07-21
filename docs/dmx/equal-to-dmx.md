---
title: = (等しい) (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0633540153f2dd9dfd60831a58744ea2d6331fbd
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670289"
---
# <a name="-equal-to-dmx"></a>= (等号) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1つのデータマイニング拡張機能 (DMX) 式の値が、別の DMX 式の値と等しいかどうかを判断する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression = DMX_Expression   
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが NULL 以外であり、1 番目のパラメーターの値が 2 番目のパラメーターの値と等しい場合、TRUE を含むブール値です。 両方のパラメーターが null 以外で、最初のパラメーターの値が2番目のパラメーターの値と等しくない場合、ブール値には FALSE が含まれます。 ブール値には、いずれかのパラメーターまたは両方のパラメーターが null 値に評価される場合、null 値が含まれます。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;比較演算子](../dmx/operators-comparison.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
