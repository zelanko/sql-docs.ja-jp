---
title: = (等しい) (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- equal operator (=)
- = (equals operator)
ms.assetid: 6ac019b1-6373-4e2c-a1ad-fe2dc6188ac3
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c4f962dbda2fbd1c13725d64ddc9519d14cb9275
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="-equal-to-dmx"></a>= (等号) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  あるデータ マイニング拡張機能 (DMX) 式の値が他の DMX 式の値と等しいかどうかを判断する比較演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression = DMX_Expression   
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが NULL 以外であり、1 番目のパラメーターの値が 2 番目のパラメーターの値と等しい場合、TRUE を含むブール値です。 両方のパラメーターが NULL 以外であり、1 番目のパラメーターの値が 2 番目のパラメーターと等しくない場合、FALSE を含むブール値です。 どちらかまたは両方のパラメーターの結果が NULL 値の場合、NULL 値を含むブール値です。  
  
## <a name="see-also"></a>参照  
 [比較演算子&#40;DMX&#41;](../dmx/operators-comparison.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; 演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
